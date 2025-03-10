# Getting HogPilled: how to win with PostHog

Most startups fail, and most startups that win do it by accident. 

We can do better.

A strong approach to product analytics lets us **win on purpose**. We define success as a number we can measure, then describe the user behavior that feeds that number.

This allows us to track if a product is meeting its business goals over time, and use that information to iterate into more impact for customers and profitability for ourselves.

Here's how.

# North Star metric

We start with a number that represents the health of our immediate goals.

It's not going to be revenue.

Instead, we want to count something that's a **precursor to revenue**. Something where, if it doesn't happen, we don't have a business. Examples from businesses you've heard of:

**Facebook**: Daily active users  
**Airbnb**: Nights booked  
**Uber**: Number of rides

See how easy it is to understand these numbers? A good North Star is measurable and easy to communicate. Everyone on the team, no matter their role, grasps their relationship to it.

If you're *super* early, you could start with a metric like signups: how many people care enough to try your product?

## Our North Star

<img alt="pencil" height=75 align=right src="https://github.com/user-attachments/assets/d805b1c4-c11e-4e14-a29d-97f5f7493049"/>

Right now, traction for our business looks like `[Traction goal]`

We can't get there without growth in `[North Star metric]`, so that's what we'll measure to determine success.

# Defining our v0 metrics tree

With a North Star in mind, we can back out to the **user behavior** that feeds it.

<img height="700" alt="abstract-metrics-tree" src="https://github.com/user-attachments/assets/3d8bb8c5-9398-470e-b36d-8970a7267a49" />

**Events** are things that users do that we can track in code, and then measure across all usage of the product.

## Example: ride sharing

Uber can't make money if no one launches the app. `app_launched`, then, becomes, an essential event for them keep track of.

But there's still no money until `ride_requested` happens.

Even that doesn't quite get us to a ride. We need a couple more: `ride_accepted`  and `ride_began`

<img width="1688" alt="ride-sharing-metrics-tree" src="https://github.com/user-attachments/assets/fc799eaa-db34-4669-9833-9b971ae22640" />

It's these events *together* that give us a picture of how people use the product to get a ride. While counting only `ride_began` would give us enough to measure our North Star, it would *not* be enough to learn how to influence it.

## Funnels

<img height="500" alt="ride-sharing-funnel" src="https://github.com/user-attachments/assets/08800bb0-2ce6-4406-8e36-2c7e69314258" />

Because events often happen in a predictable sequence, we can use that sequence to learn if users are getting stuck or bailing out.

This is called a **funnel**.

Funnels are simple: they measure successful progress between events. More people will launch the app than start a ride, but you still want to maximize the progress from one to the other. A funnel lets you understand how well that's going.

If there's a sharp drop between, say, accepting a ride and starting one, that could point to an issue that needs to be fixed in the product.

Funnels give us the information we need to diagnose problems and measure the impact of new solutions. We'll want to make sure we capture just enough event data to measure the critical path between starting in our product and succeeding with it.

## Our metrics tree

So: to define the path between a user starting in our product and then taking the actions that move our North Star up and to the right, let's list some necessary events.

<img alt="pencil" height=75 align=right src="https://github.com/user-attachments/assets/d805b1c4-c11e-4e14-a29d-97f5f7493049"/>

**Traction:** `[Traction goal]`

**North Star metric:** `[North Star metric]`  

**3-5 events that drive this metric:**

- [Event]  
- [Event]  
- [Event]

# Integration planning

Now:

- We know what we're measuring  
- We know why we're measuring it  
- We know what events lead to the outcome we want

With these details in-hand, we can make a plan to capture the data we need. This data collection will help us understand how users interact with our product, and how well our product meets our goals.

Ideal event names are self-explanatory. Don't stuff data into event names – they should be **comparable across all users** of your product. Instead, we want to tuck additional data into properties *on* events.

## Identifying users

<img alt="pencil" height=75 align=right src="https://github.com/user-attachments/assets/d805b1c4-c11e-4e14-a29d-97f5f7493049"/>


| `Unique ID` | `Where/when to call identify()` | `Properties to attach` |
| :---- | :---- | :---- |
|[identifier]|  |  |

*Unique ID: Ideally, an ID from your database that won't change, but you can use something else, like an email address, if that's not feasible*

*Typically `identify()` is called in the client, but some architectures, like SSR web apps, will call it on the server*

## First round of events to capture

<img alt="pencil" height=75 align=right src="https://github.com/user-attachments/assets/d805b1c4-c11e-4e14-a29d-97f5f7493049"/>


| `Event name` | `Server or client?` | `Properties to attach` |
| :---- | :---- | :---- |
| `event_name` |  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |

## Integration references

For more detail on PostHog's data model, identifying users, and general integration guidance, check out our docs:

- [PostHog data model](https://posthog.com/docs/how-posthog-works/data-model)  
- [Identifying users](https://posthog.com/docs/getting-started/identify-users)  
- [Event tracking](https://posthog.com/tutorials/event-tracking-guide)  
- [SDKs](https://posthog.com/docs/libraries)  
- [Framework guides](https://posthog.com/docs/frameworks)

## Gotchas

Integration is straightforward, but things can get messier as time goes on. Here are a few things to watch out for.

### Event naming

Pick a [naming convention](https://posthog.com/docs/product-analytics/best-practices#3-implement-a-naming-convention) and stick with it\! There isn't a right choice here, only a wrong choice: different people on your team using different event names or conventions to describe the same behavior.

Be warned: PostHog's event storage is 'write only' for all practical purposes. You can't edit existing events, so it's important to design against naming drift. Otherwise, you may find queries much harder to work with down the road. 

### User identity

Complex authentication flows and tracking anonymous users from both client and server can complicate identifying users.

PostHog enforces some rules use of the identify function to prevent users from being merged incorrectly. Learn more about [Alias](https://posthog.com/docs/product-analytics/identify#alias-assigning-multiple-distinct-ids-to-the-same-user) if you intend to provide more than one of your own IDs for a user, or you need to merge identities on the server.


# Next steps

Next, let's make a plan to measure:

- [How many users are getting value from your product after signup](2-tracking%20activation.md)  
- [How many users stick around over time](3-measuring%20retention.md)

## Further reading

- [Finding your North Star metric and why it matters](https://posthog.com/founders/north-star-metrics)

