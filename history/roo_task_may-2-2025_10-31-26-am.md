**User:**

<task>
幫我建立一個 AI Agent 提示詞 內容使用英文
需要符合規範

此 AI Agent 專用撰寫 prisma 的 repository
只建立基礎的功能 findById findAll create  update delete count
不需要額外 inclde 等等

workflow 的部份 需要跟使用者互動
詢問使用者需要建立那一張 table
並且告知輸出 會加入什麼檔案 什麼 repository
有哪些方法 等等

import 的位置是固定範例

'user-repository.ts' (see below for file content)
</task>

<file_content path="user-repository.ts">
 1 | /**
 2 |  * 用戶存儲庫
 3 |  * 負責所有與用戶相關的數據存取操作
 4 |  */
 5 | 
 6 | import type { Prisma, User as PrismaUser } from "../../generated/prisma/client";
 7 | import { prisma } from "../prisma-client";
 8 | import type { ExtendedPrismaClient } from "../prisma-client";
 9 | 
10 | export class UserRepository {
11 |   /**
12 |    * 構造函數，通過依賴注入接收 Prisma 客戶端
13 |    * @param prisma Prisma 客戶端實例
14 |    */
15 |   constructor(private prisma: ExtendedPrismaClient) {}
16 | 
17 |   /**
18 |    * 根據ID查找用戶
19 |    */
20 |   async findById(id: number): Promise<PrismaUser | null> {
21 |     return this.prisma.user.findUnique({
22 |       where: { userId: id },
23 |     });
24 |   }
25 | 
26 |   /**
27 |    * 查找多個用戶，可選過濾與分頁
28 |    */
29 |   async findAll(
30 |     where?: Prisma.UserWhereInput,
31 |     orderBy?: Prisma.UserOrderByWithRelationInput,
32 |     skip?: number,
33 |     take?: number,
34 |   ): Promise<PrismaUser[]> {
35 |     return this.prisma.user.findMany({
36 |       where,
37 |       orderBy,
38 |       skip,
39 |       take,
40 |     });
41 |   }
42 | 
43 |   /**
44 |    * 創建新用戶
45 |    */
46 |   async create(data: Prisma.UserCreateInput): Promise<PrismaUser> {
47 |     return this.prisma.user.create({
48 |       data,
49 |     });
50 |   }
51 | 
52 |   /**
53 |    * 更新用戶信息
54 |    */
55 |   async update(id: number, data: Prisma.UserUpdateInput): Promise<PrismaUser> {
56 |     return this.prisma.user.update({
57 |       where: { userId: id },
58 |       data,
59 |     });
60 |   }
61 | 
62 |   /**
63 |    * 刪除用戶
64 |    */
65 |   async delete(id: number): Promise<PrismaUser> {
66 |     return this.prisma.user.delete({
67 |       where: { userId: id },
68 |     });
69 |   }
70 | 
71 |   /**
72 |    * 根據條件計算用戶數量
73 |    */
74 |   async count(where?: Prisma.UserWhereInput): Promise<number> {
75 |     return this.prisma.user.count({
76 |       where,
77 |     });
78 |   }
79 | }
80 | 
81 | // 導出單例實例
82 | export const userRepository = new UserRepository(prisma);

</file_content>
<environment_details>
# VSCode Visible Files
user-repository.ts

# VSCode Open Tabs
.github/prompts/elysia-routes-typescript.prompts.md,.github/prompts/services-typescript.prompts.md,user-repository.ts

# Current Time
5/2/2025, 10:27:57 AM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
(Not available)

# Current Cost
$0.00

# Current Mode
<slug>lang-gpt-prompts</slug>
<name>lang-gpt.prompts</name>
<model>openai/gpt-4.1</model>


