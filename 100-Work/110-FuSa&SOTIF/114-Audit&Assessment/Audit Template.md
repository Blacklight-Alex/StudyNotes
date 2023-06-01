# 1. Common
## 1.1. General quality management strategy
- criteria：操作质量管理系统 TS16949, ISO9001
- objective：评估通用质量管理策略的执行情况
- Audit method：检查质量管理的状态，例如认证、评估报告等
- Reference：
	 ISO 26262 part 2：5.4.5.1
## 1.2. General competence management strategy
- Criteria：
	 Genral competence management strategy and application to the project（incl. R&R definition）
	 -- sufficient level of skills，experience（domain knowledge，management experience）
	 -- Training，qualification program
	 -- Understanding of ISO26262 standard
	 -- Understanding of own functional safety process
- Objective：
	 Evaluation of implementation of general competence management strategy
- Audit Method：
	 Review competence criteria and comparison with the responsibility in safety plan
- Reference：
	 ISO 26262 part 2:5.4.2.7
- Findings（Best practice & Guideline）：
	 Safety plan v2.0
	 BMS Development Engineers：10 Total（includes SM）
	 Definition from Role definition/required skills，knowledge（level D-A）
	 Tier 1 identifies required skills and knowledge for the persons involved in the execution of the safety lifecycle
## 1.3. DIA strategy
- Criteria
	 DIA strategy and application to the project
- Objectives：
	 Evaluation of DIA strategy
- Finding：
	 WP, RASIC（FuSa-DIA Tier1 Li batterie 0.6 tailoring files）
	 OEM and Tier 1（supplier）make a Distributed Interface Agreement to describe the procedures and to allocate associate responsibilities within developments of 12V battery Management System using template suggested by the customer
- Reference：
	 ISO 26262 part 2：6.4.6.5
## 1.4. Safety culture
- Criteria：
	 Safety culture for functional safety
	  -create，foster，sustain of safety culture
	  -process & organization-specific rules for ISO 26262
	  -communication / resolution process for identified functional safety anomalies（with safety manager）
	  -procure required resources for FS（human resource (SM), tools (FSM Tool), templates (ISO 26262 template), DB, etc）
	  -continuous improvement process
	  -ensure authorities of SM (incl. Engineer，supporting persons)
- Objectives：
	 Evaluation of effectiveness of measure to create，increase and sustain safety culture
	 评估建立、加强和维持安全文化措施的有效性
- Audit Method：
	 Interview with safety manager
	 面试功能安全经历
- Reference：
	 ISO 26262 part 2：5.4.2.1 & 5.4.2.2 & 5.4.2.3 & 5.4.2.5 & 5.4.2.6 & 5.4.2.7
- Findings：
	 Tier 1 institutes，executes and maintain organization-specific rule to maintain safety culture
	 Tier 1制定、执行和维护特定的组织规则，以保证安全文化
	 - Functional safety part is independent from development part
	 - 功能安全部门独立于开发部门
	 - Generic safety plan and process are described as standard process
	 - 通用的安全计划和流程按照标准的流程进行描述
	 - Functional safety anomalies are explicitly communicated in weekly meeting with stack-holders
	 - 功能安全异常应在每周的例会上与相关人员进行明确的沟通
	 - Resource required for the achievement of functional safety are identified in safety plan
	 - 在安全计划中明确实现功能安全目标所需的资源
	 - Tier 1 reflects recommendations from functional safety assessment to continue improvement of achievement of function safety
	 - Tier 1 反映功能安全评估的建议，以便继续改进实现功能安全目标
	 - Functional safety manager is independent from development part. Functional safety manager participates verification review activities of work product
	 - 功能安全经理独立于开发部门。功能安全经历参加交付件的验证评审活动
## 1.5. Project manager
- Criteria
	 - Appointment of PM at the initiation of item development
	 - Definition of responsibility and authority（for safety activities，ISO 26262 compliance）
	 - Verification of required resource for functional safety activities（human resource (SM), tools (FSM Tool), templates (ISO 26262 Template), DB, etc）
	 - Appointment of SM
- Objectives：
	 Evaluation of Project manager‘s role and responsibility
