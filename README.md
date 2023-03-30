# How do Developers Talk about GitHub Actions? Evidence from Online Software Development Community

Artifact package for the ICSE'24 paper "How do Developers Talk about GitHub Actions? Evidence from Online Software Development Community". This reproducible repository includes our data, scripts, and survey questions.

## Abstract of the Paper
Continuous integration, deployment and delivery (CI/CD) have become cornerstones of DevOps practices. In recent years, GitHub Action (GHA) has rapidly replaced the traditional CI/CD tools on GitHub, providing efficiently automated workflows for developers. With the widespread use and influence of GHA, it is critical to
understand the existing problems that GHA developers face in their practices as well as the potential solutions to these problems. Unfortunately, we currently have relatively little knowledge in this area. To fill this gap, we conduct a large-scale empirical study of 3,285 Stack Overflow posts and 130 GitHub issues. Our study leads to the first comprehensive taxonomy of topics related to GHA, covering the 4 phases of the GHA lifecycle, with 16 categories and 50 topics. By analyzing the characteristics of the posts and issues, we find that the Comparison, Configuration, and Component categories are more popular than other categories, and there are fewer experts in the GHA than in other domains, and such a phenomenon is most significant with respect to the Operation phase. Further, we manually analyze 1,224 accepted answers on Stack Overflow and 82 closed GitHub issues, distilling 51 fix patterns for different GHA-related problems. Our findings can contribute to the research and development of emerging GHA practices, guiding the future support of tools and technologies.

## Data
1. Data Collection
	* SO data, i.e., posts, from the official SO data dump (as of October 2021)
	* GitHub data, i.e., issues, using the GitHub Search API 4
2. Data for manual classification
	* SO post: We extract all posts with at least one tag of “github-actions”, “github-action”, “github-package-registry”, “building-github-actions”,“github-actions-runners”, and “github-actions-self-hosted-runners”.
	* GitHub issue: We use the GitHub Search API to filter the GHA-related issues. We filter out projects with less than 10 changes (commits or pull requests) in the last three months. We obtain all issues(exclude pull requests) created between July 31, 2008 and September 30, 2021, and extract issues tagged with “github action” or “github-action”. 
	* This data includes  
    	1. 3,285 SO posts (Q\_S) with 1,224 accepted SO answers (A\_S)
    	2. 130 GitHub issues (Q\_G) with 82 closed GitHub issues (A\_G)
    * The data for manual classification can be found in `post_issue.csv`
    * Data structure: (id, paper_no, type, title, url)
	    1. id: the meta
	    2. paper\_no: the number used in this paper. "P1" and "I1" represent the first SO post and the first GitHub question in our dataset, respectively.
	    3. type: "github issue" or "so post"
	    4. title: the title of a post or an issue
	    5. url: url of a post or an issue   
3. Data for characteristics analysis
	* The data for manual classification can be found in `post_popularity.csv` and `post_issue_difficulty.csv`
	* post\_popularity includes 3,285 SO posts' view number, favorite number, score and answer number.
	* post\_issue\_difficulty includes the following matrixs of 3,285 SO posts and 130 issues:
		1. interval\_fir\_ans: median time interval to the first answer (issue comment), in second
		2. interval\_acc\_ans: median time interval to the accepted answer (issue closure), in second
		3. body\_len: the sum of character numbers of the question (issue) description

## Script
We implement the prediction models using Python with the scipy package
* Spearman's rank correlation coefficient `correlations.py`

## Figure
* Figure 1: The trend of GHA discussed on Stack Overflow
* Figure 2: The taxonomy of GHA-related topics
* Table 1: Popularity of GHA-related discussion categories
* Table 2: Difficulty of GHA-related discussion categories
* Table 3: Correlation between Popularity and Difficulty of GHA-related discussion categories (on SO)

