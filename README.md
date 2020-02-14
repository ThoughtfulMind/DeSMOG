# Climate change stance classifier

TODOs

- [ ] Training and test data
   - [ ] SemEval 2016 task 6 train, trial--both very small (211 for, 15 against)
   - [ ] SemEval 2016 test (subtask A)--169 tweets (123 for, 11 against, 35 none)
   - [ ] Mohammad et al. paper--data requested
   - [ ] Dallas' annotated news data
   - [ ] Yiwei's news data--needs annotation
   - [ ] Perspectrum (Chen et al. 2019)
   - [ ] tweets (Koenecke)
   - full news data can be used as in-domain data for initial fine-tuning
- [ ] Training classifier
   - [ ] Decide how to transform MTurk labels
   - [ ] Fine-tune on unlabeled in-domain data; then on all in-domain data 
   - [ ] Baselines: 
	- 
	- STANCY on perspectrum (https://www.aclweb.org/anthology/D19-1675.pdf)
	    - swap out their C for our single target sentence
	    - instead of BERT, use GPT
- [ ] MTurk 
   - [x] pilot, iterate with smaller subsample to check inter-annotator agreement
   - [x] Lock down non-pilot specifics:
	- [x] Config settings: 98% minPercentPreviousHITsApproved, 1000 minNumPreviousHITsApproved, USonly = yes
	- [x] Collect 2,000 total annotations in 5 rounds: N=300, 400, 400, 450, 450
	- [x] 8 annotators per annotation item
	- [x] Each HIT will have N/10 true items to annotate + 5 screen items (screen items differ b/w rounds, so need 25 total) (so Round 1 will have 35; Round 2, 45; Round 3, 50)
	- [x] N items/(N/10 items/HIT) = 10 HITs per round; multiply by 6 annotators = 60 annotators paid
	- [x] Payment (based on $12/hr MW in CA): $4, $5.14, $5.7 for Rounds 1, 2, 3, 4, 5; total cost = $4*60+$5.14*120+$5.7*120 = $1,540.8 USD
	- [ ] Exclusion criteria for all rounds, after collection:
		- [ ] Turkers who choose agrees/disagrees on screen Q for which answer is disagrees/agrees
		- [ ] For each Turker, calculate %items for which all other 5 Turkers chose agrees/disagrees but they chose disagrees/agrees; if this % is greater than N--exclude. N>=10%?
		- [ ] If find an effect from party--drop annotations s.t. balance of annotations per item from D and R
		- [ ] increase task size, check IRR b/w first and second half of exp (60)
   - [x] Analysis:
	- [x] Item length effect on rating
	- [x] average rating for each item, divided by liberal vs. conservative sources


- Miscellaneous ideas:
	- Track whether people decide to click for more context--signal of the ambiguity of the sentence (medium priority)
	- Question mark button for more information about abbreviations? (Can we track whether someone's clicked on a question mark?)
	- Future study in which I manipulate stance-taking verb
            - How do you mix them? Across, within speaker thing?

References:
   - https://towardsdatascience.com/transfer-learning-in-nlp-for-tweet-stance-classification-8ab014da8dde
   - STANCY https://www.aclweb.org/anthology/D19-1675.pdf
   - http://www.saifmohammad.com/WebDocs/StarSem2016-stance-tweets.pdf

