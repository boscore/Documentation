## I. Preface:

Since Daniel Larimer introduced DPoS into EOS, how to better select Block Producers has become the focus of much community debate.

In this regard, BOS follows the EOS voting mechanism. That is a one-vote multi-selection (maximum 30 selections) mechanism. Due to the existence of Pareto's law, the voting rights tend to be concentrated in the hands of a few people. As well, a one-vote multi-selection mechanism allows token holders to trade votes, which ultimately leads to the Block Producers being controlled in the hands of a small number of token holders, thereby increasing the imbalance and centralization of the Block Producers, further leading to an increase in the gap between rankings. To this end, in the design of the BET voting system, we aim to introduce an improved [Borda voting mechanism](https://en.wikipedia.org/wiki/Borda_count) to alleviate this problem in order to find a more reasonable means to make a corresponding contribution in ensuring system security and widespread distribution; which ultimately leads to a better and more inclusive distribution of WPS funds.

## II.  Proof of Stake mechanism and Voting:

1. There are many articles about the Proof of Stake mechanism. There is no more detailed discussion here. Only the discussion of Block Producer concentration and security is discussed. For the sake of discussion, we simplify the above. We assume that all voting rights are from voters, simplifying the original model as a probability discovery model, then we assume that a holder's shareholding ratio is Q, secret cheating function H, cheating is found after loss function F(Q), maintaining system stability. The general return function is X(Q), the cheating gain is W, the hypothetical function here is only used for qualitative analysis, so we can simply get the strategic relationship of the stakeholder:

Judging the relationship between `W+(H-1)*F(Q)` and X(Q) and determining the corresponding strategy. Because F is a positive correlation function of Q, X is also a positive correlation function of Q, and W is a random parameter with speculation. So it can be concluded that the cheating gain will be significantly reduced with the increase of Q, under the assumption of rational natural person. 

Choosing to maintain justice is a dominant strategy. So from this perspective, the PoS mechanism is a stable model. In fact, when we further analyze the ethical parameters, we can obtain the following relationships and conclusions between the equity structure and the stakeholders' income:

A) Absolute concentration structure of Shares

If the equity is absolutely concentrated on the network operators, the supervision will be difficult, and the moral value of the network operators will decrease or even become negative.

Operator responsibility (→min)=operator morality (→-)×{1+ operator asset ownership (max)}

stakeholders' income (→min)=operator's responsibility (→min)×operator's ability×operating conditions.

B) Relatively concentrated structure of equity

The relative concentration of equity can encourage operators, stabilize the backbone team, and generate checks and balances.

Operator Responsibility (→max)=Operator Ethics (→max)×{1+ Operator Asset Ownership (max)}

stakeholders' income (→max)=operator's responsibility (→max)×operator's ability×operating conditions.

C) Equity dispersion structure

The equity is too scattered, the supervisory motivation is insufficient, and the moral value of the network operators will decrease or even become negative.

Operator Responsibility (→min)=Operator Ethics (→-)×{1+ Operator Asset Ownership (min)}

stakeholders' income (→min)=operator's responsibility (→min)×operator's ability×operating conditions.

 

From the analysis, we can determine that (B) relative concentration of equity is the preferred equity structure (for detailed knowledge, please refer to the books and papers related to equity structure).

Therefore, we need to avoid the concentration of large token holder consortiums under the premise of the stability of the system. So the question remains: is there an ideal voting solution?

## 2. Voting and election

Before discussing this issue in detail, let's try to define the problem:

We assume that there are N people participating in the election, there are a total of K people to vote, and there is an arrangement in the satisfaction of each voter in the hearts of the candidates. Our aim is to develop an election plan that will eventually be "fair" for everyone. The sequence of voting results.

So what is fair? Here we use the five rules of arrow:

- Every voter has the same influence; further, it is non-authoritarian.
- In addition to being unreasonable, voters have no other restrictions on the ordering of their minds.
- If all voters think A > B, the election result will also show A > B.
- The ranking of the election results for A and B should be determined only by the relative order of A and B within the file, regardless of any third party.
- If all voters are rationally sorting the choices and voting honestly, the results of the elections should also show a rational order.

But unfortunately there are a variety of proof methods to prove that such "justice" does not exist, which is also the content of the arrow impossible theorem. Since our system will be modified based on the Borda system, here we give proof of the theorem in the Borda case:

