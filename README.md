# Daily-MYSQL-Practice
I am documenting my daily MySQL learning here to keep track of my progress.
Day 1-
****CASE statements-**

The CASE statement in SQL allows you to shape, transform, manipulate, and filter data based on specified conditions. It's a conditional expression tool that lets you customize query results, create new categories, and apply conditional logic.
Table- Marvel_avengers

actor	character	superhero_alias	platform	followers	posts	engagement_rate	avg_likes	avg_comments
Robert Downey Jr.	Tony Stark	Iron Man	Instagram	500000	200	8.20	12000	800
Chris Evans	Steve Rogers	Captain America	Twitter	300000	150	6.50	8000	500
Scarlett Johansson	Natasha Romanoff	Black Widow	Instagram	700000	300	7.80	15000	1000
Chris Hemsworth	Thor	Thor	YouTube	400000	100	9.10	20000	1200
Mark Ruffalo	Bruce Banner	Hulk	Twitter	200000	80	5.30	6000	400
Jeremy Renner	Clint Barton	Hawkeye	Instagram	350000	120	6.90	9000	600
Mark Ruffalo	Bruce Banner	Hulk	Instagram	320000	110	6.10	8000	450
Tom Hiddleston	Loki	Loki	TikTok	600000	250	9.50	25000	1800
Samuel L. Jackson	Nick Fury	Nick Fury	Twitter	250000	70	4.80	5000	300
Elizabeth Olsen	Wanda Maximoff	Scarlet Witch	Instagram	550000	180	7.20	11000	900
Paul Bettany	Vision	Vision	YouTube	450000	160	8.30	18000	1400
Anthony Mackie	Sam Wilson	Falcon	Twitter	180000	90	5.60	7000	400
Sebastian Stan	Bucky Barnes	Winter Soldier	Instagram	320000	110	6.10	8000	450
Paul Rudd	Scott Lang	Ant-Man	TikTok	420000	200	9.80	21000	1600
Robert Downey Jr.	Tony Stark	Iron Man	Twitter	350000	120	6.90	9000	600
Evan Peters	Pietro Maximoff	Quicksilver	YouTube	400000	180	7.80	14000	900
Evangeline Lilly	Hope Van Dyne	Wasp	Instagram	280000	140	6.70	10000	600
Chadwick Boseman	T'Challa	Black Panther	Twitter	400000	180	7.90	12000	800
Brie Larson	Carol Danvers	Captain Marvel	YouTube	600000	300	9.20	25000	1800
Benedict Cumberbatch	Stephen Strange	Doctor Strange	Instagram	320000	120	7.00	9000	550
Tom Holland	Peter Parker	Spider-Man	TikTok	500000	250	9.60	22000	1600
Chris Pratt	Peter Quill	Star-Lord	YouTube	280000	80	5.20	6000	350
Zoe Saldana	Gamora	Gamora	Instagram	200000	70	4.50	5000	280
Bradley Cooper	Rocket Raccoon	Rocket Raccoon	Twitter	150000	100	6.80	6000	320
Vin Diesel	Groot	Groot	TikTok	250000	120	7.30	8000	500
Dave Bautista	Drax the Destroyer	Drax the Destroyer	Instagram	180000	80	5.90	7000	400
Josh Brolin	Thanos	Thanos	YouTube	700000	200	8.20	15000	1000
Danai Gurira	Okoye	Okoye	Instagram	400000	140	7.00	10000	600
Karen Gillan	Nebula	Nebula	Instagram	260000	120	6.40	9000	550
Letitia Wright	Shuri	Shuri	Instagram	300000	110	6.10	8000	500
Benedict Wong	Wong	Wong	Twitter	150000	70	4.50	4000	250
Pom Klementieff	Mantis	Mantis	TikTok	180000	80	5.90	6000	350
Anthony Mackie	Sam Wilson	Falcon	Twitter	400000	170	7.50	11000	750
Letitia Wright	Shuri	Shuri	TikTok	220000	100	6.30	8000	450
Benedict Wong	Wong	Wong	Instagram	280000	130	6.80	7000	400
Chris Hemsworth	Thor	Thor	Instagram	500000	250	9.60	22000	1600
Mark Ruffalo	Bruce Banner	Hulk	Instagram	250000	100	6.50	8000	400
Samuel L. Jackson	Nick Fury	Nick Fury	YouTube	550000	300	7.60	25000	1800
Elizabeth Olsen	Wanda Maximoff	Scarlet Witch	Instagram	380000	160	8.70	13000	850
Paul Bettany	Vision	Vision	Twitter	400000	200	9.10	18000	1200
Anthony Mackie	Sam Wilson	Falcon	TikTok	220000	100	6.30	7000	450
Robert Downey Jr.	Tony Stark	Iron Man	Instagram	550000	280	7.30	16000	1000
Robert Downey Jr.	Tony Stark	Iron Man	TikTok	380000	140	6.80	10000	650
Chris Pratt	Peter Quill	Star-Lord	YouTube	320000	120	6.70	9000	600
Dave Bautista	Drax the Destroyer	Drax the Destroyer	Instagram	300000	110	6.10	8000	500
Brie Larson	Carol Danvers	Captain Marvel	TikTok	450000	200	9.00	21000	1500
Zoe Saldana	Gamora	Gamora	Twitter	180000	70	4.80	4000	300
Bradley Cooper	Rocket Raccoon	Rocket Raccoon	Instagram	250000	100	6.50	8000	400
Chris Hemsworth	Thor	Thor	Twitter	320000	120	6.70	9000	600
Mark Ruffalo	Bruce Banner	Hulk	Twitter	240000	90	5.30	7000	400
Samuel L. Jackson	Nick Fury	Nick Fury	TikTok	350000	150	7.50	12000	800
Tom Hiddleston	Loki	Loki	Instagram	420000	200	8.50	15000	1000


1--Select character, superhero_alias, platform,
CASE When  followers >= 500000 THEN 'Popular' END AS popular_category from marvel_avengers;

**Multiple coniditons--**

2--Select actor, character, CASE
When engagement_rate >= 8.0 Then 'High Engagement'
When engagement_rate Between 6.0 and 7.9 Then 'Moderate Engagement'
When engagement_rate < 6.0 Then 'Low Engagement'
End as Engagement Category
where platform IN ('Tiktok', 'Instagram');

**Using CASE-ELSE Clause with CASE Statement in SELECT Statement-**

3. Select character, superhero_alias, platform, CASE
When followers >= 700000 Then 'Highly Popular'
When followers between 300000 and 699999 Then 'Moderately Popular'
Else 'Less Popular'
End as popualrity_category from marvel_avengers;

**Example-- In this step, we define the different categories for likes based on the average number of likes:

"Super Likes" for characters with an average of 15,000 or more likes.
"Good Likes" for characters with an average between 5,000 and 14,999 likes (inclusive).
"Low Likes" for characters with an average of fewer than 5,000 likes.**

SELECT 
actor, character, platform, avg_likes,
CASE
When avg_likes >= 15000 Then 'Super Likes'
When avg_likes between 5000 and 14999 Then 'Good Likes'
Else 'Low Likes'
End as  corresponding_likes
FROM marvel_avengers Order by avg_likes desc;

**Filtering Conditions** with CASE Statement in WHERE Clause

Select actor, character, platform from marvel_avengers
Where 
CASE 
When platform="instagram" then followers >= 500000
When platfrom = "twitter" the followers >= 200000
Else followers >= 100000
End;