# Current Workspace Directory (/home/bevis/repo/LangGPT) Files
.gitignore
LICENSE
Docs/
Docs/【论文中文版】LangGPT：面向大模型的自然语言编程框架.pdf
Docs/AgentsResume.md
Docs/GPTBestPractise.md
Docs/HowToWritestructuredPrompts.md
Docs/PPT_Agents_LangGPT.pdf
Docs/PromptAnnualReview.md
Docs/PromptChain.md
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片1.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片2.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片3.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片4.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片5.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片6.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片7.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片8.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片9.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片10.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片11.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片12.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片13.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片14.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片15.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片16.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片17.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片18.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片19.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片20.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片21.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片22.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片23.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片24.PNG
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/幻灯片25.PNG
Docs/imgs/agiclink_p2.jpg
Docs/imgs/aigclink_p1.png
Docs/imgs/aigclink_p3.jpg
Docs/imgs/aigclink_p4.jpg
Docs/imgs/image-1.png
Docs/imgs/image-2.png
Docs/imgs/image-3.png
Docs/imgs/image-4.png
Docs/imgs/image-5.png
Docs/imgs/image-6.png
Docs/imgs/image-7.png
Docs/imgs/image-8.png
Docs/imgs/image-9.png
Docs/imgs/image.png
Docs/imgs/inputPredict.png
Docs/PromptAnnualReview/AIGC_20240113_meeting_1.jpg
Docs/PromptAnnualReview/AIGC_20240113_meeting_2.jpg
Docs/PromptAnnualReview/AIGC_20240113_meeting_3.jpg
Docs/PromptAnnualReview/AIGC_20240113_meeting_4.jpg
Docs/PromptAnnualReview/AIGC_20240113_meeting_5.jpg
Docs/PromptAnnualReview/幻灯片1.PNG
Docs/PromptAnnualReview/幻灯片2.PNG
Docs/PromptAnnualReview/幻灯片3.PNG
Docs/PromptAnnualReview/幻灯片4.PNG
Docs/PromptAnnualReview/幻灯片5.PNG
Docs/PromptAnnualReview/幻灯片6.PNG
Docs/PromptAnnualReview/幻灯片7.PNG
Docs/PromptAnnualReview/幻灯片8.PNG
Docs/PromptAnnualReview/幻灯片9.PNG
Docs/PromptAnnualReview/幻灯片10.PNG
Docs/PromptAnnualReview/幻灯片11.PNG
Docs/PromptAnnualReview/幻灯片12.PNG
Docs/PromptAnnualReview/幻灯片13.PNG
Docs/PromptAnnualReview/幻灯片14.PNG
Docs/PromptAnnualReview/幻灯片15.PNG
Docs/PromptAnnualReview/幻灯片16.PNG
Docs/PromptAnnualReview/幻灯片17.PNG
Docs/PromptAnnualReview/幻灯片18.PNG
Docs/PromptAnnualReview/幻灯片19.PNG
Docs/PromptAnnualReview/幻灯片20.PNG
Docs/PromptAnnualReview/幻灯片21.PNG
Docs/PromptAnnualReview/幻灯片22.PNG
Docs/PromptAnnualReview/幻灯片23.PNG
Docs/PromptAnnualReview/幻灯片24.PNG
Docs/PromptAnnualReview/幻灯片25.PNG
Docs/PromptAnnualReview/幻灯片26.PNG
Docs/PromptAnnualReview/幻灯片27.PNG
Docs/PromptAnnualReview/幻灯片28.PNG
Docs/PromptAnnualReview/幻灯片29.PNG
Docs/PromptAnnualReview/幻灯片30.PNG
Docs/PromptAnnualReview/幻灯片31.PNG
Docs/PromptAnnualReview/幻灯片32.PNG
Docs/PromptAnnualReview/幻灯片33.PNG
Docs/PromptAnnualReview/幻灯片34.PNG
Docs/PromptAnnualReview/幻灯片35.PNG
Docs/PromptAnnualReview/幻灯片36.PNG
examples/
examples/chinese_xiaohongshu_writer/ChatGPT-小红书爆款生成器对话.md
examples/chinese_xiaohongshu_writer/xhs_title.jpg
history/
history/roo_task_apr-22-2025_1-34-43-pm.md
history/roo_task_apr-22-2025_1-39-41-pm.md
history/roo_task_apr-22-2025_2-09-15-pm.md
history/roo_task_apr-22-2025_11-28-59-am.md
history/roo_task_apr-22-2025_11-50-27-am.md
history/roo_task_apr-22-2025_12-26-40-pm.md
history/roo_task_apr-23-2025_3-43-29-pm.md
history/roo_task_apr-23-2025_4-24-07-pm.md
history/roo_task_apr-23-2025_5-03-33-pm.md
history/roo_task_apr-23-2025_5-20-01-pm.md
history/roo_task_apr-23-2025_5-29-36-pm.md
history/roo_task_apr-23-2025_11-23-51-am.md
history/roo_task_apr-23-2025_11-42-07-am.md
history/roo_task_apr-24-2025_3-40-11-pm.md
history/roo_task_apr-24-2025_4-55-53-pm.md
history/roo_task_apr-24-2025_9-51-58-am.md
history/roo_task_apr-24-2025_10-32-08-am.md
history/roo_task_apr-24-2025_11-50-56-am.md
history/roo_task_apr-24-2025_11-57-50-am.md
history/roo_task_apr-24-2025_12-10-45-pm.md
history/roo_task_apr-25-2025_9-12-30-am.md
history/roo_task_apr-25-2025_9-52-33-am.md
history/roo_task_apr-25-2025_10-18-09-am.md
history/roo_task_apr-25-2025_10-21-59-am.md
history/roo_task_apr-25-2025_10-46-44-am.md
history/roo_task_apr-25-2025_11-11-24-am.md
history/roo_task_apr-25-2025_11-24-10-am.md
history/good/roo_task_apr-30-2025_5-41-40-pm-with-elysia-routes-typescript.prompts-v1.3.md
imgs/
imgs/logo.png
imgs/wx_tmp.jpg
LangGPT/
Papers/
Papers/LangGPT_paper_cn.md
Papers/README.md
Papers/StructuredPrompting.pdf
Papers/figures/Figure1.png
Papers/figures/Figure2.png
Papers/figures/Figure3.png
Papers/figures/Figure4.png
Papers/figures/Figure5.png
Papers/figures/Table1.png
Papers/figures/Table2.png
Papers/figures/Table3.png
Papers/figures/Table4.png
Papers/figures/Table5.png
PromptShow/
PromptShow/LICENSE
PromptShow/yarn.lock
PromptShow/components/Carbon.js
PromptShow/components/Header.js
PromptShow/components/SnippetToolbar.js
PromptShow/components/Toggle.js
PromptShow/components/Themes/index.js
PromptShow/cypress/util.js
PromptShow/cypress/plugins/index.js
PromptShow/public/favicon.ico
PromptShow/public/manifest.json
PromptShow/public/robots.txt
PromptShow/public/static/react-crop.css
PromptShow/public/static/brand/logo-banner-transparent.png
PromptShow/public/static/presets/0.png
PromptShow/public/static/presets/1.png
PromptShow/public/static/presets/2.png
PromptShow/public/static/presets/3.png
PromptShow/public/static/presets/4.png
PromptShow/public/static/presets/5.png
PromptShow/public/static/presets/6.png
PromptShow/public/static/presets/7.png
PromptShow/public/static/presets/8.png
PromptShow/public/static/presets/9.png
PromptShow/public/static/presets/10.png
PromptShow/public/static/presets/11.png
PromptShow/public/static/presets/12.png
PromptShow/public/static/presets/13.png
PromptShow/public/static/presets/14.png
PromptShow/public/static/presets/15.png
PromptShow/public/static/presets/16.png
PromptShow/public/static/presets/17.png
PromptShow/public/static/presets/18.png
PromptShow/public/static/presets/19.png
PromptShow/public/static/presets/20.png
PromptShow/public/static/presets/21.png
PromptShow/public/static/presets/22.png
PromptShow/public/static/presets/23.png
PromptShow/public/static/presets/24.png
PromptShow/public/static/presets/25.png
PromptShow/public/static/presets/26.png
PromptShow/public/static/presets/27.png
PromptShow/public/static/presets/28.png
PromptShow/public/static/presets/29.png
PromptShow/public/static/presets/30.png
PromptShow/public/static/svg/github.svg
PromptShow/public/static/svg/open-source-companies-2.svg
PromptShow/public/static/svg/open-source-companies.svg
PromptShow/public/static/svg/person.svg
PromptShow/public/static/svg/snippets.svg
PromptShow/public/static/svg/user.svg
PromptShow/public/static/themes/night-owl.min.css
PromptShow/public/static/themes/nord.min.css
PromptShow/public/static/themes/one-dark.min.css
PromptShow/public/static/themes/one-light.min.css
PromptShow/public/static/themes/synthwave-84.min.css
PromptShow/public/static/themes/verminal.min.css
src/

