# Video Game Dataset Project
data analysis final project leanpub

```markdown
# Data Analysis Journey: Before and After Comparison

## Introduction
This repository showcases a before-and-after comparison of my very first data analysis project. The original analysis was created during my initial learning phase, and the refined version reflects improvements in coding style, data cleaning, and visualizations after gaining more experience as a data scientist.

### Project Goal
The purpose of this project was to analyze popular Steam games and determine which gaming companies are runner-ups to the major players in the industry. Additionally, I wanted to see how certain games, such as Counter-Strike: Global Offensive, performed over time.

## Before: My First Data Project

The original code represents my first-ever attempt at conducting a data science project. It involved using basic data manipulation and plotting techniques, but several aspects of the code and analysis could have been improved:

- **Data Cleaning**: Minimal data cleaning and filtering were done.
- **Plotting**: The original visualizations were basic and could be more effective.
- **Efficiency**: There were redundancies in the code that made the analysis less efficient.
- **Documentation**: The explanation and structure of the analysis were not clear enough for others to follow easily.

Here is the original code snippet I worked with:

```r
# Original Data Cleaning and Plotting
games_tidy <- games %>% 
  select(gamename,avg,month,year) %>%
  top_n(15,year) %>%
  arrange(desc(avg)) %>%
  filter(gamename %in% c("Counter-Strike: Global Offensive",
                         "Dota 2","PLAYERUNKNOWN'S BATTLEGROUNDS",
                         "Rust","Apex Legends","Grand Theft Auto V",
                         "Team Fortress 2","Cyberpunk 2077",
                         "Tom Clancy's Rainbow Six Siege","ARK: Survival Evolved"))

games_tidy_plot <- ggplot(data = games_tidy) + 
  geom_point(aes(x = gamename, y = avg, color = gamename)) +  
  theme(axis.text.x = element_text(angle = 60, hjust = 1))

games_tidy_plot
```

### Reflections on the Original Code:
- **Complex Filtering**: The `filter()` and `select()` steps could have been simplified, reducing repetition.
- **Plot Customization**: Limited customization made the plot difficult to read.
- **No Version Control**: I wasn’t using version control effectively in the initial stages.

## After: A Refined and Improved Approach

After growing my skills through various projects and internships, I was able to enhance my analysis in the following ways:

- **Improved Data Cleaning**: The code has been refactored to use more efficient filtering and grouping functions.
- **Better Visualizations**: More informative and clean visualizations were added, making the results clearer.
- **Code Efficiency**: Redundant steps were removed, and the workflow became smoother.
- **Documentation**: Improved inline comments and sectioning in the code made it easier for others to follow and understand the purpose of each part of the analysis.

### Updated Code Snippet:

```r
# Refined Data Cleaning and Plotting
games_tidy <- games %>%
  filter(gamename %in% c("Counter-Strike: Global Offensive", "Dota 2", 
                         "PLAYERUNKNOWN'S BATTLEGROUNDS", "Rust", "Apex Legends",
                         "Grand Theft Auto V", "Team Fortress 2", "Cyberpunk 2077",
                         "Tom Clancy's Rainbow Six Siege", "ARK: Survival Evolved")) %>%
  filter(year == 2021) %>%
  select(gamename, avg, month, year) %>%
  slice_max(order_by = avg, n = 15) %>%
  arrange(desc(avg))

games_tidy_plot <- ggplot(data = games_tidy) + 
  geom_point(aes(x = gamename, y = avg, color = gamename)) + 
  theme(axis.text.x = element_text(angle = 60, hjust = 1))

ggsave("results/results.pdf", plot = games_tidy_plot)
```

### Key Improvements:
- **Refined Data Selection**: The code now efficiently selects relevant data points and organizes them with improved filtering.
- **Plotting**: The plot now uses a cleaner `slice_max()` function to order the data, improving both performance and readability.
- **Saving Results**: Added the `ggsave()` function to store the output, promoting reproducibility and better organization.

## Reflections and Growth

Over time, I’ve learned to:
- **Write cleaner and more efficient code**: I now focus on reducing redundancy and improving performance.
- **Focus on reproducibility**: Saving results and session information ensures that my work can be easily replicated.
- **Improve visualizations**: I’ve grown in creating more insightful and polished visual representations of data.

The changes in this project reflect my development as a data scientist, from writing simple code to producing more structured, efficient, and professional-level analyses.

## What's Next?

- Explore what games are currently trending and compare them to 2021 data.
- Use additional external datasets to compare performance across platforms, not just Steam.

## View the Full Comparison

To view the full before-and-after comparison, including both versions of the code, visit my GitHub repository:
[My Career GitHub Repository](https://github.com/jabirG/My-Career)

For more detailed information on my growth and experience, check out my [LinkedIn](https://www.linkedin.com/in/jabir-ghaffar-977438209/).
```
