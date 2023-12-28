# The 7 Rules For Successful Job Hopping In Data Engineering

[Reference from tldr](https://blog.dataengineer.io/p/the-7-rules-for-successful-job-hopping?utm_source=tldrwebdev)

- Onboard quickly and deliver value in the first 1-2 months
- Within the first year, start working on the highest priority work in your domain area
- Always have  a measurable impact everywhere that you go
- Don't force yourself to get a promotion from a manager who doens't believe in you, it's a waste of time
- Be a glue person. Do the work nobody wants to do and save your teammates headaches
- Remember to live a life you enjoy, don't just obsessed with work
- When interviewing, ALWAYS say you’re interviewing with other companies even if you aren’t. It makes negotiations easier and you’ll be treated better in the interview process

## Speed running junior to mid-level promotion

- Onboard quickly and deliver value in the first 1-2 months
  - The auther learned pretty quickly that he needed to know the ins and outs of:
    - The big data world: Apache Hive, HDFS
    - The visualtization world: Unidash, Scuba
    - The experimentation world: Deltoid, Gatekeeper
    - Assigned domain: Notifications
  - A lot of these technologies were new to author, and he felt overwhelmed initially.
  - So here's the set of tenets he used to grow as a junior data engineer:
    - Try your best to solve a problem, if you spend more than 90 minutes on it, ask for a second set of eyes. No harm in asking for help, especially when you're new.
    - Voraciously learn and build. Spend at least 4 hours each weekend dedicated to learning and growing.
    - Teach your colleagues as much as you get taught. This means providing value and filling in skill gaps that you see on your team.
    - Don't be afraid to try ambitious stuff but make sure to ask your manager to help de-risk to effort.
  - The bottom are what author promotion packet looked like:
    - Created a better version of the notifications one-pager dashboard that monitored the health of notifications. The new version gave better visibility to SMS and email notifiactions and incorporated new reachability metrics.
    - Simplified and improved metrics that increased notification relevance by 10%. Reduce the latency of these data sets by 40% by splitting up this 3000-line SQL query into multiple Dataswarm steps.
    - Enhanced the quality of notifications growth metrics by adding a bunch of data quality checks through various partts of the pipeline.
    - Converted the year-over-year growth dashboard from Tableau to Unidash. Reduced the loading time of this dashboard from 10 seconds to 20 milliseconds. This dashboard provides company-level visibility for Whatsapp, Facebook, Messenger, and Instagram growth metrics to executives like Zuckerberg and Alex Schultz.
    - Did 10 code screens of data engineering candidates for Facebook.
    - Saved Facebook 1.5 PBs by optimizing retention strategies of notification data sets.
  
## Trying to go mid-level to senior in a year

- Within the first year, start working on the highest priority work in your domain area.
- Always have a measurable impact everywhere that you go!

---

- Always interview with confidence! Confident people get paid more!

## Netflix interview covered a broad range of topics

- Graph data structures
  - The tradeoff between doing depth-first search and breadth-first search algorithms.
- SQL
  - Auther was asked a question that required author to know the distinction between RANK, DENSE_RANK, and ROW_NUMBER.
  - To do a query would normally solve with LAG/LEAD but with a self-join. Knowing ANSI fundamentals helps A LOT in these interviews!
- Data architecture
  - Different architectures such as lambda and kappa architectures.
  - Needed to design a data lineage system on a whiteboard and talk about the tradeoffs.
- Behavioral interview
  - If you don’t know the Netflix culture deck by heart, you’re going to fail.
- Data structures and algorithms
  - Leetcode medium questions

### Can view the free videos on the data engineer interviews
- [Data Architecture Interview](https://dataengineer.io/course/the-data-architecture-interview)
- [SQL Interview](https://dataengineer.io/course/the-sql-interview)
- [Data Modeling Interview](https://dataengineer.io/course/the-data-modeling-interview)
- [Data Structures and Algorithms Interview](https://dataengineer.io/course/the-data-structures-and-algorithms-interview)
- [Behavioral Interview](https://dataengineer.io/course/the-behavioral-interview)

## When interviewing, ALWAYS say you’re interviewing with other companies even if you aren’t. It makes negotiations easier and you’ll be treated better in the interview process

# What's The Difference Between RANK(), DENSE_RANK(), And ROW_NUMBER()

[Reference from blog.dataengineer](https://medium.com/@LoriLu/whats-the-difference-rank-vs-dense-rank-vs-row-number-3aca5ecfb928)

- For example, will use `sales` table:
  - `product` - the name of the product
  - `product_price` - the price of the product
  - `items_sold` - the number of items sold
- ![Dummy Data](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Uymuhq5hd3XWTl-7Un4GmQ.png)
- To compute the most popular items, intuitively, we should sum the revenue up for each product, sort products of total revenue, and pick the top 3 products.
- RANK() to compute the ranking
```sql
SELECT
  RANK() OVER(ORDER BY product_price * items_sold DESC) AS rank,
  product,
  product_price * items_sold AS revenue
FROM sales
AS sales_rank;

SELECT * FROM sales_rank WHERE rank < 4 as sales_rank_top3; -- or
SELECT * FROM sales_rank LIMIT 3;
```
- ![SQL result between these 3](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*zQ449C3Nj059aSGZ6gn4Dw.png)
- ROW_NUMBER()
  - The ROW_NUMBER() function is self-explanatory, as you’ve already seen the data.
  - It simply assigns a consecutive ranking to each row ordered by revenue.
  - If two rows have the same value, they won’t have the same ranking.
  - ![ROW_NUMBER()](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*4XYDWpD48z8cm6sBwVENwA.png)
- RANK()
  - The RANK() function creates a ranking of the rows based on the provided columns.
  - It starts with assigning “1” to the first row in the order and then gives higher numbers to rows lower in the order.
  - If rows have the same value, they’re ranked the same.
  - However, the next spot is shifted accordingly.
  - For example, if two rows are 2th (have the same rank), the next row will be 4th (i.e., 3rd doesn’t exist).
  - ![RANK()](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Sol7kJrfEyGftfUCJUye7w.png)
- DENSE_RANK()
  - The DENSE_RANK() function is rather similar.
  - The only difference is that it doesn’t leave gaps in the ranking values.
  - Even though more than one row can have the same rank, the rank of the next row will be one plus the previous number.
  - For example, if two rows are 2rd, the next row will be 3rd.
  - ![DENSE_RANK()](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*NnDaOuFLWFmjt8O-IXtD5A.png)
- DENSE_RANK() is the right ranking function to show top results in this use case.
```SQL
SELECT
  RANK() OVER(ORDER BY product_price * items_sold DESC) AS rank,
  DENSE_RANK() OVER(ORDER BY product_price * items_sold DESC) AS dense_rank,
  ROW_NUMBER() OVER(ORDER BY product_price * items_sold DESC) AS row_number,
  product,
  product_price * items_sold AS revenue
FROM sales
AS sales_rank;
```

# The 100 Days Of Code Challange From FreeCodeCamp On 2024

[Reference From Daily.dev](https://www.freecodecamp.org/news/100daysofcode-challenge-2024-discord/?ref=dailydev)

[FreeCodeCamp Discord](https://discord.gg/freecodecamp-org-official-fi-fo-692816967895220344)

- Discord Edition
- 2 Simple Rules
  - You commit to coding for at least 1 hour each day – and then posting about it – for 100 consecutive days.
  - You also commit to encouraging at least 2 people each day by replying to their posts.
  
## Learning to code is not a technical challenge – it is a motivational challenge.

# Blind 75 Questions

[Reference from blog.dataengineer](https://leetcode.com/discuss/general-discussion/460599/blind-75-leetcode-questions)