(File list truncated. Use list_files on specific subdirectories if you need to explore further.)
</environment_details>

---

**Assistant:**

# Role: Prisma Repository AI Agent

## Profile

- Author: Vanisoul
- Version: 1.0
- Language: English
- Description:  
  You are an expert AI Agent specialized in generating TypeScript Prisma repository classes. You create repositories with only the essential CRUD and count methods (`findById`, `findAll`, `create`, `update`, `delete`, `count`) for a specified table/model. You strictly follow the import and code structure conventions as demonstrated in the provided `user-repository.ts` example. You interact with the user to determine the target table/model and clearly communicate what files and methods will be generated.

### Prisma Repository Generation Skills

1. Generate TypeScript repository classes for any given Prisma model/table, following the provided code structure and import conventions.
2. Implement only the following methods: `findById`, `findAll`, `create`, `update`, `delete`, `count`.
3. Ensure all imports and type usages match the pattern in the `user-repository.ts` example.
4. Avoid adding extra features such as `include`, relations, or custom queries unless explicitly requested.

### User Interaction & Guidance

1. Guide the user through the process by asking which table/model to generate the repository for.
2. Clearly inform the user about:
   - The file(s) that will be created or modified.
   - The repository class name and its location.
   - The methods that will be included.
3. Confirm with the user before generating or overwriting any files.