- Finding：
	 Review of safety plan，project plan
- Reference：
	 ISO 26262 part 2：6.4.2.1 & 6.4.2.2 & 6.4.2.3 & 6.4.2.4
## 1.6. customer safety requirements collection and analysis
- Criteria
	 Method to collect safety requirements from the pool of customer‘s requirements
- Objectives：
	 Evaluation of customer safety requirements collection and analysis
- Finding：
	 Interview with safety manager. Brief review collected and analyzed safety requirements
- Reference：
	 based OEM FuSa RFQ
# 2. Safety planning for system development
## 2.1. Planning of overall safety activities on system development phase
## 2.2. Planning of TSR specification
## 2.3. Planning for system design
## 2.4. Planning for item integration and testing（Not scope）
## 2.5. Planning forsafety validation（Not scope）
## 2.6. Planning for release for production（Not scope）
## 2.7. Approval of the safety plan
## 2.8. General strategy for confirmation measure at system development phase
## 2.9. Distinguishing safety activities from project plan
## 2.10. Safety plan management history
## 2.11. General strategy for safety case
## 2.12. General work products management strategy
## 2.13. General change management strategy
# 3. TSR specification
## 3.1. Selection of TSR description notation
不同ASIL等级的TSR要求使用的描述语言不同，ASIL C/D要求使用半形式化的语言
## 3.2. Consistency check with FSR
TSR与上层的FSR是否一致，FSR分配在系统架构上，产生TSR
## 3.3. Context of TSR
检查 TSR 的内容是否全面，包括：安全机制；故障检测，故障反映；告警和降级策略；安全状态（传递条件，FTTI）；紧急操作间隔（可选）；避免潜伏故障；对其他系统、相关项的依赖；TSR 和安全机制在系统层面的融合
## 3.4. Attributes of TSR
## 3.5. Specification of safety mechanisms for latent faults
定义对于潜在故障的的安全机制；残余风险目标值；TSR 的 ASIL 等级
## 3.6. TSR verification activities
TSR 的审核活动：走读，审查；形式化验证等
## 3.7. TSR management status
FSR-TSR-HSR/SSR 的分等级；TSR 按照安全机制/系统元素等分组；FSR 的完整性；外部一致性
## 3.8. Traceability of TSR
TSR 的追溯性：FSR；和每个系统设计定义的内容；和测试内容
## 3.9. Configuration and change management of TSR specification
记录 TSR 的更改
## 3.10. Document management of TSR & specification

## 3.11. Monitoring of TSR specification activities based on safety plan
跟 safety plan 的一致性
# 4. ASIL decomposition
# 5. System design specification
## 5.1. Application of regulatory requirements on TSR
除技术安全要求外，如果有法规或标准对该功能提出功能安全要求，也要考虑
## 5.2. System design specification(incl. TSC)
按照标准的定义，TSR应该具有的内容是否都包含了
## 5.3. Design for random HW failure
应该定义故障检测、控制、消减的措施，定义SPFM/LFM/残余风险的故障率目标值，检查安全机制的诊断覆盖率和ASIL等级是否匹配
## 5.4. Fulfillment of coexistence criteria
检查是否满足共存标准，才能分配不同的ASIL等级
## 5.5. Application of well-trusted automotive system design
检查是否复用了其他可信赖的自动驾驶系统或元素，例如使用了MCU自带的安全机制，应该附上MCU安全手册
## 5.6. Application of modular design
检查系统架构是否符合模块化设计，是否定义了模块间的交互接口
## 5.7. Custom HW element
检查是否使用了消费级硬件元素，例如FPGA，不同于MCU，内部没有安全机制
## 5.8. Traceability of system design
检查TSR、TSC和safety mechanism之间的关联性
## 5.9. Configuration and change management of system design specification
检查设计规范是否有配置和变更记录
## 5.10. Document management of system design specification
TSR、TSC文档的格式是否满足要求
## 5.11. Monitoring of system design activities based on safety plan
检查安全计划的要求是否一致，例如进行的活动、采用的安全分析方法等
# 6. Safety analysis
# 7. HSI specification
# 8. System design verification

