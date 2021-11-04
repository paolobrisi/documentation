===============================================
Connect a Worldline Payment Terminal to the PoS
===============================================

Connecting a payment terminal allows you to offer a fluid payment flow to your customers and ease
the work of your cashiers.

.. note::
   Please note that Worldline is currently only available in Belgium.

Configuration
=============

Connect an IoT Box
------------------

Connecting a Worldline Payment Terminal to Odoo is a feature that requires an IoT Box. For more
information on how to connect one to your database, please refer to the
:doc:`IoT documentation </applications/productivity/iot/config/connect>`.

Configure the protocol
----------------------

From your terminal, click on :menuselection:`"." --> 3 --> stop --> 3 --> 0 --> 9 -->
enter the technician password "1235789" --> OK --> 4 --> 2`. Then, click on :menuselection:`Modifier
--> CTEP (as Protocole ECR) --> OK`. Click on **OK** thrice on the next screens
(*CTEP ticket caisse*, *Largeur ticket caisse* and *Jeu de caractères ISO*). Finally, click on
**Stop** three times; the terminal automatically restarts.

.. seealso::
   Here are some useful :ref:`tips tips<worldline/yomani-info>`.

Set the IP address
------------------

From your terminal, click on :menuselection:`"." --> 3 --> stop --> 3 --> 0 --> 9 --> enter the
technician password "1235789" --> OK --> 4 --> 9`. Then, click on :menuselection:`Modifier -->
TCP/IP (after "Configuration caisse") --> OK --> OK` (*TCP Configuration client* screen).

Finally, set up the hostname and port number.

Hostname (*Nom de l'hôte on your terminal*)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To set up the hostname, enter your IoT box's IP address' sequence numbers and press **OK** at each
"." until you reach the colon symbol.

.. admonition:: Example

   | For example, here's an IP address sequence: `10.30.19.4:8069`.
   | On the "Nom de l'hôte" screen, type :menuselection:`10 --> OK --> 30 --> OK --> 19 --> OK --> 4
     --> OK --> leave empty --> OK`.

.. note::
   Your IoT box's IP address is available in your IoT Box application's database.

Port number (*Numéro de port* on your terminal)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

After "Numéro de port", enter :menuselection:`"9001" --> OK` (*Protocole ECR SSL non*)
:menuselection:`--> OK`. Click on **Stop** three times; the terminal automatically restarts.

Configure the payment method
----------------------------

From the Point of Sale application, go to the :menuselection:`Configuration --> Settings -->
Payment terminals` and activate the *Worldline* payment terminal.

.. image:: worldline/worldline-payment-terminals.png
   :align: center

Then, go to :menuselection:`Configuration --> Payment methods`. Create a new payment method for
Worldline. Select the payment terminal *Worldline* and your payment terminal device on your Payment
Method form.

.. _worldline/yomani-info:

.. tip::
   - Technician password: `1235789`
   - To reach Wordline's technical assistance, call `02 727 61 11` and choose
     :menuselection:`commerçant --> assistance technique`.
   - Configure the cashier terminal if you have both a customer and a cashier terminal.
   - To avoid blocking the terminal, check the initial configuration beforehand.
   - Set a fixed IP to your IoT Box’s router to prevent losing the connexion.

Pay with a payment terminal
===========================

When processing a payment, select your Worldline payment method. Check the amount and click on
*Send*. When the payment is successful, the status changes to *Payment Successful*.

Once your payment is processed, the type of card used and the transaction ID appear on the payment
record.

.. image:: worldline/worldline-payment.png
   :align: center

.. note::
   * In case of connexion issues between Odoo and the payment terminal, force the payment by
     clicking on *Force Done*, which allows you to validate the order.
     This option will only be available after receiving an error message informing you that the
     connection failed.
   * To cancel the payment request, click on **cancel**.