Let a given k integers m1, m2, ..., mk, let σ(1,2,...,n) be a permutation group of (1,2,...,n), and define the following mapping:

![img](https://lh3.googleusercontent.com/TsZpYlLy_fX85Zakg13UO1FjWn7rFaGMijOFyr-ISaZj-fzCHQyrNyBilXX0Y5OXpsFnMfbaIy_lhtJL1jqRaKMFgm4-pvfSFPqK3MeN_haRyeBIVEGKUpkpfpkJTcuRFw)

For any set of numbers t1>t2>...>tn, use the above k permutations to make an n×k matrix:

![img](https://lh3.googleusercontent.com/i5L_PiMmqnL_0WDMFuqWNQSdFjOZHL0LocYq1dpos32NNo88rS5mc5UD1QBmccWHGqAU0rrZt0pFxyXecIEDUzSV1JqJxZEkfA0kNM4zrMiwSumMt_E1WqpR_POu3kFWfw)

Define n numbers in turn:

![img](https://lh3.googleusercontent.com/fxba493G10oHEBHaVd2u7XoMqhGr3zckxbDJJ1puzyQO2Fo_dFa15j3zQmCqxM3LvncUUYMZL96ViFPFxdcfbqIGwchxQkYwI8SaTp-thCxIQmT87v1Pd7NV5BOepNH9zA)

Then there are:

![img](https://lh4.googleusercontent.com/1FQGHcARpqJJahP6BEVnF0CFlQwg6sl_Q4xMKLz3mbIDIlyhsRZihKwGD02ijpAADQaU9HEF1cpzKDd4ghsHvvvDAbFQmTnDARpnlLwids4wWZNqG9Z9blN-FJG3nCWjZA)

We know that we can find n sets of numbers for the above equation.

![img](https://lh4.googleusercontent.com/0_TyyFPeL6uugOr_gT6ofu0YcVuskjH6a9a2UzbKUZlEWFt71uefVoXkOdzerhAOHtze-1zTxxAphPOCZASp_-aDw4s1jQpqmIy83hlKiybPxPMkVeDevQ8-2dNNkGFKbw)

Corresponding

![img](https://lh3.googleusercontent.com/tCk81GvjlZFNh-MhH3Kzx2EbNbVRHmXBSF103J4el6jPe04eE2ls44vLlqkuziMrVNUn6cZ1pbH94ysuOqf7zzrsGehTLtC8f6KksHs4K5fJpJKVivihZHJcK5d-hCO4hw)

Satisfy:

![img](https://lh5.googleusercontent.com/3IfTAYljWO9aOvdlQU8YHUUqOmjg7Tf_2v_w-UP4LaKvKa-hLEjbq0f4YWdR0nSaGQYd9liu-mFuF1FKZiw3LlA8mkO02YBE8WjxdhJknifNlLrLB2sSgeKmgfmR4m0rjQ)

In other words, the Borda score method is also unstable. So where is the problem, in fact, our assumptions constraints such fairness. In his paper, scholar Saari elaborated on the above issues. One of Saari's arguments is that Articles 4 and 5 of Arrow's conditions are “offset” with each other, so they have carried out the fourth rule. The amendment is as follows:

4. Election results The ranking of A and B should be determined only by the relative order and distance of A and B in the file, regardless of any third party.

So under this assumption, Saari proves that the Borda Count election process is "fair" on the premise of more than two candidates! For specific technical details, please refer to [Saari's related papers](https://en.wikipedia.org/wiki/Donald_G._Saari#Papers). In other words, the Borda Count election process is better in this sense. Therefore, we try to adapt the BET voting system with the PoS system under this conclusion.

## III.BET voting system.

Next we will give a general description of the voting system:

It is assumed that the number of people participating in the election is N, K people vote.

Our voting rules are as follows:

1. For any voter, it is required to give a sequence Ln of the order in which the candidates fit or not.

2. The voter's voting weight is recorded as the number of tokens held and mortgaged by Pi.

3. Given a function F(i), the function returns a score for the different sequence numbers of the sequence. The specific function will be given below.

4. The rules for scoring any candidate are as follows:

`Vk=∑F(i,j)*Pi`

5. Sort all candidates who participated in the election and draw the final selection sequence.

Assumptions:

In this program, we limit each voter, assuming that any voter can vote for the number of votes held in their hands, that is, Pi, and only one vote at a time, so we can treat each voter as a collection of voters with the same willingness to vote, each with only one vote, further seeing this becomes a model for the Borda count to vote for the Borda count. So it has the same theoretical characteristics as the Borda count system.

Of course, we can also follow the Borda count system exactly as follows:

1. Require each voting participant to mortgage the corresponding token,

2. Require it to give the corresponding selection sequence Ln

3. Given a function F(i), the function returns a score for the different sequence numbers of the sequence. The specific function will be given below.

4. The rules for scoring any candidate are as follows:

Vk=∑F(i,j)

But this does not reflect the advantages of the PoS system discussed above.

Further, for any token holder Pi, since he needs to vote (sort) all candidates, that is, he contributes to any candidate, but the degree of contribution is according to function F. Therefore, comparing the one-vote and multi-selection systems obviously weakens the role of the voting rights. The following figure compares the control with one-vote and multi-selection under different F functions:

![img](https://lh4.googleusercontent.com/DsLbbU7Z9ZYrhEo0onABfOFWyGrLG0u97JYStXUN7wg9QCAOb8k7wv87DdOi9Ey9rc87uT9oY3DiZIJ_sCWRdcUNJ7eoIi7qznJKqm43-J64-Fnuxs9fmDtpEGFBwKdeqw)

The area below the line is the maximum vote for a voter voter

![img](https://lh3.googleusercontent.com/qt9rDZoVloo36bB7F7qfhcVwdw9nE8r1PXksXTSFtaKb64B4hD7O5YzRU9OtpTEdq9UY_qLT_Tl6h8c44K-effxMnT5rD3tir2vSKIpXIhhKlRdLrlU6pveqTYxn33rVTw)

The area below the line is the maximum vote when F is the Borda count system.

![img](https://lh6.googleusercontent.com/Yz4SxtHF4Vh4_3WrIgQbYzKS6MA9PzIXpV31L_hCjtCFNUBsryPPOAa1ItKQr6Te0MyUFxXOBKr4HZUE03FwWhuy0On4K4mPVV_rwEYkpthj9Htda3SYO6ThOAGFbA0yiQ)

The maximum area below the line is the voting maximum when F is X^(-σ)

Although not rigorous, you can intuitively feel the difference between them.

Next, we will illustrate the features and advantages of the program through a few simple examples:

1. Suppose there are three voters A, B, and C. For the sake of discussion, let's assume that the candidates are the same three, and assume that they vote for themselves. Our voting principle is to choose two of the three to win.

We assume that A, B, and C hold the number of tokens a, b, and c, respectively. If we assume conspiracy in a and b, if EOS's current voting system is adopted, c will lose the final right as long as a+b>c. But under the BET system, you need a+2b>2c to get the corresponding result. In the case where the differences among the candidates are not different, a and c can be elected.

2. Consider another example of bribery. Let's assume that there is a large A with 2,000,000 tokens. The support of other candidates is only between 1,000,000 and 6,000,000. If the EOS strategy is adopted, then the other candidates cannot agree. Under the premise, A can control the entire order of the elected person. Due to the strong control of A, many candidates will choose to trade with A, which will eventually lead to the further strengthening of A's control.

For the BET system, the situation will be different. For example, we use (n+1-i)/n as the F function, n is assumed to be 25, then for the big A, it is for the i support. The contribution value provided by the account is `(n+1-i)/n*a`. For example, when i is 20, the contribution value is 4,800,000, that is, when there is a token held by the voter in the hand, the token exceeds the value.

Choosing to work with this token holder is a better strategy than working with A. Therefore, this can weaken the control power of A to a certain extent and at the same time ensure the interests of many stakeholders. At the same time, because the plan is necessary to fill the gap, the voter is maximizing the profit for the benefit of the rational person. In addition to yourself, the remaining votes will be voted for the most stable candidates for the system, thus ensuring the security and stability of the system.

## IV. Summary

The design is a further exploration of the existing EOS voting system, with the research results of Saari et al., which can make the BET voting system more perfect, but as the Arrow impossible theorem says, when it is limited to certain conditions, the perfect voting plan does not exist. So we hope to better the current model under reasonable assumptions.
