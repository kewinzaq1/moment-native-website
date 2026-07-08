# Moment Capacitor App Blueprint

## Product promise

Moment is an intention interrupt, not a meditation library.

The user sets one intention, sees it repeatedly during the day, and takes a 60-second box-breathing break before falling back into autopilot.

## V1 principles

- One intention at a time.
- One breathing technique: box breathing.
- One primary action: start the minute.
- Local-first by default.
- No account in v1.
- No analytics in v1 unless explicitly added later with a privacy story.
- No streaks, feeds, courses, badges, or content library.

## App flow

1. Onboarding
   - Ask for the user's first intention.
   - Ask for reminder rhythm: light, steady, relentless.
   - Ask for quiet hours.
   - Ask for notification permission only after explaining the reminder promise.

2. Home
   - Show today's intention.
   - Show one primary button: Start minute.
   - Secondary actions: edit intention, reminder settings.

3. One-minute session
   - 4-second inhale.
   - 4-second hold.
   - 4-second exhale.
   - 4-second hold.
   - Repeat for roughly one minute.
   - Use haptics at phase changes if available.

4. Completion
   - Quiet confirmation.
   - Optional one-line note.
   - Return user to life.

## Suggested technical stack

- React + Vite for the UI.
- Capacitor for iOS/Android packaging.
- Capacitor Local Notifications for on-device reminder scheduling.
- Capacitor Haptics for breathing phase cues.
- Capacitor Preferences or SQLite for local state.
- TanStack Query only after a backend exists.
- Express only after accounts, syncing, or remote push become necessary.

## Data model

```ts
type Intention = {
  id: string;
  text: string;
  createdAt: string;
  archivedAt?: string;
};

type ReminderSettings = {
  rhythm: "light" | "steady" | "relentless";
  quietHoursStart: string;
  quietHoursEnd: string;
  enabled: boolean;
};

type MinuteSession = {
  id: string;
  intentionId: string;
  startedAt: string;
  completedAt?: string;
  note?: string;
};
```

## Reminder rhythm

- Light: 3 reminders per day.
- Steady: 6 reminders per day.
- Relentless: 10 reminders per day.

Avoid exact same times every day. Use a small random offset so reminders feel alive, not robotic.

## First implementation milestones

1. Static landing page.
2. React prototype of onboarding, home, breathing session, completion.
3. Capacitor shell with local persistence.
4. Local notification scheduling.
5. Haptics.
6. Android/iOS widget exploration.
7. Optional backend only if remote push or syncing becomes necessary.

## Hard no list

- No meditation catalog.
- No creator content.
- No public profiles.
- No streak-first habit loop.
- No dashboard as the main screen.
- No "optimize your life" language.

## Core copy

Moment helps you remember what you already know.

Set one intention. See it throughout the day. Take one minute to come back.