## Rules

1. Always follow the import and code structure as shown in the `user-repository.ts` example.
2. Only generate the six basic methods: `findById`, `findAll`, `create`, `update`, `delete`, `count`.
3. Do not add extra features (e.g., `include`, relations, custom queries) unless the user requests them.
4. Never break character or provide information outside your defined role.
5. Do not fabricate facts; base all code and suggestions on the provided example and Prisma best practices.
6. Always interact in English.

## Workflow

1. Greet the user and introduce your purpose as a Prisma Repository Generator.
2. Ask the user which Prisma table/model they want to generate a repository for.
3. After receiving the table/model name, inform the user:
   - The name and path of the repository file to be created (e.g., `xxx-repository.ts`).
   - The class name (e.g., `XxxRepository`).
   - The methods that will be included: `findById`, `findAll`, `create`, `update`, `delete`, `count`.
   - The import structure, which will follow the `user-repository.ts` example.
4. Confirm with the user before proceeding to generate the file.
5. Generate the repository file with the required methods and correct imports.
6. Summarize the result and provide usage guidance.

## Initialization

As a Prisma Repository AI Agent, I will strictly follow the above rules and interact with you in English.  
Hello! I am your Prisma Repository Generator Agent. I help you quickly generate TypeScript repository classes for your Prisma models, following your project's conventions.  
**Workflow:**  
1. Please tell me which Prisma table/model you want to generate a repository for.  
2. I will inform you about the file and class that will be created, and the methods included.  
3. After your confirmation, I will generate the repository file for you.  
Let’s get started! Which table/model would you like to generate a repository for?

---

**User:**

[ERROR] You did not use a tool in your previous response! Please retry with a tool use.

# Reminder: Instructions for Tool Use

Tool uses are formatted using XML-style tags. The tool name is enclosed in opening and closing tags, and each parameter is similarly enclosed within its own set of tags. Here's the structure:

<tool_name>
<parameter1_name>value1</parameter1_name>
<parameter2_name>value2</parameter2_name>
...
</tool_name>

For example:

<attempt_completion>
<result>
I have completed the task...
</result>
</attempt_completion>

Always adhere to this format for all tool uses to ensure proper parsing and execution.

# Next Steps

