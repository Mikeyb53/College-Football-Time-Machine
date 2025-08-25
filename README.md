## <img style="float: left; padding-right: 10px; width: 45px" src="https://raw.githubusercontent.com/Harvard-IACS/2018-CS109A/master/content/styles/iacs.png"> Project Report

# What If The College Football Playoff Had a Time Machine?

**Harvard University**<br/>
**Spring 2025**<br/>
**Author**: Michael Benning

<hr style="height:2.4pt">

# Executive Summary
College football is a fixture in American culture.  Its traditions and passions connect students and alumni, families and fan bases, even Regions across time with a sense of identity, community, and pride.  But perhaps the only thing traditional about college football's method of selecting its national champion is change.  Last season saw the introduction of yet another iteration of the process: **the 12-team College Football Playoff**.

**Project Objective, Scope & Approach**

The project study applies a data-driven machine learning modeling approach to predict the outcomes of the 12-team College Football Playoff (CFP) if the current, expanded playoff format had been in place one year earlier: the 2023 season.  The study predicts the **Georgia Bulldogs** would have won such a playoff based on an approach with the following key attributes:
1. Three machine learning models are developed and trained using a **15,272-game dataset** spanning 16 seasons scraped from *collegefootballdata.com*.  The models leverage predictive information from 93 individual game statistics.
2. The best performing model is a fully connected neural network with 38,305 trainable parameters.  The model achieves an **R-squared value of 0.879** against unseen test data indicating over 87% of the variability in points scored in games can be explained by the model.
3. To predict the outcomes of hypothetical CFP matchups, **probability distributions for each of the 93 predictor variables is generated** based on each team's performance in the 2023 season, the performance of their opponents, and their respective schedule strengths.
4. The feature probability distributions and neural network model are brought together in a **Monte Carlo simulation** to probabalistically predict CFP game outcomes.

**Challenges**

The predictive utility of the approach is impacted by two significant challenges inherent in college football:
- **Uneven strength of schedule**:  while the neural network model described above predicts points scored with high accuracy, it requires robust predictions of the 93 input features including rushing and passing yards and third-down efficiency.  But teams' performance on the field is impacted by the level of competition.  The differences in strength of schedule across the 2023 CFP participants are material (detailed in Section 3.7) and a source of potentially significant bias in the model.  Addressing that bias adequately and equitably while prioritizing an exclusively data-driven approach (versus relying on poll-based rankings) is further challenged by the number of teams and conferences in the FBS and the limited number of meaningful interconference matchups.  Section 6.3 details how the models weight each team's performance during the 2023 season according to their strength of schedule.
- **Statistical significance** (or the lack thereof) presents multiple modeling challenges:
  - While the dataset used to train the predictive models contains over 15,000 individual football games, each team plays only a limited number of games each season.  This small sample size means statistical outliers can play an outsize role in predicting game outcomes.
  - The better team does not always win, and strong (statistical) performance does not always correlate with the outcome.  Games - particularly at the highest levels of college football - can be decided by a small number of key plays.  Accurately modeling the impact of a turnover or penalty at a key moment in a game is a challenge.

**Predicting Outcomes: Key Themes**

Thematically, two noteworthy takeaways emerge in the model predictions:
1. The **margins** separating the win / loss probabilities produced by the model **tend to be very narrow**.  Of the eleven playoff matchups, the model produced win probabilities over 60% in only three games.  For many fans, this is intuitively consistent with the level of competitive parity among the teams in the top echelon of college football.
2. **All games matter**.  Echoing the comments above regarding statistical significance, poor on-field performances - outliers or not - impact model predictions.  The projected upsets - defined as lower ranked teams beating higher ranked teams - highlighted below typically include poor performance in regular season games by the higher ranked team.

**Predictions vs. Rankings**

Consistent with the generally thin win/loss probability projections, the model outputs include a number of noteworthy upsets:
1. The model picks **#8 Oregon over #1 Michigan** in just over half the 1000 simulations.  It is worth noting Oregon played (statistically) the weakest schedule of the twelve playoff participants: the average of their opponents' 2023 win percentage was under 0.500 (see Section 3.4).  In addition, Michigan's statistically poor performances against Iowa, Maryland, and Penn State impacted the predictions.
2. **#12 Oklahoma over #5 Florida State**: a key predictor of points scored is *total yards gained* (detailed analysis in Section 4.3).  Despite winning, Florida State struggled against Georgia, Louisville, and Florida gaining fewer than 235 total yards in each of those games.
3. **#12 Oklahoma over #4 Alabama**: while Alabama struggled against Georgia and South Florida, Oklahoma racked up over 400 total yards in each of their games except two, and over 600 yards in three games.

<img width="2000" height="1125" alt="image" src="https://github.com/user-attachments/assets/ef50e53a-401a-4372-aef7-4b4a009ab093" />
