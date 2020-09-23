[Go back to Home](.)

This is an example of the test csv file.

| Context | Response A | Response B | Context IDs | Response A ID | Response B ID | Hour Gap | Response A Feedback | Response B Feedback | Response A Normalized Rank | Response B Normalized Rank |
| :----- | :-------- | :-------- | :--------: |        :--------: | :--------: | :--------: | :--------: | :--------: | :--------: | :--------: | :--------: |
| Dear Redditors. What do you consider the most important invention in human history?. | Still the Wheel... | every invention has been the most important until the next one. One of the recent important ones was a clock. That's what allowed accurage navigation across Longitutde. | t3_1tvflj | t1_cebtqav | t1_cebtpsw | 0.03 | 31 | -3 | 0.8261 | 0.0000 |

The table below describes each column of the csv file.

| Column | Type | Description |
| :----- | :--------: | :-------- |
| `Context` | str | if multi-turn, turns delimited by "_EOS_" |
| `Response` | str | a response of the given Context |
| `Context IDs` | str | Reddit IDs of turns in `Context`, separated by space if multi-turn | 
| `Response ID`  | str | Reddit ID of `Response` | 
| `Hour Gap`  | float | The difference (in hours) between the time when `Response A` and `Response B` were created | 
| `Response Feedback`  | int | depends on tasks: <br> - `updown`: number of upvotes;<br> - `width`: number of direct replies; <br> - `depth`: number of replies of its longest follow-up thread | 
| `Response Normalized Rank` | float | if all `m` responses of `Context` ranked by `Response Feedback`, the `i`-th response gets a noramlized rank of `i/(m-1)` (`i` starts from 0, and `i==0` indicates least feedback) | 