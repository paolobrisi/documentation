======
Stripe
======

`Stripe <https://stripe.com/>`_ is a United States-based online payment solution provider, allowing
businesses to accept **credit cards** and other payment methods.

Configuration
=============

.. seealso::
   - :ref:`payment_acquirers/add_new`

Credentials tab
---------------

On premise or on Odoo SH, Odoo needs your **API Credentials** to connect with your Stripe account,
which comprises:

- :ref:`Publishable Key <stripe/api_keys>`: The key solely used to identify the account with Stripe.
- :ref:`Secret Key <stripe/api_keys>`: The key to sign the merchant account with Stripe.
- :ref:`Webhook Signing Secret <stripe/webhook>`: When you enable your webhook on your Stripe
  account, this signing secret must be set to authenticate the messages sent from Stripe to Odoo.

You'll be able to easily create your account by using the **Connect Stripe** button. Once you come
back on your database from the onboarding :

1) Copy/paste your Publishable and Secret keys (see :ref:`below <stripe/api_keys>`);
2) Generate your webhook by clicking the **Generate your webhook** button.

On SaaS, click the button **Connect Stripe** and follow the Stripe Onboarding :

1) Fill the Stripe Onboarding information in order to create your account;
2) Stripe sends an email to validate your email address;
3) At the end of the process, you're redirected to Odoo. If you completed Stripe onboarding, you're
   all set and your acquirer is enabled.

.. note::
   On SaaS, it's also possible to set your own :ref:`API Keys <stripe/api_keys>`. You have to
   activate the :ref:`Debug Mode <developer-mode>` and go to the Stripe Acquirer form.

.. important::
   If you are trying Stripe as a test, in the **test mode**, change the **State** to *Test
   Mode*. We recommend doing this on a test Odoo database, rather than on your main database.

.. _stripe/api_keys:

Publishable and Secret keys
~~~~~~~~~~~~~~~~~~~~~~~~~~~

To retrieve the publishable and secret keys, follow this `link to your API keys
<https://dashboard.stripe.com/account/apikeys>`_, or log into your Stripe dashboard and go to
:menuselection:`Developers --> API Keys --> Standard Keys`.

.. _stripe/webhook:

Webhook Signing Secret
~~~~~~~~~~~~~~~~~~~~~~

To retrieve the webhook signing secret, you first need to create a webhook.

.. note::
   If your instance is up-to-date on version 15.0, simply click the button **Generate your Webhook**
   and you're all set.

To do so, follow this `link to your webhooks <https://dashboard.stripe.com/webhooks>`_, or log into
your Stripe dashboard and go to :menuselection:`Developers --> Webhooks`. Then, click on **Add
endpoint** in your **Hosted endpoints**. A form opens, where you'll need to add the following data:

- | In the **Endpoint URL**, enter your Odoo database's URL followed by ``/payment/stripe/webhook``.
  | For example: ``https://yourcompany.odoo.com/payment/stripe/webhook``
- At the end of the form, you can **Select events** to listen to. Click on it and, in the
  **Checkout** section, select **checkout.session.completed**.

.. note::
   It is possible to select other events, but they are currently not processed by Odoo.

When you click on **Add endpoint**, your Webhook is configured. You can then click on **reveal** to
display your signing secret.

Enable local payment methods
----------------------------

Local payment methods are payment methods that are only available for certain merchants and
customers countries and currencies.

To enable specific local payment methods with Stripe, list them as supported payment icons. To do
so, go to :menuselection:`Payment Acquirers --> Stripe --> Configuration` and add the desired
payment methods in the **Supported Payment Icons** field. If the desired payment method is already
listed, you don't have anything to do. If a payment icon record doesn't exist in the database, its
related payment method is considered enabled with Stripe.

.. image:: media/stripe_enable_local_payment_method.png
   :align: center
   :alt: Select and add icons of the payment methods you want to enable

.. seealso::
   - :doc:`../payment_acquirers`