If you have completed the user's task, use the attempt_completion tool. 
If you require additional information from the user, use the ask_followup_question tool. 
Otherwise, if you have not completed the task and do not need additional information, then proceed with the next step of the task. 
(This is an automated message, so do not respond to it conversationally.)
<environment_details>
# VSCode Visible Files
user-repository.ts

# VSCode Open Tabs
.github/prompts/elysia-routes-typescript.prompts.md,.github/prompts/services-typescript.prompts.md,user-repository.ts

# Current Time
5/2/2025, 10:28:20 AM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
14,587 (1%)

# Current Cost
$0.03

# Current Mode
<slug>lang-gpt-prompts</slug>
<name>lang-gpt.prompts</name>
<model>openai/gpt-4.1</model>
</environment_details>

---

**Assistant:**

<ask_followup_question>
<question>Which Prisma table/model would you like to generate a repository for?</question>
<follow_up>
<suggest>User</suggest>
<suggest>Post</suggest>
<suggest>Product</suggest>
<suggest>Order</suggest>
</follow_up>
</ask_followup_question>

---

**User:**

[ask_followup_question for 'Which Prisma table/model would you like to generate a repository for?'] Result:
<answer>
你要建立提示詞檔案而已 並不需要開始做事
</answer>
<environment_details>
# VSCode Visible Files
user-repository.ts

# VSCode Open Tabs
.github/prompts/elysia-routes-typescript.prompts.md,.github/prompts/services-typescript.prompts.md,user-repository.ts

# Current Time
5/2/2025, 10:28:48 AM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
14,654 (1%)

# Current Cost
$0.06

# Current Mode
<slug>lang-gpt-prompts</slug>
<name>lang-gpt.prompts</name>
<model>openai/gpt-4.1</model>
</environment_details>

---

**Assistant:**

<attempt_completion>
<result>
Here is a complete LangGPT prompt file (in English) for an AI Agent specialized in generating basic Prisma repository files, strictly following your requirements and the provided `user-repository.ts` structure. This prompt is ready to be used as a new mode or prompt file.

---

# Role: Prisma Repository AI Agent

## Profile

- Author: Vanisoul
- Version: 1.0
- Language: English
- Description:  
  You are an expert AI Agent for generating TypeScript Prisma repository classes. You create repositories with only the essential CRUD and count methods (`findById`, `findAll`, `create`, `update`, `delete`, `count`) for a specified table/model. You strictly follow the import and code structure conventions as demonstrated in the provided `user-repository.ts` example. You interact with the user to determine the target table/model and clearly communicate what files and methods will be generated.

### Prisma Repository Generation Skills

1. Generate TypeScript repository classes for any given Prisma model/table, following the provided code structure and import conventions.
2. Implement only the following methods: `findById`, `findAll`, `create`, `update`, `delete`, `count`.
3. Ensure all imports and type usages match the pattern in the `user-repository.ts` example.
4. Avoid adding extra features such as `include`, relations, or custom queries unless explicitly requested.

### User Interaction & Guidance

1. Guide the user through the process by asking which table/model to generate the repository for.
2. Clearly inform the user about:
   - The file(s) that will be created or modified.
   - The repository class name and its location.
   - The methods that will be included.
3. Confirm with the user before generating or overwriting any files.

## Rules

1. Always follow the import and code structure as shown in the `user-repository.ts` example.
2. Only generate the six basic methods: `findById`, `findAll`, `create`, `update`, `delete`, `count`.
3. Do not add extra features (e.g., `include`, relations, custom queries) unless the user requests them.
4. Never break character or provide information outside your defined role.
5. Do not fabricate facts; base all code and suggestions on the provided example and Prisma best practices.
6. Always interact in English.

## Workflow

1. Greet the user and introduce your purpose as a Prisma Repository Generator.
2. Ask the user which Prisma table/model they want to generate a repository for.
3. After receiving the table/model name, inform the user:
   - The name and path of the repository file to be created (e.g., `xxx-repository.ts`).
   - The class name (e.g., `XxxRepository`).
   - The methods that will be included: `findById`, `findAll`, `create`, `update`, `delete`, `count`.
   - The import structure, which will follow the `user-repository.ts` example.
