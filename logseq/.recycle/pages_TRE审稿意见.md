Review Report

## Reviewer #2: 
This paper considers a joint transportation problem where multiple carriers form an alliance 
and share freight tasks and vehicle capacities in orders to reduce their transportation costs. Two issues, the assignment of freight tasks and the allocation of cost savings among the carriers, are addressed. For the first issue, the freight task assignment problem is formulated as a collaborative multi-depot vehicle routing problem (CMDVRP) and a nonlinear mixed integer programming model is established for the problem. This model considers the freight transfer between any two depots and the freight delivery from each depot to a subset of customers simultaneously. A two-stage algorithm based on simulated annealing (TSA) and a modified variable neighborhood search algorithm (MVNR) are proposed to solve the problem. For the second issue, a so-called weighted equal cost savings (WECS) method is proposed for the allocation of cost savings among the carriers. WECS is similar to the equal profit method (EPM) proposed in the literature, the only difference is that the former considers the contribution of each player (carrier) in the definition of its relative cost savings, i.e., the relative cost savings of each player in WECS is obtained by that in EPS divided by a weight depending on the contribution of the player. The contribution of each carrier is determined heuristically. A case study based on data from a logistics service platform Zallsoon is conducted to demonstrate the magnitude of cost savings of joint transportation and the applicability of the proposed algorithms for solving CMDVRP and the cost savings allocation method WECS. The problem studied is of practical importance, however, **the contribution of this paper is minor as explained in the following comments**.

1. The nonlinear mixed integer programming model P for CMDVRP is wrong, because subtour elimination constraints are missing. The present model cannot avoid the existence of a vehicle route (tour) which only visits customers without passing any depot. Moreover, this model is nonlinear because of nonlinear constraints (6). It should be possible to replace constraints (6) by linear constraints to make P linear. If P is a linear mixed integer programming model, it can be solved by a commercial MIP solver such as the MIP solver of CPLEX, so that the solution quality obtained by the proposed algorithms for CMDVRP can be evaluated by comparing it with that obtained by the MIP solver, at least for small instances of the problem.
模型错误，缺少子环消除约束；
非线性约束6可以转换为线性约束；转换为线性约束后模型变为MILP，可以用商业求解器求解与算法对比


2. Various multi-depot vehicle routing problems were studied in the literature, and the simulated annealing algorithm and the variable neighborhood search algorithm proposed in this paper are rather classical, so there is no novelty or little novelty in both the problem CMDVRP studied and the solution algorithms proposed. Moreover, only one case study is reported, no extensive numerical experiments are conducted to evaluate the performance of the proposed algorithms in terms of solution quality and computation time, so we do not know whether the proposed algorithms can provide high quality solutions for CMDVRP.
模拟退火算法和变领域搜索算法比较经典，缺少创新；
仅做了一个算例研究，没有进行大量的数值实验来评估算法。
3. The title of this paper is not appropriate, because its contribution to cost allocation in joint transportation is minor. As mentioned above, the proposed cost allocation method WECS is similar to the equal profit method (EPM) in the literature, the only difference is that the former considers the contribution of each player (carrier) in the definition of its relative cost savings. However, the way of considering the contribution of each carrier is very similar and almost identical to that proposed in the reference (Dai, B., Chen, H., 2012) cited in this paper under review.
标题不合适，对联合运输的成本分配贡献很小，考虑各承运人贡献的方式与本文中引用的参考文献中提出的方式几乎相同。（Dai, B., Chen, H., 2012. Profit allocation mechanisms for carrier collaboration in pickup and delivery
service. Computers & Industrial Engineering 62, 633–643. doi:10.1016/j.cie.2011.11.029.）
4. For the example considered in the case study with four carriers, both the Shapley value and the allocation obtained by WECS are in the core of the corresponding cooperative game. Since the Shapley value already considers the contribution of each player in the game, what is the advantage of the WECS allocation compared with the Shapley value?  
 WECS分配相比shapley有什么优势？
5. In subsection 3.1 introducing the two-stage simulated annealing algorithm (TSA), the solution coding mode is presented. However, since TSA is based on local search not as genetic algorithms working on a population of solutions and applying crossover and mutation operations to generate new solutions, is the coding of solutions necessary in TSA? 
 由于模拟退火算法是基于局部搜索的，而不是想遗传算法那样处理一组解并应用交叉和变异来生成新解，那么模拟退火操作中是否需要对解进行编码？
