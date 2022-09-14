# API Key Usage

Here's the API Key Usage block:

![](../../.gitbook/assets/screenshot-nimbusweb.me-2022.06.30-18\_28\_23.png)

**Last Updated** - field that contains the date of purchase of the user's tariff plan and the name of the tariff plan.&#x20;

**Terms of use of the tariff plan:**

* The first day of the tariff starts at the time of its purchase, in the image above this time is 17:36;
* The end date and time of the tariff is set to the same date and time in a month, for the image above it will be 07.30.2022 17:56;
* The tariff plan does not last less than 30 days, that is, if you bought it on 02.15.2022 17:56, then it will end on 03.17.2022 17:56;
* The tariff can last 31 days if there are 31 days in the month in which it was purchased;
* Credits Today - the daily rate of credits at the current tariff, for example, for the screen above, the day began on 06.30.2022 17:56 and ends on 07.01.2022 17:56;
* Credits Yesterday - the daily rate of credits at the current tariff, for example, for the screen above, this parameter will contain credits for the time period 06.30.2022 17:56 - 07.01.2022 17:56;
* Crefidts This Month - the total number of credits provided under this user tariff;
* Credits Last Month - the number of credits used by the user during the previous tariff used. Moreover, it is important to understand that if a user bought one tariff, then, for example, a day later he bought a second tariff and a day later bought a third tariff, then this parameter will contain credits used during the second tariff.

&#x20; **Credit period:**

* At the end of the month or at the end of all credits on the last day of the month, we extend the current plan for another week on credit:\


![](../../.gitbook/assets/screenshot-nimbusweb.me-2022.06.30-19\_37\_08.png)

* If the user does not pay for a new plan during the credit or does not pay for the plan that has already been installed, then the current plan is blocked, the user can no longer use credits using his API keys:

![](../../.gitbook/assets/screenshot-nimbusweb.me-2022.06.30-19\_51\_37.png)

* All credits spent during the credit period will be deducted in the new user plan. As an example, a new plan was bought after 4 credits were spent during the credit period, therefore 4 credits are deducted in the "Credits This Month" parameter:

![](../../.gitbook/assets/screenshot-nimbusweb.me-2022.07.01-11\_17\_31.png)

* During the credit period, the user cannot switch to the Basic plan;
* The user receives a series of e-mail notifications before and after the credit period:\
  \- 5 days before plan ends;\
  \- 1 day before the end of the plan;\
  \- first day of the credit;\
  \- the last day of the plan.

**Buy Credits**

You can buy additional credits to your current plan. Clicking on the text "Need more? Buy credits" opens a modal form for selecting the required number of credits:

![](../../.gitbook/assets/screenshot-nimbusweb.me-2022.07.01-16\_53\_28.png)

After clicking on the "Buy credit" button, it opens a payment widget for payment in cryptocurrency:

![](../../.gitbook/assets/screenshot-nimbusweb.me-2022.07.01-17\_07\_13.png)

After the purchase, additional credits are added to the current plan, in the example, an additional package was purchased for 1 000 000 credits Requests/Day:

![](../../.gitbook/assets/screenshot-nimbusweb.me-2022.07.01-17\_33\_02.png)

The expiration date of the add-on package is tied to the expiration date of the plan during which it was purchased.

{% hint style="info" %}
The user can purchase additional packages during the credit period. When the credit ends, the additional package is suspended. When a user purchases a plan, those additional packages purchased at the time of the credit will be associated with the new plan. For an additional package in the new plan, those days that were used during the credit period are deducted.
{% endhint %}