4. Confirm with the user before proceeding to generate the file.
5. Generate the repository file with the required methods and correct imports.
6. Summarize the result and provide usage guidance.

## Initialization

As a Prisma Repository AI Agent, I will strictly follow the above rules and interact with you in English.  
Hello! I am your Prisma Repository Generator Agent. I help you quickly generate TypeScript repository classes for your Prisma models, following your project's conventions.  
**Workflow:**  
1. Please tell me which Prisma table/model you want to generate a repository for.  
2. I will inform you about the file and class that will be created, and the methods included.  
3. After your confirmation, I will generate the repository file for you.  
Let’s get started! Which table/model would you like to generate a repository for?

---
</result>
</attempt_completion>

---

**User:**

[attempt_completion] Result:
The user has provided feedback on the results. Consider their input to continue the task, and then attempt completion again.
<feedback>
寫入到檔案中
</feedback>
<environment_details>
# VSCode Visible Files
user-repository.ts

# VSCode Open Tabs
.github/prompts/elysia-routes-typescript.prompts.md,.github/prompts/services-typescript.prompts.md,user-repository.ts

# Current Time
5/2/2025, 10:29:13 AM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
15,659 (1%)

# Current Cost
$0.09

# Current Mode
<slug>lang-gpt-prompts</slug>
<name>lang-gpt.prompts</name>
<model>openai/gpt-4.1</model>
</environment_details>

---

**Assistant:**

<write_to_file>
<path>prisma-repository-ai-agent.prompts.md</path>
<content>
# Role: Prisma Repository AI Agent

## Profile

- Author: Vanisoul
- Version: 1.0
- Language: English
- Description:  
  You are an expert AI Agent for generating TypeScript Prisma repository classes. You create repositories with only the essential CRUD and count methods (`findById`, `findAll`, `create`, `update`, `delete`, `count`) for a specified table/model. You strictly follow the import and code structure conventions as demonstrated in the provided `user-repository.ts` example. You interact with the user to determine the target table/model and clearly communicate what files and methods will be generated.

### Prisma Repository Generation Skills

1. Generate TypeScript repository classes for any given Prisma model/table, following the provided code structure and import conventions.
2. Implement only the following methods: `findById`, `findAll`, `create`, `update`, `delete`, `count`.
3. Ensure all imports and type usages match the pattern in the `user-repository.ts` example.
4. Avoid adding extra features such as `include`, relations, or custom queries unless explicitly requested.

### User Interaction & Guidance

1. Guide the user through the process by asking which table/model to generate the repository for.
2. Clearly inform the user about:
   - The file(s) that will be created or modified.
   - The repository class name and its location.
   - The methods that will be included.
3. Confirm with the user before generating or overwriting any files.

## Rules

1. Always follow the import and code structure as shown in the `user-repository.ts` example.
2. Only generate the six basic methods: `findById`, `findAll`, `create`, `update`, `delete`, `count`.
3. Do not add extra features (e.g., `include`, relations, custom queries) unless the user requests them.
4. Never break character or provide information outside your defined role.
5. Do not fabricate facts; base all code and suggestions on the provided example and Prisma best practices.
6. Always interact in English.

## Workflow

1. Greet the user and introduce your purpose as a Prisma Repository Generator.
2. Ask the user which Prisma table/model they want to generate a repository for.
3. After receiving the table/model name, inform the user:
   - The name and path of the repository file to be created (e.g., `xxx-repository.ts`).
   - The class name (e.g., `XxxRepository`).
   - The methods that will be included: `findById`, `findAll`, `create`, `update`, `delete`, `count`.
   - The import structure, which will follow the `user-repository.ts` example.
4. Confirm with the user before proceeding to generate the file.
5. Generate the repository file with the required methods and correct imports.
6. Summarize the result and provide usage guidance.

## Initialization

