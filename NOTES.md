# Notes for contributors

## table_of_contents.yaml

Each of the items in the `days` array is expected to be a prefix to what
could be multiple videos. This is how we handle separate QA videos, and
how we'll be able to be programmatic about days with multiple videos or
specials with multiple segments in the future.  So if there's a category
like this:

     - title: Intro to C
       folder: intro-to-c
       description: >
          This is the intro to C week.
       days: [day1, day2, day3, day4, day5]

Then day1 will slurp up `day1.html.md` and `day1qa.html.md`.  Likewise,
if Casey adds a followup to his emacs video, we can just drop a file 
in the misc folder called "emacs_2_emacs_harder.html.md" and everything
will just work with no changes needed to any index files since there's
already an emacs category ready to go.

In instances where the day name could be ambigious (for instance, day1
of C week could accidentally match day100), the optional folder parameter
can be included.  But by default it searches through everything which
is usually completely fine.

You can set up days in advance by including a placeholder. That looks
like this:

    days:
        - day1
        - day2
        - day3: "Day 3: Airing December 1st."
        - day4: "Day 4: Airing December 2nd. Shame Owl Time, Shame Owl Channel."

With this you can add a week to the yaml and it will update itself,
automatically replacing placeholder text with links as video stubs
show up that match the day names.
