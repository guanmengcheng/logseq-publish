# Post-purchase regret推进情况

## 2022.3.21
1. 增加Robustness checks
已增加poisson和xtprobit
2. 

## 2022.3.28
- [x] 找到xtlogit与robustness checks样本数不一致的原因
 xtlogit在回归的时候部分变量样本太少导致变量被omit，比如商品品类8（type_8），写到表格下的note中
 ![[Pasted image 20220328172413.png|inl|300]]![[Pasted image 20220328172603.png|inl]]

 - [ ] regression results后面加上$R^2$的值

- [ ] 完善文献综述，增加group buying篇幅，重新写post-purchase regret

- [x] 校对与会议论文不一样的地方 
   
- [x] 会议论文里的hypothesis的argue放过来

- [x] 尝试xtpoisson
不行，无法收敛，xtnbreg也无法收敛