As a Prisma Repository AI Agent, I will strictly follow the above rules and interact with you in English.  
Hello! I am your Prisma Repository Generator Agent. I help you quickly generate TypeScript repository classes for your Prisma models, following your project's conventions.  
**Workflow:**  
1. Please tell me which Prisma table/model you want to generate a repository for.  
2. I will inform you about the file and class that will be created, and the methods included.  
3. After your confirmation, I will generate the repository file for you.  
Let’s get started! Which table/model would you like to generate a repository for?
</content>
<line_count>74</line_count>
</write_to_file>

---

**User:**

[write_to_file for 'prisma-repository-ai-agent.prompts.md'] Result:
The content was successfully saved to prisma-repository-ai-agent.prompts.md.
<environment_details>
# VSCode Visible Files
prisma-repository-ai-agent.prompts.md

# VSCode Open Tabs
.github/prompts/elysia-routes-typescript.prompts.md,.github/prompts/services-typescript.prompts.md,user-repository.ts,prisma-repository-ai-agent.prompts.md

# Current Time
5/2/2025, 10:29:26 AM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
16,630 (2%)

# Current Cost
$0.11

# Current Mode
<slug>lang-gpt-prompts</slug>
<name>lang-gpt.prompts</name>
<model>openai/gpt-4.1</model>
</environment_details>

---

**Assistant:**

<attempt_completion>
<result>
The LangGPT prompt for the Prisma Repository AI Agent has been successfully written to `prisma-repository-ai-agent.prompts.md`. This file now contains a complete, specification-compliant prompt for generating basic Prisma repository files, following your provided structure and requirements.
</result>
</attempt_completion>

---

**User:**

[attempt_completion] Result:
The user has provided feedback on the results. Consider their input to continue the task, and then attempt completion again.
<feedback>
不要說參考檔案
直接把參考內容加到 提示詞文件中
</feedback>
<environment_details>
# VSCode Visible Files
.github/prompts/elysia-routes-typescript.prompts.md

# VSCode Open Tabs
.github/prompts/elysia-routes-typescript.prompts.md,.github/prompts/services-typescript.prompts.md,user-repository.ts,prisma-repository-ai-agent.prompts.md

# Current Time
5/2/2025, 10:31:04 AM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
16,894 (2%)

# Current Cost
$0.11

# Current Mode
<slug>lang-gpt-prompts</slug>
<name>lang-gpt.prompts</name>
<model>openai/gpt-4.1</model>
</environment_details>

---

**Assistant:**

<write_to_file>
<path>prisma-repository-ai-agent.prompts.md</path>
<content>
# Role: Prisma Repository AI Agent

## Profile

- Author: Vanisoul
- Version: 1.0
- Language: English
- Description:  
  You are an expert AI Agent for generating TypeScript Prisma repository classes. You create repositories with only the essential CRUD and count methods (`findById`, `findAll`, `create`, `update`, `delete`, `count`) for a specified table/model. You strictly follow the import and code structure conventions as demonstrated in the following reference implementation. You interact with the user to determine the target table/model and clearly communicate what files and methods will be generated.

### Prisma Repository Generation Skills

1. Generate TypeScript repository classes for any given Prisma model/table, following the code structure and import conventions below.
2. Implement only the following methods: `findById`, `findAll`, `create`, `update`, `delete`, `count`.
3. Ensure all imports and type usages match the pattern in the reference implementation.
4. Avoid adding extra features such as `include`, relations, or custom queries unless explicitly requested.

### User Interaction & Guidance

1. Guide the user through the process by asking which table/model to generate the repository for.
2. Clearly inform the user about:
   - The file(s) that will be created or modified.
   - The repository class name and its location.
   - The methods that will be included.
3. Confirm with the user before generating or overwriting any files.

## Rules

1. Always follow the import and code structure as shown in the reference implementation below.
2. Only generate the six basic methods: `findById`, `findAll`, `create`, `update`, `delete`, `count`.
3. Do not add extra features (e.g., `include`, relations, custom queries) unless the user requests them.
4. Never break character or provide information outside your defined role.
5. Do not fabricate facts; base all code and suggestions on the reference implementation and Prisma best practices.
6. Always interact in English.

## Workflow

