
# How to grow from senior to lead role

[Reference from TLDR gmail](https://newsletter.eng-leadership.com/p/how-to-grow-from-senior-to-a-lead?r=2bjtip)

- After grown to senior engineering position, might feel ecstatic.
	- First thing to think, what else can learn and grow more.
	- Dont feel stuck in the position, engineering have the unlimited knowledge to absorb.
	- Think how to grow from engineering to lead.
- Make a choice, Tech Lead or Team Lead?
	- Which growing path suitable to you
		- Management (Engineering Manager)
		- IC (Staff Engineer)
		- Architecture (Software Architect)
	- Tech Lead:
		- More Technical Direction and Less People Management
	- Team Lead:
		- More People Management and Less Technical Direction
- Make sure to let your manager know about your goals and aspirations
	- They will not be able to put you in the position to showcase the skills needed to grow that position.
	- There is also a limited scope that your manager can see about what you are doing daily.
	- Note the wins close down.
- Keep a brag list of all the wins that you achieved
	- Your manager will not see what you have done all of the wins.
	- When the time comes to talk about the promotion, the values that you have, you can pick up your win lists that you achieved.
	- It will help you immensely.
	- No matter the role you currently hold, this is really important to do.
- Become product-minded
	- A good software engineering thinks like a product manager.
- Quotes
	- “Sitting back and not asking for feedback is the worst thing you can do as an engineer. If you want to improve, there has to be a constant feedback loop.” — Ankur Tyagi
	- “The brag list will also help jog your memory for writing resumes and answering behavior and technical deep dive interviews.” — Mike Thornton
	- “Find opportunities and ask for them instead of waiting to be given.” — Anemari Fiser

# Work Place (TS) Senior Experience
## chinese

### 三大纪律

- 未经授权别操作
- 变更不要在白天
- 预期有异赶紧停

### 八项注意

- 安全规范记心头
- 数据安全大过天
- 应急预案必须有
- 分析复盘要及时
- 出现故障先通报
- 技术经理快到厂
- 恢复业务是首要
- 客户满意最优先

### 建议

- 机器管理上面的事情
- 建立在一个运维的系统之上
- 自动化
- 优化，运用，中间件
- 备份，安装，故障处理
- 工作原理
- 优化系统
- query 怎么去运作
- 了解中间件的原理

1. 多学习，多实践，实验，试错
2. 理解深处的原因
3. 遇到问题不要只停留在表面

## english

### Top 3 rules

- Dont operate without authorization
- Dont change during the day
- Stop when there is an exception

### Top 8 attentions

- Safety regulations are in mind
- Data security is the most important thing
- There must have an emergency plan (Plan B)
- Analyze and review in time
- Report to the manager when there is an exception
- The manager should come to the scene as soon as possible
- Restore business is the top priority
- Customer satisfaction is the top priority

### Suggestions

- Machine management
- Build on top of an operation and maintenance system
- Automation
- Optimization, application, middleware
- Backup, installation, fault handling
- Working principle
- Optimize the system
- How query works
- Understand the principle of middleware

1. Learn more, practice more, experiment, trial and error
2. Understand the deep reasons
3. Dont just stay on the surface when encountering problems

# New Bluetooth Flaw Let Hackers Take Over Devices

[Reference from thehackernews](https://thehackernews.com/2023/12/new-bluetooth-flaw-let-hackers-take.html?_m=3n%2e009a%2e3220%2ene0ao45e79%2e27nu)

- CVE-2023-45866
- This issue is related to the case of authentication bypass that enables attackers to connect to susceptible devices and inject keystrokes to achiueve code execution as the victim.
- "Multiple Bluetooth stacks have authentication bypass vulnerabilities that permit an attacker to connect to a discoverable host without user confirmation and inject keystrokes." - Marc Newlin
- The attack taking advantages the target device with "unauthenticated pairing mechanism", such as keyboard, mouse, smart lock, that using bluetooth.
- Attacker connected sucessfully to the target device, attacker can inject keystrokes to install apps and run arbitrary commands.
- Attacker can just performe the attack using Linux computer with a regular Bluetooth adapter. It is not require any specilized hardware.
- The vulnerability affects a wide range of devices running Android, Linux, iOS, and macOS.
- The bug affects macOS and iOS when Bluetooth is enabled and a Magic Keyboard has been paired with the victim's device.
- Also works on Apple's LockDown mode.
- "could lead to remote (proximal/adjacent) escalation of privilege with no additional execution privileges needed." - Google