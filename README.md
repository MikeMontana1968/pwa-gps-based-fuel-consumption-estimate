# pwa-gps-based-fuel-consumption-estimate
Prompted thru ClaudeAI to (naively) estimate fuel consumption by integrating GPS supplied speed once a minute.

Code is all Claude (!)

Goal: Estimate fuel consumption by simply adding up average speed over a time period and dividing it out based on 45mpg Highway, 38mpg City. And do this on a mobile platform without having to go through a tedious iOS/Android development path. And not go through the dance of manually sideloading an APK. I just wanted to explore the idea.

When you start the app, it will ask for GPS permission - which is the whole point here. Say Yes.

Then at the bottom you can set your estimated MPGs for Highway/City. 

It doesnt do anything about fuel consumption at idle. Its dumb that way - just exploring an idea.

