## Project Overview

Leap is a prototype e-commerce platform designed for colleges and student organizations to sell branded merchandise and generate funding. The intention is for student organizations to potentially take this foundation, swap in their own branding and products, and have a functional online store. The project demonstrates product browsing, variant selection, cart management, secure checkout with Stripe, and order history tracking.

<img width="30%" alt="step-1" src="https://github.com/user-attachments/assets/84923104-d513-456d-9a81-43558caad505" />
<img width="30%" alt="step-2" src="https://github.com/user-attachments/assets/3b18c5cf-c7e7-441e-939f-1bfcee3183aa" />
<img width="30%" alt="step-3" src="https://github.com/user-attachments/assets/54e787e4-0095-4ed0-8cd2-987ce6986c75" />
<img width="30%" alt="step-4" src="https://github.com/user-attachments/assets/1591b580-4f31-4f30-b87d-039c290e66f6" />
<img width="30%" alt="step-5" src="https://github.com/user-attachments/assets/0b1c5fd5-0e50-49d4-b31f-e28a74a18ca2" />

## My Role

I serve as the Tech Lead on a team of three developers (Jay Arends, Tinisha Davis, and myself) and two business consultants (London Marroquin and Phay) from the business cohort. My responsibilities include making architectural decisions, implementing core features, and ensuring code quality through testing.

## Work Completed

Weeks 7-10 focused on completing the checkout flow, polishing the user interface, and finalizing documentation.

**Payment Integration**

Stripe was integrated for secure payment processing using test mode. A Supabase Edge Function (`create-payment-intent`) handles server-side payment creation, keeping sensitive keys secure. On successful payment, the system creates an order record, saves cart items as order items, and decrements inventory for each purchased variant.

**Order Management**

An OrderConfirmation page displays a success message with order details. The OrderHistory page shows all past orders with product images, variant details, quantities, prices, status badges, and timestamps.

**Cart Functionality**

The CartSidebar was enhanced with quantity controls for adjusting or removing items. A cart indicator badge was added to the Navbar showing item count, updating in real-time. The CartCard component displays product name, unit price, line total (when quantity exceeds one), and variant details.

**UI Theming**

A centralized color theming system was implemented using CSS variables paired with a custom Mantine theme. The "forest" color palette provides consistent styling across all components with documentation comments explaining the setup. Changing the entire site's look requires updating just a few values.

**Testing**

The Cypress test suite was expanded to 42 end-to-end tests covering Home, ProductView, CartSidebar, CategoryFilter, SearchBar, Checkout, Navbar, and OrderHistory. CI/CD runs all tests automatically on pull requests via GitHub Actions.

**Admin Page**

A mock Admin dashboard was added with tabs for Overview, Products, Users, and Settings. The Products tab displays real product data with simulated edit and delete actions that only affect what's shown on screen. This showcases what an administrative interface could look like without risking actual data changes.

<img width="30%" alt="admin-1" src="https://github.com/user-attachments/assets/cd06b9d8-adea-49bf-8e5c-bea9d01e9d94" />
<img width="30%" alt="admin-2" src="https://github.com/user-attachments/assets/148f58f5-dda3-4472-aaac-741733e6feb6" />
<img width="30%" alt="admin-3" src="https://github.com/user-attachments/assets/8a89aff1-40d7-4644-9df6-19372730944f" />
<img width="30%" alt="admin-4" src="https://github.com/user-attachments/assets/43312244-3254-4120-bb98-2b7151b4acff" />

## Challenges and Solutions

**Stripe Integration**

Integrating Stripe required keeping sensitive keys on the server while the frontend handles the payment form. The Edge Function approach solved this cleanly. Getting CORS and error handling right took debugging, but the final setup follows Stripe's recommended patterns.

**Theming Across Two Systems**

Mantine components need colors defined in JavaScript, while inline styles use CSS variables. Rather than overcomplicating things, I documented the intentional duplication and added comments explaining that both files need to be updated together.

**Flaky Tests**

Some Cypress tests failed randomly because they ran faster than React could update the screen. The fix was adding waits for animations to complete before checking results.

## Key Learnings

This phase taught me how payment security works in practice: why secret keys stay on the server, how payment intents flow between client and server, and how to handle confirmations.<img width="2852" height="1854" alt="1" src="https://github.com/user-attachments/assets/bd5cc247-a25f-4224-95b2-5fa904d80978" />
