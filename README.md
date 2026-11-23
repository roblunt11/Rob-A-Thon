# Marathon and Half Marathon Plan Builder

A small web app that turns your running level and a race date into a week-by-week marathon or half marathon training plan. View it on a calendar, then export it to an `.ics` file for Apple Calendar, Google Calendar or Outlook.

It is a single `index.html` file. There is no build step, no dependencies and no backend: everything runs in your browser and nothing is sent or stored anywhere.

## Features

- **Race distance:** marathon or half marathon.
- **Running level:** beginner, novice, intermediate or expert.
- **Runs per week:** 3, 4, 5 or 6.
- **Preferred long run day:** Sunday, Saturday, or let the planner choose.
- **Parkrun:** tick the box and parkrun becomes a fixed Saturday-morning run, counted as one of your runs each week. You can also add a run to and from the park and say how far it is each way, and the Saturday total is shown as you type.
- **Other sports:** add regular activities (for example 5-a-side football on Saturday mornings, or an hour of basketball on Wednesdays and Sundays). Those days are kept free of runs.
- **Calendar view:** month grid with colour-coded sessions. Click any day for the session details.
- **Week-by-week table:** phase, running distance and time spent on other sports for each week.
- **`.ics` export:** all-day events for every run and activity, with a description for each session.
- **Pace guidance (optional):** enter a recent race time or a goal marathon time and each session gets rough target paces.
- **Units:** kilometres or miles.

## Use it

Open `index.html` in any modern browser, or host it with GitHub Pages (below).

1. Choose your level, runs per week and long run day.
2. Pick your marathon date.
3. Optionally tick parkrun (and set your run to and from the park), and add other sports and the days you do them.
4. Select **Build my plan**.
5. Browse the calendar, then select **Download .ics** and import the file into your calendar app.

## Host it on GitHub Pages

1. Push `index.html` (and this README) to a repository.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, and save.
4. After a minute or two the app is live at `https://<your-username>.github.io/<repo-name>/`.

## How the plan is built

- **Length:** from the next Monday to race week. Marathon plans run up to 24 weeks (minimum 8) and half marathon plans up to 16 weeks (minimum 6). If your race is further away, the plan covers the final weeks before it.
- **Long run:** builds steadily from a starting distance to a peak before the taper.

  | Level | Marathon (start to peak) | Half marathon (start to peak) |
  | --- | --- | --- |
  | Beginner | 6 to 32 km | 5 to 16 km |
  | Novice | 10 to 32 km | 8 to 18 km |
  | Intermediate | 14 to 34 km | 10 to 20 km |
  | Expert | 18 to 35 km | 12 to 21 km |

- **Cutback weeks:** every fourth week during the build is reduced to 75% of the planned volume.
- **Taper:** marathon plans taper for two weeks (long runs at 65% then 45% of the peak). Half marathon plans taper for one week (long run at 70% of the peak). The other runs scale down with it.
- **Race week:** short shakeout runs, rest days, then the race on your chosen date.
- **Session types:** easy, tempo, intervals, medium-long and long runs. Lower levels get fewer hard sessions (beginners run easy plus a long run, novices add tempo runs, and intermediate and expert runners add intervals, with a medium-long run at six runs a week).
- **Parkrun:** parkrun takes Saturday and replaces one easy run, so the other runs are built around it. The long run stays on Sunday where possible, and the planner avoids a run or hard session on Friday. Parkrun is run easy to steady in most weeks, can be pushed a little on lighter cutback weeks, and is dropped from the final three days before your race. The run to and from the park is halved during taper weeks.
- **Scheduling around other sports:** run days are chosen from the days you are free. The planner avoids back-to-back runs where it can and keeps hard sessions away from the long run. If your other sports leave fewer free days than the runs per week you chose, it uses the days available and tells you. Other sports in the final three days before the race are left out of the calendar.

## Pace guidance

Paces are optional and are rough guidance only. They are not tailored to the individual runner. They combine two published methods:

- **Daniels' VDOT system** (Daniels and Gilbert, 1979 oxygen-cost equations) turns a race result or goal time into a fitness score, then into easy, tempo and interval paces. Easy running is set at roughly 60 to 70% of that score, tempo at about 88% and intervals at about 98%.
- **Riegel's endurance model** (1981), `T2 = T1 x (D2 / D1)^1.06`, is used as a cross-check when forecasting a marathon time from a shorter race. The app shows the range between the two methods and uses their average for race pace.
- **Goal time:** if you enter a goal finish time, that becomes your race pace and the training paces are set from it.

**Limits to be aware of:** the formulas ignore your training history, age, health, weather, terrain and how much marathon-specific training you have done. A marathon forecast from a 5K or 10K is often optimistic for a first marathon. Run easy days by feel, and slow down if you cannot hold a conversation. Adjust the paces as your fitness changes.

## Customise it

The plan settings live at the top of the `<script>` section in `index.html`:

- `RACES`: for each race distance, the plan length limits, taper and starting and peak long run distances for each level.
- `LEVELS`: which session types each level skips.
- `MIX`: the session types used for each number of runs per week.
- `TYPES`: session names, distance proportions and colours.

## Disclaimer

This is a generic training template, not personalised coaching or medical advice. If you have any health conditions or injuries, or you are new to running, speak to a doctor or qualified coach before starting a marathon programme. Adjust or skip sessions if something hurts.

## Licence

Released under the [MIT Licence](LICENSE). The software is provided as is, with no warranty. Training plans and paces are rough guidance only (see the disclaimer above).