In conclusion, the contribution of this paper is very marginal thus not sufficient to be accepted for publication in TRE.

## Reviewer #1: 
This paper focuses on the joint transportation of an alliance of logistics companies and its related challenges, i.e., freight task assignment and profit allocations. The authors model the freight task assignment as a Collaborative Multi-depot Vehicle Routing Problem (CMDVRP), develop a two-stage Simulated Annealing (SA) algorithm and a Variable Neighborhood Search (VNS) algorithm to solve this problem respectively, and compare their performances. Five types of profit allocation strategies are considered in this paper. The proposed models are implemented to a case to demonstrate the model performance. 

Although this paper is interesting, I am concerned about its limited contribution to the literature and its significant flaws. Therefore, I recommend rejection on this paper. My detailed comments are as follows:
贡献不足
1. This study does not have enough innovations in both topic and methodology to make significant contributions to the literature. The joint transportation essentially enables each logistics firm to use other firms' distribution centers for transshipment. The benefits of transshipment have already been discussed in Hall (1987) and Daganzo (2005). For CMDVRP, I also find resemblances between this paper and other studies in the literature, e.g., Wang et al. (2017), Wang et al. (2020), and Wang et al. (2021). However, authors do not mention these studies and fail to thoroughly discuss them in the literature review for CMDVRP part. Therefore, the contribution of this study regarding CMDVRP is not convincing. The solution approaches used in this paper are very standard procedures from literature. For profit allocation, four out of five strategies considered in this study are obtained from the literature. The weighted equal cost savings allocation strategy proposed by this paper assumes that the contribution of each firm within an alliance is determined by its pre-collaboration revenue, which can hardly be considered as a major contribution.
与其他文献有相似性Wang et al. (2017), Wang et al. (2020), and Wang et al. (2021)，但作者没有提及；

References: 
Daganzo, C. (2005). Logistics systems analysis. Springer Science & Business Media.
Hall, R. W. (1987). Direct versus terminal freight routing on a network with concave costs. Transportation Research Part B: Methodological, 21(4), 287-298.
Wang, Y., Ma, X., Li, Z., Liu, Y., Xu, M., & Wang, Y. (2017). Profit distribution in collaborative multiple centers vehicle routing problem. Journal of cleaner production, 144, 203-219.
Wang, Y., Zhang, S., Guan, X., Peng, S., Wang, H., Liu, Y., & Xu, M. (2020). Collaborative multi-depot logistics network design with time window assignment. Expert Systems with Applications, 140, 112910.
Wang, Y., Li, Q., Guan, X., Xu, M., Liu, Y., & Wang, H. (2021). Two-echelon collaborative multi-depot multi-period vehicle routing problem. Expert Systems with Applications, 167, 114201.

2. This paper has major flaws in the mathematical formulation of CMDVRP, by failing to (i) eliminate subtours in the VRP; and (ii) ensure enough inventory at each distribution center to serve its assigned customers (the inventory at each distribution center should also be a variable). 
缺少子环消除约束；
确保每个配送中心有足够的库存为其指定的客户提供服务；
3. The two-stage simulated annealing framework proposed in this paper is not satisfactory. 
(i) In the first stage, the algorithm assigns customers to their nearest distribution centers, and the assignment of customers will not be changed when optimizing the CMDVRP. This assignment strategy only makes sense if customers go to the distribution centers by themselves. However, it is not the optimal strategy if distribution centers dispatch vehicles to visit customers. The results from the first step in the algorithm on page 12 can only be considered as an initial solution, and it is necessary to keep perturbing and updating the customers' assignments to search for the near-optimal solution. The VNS implementation in this paper also has this issue.
(ii) Randomly generating routes to seek initial feasible solutions as described in algorithm step 3 on page 12 is an unsound method. It may take a very long time to find a feasible solution, and the obtained solution could be a bad starting point to run the simulated annealing algorithm. I would suggest the authors consider using the cluster-first-route-second type of heuristics to generate the initial feasible solution, such as the Two-phase assignment approach (Fisher and Jaikumar, 1981). References: Fisher, M. L., & Jaikumar, R. (1981). A generalized assignment heuristic for vehicle routing. Networks, 11(2), 109-124.
(iii) The types of local perturbations are very limited in this paper. The authors should customize the perturbation strategies, instead of sticking to the most basic methods. 
两阶段模拟退火框架并不令人满意。
（1）在第一阶段，算法将客户分配到最近的配送中心，在优化CMDVRP时，客户分配不会改变。只有当客户自己去配送中心时，这种分配策略才有意义。然而，如果配送中心派遣车辆拜访客户，这并不是最佳策略。调查结果第12页算法中的第一步只能被视为初始解，有必要不断扰动和更新客户的分配，以寻找接近最优的解。本文中的VNS实现也存在这个问题。
（2）如第12页算法步骤3所述，随机生成路线以寻求初始可行解是不可靠的方法。这可能需要很长时间才能完成㼿找到一个可行的解，得到的解可能是运行模拟退火算法的一个不好的起点。我建议作者考虑使用集群。我建议作者考虑cluster-first-route-second启发式算法，以生成初始可行解，例如两阶段分配法Fisher, M. L., & Jaikumar, R. (1981)，A generalized assignment heuristic for vehicle routing. Networks, 11(2), 109-124.
（3）本文中的局部扰动类型非常有限，应该指定扰动策略。

