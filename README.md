
# Stripe Integration for Django eCommerce

This Django application provides seamless integration with Stripe for handling payments in an eCommerce platform. It includes views for listing products, displaying product details, creating Stripe checkout sessions, handling webhooks, and displaying success/cancel pages.

## Getting Started

1. Install the required dependencies using:

   ```bash
   pip install stripe
   ```
2. Set up your Django project and add the following settings to your `settings.py`:

   ```python
   # settings.py

   # Stripe API keys
   STRIPE_SECRET_KEY = 'your_stripe_secret_key'
   STRIPE_WEBHOOK_SECRET = 'your_stripe_webhook_secret'

   # URLs for success and cancel pages
   PAYMENT_SUCCESS_URL = 'your_success_url'
   PAYMENT_CANCEL_URL = 'your_cancel_url'

   # Domain for product image URLs
   BACKEND_DOMAIN = 'your_backend_domain'
   ```
3. Include the app in your `INSTALLED_APPS`:

   ```python
   # settings.py

   INSTALLED_APPS = [
       # ...
       'yourapp',
   ]
   ```

## Usage

### Views

1. **Product List View:**

   - URL: `/products/`
   - Displays a list of available products.
2. **Product Detail View:**

   - URL: `/products/<product_id>/`
   - Shows detailed information about a specific product, including available prices.
3. **Create Stripe Checkout Session View:**

   - URL: `/create-checkout-session/<pk>/`
   - Creates a checkout session for the selected product price and redirects the user to the Stripe checkout page.
4. **Stripe Webhook View:**

   - URL: `/webhook/`
   - Handles Stripe webhook events, specifically `checkout.session.completed`. Sends a confirmation email to the customer and updates the payment status.
5. **Success View:**

   - URL: `/success/`
   - Displays a success page after a successful payment.
6. **Cancel View:**

   - URL: `/cancel/`
   - Displays a page when the user cancels the payment.

### Models

1. **Product:**

   - Represents a product with attributes like name, description, quantity, and URL.
2. **Price:**

   - Represents the price of a product.
3. **PaymentHistory:**

   - Records payment history, including email, product, and payment status.

## Important Notes

- Ensure that you have set up your Stripe account and obtained the necessary API keys.
- Properly configure your webhook secret to handle events securely.
- Customize email content and sender in the `StripeWebhookView` to match your application's needs.

## Contributing

Feel free to contribute to this project by opening issues or submitting pull requests. Your feedback is highly appreciated!

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.
