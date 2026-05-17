## Project Overview

The app that I have been working on is a prototype intended to become/be expanded into an e-commerce web application for North Seattle College, designed to showcase and sell official apparel, accessories, and branded merchandise. The project aims to solve a common problem for college campuses: providing students and staff with a convenient, modern way to browse and purchase school merchandise online, with a streamlined pickup process to be implemented later on (likely by another team).

This is a multi-phase capstone project with the goal of creating a functional prototype that could be handed off to future development teams for production deployment. The current phase focuses on core shopping functionality like browsing products, viewing details, selecting variants, and managing a cart.

Here's a brief demo of the current state:

https://github.com/user-attachments/assets/0068e455-36aa-4d71-aede-62e962e503ff

Subsequent work involves incorporating a checkout process (view cart and checkout, likely simulating transactions w/ stripe test mode), and proper profile management (like admins for editing inventory).

## My Role

I serve as the Tech Lead on a team of three developers (Jay, Tinisha, and myself) and one/two business consultants from the business cohort. My responsibilities include making architectural decisions, setting up the development infrastructure, implementing core features, and ensuring code quality through testing. I also coordinate with teammates on component assignments.

## Work Completed

Over the first five weeks of the project, I helped establish the technical foundation and building out the primary user-facing features.

During the initial weeks, I also helped research and finalize the tech stack. After evaluating options, the team selected React 19 with Vite for the frontend, Mantine UI for the component library, Supabase for the backend (PostgreSQL database, authentication, and REST API), and Cypress for end-to-end testing. This stack was chosen to balance modern tooling with ease of handoff to future teams.

The Supabase database schema was designed with tables for products, product variants, cart items, orders, order items, and user profiles. A key design decision was implementing a product variants system that tracks inventory by size and color combinations, each with its own SKU. This allows for accurate stock tracking at the variant level rather than just the product level.

<img width="1049" height="784" alt="db schema" src="https://github.com/user-attachments/assets/1d189213-fc7e-43cf-ac07-a8e65be8d339" />

On the frontend, I helped build the Home page with a responsive product grid using Mantine's SimpleGrid component. Each ProductCard displays the product image, category, name, price, and an "Out of Stock" badge when all variants have zero inventory. The ProductView page was also implemented, which displays full product details including a gallery, variant selectors for size and color, stock indicators, and an Add to Cart button. The page pulls product information from the database and shows related products from the same category.

React Router was set up for client-side navigation between pages. One recent challenge was ensuring that navigating between products via the "You May Also Like" section properly reset the component state. This was solved using React's key prop pattern, which forces a full remount when the product ID changes. I thought this was a cleaner approach than manually resetting state in useEffect.

For testing, comprehensive Cypress end-to-end tests were written for both the Home page and ProductView page. The tests cover product display, variant selection, stock indicators, and navigation. Detailed comments were added throughout the test files to help teammates (or future teams) who are new to Cypress understand the syntax and patterns.

## Challenges and Solutions

One challenge was designing the stock indicator logic. After getting an idea for how real e-commerce sites might handle this, I decided on a tiered approach: the Home page only shows a badge when a product is completely out of stock (all variants at zero), while the ProductView page shows specific warnings like "Only 3 left" for the selected variant.

Testing also presented hurdles. Cypress runs faster than React renders, which caused flaky tests when checking UI state immediately after interactions. The solution was to wait for specific elements to appear before asserting, and in some cases, to test outcomes (like SKU changes) rather than visual state (like button highlighting).

## Key Learnings

On the technical side, this project deepened my understanding of React patterns, particularly around derived state with useMemo, component remounting with keys, and structuring service files for database operations.

Perhaps the most valuable learning was about writing code for handoff. Knowing that future teams may inherit this codebase pushed me to prioritize clarity and consistency over just getting things working. Weekly status reports also helped me reflect on progress and improve my ability to estimate work and communicate with the team.
