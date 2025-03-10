# Tracking activations: getting the most out of your PostHog integration

We've got the basics of our PostHog integration up and rolling.

Next we need to define and track the behavior that indicates a user is actually getting something from our product.

We call this **activation**: once someone passes this threshold, they're likely to keep coming back, building their skills and otherwise making progress with us. If someone *does not* pass this threshold, they still don't know why we're valuable.

Like our North Star, we want to think about activation as a precursor to revenue. What steps must someone take in our product to reach the point where they would be happy to pay for it, understanding the value it provides?

Just because someone has signed up or logged in doesn't mean they're *using* our tools. That's where measuring activation comes in.

Once we know how many people do or don't activate, we can adjust our product design to influence that number.

# Activation by example

Let's talk through a few cases of activation you might have seen yourself:

For **Dropbox**, activation was simple: a user who stored one file within the first week was likely to become a long-term customer. Seeing your files sync so seamlessly is persuasive, and likely sparks more ideas about how to use the product. If you never get there, you don't understand the value firsthand.

In **Uber's** case, activation was taking a first ride. Once you understand the simplicity of pushing a button and receiving transportation, you'll likely do it again.

Some products have wide variability in how they get used, like **Pinterest**. Rather than focus on a specific behavior, they counted activation according to the number of days within a month someone used the product. Anything more than four counted as activation.

Quantity is a totally reasonable factor in activation! For **PostHog's** session replay product, we count activation as anyone who has watched at least five replays. Just looking at one or two is more like kicking the tires.

Activation looks different for every product. It can be expressed as a quantity of events, or even as a composite of multiple events.

# Activation worksheet

So let's think about activation for our product. What event or events correspond to seriously *getting* what we do and cementing why a customer would want to keep using us?

## For us, activation looks like...

<img alt="pencil" height=75 align=right src="https://github.com/user-attachments/assets/d805b1c4-c11e-4e14-a29d-97f5f7493049"/>


[Document activation behavior here. If you're not yet certain, a hypothesis is fine.]

## Activation events

<img alt="pencil" height=75 align=right src="https://github.com/user-attachments/assets/d805b1c4-c11e-4e14-a29d-97f5f7493049"/>


| `Activation event` | `Quantity (optional)` | `Timeframe (optional)` | `Already tracking?` |
| :---- | :---- | :---- | :---- |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |

# Tracking activation

With the product emitting events we need to measure activation, we can create a new **insight** to provide ongoing measurement and reporting.  

![funnel](https://github.com/user-attachments/assets/57a51d39-4a19-44d4-9693-9c71856bb502)

One good way to start is to use a **funnel**. This will show you progression from the total population of users – people who have logged in, say – toward the events that represent your activation. You'll see the percentage of dropoff for each step, and this will give you something to chip away at with your product design.

Each step in a funnel can be finely constrained using filters, so you're measuring exactly the behavior that you described in the above worksheet.

Learn more: [Funnel documentation](https://posthog.com/docs/product-analytics/funnels).

Once your funnel is created, add it to your project's [dashboard](https://posthog.com/docs/product-analytics/dashboards). 

## Advanced activation tracking

If you have a more complex activation sequence, where the intermediate steps could happen in any order, you may need to write a custom query. This post [on how we found our activation metric](https://posthog.com/product-engineers/activation-metrics) walks through the thinking and the queries behind this approach.

# Next steps

With event data ingesting reliably into PostHog, and a clear sense of your activation criteria now reporting for your team, it's time to think about **retention**: how many of your users *continue using your product.*

## Additional reading

- [WTF is activation and why should engineers care?](https://posthog.com/newsletter/wtf-is-activation)  
- [Experiments](https://posthog.com/experiments): test out product variations and measure the results