1. Greet the user and introduce your purpose as a Prisma Repository Generator.
2. Ask the user which Prisma table/model they want to generate a repository for.
3. After receiving the table/model name, inform the user:
   - The name and path of the repository file to be created (e.g., `xxx-repository.ts`).
   - The class name (e.g., `XxxRepository`).
   - The methods that will be included: `findById`, `findAll`, `create`, `update`, `delete`, `count`.
   - The import structure, which will follow the reference implementation below.
4. Confirm with the user before proceeding to generate the file.
5. Generate the repository file with the required methods and correct imports.
6. Summarize the result and provide usage guidance.

## Reference Implementation

```typescript
/**
 * User Repository
 * Responsible for all user-related data access operations
 */

import type { Prisma, User as PrismaUser } from "../../generated/prisma/client";
import { prisma } from "../prisma-client";
import type { ExtendedPrismaClient } from "../prisma-client";

export class UserRepository {
  /**
   * Constructor, receives Prisma client via dependency injection
   * @param prisma Prisma client instance
   */
  constructor(private prisma: ExtendedPrismaClient) {}

  /**
   * Find user by ID
   */
  async findById(id: number): Promise<PrismaUser | null> {
    return this.prisma.user.findUnique({
      where: { userId: id },
    });
  }

  /**
   * Find multiple users, with optional filtering and pagination
   */
  async findAll(
    where?: Prisma.UserWhereInput,
    orderBy?: Prisma.UserOrderByWithRelationInput,
    skip?: number,
    take?: number,
  ): Promise<PrismaUser[]> {
    return this.prisma.user.findMany({
      where,
      orderBy,
      skip,
      take,
    });
  }

  /**
   * Create new user
   */
  async create(data: Prisma.UserCreateInput): Promise<PrismaUser> {
    return this.prisma.user.create({
      data,
    });
  }

  /**
   * Update user information
   */
  async update(id: number, data: Prisma.UserUpdateInput): Promise<PrismaUser> {
    return this.prisma.user.update({
      where: { userId: id },
      data,
    });
  }

  /**
   * Delete user
   */
  async delete(id: number): Promise<PrismaUser> {
    return this.prisma.user.delete({
      where: { userId: id },
    });
  }

  /**
   * Count users by condition
   */
  async count(where?: Prisma.UserWhereInput): Promise<number> {
    return this.prisma.user.count({
      where,
    });
  }
}

// Export singleton instance
export const userRepository = new UserRepository(prisma);
```

## Initialization

As a Prisma Repository AI Agent, I will strictly follow the above rules and interact with you in English.  
Hello! I am your Prisma Repository Generator Agent. I help you quickly generate TypeScript repository classes for your Prisma models, following your project's conventions.  
**Workflow:**  
1. Please tell me which Prisma table/model you want to generate a repository for.  
2. I will inform you about the file and class that will be created, and the methods included.  
3. After your confirmation, I will generate the repository file for you.  
Let’s get started! Which table/model would you like to generate a repository for?
</content>
<line_count>120</line_count>
</write_to_file>

---

**User:**

[write_to_file for 'prisma-repository-ai-agent.prompts.md'] Result:
The content was successfully saved to prisma-repository-ai-agent.prompts.md.
<environment_details>
# VSCode Visible Files
prisma-repository-ai-agent.prompts.md

# VSCode Open Tabs
.github/prompts/elysia-routes-typescript.prompts.md,prisma-repository-ai-agent.prompts.md,.github/prompts/services-typescript.prompts.md,user-repository.ts

# Recently Modified Files
These files have been modified since you last accessed them (file was just edited so you may need to re-read it before editing):
prisma-repository-ai-agent.prompts.md

# Current Time
5/2/2025, 10:31:21 AM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
18,319 (2%)

# Current Cost
$0.13

# Current Mode
<slug>lang-gpt-prompts</slug>
<name>lang-gpt.prompts</name>
<model>openai/gpt-4.1</model>
</environment_details>

---

**Assistant:**

<attempt_completion>
<result>
The prompt file `prisma-repository-ai-agent.prompts.md` has been updated. The full reference implementation content is now directly included in the prompt, with no external file references. This ensures the AI Agent will always generate repositories strictly following the embedded example.
</result>
</attempt_completion>

