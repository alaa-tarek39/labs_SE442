# Lab 1 · Lifecycle findings

Pair:ALaa Tarek Ali

Device: [Your Android phone model], Android [Version] (API [Level])

.NET / MAUI: .NET 10, MAUI [Installed Version]

## Event table

| # | Action | Events seen, in order | Count kept? | Notes |
|---|---|---|---|---|
| 1 | Home, then back from Recents | 21:16:44:998 | Yes (3) | The counter value remained unchanged after returning to the app. |
| 2 | Rotate and rotate back | 21:19:23:044 | Yes (3) | The counter value remained unchanged after rotation. |
| 3 | Open another app, then back | 21:21:15:630 | Yes (3) | The counter value remained unchanged after switching apps. |
| 4 | Swipe away from Recents | 21:21:56:502| No (0) | The counter reset to zero after reopening the application. Destroying: [Yes]. |
|

## Interpretation

The counter value remained unchanged when the application was sent to the background, rotated, or when switching to another application.

However, after swiping the application away and reopening it, the counter reset to zero.

This shows that data stored only in memory may be lost when the application is restarted.

## Where we would save a draft

We would save in Deactivated and Stopped because these events indicate that the application is moving away from the foreground or becoming inactive. Saving important data at these points helps protect the user's work before the operating system may terminate the application.

## Destroying is a poor choice

Destroying is a poor choice because it is not guaranteed to occur before the application process is terminated.

In row 4, the counter reset to zero after reopening the application. This demonstrates why important data should be saved earlier instead of relying only on the Destroying event.

## Constraint link

Memory is a limited resource shared by applications. Android may terminate background processes when memory is under pressure.

Therefore, the application should save important data before it is terminated to prevent losing the user's work.

## Surprises

One surprising result was that the counter remained unchanged during Home, rotation, and switching between applications, but reset to zero after swiping the application away and reopening it.

## Generated or external code

None.