4. The comparison between SA and VNS in this study is not convincing. First, both of these two algorithms are able to jump out of the local optimum. The statement of SA's weakness as compared to VNS on page 13 "…But it is prone to fall into the local optimum and be difficult…" is not accurate. VNS is also not able to guarantee a global optimum. The performance of algorithms heavily rely on the initial solution, local perturbation, and parameter values. In addition, this paper implements these two algorithms with different methods for generating initial feasible solutions and perturbing solutions. Therefore, the comparison is not meaningful. Based on the results in Table 3 and Figure 10, the differences between these two solution approaches are not significant, which makes me wonder about the benefits of implementing both algorithms and making the comparisons.
SA和VNS之间的比较并不让人信服。首先，这两种算法都能跳出局部最优，但是13页写了SA的劣势是容易陷入局部最优，这是不准确的。
5. The sections for SA and VNS can be pruned. The implementations of these two algorithms in this paper are very standard procedures, which should be well known to the readers of this journal and do not need 6 pages of paper to explain the basic concepts. Therefore, I would suggest the authors remove the detailed explanation of the common knowledge in this domain, and emphasize their original ideas.
SA和VNS的部分可以删减，两种算法的实现都是非常标准的流程，不需要陈述过多。
6. The background of the numerical experiment is not clear. Although the authors introduce Zallsoon service at the beginning of section 5, the statement of "…In this paper, a typical logistics alliance composed of four firms (labeled A-D) is selected as the research object…" on page 20 indicates that the numerical study looks at a theoretical case. The authors should clarify whether the numerical study is based on a real-world case or a self-defined theoretical case. In addition, this paper does not list the parameter values in section 5 and fails to provide the context of the numerical case. Last but not the least, the sensitivity analysis is missing, and it is difficult to draw managerial insights from the results of one single case.  
数值实验的背景不清楚， 应澄清数值研究是基于现实世界的案例还是设计的案例。此外，本文没有列出第5节中的参数值，也没有提供数值案例的背景，缺少敏感性分析。
7. Section 6 should be rearranged. I would suggest moving the first paragraph to the introduction, since it is the background information. The authors do not mention the context of the discussion in the second paragraph, e.g., the study area size and the number of customers. Thus, the discussion could be misleading.
第6节应该重新安排，建议把第一段放在intro，第二段没有提到背景，如研究区域大小及客户的容量。
8. Overall, the writing should be improved. There are many long sentences without proper punctuations, making it difficult for readers to grasp the gist of authors' ideas. For example: 
        The first sentence of Section 1 Introduction: "With extensive applications of E-commerce and more personalized consumption demand of customers, the distribution of goods is characterized by small batch, high frequency, and timeliness, and fuel prices have been rising in recent years, both of which lead to high logistics cost and social problems such as urban traffic congestion and air pollution." Comment: The logic is unclear. How will high fuel price lead to congestion?
        Top paragraph on page 3: "Mancini (2016) investigates the multi-depot multi-period vehicle routing problem with a heterogeneous fleet with the goal of minimizing the total delivery cost and puts forward an adaptive large neighborhood search based matheuristic approach to solve the problem." Comment: There is a typo "matheuristic", and there is no punctuation within this 40-word sentence.
        Last paragraph on page 3: "Therefore, when solving the assignment problem of freight tasks in joint transportation, the cargo transfer process and the cargo delivery process need to be taken into account simultaneously, including the transportation cost and constraints of two processes, which is called the collaborative multi-depot vehicle routing problem (CMDVRP), and can be studied as MDVRP with collaborative gaming among multiple distribution centers." Comment: the collaborative multi-depot vehicle routing problem should refer to the assignment problem, but "which" in this sentence seems to be misplaced.
