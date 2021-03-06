# Building Bots

**⚠️ This guide is not financial advice and is for educational purposes only ⚠️**

Let's take a brief moment to go over the Manta Trader Bot Building Editor. Below is the most basic view you will see when you press _New Bot_ from the dashboard menu: ![editor](https://github.com/Manta-AI/Manta-Docs/raw/master/src/imgs/editor.png)

The strategy box is the place in which you will define the criteria for how your bot will trade. To begin, press _Add IF_. This will greet you with a menu where you can select an initial trigger that will start your strategy.

The first thing you must do is select the type of security to trade. For this example, we'll be creating a basic stock bot that trades TSLA. If you want to dynamically scan for stocks to trade based on filters, have a look at our Scanning Documentation \(coming soon\).

Next, select some kind of initial trigger. **If you want to start with a technical analysis indicator as your initial trigger**, select _At Any Time_. This trigger will always trigger true and advance to the next condition. For this tutorial, we have selected the trigger that monitors if a stock has been gapping up over the previous _n_ periods.

![trigger](https://github.com/Manta-AI/Manta-Docs/raw/master/src/imgs/trigger.png)

Clicking _Add IF_ will add this to the flow of our bot:

![triggeradded](https://github.com/Manta-AI/Manta-Docs/raw/master/src/imgs/triggeradded.png)

We can now add another _IF_ statement, a technical indicator, or an action. For this guide, we will first add a technical indicator by pressing _Add INDICATOR_, we'll select a Simple Moving Average Indicator and set its period to 14.

Notice now, that you'll have two options, _Add AND_ and _Add OR_. If you select _Add AND_ this technical indicator will be reliant on the previous indicator in order to advance. However, if you select _Add OR_, if either our SMA or our gapping up trigger is satisfied, it will cause the bot to make the subsequent action. We'll select _Add AND_ and use this SMA as a confirmation of an upward trend.

Next, after the uptrend is confirmed we should buy into the security. We can do this by adding a _THEN_ statement. This is done by pressing _Add THEN_.

![trigger and action](https://github.com/Manta-AI/Manta-Docs/raw/master/src/imgs/triggerandaction.png)

Our bot can now buy into TSLA when it detects an uptrend. However, what happens when we start making money on the position, or start losing? We will set our sell conditions to either sell out if we hit a 2% stoploss, but also sell if we reach a 4% profit level. That way, even if the strategy has a 50% win rate, profit will still be realized. We can do this by:

* Adding an _IF_ condition to check if we have an unrealized 2% loss
* Adding an _OR IF_ condition to check if the current position has increased 4% 
* Adding a _THEN_ trigger to sell our position if either of the previous conditions have been met. 

![completed flow](https://github.com/Manta-AI/Manta-Docs/raw/master/src/imgs/completedflow.png)

Now the logic of our strategy is complete. To conclude this tutorial, we will give the strategy a name that we can identify later and select the time you want the bot to trade.

If you want the bot to only trade during early market volatility, you can set the times here. Otherwise, your bot will automatically only trade during market hours.

Lastly, set the time interval for your bot to trade. If you set your bot to _1 Minute_ then every 60 seconds your bot will pull new data and check if the conditions for the current trigger or action are met.

When you have done these items, you're ready to press _Create Bot_ and move on to [back testing](https://github.com/Manta-AI/Manta-Docs/blob/master/pages/backtesting.md)!

