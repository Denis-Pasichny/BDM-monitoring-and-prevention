This project is based on earlier work presented by Dr. Nadav Nitzan https://www.linkedin.com/in/dr-nadav-nitzan-7a33a315/ and others. Huge thanks for inspiring me to contribute to this topic.

**INTRODUCTION**
Basil Downy Mildew(BDM) is considered a dire threat when it comes to the overall well being of the Basil growing industry in Israel. It can and will wipe out this plant if left unchecked.

Current BDM prevention mechanisms (in Israel) are based on heuristically fumigating plants ("Treatment") inside a greenhouse when certain environmental conditions are met.
This approach is rigid and therefore relays on excess of 30% to 40% more chemicals.
Moreover, the pathogen Peronospora belbahrii , which gets exposed to greater quantities of fungicidal preparations, spurs new variants which are resistant to those types of treatments.

Taking into account food regulations and the impose of ever decreasing amounts of alternative treatments, It is evident that a new and better approach must be implemented in order to keep Basil a productively growable product in Israel.

I would like to use Agentic AI in the hopes of finding new metrices or/and improve given ones in order to make the BDM treatment more effective and as a result, decrease dosage of chemicals used, hence less resistant variants. I will be focusing on weather conditions as a possible factor that has not been accounted for as of yet.

**WHY I USE AGENTIC AI**
Using Agentic AI can assist me in achieving the above mentioned goal in a couple of ways:

DATA PROCESSING - Agricultural research is a field which accumulates a lot of data. By using pattern learning algorithms, we can process this data to help gain insights no human can acquire nakedly.

IMPLEMENTATION - Growers, farmers and researchers lack the skills to develop their own software and usually don't have the means to hire a professional to do so. However, they can certainly articulate their desire to an agents' system via it's LLM component and get a solution that way.

STRUCTURE - The way Agentic AI operates, it exercises a broad set of tools and experts which amplify the potential to solve a given human made problem.
Conveniently, it's reasoning process is open to us (the user) and can be judged and corrected/self corrected based on metrices.

FUN AND EDUCATIONAL - Finally, it looks awesome and cool to be able to use the ADK toolkit :)

**ARCHITECTURE OVERVIEW**
![https://www.canva.com/design/DAG5tcZuCYc/qNfig-CvSiajahxynreW-w/edit?utm_content=DAG5tcZuCYc&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton](url to embed)

**Agents**
1.`assert_agent` - His duty is to process user's request, understand it and delegate the task to `task_master_agent`. At the end it summarizes the answer before presenting it to the user.
2.`task_master_agent` - Evaluates the kind of input presented by the assert_agent and dictates the modus operandi. It either calls `calc_infection_severity()` tool or asks weather_agent to extract climate parameters based on user's input.
3.`weather_agent` - His only task is to get climate parameters for a specific place on earth by connecting to an external service such as Climate services information system(CSIS), getting the appropriate info and returning it to task_master_agent.

**Custom tools**
`calc_infection_severity()` - Get temperature, humidity, moisture values and calculate potential infection severity index(1-5).

**Build-in tools**
Gemini.1.25 - used to process user's messages.
Code Executioner - Builds Inline code if the need arises. May be called only by task_master_agent

**Execution scenarios/ Input types**
Three different procedures might occur with respect to how the user interacts with the Agentic system.
1.The user decides to query about topics unrelated to BDM, resulting in a gentlemen's response from the assert_agent, explaining that the Agent only processes request concerning BDM.
2.The user asks for guidelines concerning BDM prevention while having exact environmental conditions in which Basil was grown and would like to assess the Severity Disease Index (SDI) in order to plan for treatment.
3.The user doesn't have precise environmental measurements, but can provide other means of useful information such as date, time or maybe geographical region, out of which SDI can be deduced.