In addition, some phrases in the paper are not common expressions, e.g., "reduces the total cost by the average of about 16%" in the abstract; "solving difficulty" on page 10 may be replaced with "computational difficulties"; "Let denote by the current solution S" on page 15.
写作应该提高，有很多长句没有正确的标点符号。





## Reviewer #3: 
Title: Cost Allocation in Joint Transportation

Overview and general recommendation:

The joint transportation is an important topic both in practice and academic. It helps to reduce cost, improve efficiency and more environmentally friendly comparting to separate management. This paper discussed two important problems in the collaborative transportation: vehicle routing and cost allocation. The authors proposed a collaborative multi-depot vehicle routing model to solve both transfer and delivery routing by minimizing the total cost. The paper is well written and structured. However, this is a well-known problem, based on previous literature the CMDVRP model presented in the paper and SA algorithm applied to solve the model has been studied and applied widely in academia and business. Both topic and methods in the paper lack of novelty. This is a good case study but has no sufficient contribution to the research field. Therefore, my recommendation is Major Revision. 
SA算法已经很成熟，没有新颖性，这是一个很好的案例研究，但是理论贡献不足。建议大修

Major comments: 
1.      Methodology: 
1)      I would ask the authors to specify the main contribution and novelty of the paper.
我想请作者详细说明论文的主要贡献和新颖之处。

3)      The algorithm to solve the vehicle routing problem is not new and not proposed by the author. There are all various of algorithms to solve the routing problem, why choose simulated annealing? In addition, shortage of transportation capacity is not considered, and the dynamic customer demand is not considered in the vehicle routing problem. 
解决车辆路径问题的算法不是新的，也不是作者提出的。有各种各样的算法来解决路由问题，为什么选择模拟退火呢？此外，车辆路径问题没有考虑运输能力的不足，也没有考虑动态的客户需求。
5)      In the weighted equal cost savings method, can you explain why the revenue is used to measure the contribution of firm in joint transportation since revenue represents a total income and general? It can't denote the quantity and quality of freight tasks can be provided by member firm or willing to contribute. And more importantly, regarding the performance of stakeholders in the joint transportation, how to measure them and taken as weight is more practical.
在加权等成本节约法中，你能解释为什么收入用于衡量公司在联合运输中的贡献，因为收入代表总收入和一般收入吗？它不能表示成员公司或愿意提供的货运任务的数量和质量。更重要的是，关于利益相关者在联合运输中的表现，如何衡量它们并将其作为权重更为实际。
7.      Interpretation of the results: 
8)      Page 23, paragraph 3: The conclusion of "In general, the monotonicity and super additivity properties hold (Lozano et al., 2013), since adding new members will increase the possibilities for the optimization of vehicle loading and vehicle routing, both pushing the reduction of transportation cost. "the statement is missing rigorous simulation or theory support.  
第23页，第3段：“一般来说，单调性和超可加性属性成立（Lozano等人，2013年），因为增加新成员将增加优化车辆装载和车辆路线的可能性，这两个因素都推动了运输成本的降低。”该声明缺少严格的模拟或理论支持。
10)      Cost allocation is not discussed in the implementation and benefits section.
成本分配在实施和效益部分没有讨论。
Minor comment:
Typos: section 2.2 paragraph 1 line 5: "The cargo weight of each customer j is qj."
拼写错误：第2.2节第1段第5行：“每个客户的货物重量j为qj。”



## Reviewer #4: 
Overall, the manuscript is very well written and the objective of the study is very well defined. I liked the structure of the paper and the topic surely worthy of investigation. 
My only issue is with the lack of data and the applicability of the process. I understand that the authors used a numerical experiment to show their proposed approach applicability , but it would be really interesting to explore how this work on a real dataset (of course if available).


