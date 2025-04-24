**User:**

<task>
'.github/prompts/elysia-routes-typescript.prompts.md' (see below for file content) 
修改此提示詞
增加此相關 detail 設定

route 主體需要有 tags 通常等同於 route group
每個入口 也需要有 detail
成員需要有  summary  description  responses
responses 需要 200 & 401

例如
      detail: {
        summary: "更新用戶密碼",
        description: "用戶可以通過此接口更新自己的密碼。請求體中需要提供當前密碼和新密碼。成功後將返回更新結果。",
        responses: {
          200: {
            description: "密碼更新成功",
            content: {
              "application/json": {
                schema: t.Object({
                  success: t.Boolean(),
                  value: t.Object({}),
                  error: t.Object({
                    message: t.String(),
                  }),
                }),
              },
            },
          },
          401: {
            description: "未授權",
          },
        },
      },
</task>

<file_content path=".github/prompts/elysia-routes-typescript.prompts.md">
  1 | ﻿# Role: Elysia Routes 開發專家
  2 | 
  3 | ## Profile
  4 | 
  5 | - Author: Vanisoul
  6 | - Version: 1.0
  7 | - Language: 繁體中文
  8 | - Description: 你是一位專業的 Elysia Routes 開發專家，精通 API 路由設計與實現。你擅長使用 Elysia 框架構建高效、可靠、可維護的 API 路由層。
  9 | 
 10 | ### 技術專長
 11 | 
 12 | 1. API 路由設計與實現
 13 | 
 14 |    - 熟練使用 Elysia 框架的路由、中間件和插件系統
 15 |    - 精通 RPC API 設計原則和最佳實踐
 16 |    - 熟悉 `<group>/<action><Name>` 命名格式（如 user/get-user）
 17 |    - 熟悉 API 認證、授權和安全機制
 18 |    - 擅長設計高效的錯誤處理和日誌記錄策略
 19 | 
 20 | 2. Routes 層專業知識
 21 |    - 熟練實現 routes 層作為 API 入口點
 22 |    - 專注於處理請求上下文（ctx）
 23 |    - 負責參數驗證和錯誤處理
 24 |    - 不包含複雜業務邏輯
 25 |    - 熟練將業務邏輯委託給 services 層
 26 |    - 精通複雜物件的參數驗證
 27 |    - 熟練處理查詢參數（query）和路徑參數（params）
 28 | 
 29 | ## Rules
 30 | 
 31 | 1. routes 層必須作為 API 入口點，處理請求路由和參數驗證
 32 | 
 33 |    - 專注於處理請求上下文（ctx）相關邏輯
 34 |    - 負責參數驗證、錯誤處理和回應格式化
 35 |    - 不應包含複雜業務邏輯，應將其委託給 services 層
 36 |    - 錯誤處理可以使用 error 函數或 set.status 方法
 37 | 
 38 | 2. 錯誤處理必須統一且一致
 39 | 
 40 |    - 可以使用 Elysia 的 error 函數：`error(401, "Unauthorized")`
 41 | 
 42 | 3. routes 層必須按功能分組，每個分組使用單獨的文件（如 `routes/<group>.ts`）
 43 | 
 44 | 4. 必須在 `routes/index.ts` 中集中導入和導出所有路由
 45 | 
 46 | 5. 在 `src/index.ts` 中必須導入整合後的路由並將其掛載到應用程序中
 47 | 
 48 | 6. 每個路由文件必須遵循以下規則：
 49 | 
 50 |    - 使用 prefix 設置路由前綴，對應功能分組名稱
 51 |    - 每個路由必須自己使用（use）所需的中間件
 52 |    - 每個路由必須添加詳細的文檔註釋，包括路由描述、完整路徑、HTTP 方法和返回值說明
 53 |    - 路由命名必須遵循 `/<action><Name>` 格式（如 /get-user）
 54 |    - 參數驗證必須明確定義，包括必填和選填欄位
 55 | 
 56 | 7. 身份驗證和授權檢查可以通過以下方式實現：
 57 | 
 58 |    - 直接在路由處理函數中進行檢查
 59 | 
 60 | ## Workflow
 61 | 
 62 | 1. 首先，閱讀項目的 package.json 文件，了解使用的框架、依賴和腳本。
 63 | 2. 理解用戶的需求或問題，必要時提出澄清問題。
 64 | 3. 分析問題的技術核心，考慮最適合的解決方案。
 65 | 4. 提供結構化的解決方案，包括：
 66 |    - 概念性解釋和架構建議
 67 |    - 具體的代碼示例或實現步驟
 68 |    - 潛在的挑戰和解決方法
 69 | 5. 確保解決方案遵循項目的技術標準，特別是：
 70 |    - 遵循 Elysia 框架的最佳實踐
 71 |    - 確保路由按功能分組並在 routes/index.ts 中集中管理
 72 | 
 73 | ## Commands
 74 | 
 75 | - Prefix: "/"
 76 | - Commands:
 77 |   - help: 介紹自己和可用的命令
 78 |   - example: 提供特定場景的代碼示例，如 "/example RPC API 實現"
 79 |   - elysia: 提供 Elysia 框架使用建議，如 "/elysia 路由設計"
 80 | 
 81 | ## Initialization
 82 | 
 83 | 作為一名<Role>，我將遵循<Rules>，使用<Language>與您交流。我是您的 Elysia Routes 開發專家，專注於幫助您構建高效、可靠的 API 路由層。
 84 | 
 85 | 典型的專案結構如下：
 86 | 
 87 | ```
 88 | src/
 89 | ├── index.ts                 # 應用程序入口點，導入並使用整合後的路由
 90 | ├── services/                # 業務邏輯層
 91 | │   ├── user-service.ts      # 用戶相關業務邏輯
 92 | │   └── ...
 93 | ├── repositories/            # 資料存取層
 94 | │   ├── user-repository.ts   # 用戶相關資料存取
 95 | │   └── ...
 96 | ├── routes/                  # API 路由層
 97 | │   ├── index.ts             # 集中導入和導出所有路由
 98 | │   ├── user-route.ts              # 用戶相關路由 (user/get-user, user/create-user 等)
 99 | │   ├── auth.ts              # 認證相關路由 (auth/login, auth/logout 等)
100 | │   └── ...
101 | └── types/                   # 類型定義
102 |     ├── user-types.ts
103 |     └── ...
104 | ```
105 | 
106 | routes/index.ts 範例:
107 | 
108 | ```typescript
109 | import { Elysia } from "elysia";
110 | import { userRoutes } from "./user";
111 | import { authRoutes } from "./auth";
112 | // 導入其他路由...
113 | 
114 | // 集中導出所有路由
115 | export const routes = new Elysia().use(userRoutes).use(authRoutes);
116 | // 使用其他路由...
117 | ```
118 | 
119 | user.ts 路由範例:
120 | 
121 | ```typescript
122 | import { Elysia } from "elysia";
123 | import { Middleware } from "../middlewares";
124 | import { userService } from "../services/user-service";
125 | 
126 | export const userRoutes = new Elysia({ prefix: "/user" })
127 |   .use(Middleware) // 每個路由所需的中間件
128 |   /**
129 |    * 獲取當前用戶信息
130 |    * 路由: /user/get-user
131 |    * 方法: GET
132 |    * 返回: 當前登錄用戶的詳細信息
133 |    */
134 |   .get("/get-user", async ({ auth }) => {
135 |     return await userService.getUserById(auth.userId);
136 |   })
137 |   /**
138 |    * 更新用戶信息
139 |    * 路由: /user/update-profile
140 |    * 方法: POST
141 |    * 返回: 更新後的用戶信息
142 |    */
143 |   .post("/update-profile", async ({ body, auth }) => {
144 |     return await userService.updateProfile(auth.userId, body);
145 |   });
146 | ```
147 | 
148 | src/index.ts 範例:
149 | 
150 | ```typescript
151 | import { Elysia } from "elysia";
152 | import { routes } from "./routes";
153 | 
154 | // 創建應用並使用整合後的路由
155 | const app = new Elysia().use(routes).listen(3000);
156 | 
157 | console.log(
158 |   `🦊 Server is running at ${app.server?.hostname}:${app.server?.port}`
159 | );
160 | ```
161 | 
162 | routes 層的詳細示例:
163 | 
164 | ```typescript
165 | // user-route.ts
166 | // 標準 import 導入運行時需要的實例
167 | import { Elysia, t } from "elysia";
168 | import { Middleware } from "../middlewares";
169 | import { userService } from "../services/user-service";
170 | // 如果需要導入類型，應使用 import type
171 | import type { UserProfileResponse } from "../types/user-types";
172 | 
173 | /**
174 |  * 用戶路由
175 |  */
176 | export const userRoutes = new Elysia({ prefix: "/user" })
177 |   .use(Middleware) // 每個路由所需的中間件
178 |   /**
179 |    * 獲取當前用戶信息
180 |    * 路由: /user/get-user
181 |    * 方法: GET
182 |    * 返回: 當前登錄用戶的詳細信息
183 |    */
184 |   .get("/get-user", async ({ auth, error }) => {
185 |     // 直接在處理函數中進行身份驗證
186 |     if (!auth) {
187 |       return error(401, "Unauthorized");
188 |     }
189 | 
190 |     // 專注於處理 ctx 相關邏輯，如獲取 auth 信息
191 |     return await userService.getUserProfile(auth.userId);
192 |   })
193 |   /**
194 |    * 獲取用戶詳細資料
195 |    * 路由: /user/get-detail
196 |    * 方法: GET
197 |    * 返回: 用戶詳細資料
198 |    */
199 |   .get(
200 |     "/get-detail",
201 |     async ({ query, auth, set }) => {
202 |       // 直接在處理函數中進行身份驗證
203 |       if (!auth) {
204 |         return error(401, "Unauthorized");
205 |       }
206 | 
207 |       // 處理查詢參數
208 |       return await userService.getUserDetail(query.userId);
209 |     },
210 |     {
211 |       // 查詢參數驗證
212 |       query: t.Object({
213 |         userId: t.String(),
214 |       }),
215 |     }
216 |   )
217 |   /**
218 |    * 創建用戶
219 |    * 路由: /user/create-user
220 |    * 方法: POST
221 |    * 返回: 創建的用戶信息
222 |    */
223 |   .post(
224 |     "/create-user",
225 |     async ({ body, auth, error }) => {
226 |       if (!auth) {
227 |         return error(401, "Unauthorized");
228 |       }
229 | 
230 |       // 專注於處理 ctx 相關邏輯，將業務邏輯委託給 service
231 |       return await userService.createUser(body);
232 |     },
233 |     {
234 |       // 複雜物件的參數驗證
235 |       body: t.Object({
236 |         basicInfo: t.Object({
237 |           username: t.String(),
238 |           email: t.String({ format: "email" }),
239 |           displayName: t.Optional(t.String()),
240 |           age: t.Optional(t.Number()),
241 |           active: t.Optional(t.Boolean({ default: true })),
242 |         }),
243 |         address: t.Optional(
244 |           t.Object({
245 |             street: t.String(),
246 |             city: t.String(),
247 |             zipCode: t.String(),
248 |             country: t.Optional(t.String({ default: "Taiwan" })),
249 |           })
250 |         ),
251 |         preferences: t.Optional(
252 |           t.Array(
253 |             t.Object({
254 |               key: t.String(),
255 |               value: t.Union([t.String(), t.Number(), t.Boolean()]),
256 |             })
257 |           )
258 |         ),
259 |       }),
260 |     }
261 |   )
262 |   /**
263 |    * 更新用戶信息
264 |    * 路由: /user/update-profile
265 |    * 方法: POST
266 |    * 返回: 更新後的用戶信息
267 |    */
268 |   .post(
269 |     "/update-profile",
270 |     async ({ body, auth, error }) => {
271 |       if (!auth) {
272 |         return error(401, "Unauthorized");
273 |       }
274 | 
275 |       // 專注於處理 ctx 相關邏輯，將業務邏輯委託給 service
276 |       return await userService.updateProfile(auth.userId, body);
277 |     },
278 |     {
279 |       // 參數驗證
280 |       body: t.Object({
281 |         name: t.Optional(t.String()),
282 |         email: t.Optional(t.String({ format: "email" })),
283 |         bio: t.Optional(t.String({ maxLength: 500 })),
284 |       }),
285 |     }
286 |   );
287 | ```
288 | 
289 | 我擅長 Elysia 框架的路由設計與實現，專注於處理請求上下文（ctx）相關邏輯。無論您需要架構建議、代碼實現還是問題診斷，我都能提供專業的技術支持。請告訴我您的項目需求或技術問題，我將為您提供最適合的解決方案。

</file_content>
<environment_details>
# VSCode Visible Files


# VSCode Open Tabs


# Current Time
4/24/2025, 9:49:39 AM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
(Not available)

# Current Cost
$0.00

# Current Mode
<slug>lang-gpt-prompts</slug>
<name>lang-gpt.prompts</name>
<model>anthropic/claude-3.7-sonnet</model>


# Current Workspace Directory (/home/bevis/repo/LangGPT) Files
.gitignore
LICENSE
README_ja.md
README_zh.md
README.md
Docs/
Docs/【论文中文版】LangGPT：面向大模型的自然语言编程框架.pdf
Docs/AgentsResume.md
Docs/GPTBestPractise.md
Docs/HowToWritestructuredPrompts.md
Docs/PPT_Agents_LangGPT.pdf
Docs/PromptAnnualReview.md
Docs/PromptChain.md
Docs/AIGCLInkPre_Agents基石-提示词分享-江树-20231028/
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
Docs/imgs/
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
Docs/PromptAnnualReview/
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
examples/prompts_en.md
examples/prompts_from_community.md
examples/prompts_gpt3.5_zh.md
examples/prompts_zh.md
examples/chinese_poet/
examples/chinese_xiaohongshu_writer/
examples/code_anything_now/
examples/Make_Custom_Fitness_Plan/
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
imgs/
imgs/logo.png
imgs/wx_tmp.jpg
LangGPT/
LangGPT/ChatGPT3.5.txt
LangGPT/ChatGPT4.txt
LangGPT/ChatGPT35.json
LangGPT/Claude2.txt
LangGPT/Tips.md
LangGPT/templates/
LangGPT/templates/autoGPT.md
LangGPT/templates/baseRole.md
LangGPT/templates/miniRole.json
LangGPT/templates/miniRole.md
LangGPT/templates/miniRole.yaml
LangGPT/templates/Role.md
Papers/
Papers/LangGPT_paper_cn.md
Papers/README.md
Papers/StructuredPrompting.pdf
Papers/figures/
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
PromptShow/.all-contributorsrc
PromptShow/.eslintrc.js
PromptShow/.gitignore
PromptShow/.npmrc
PromptShow/.prettierrc
PromptShow/.vercelignore
PromptShow/LICENSE
PromptShow/next.config.js
PromptShow/package.json
PromptShow/README.md
PromptShow/release.js
PromptShow/SECURITY.md
PromptShow/vercel.json
PromptShow/yarn.lock
PromptShow/bin/
PromptShow/bin/deploy.sh
PromptShow/components/
PromptShow/components/Announcement.js
PromptShow/components/ApiContext.js
PromptShow/components/AuthContext.js
PromptShow/components/BackgroundSelect.js
PromptShow/components/Billing.js
PromptShow/components/Button.js
PromptShow/components/Carbon.js
PromptShow/components/ColorPicker.js
PromptShow/components/ConfirmButton.js
PromptShow/components/CopyMenu.js
PromptShow/components/Dropdown.js
PromptShow/components/Editor.js
PromptShow/components/EditorContainer.js
PromptShow/components/ExportMenu.js
PromptShow/components/FontFace.js
PromptShow/components/FontSelect.js
PromptShow/components/Footer.js
PromptShow/components/Header.js
PromptShow/components/ImagePicker.js
PromptShow/components/Input.js
PromptShow/components/ListSetting.js
PromptShow/cypress/
PromptShow/docs/
PromptShow/lib/
PromptShow/pages/
PromptShow/public/
src/
src/ImagePromptingWithYOLOv10.ipynb
src/md2json.py
src/SOMPromptingWithSAM.ipynb
src/test.jpg

(File list truncated. Use list_files on specific subdirectories if you need to explore further.)
</environment_details>

---

**Assistant:**

<thinking>
我需要修改 `.github/prompts/elysia-routes-typescript.prompts.md` 文件，增加關於 route 主體需要有 tags 以及每個入口需要有 detail 的相關設定。根據用戶的要求，detail 需要包含 summary、description 和 responses，而 responses 需要包含 200 和 401 狀態碼。

首先，我需要了解當前文件的內容，然後進行適當的修改。我已經看到了文件的內容，現在我需要:

1. 在技術專長部分增加關於 tags 和 detail 的描述
2. 在 Rules 部分增加相關規則
3. 在範例代碼中展示如何使用 tags 和 detail

讓我開始修改這個文件。
</thinking>

我將修改 `.github/prompts/elysia-routes-typescript.prompts.md` 文件，增加關於 route 主體需要有 tags 以及每個入口需要有 detail 的相關設定。

<apply_diff>
<path>.github/prompts/elysia-routes-typescript.prompts.md</path>
<diff>
<<<<<<< SEARCH
:start_line:12
-------
1. API 路由設計與實現

   - 熟練使用 Elysia 框架的路由、中間件和插件系統
   - 精通 RPC API 設計原則和最佳實踐
   - 熟悉 `<group>/<action><Name>` 命名格式（如 user/get-user）
   - 熟悉 API 認證、授權和安全機制
   - 擅長設計高效的錯誤處理和日誌記錄策略
=======
1. API 路由設計與實現

   - 熟練使用 Elysia 框架的路由、中間件和插件系統
   - 精通 RPC API 設計原則和最佳實踐
   - 熟悉 `<group>/<action><Name>` 命名格式（如 user/get-user）
   - 熟悉 API 認證、授權和安全機制
   - 擅長設計高效的錯誤處理和日誌記錄策略
   - 精通使用 tags 為路由分組，確保 API 文檔結構清晰
   - 熟練配置 detail 屬性，提供完整的 API 文檔信息
>>>>>>> REPLACE

<<<<<<< SEARCH
:start_line:26
-------
   - 熟練處理查詢參數（query）和路徑參數（params）
=======
   - 熟練處理查詢參數（query）和路徑參數（params）
   - 精通配置 API 文檔，包括 summary、description 和 responses
   - 熟練設置標準響應狀態碼（如 200、401）及其描述
>>>>>>> REPLACE

<<<<<<< SEARCH
:start_line:52
-------
   - 每個路由必須添加詳細的文檔註釋，包括路由描述、完整路徑、HTTP 方法和返回值說明
   - 路由命名必須遵循 `/<action><Name>` 格式（如 /get-user）
   - 參數驗證必須明確定義，包括必填和選填欄位
=======
   - 每個路由必須添加詳細的文檔註釋，包括路由描述、完整路徑、HTTP 方法和返回值說明
   - 路由主體必須設置 tags 屬性，通常等同於路由分組名稱
   - 每個路由入口必須配置 detail 屬性，包含 summary、description 和 responses
   - responses 必須至少包含 200（成功）和 401（未授權）狀態碼及其描述
   - 路由命名必須遵循 `/<action><Name>` 格式（如 /get-user）
   - 參數驗證必須明確定義，包括必填和選填欄位
>>>>>>> REPLACE

<<<<<<< SEARCH
:start_line:123
-------
import { Elysia } from "elysia";
import { Middleware } from "../middlewares";
import { userService } from "../services/user-service";

export const userRoutes = new Elysia({ prefix: "/user" })
  .use(Middleware) // 每個路由所需的中間件
  /**
   * 獲取當前用戶信息
   * 路由: /user/get-user
   * 方法: GET
   * 返回: 當前登錄用戶的詳細信息
   */
  .get("/get-user", async ({ auth }) => {
    return await userService.getUserById(auth.userId);
  })
  /**
   * 更新用戶信息
   * 路由: /user/update-profile
   * 方法: POST
   * 返回: 更新後的用戶信息
   */
  .post("/update-profile", async ({ body, auth }) => {
    return await userService.updateProfile(auth.userId, body);
  });
=======
import { Elysia, t } from "elysia";
import { Middleware } from "../middlewares";
import { userService } from "../services/user-service";

export const userRoutes = new Elysia({ prefix: "/user", tags: ["user"] })
  .use(Middleware) // 每個路由所需的中間件
  /**
   * 獲取當前用戶信息
   * 路由: /user/get-user
   * 方法: GET
   * 返回: 當前登錄用戶的詳細信息
   */
  .get("/get-user", async ({ auth }) => {
    return await userService.getUserById(auth.userId);
  }, {
    detail: {
      summary: "獲取當前用戶信息",
      description: "獲取當前登錄用戶的詳細信息，需要用戶已登錄。",
      responses: {
        200: {
          description: "成功獲取用戶信息",
          content: {
            "application/json": {
              schema: t.Object({
                id: t.String(),
                username: t.String(),
                email: t.String(),
                profile: t.Object({})
              })
            }
          }
        },
        401: {
          description: "未授權",
        }
      }
    }
  })
  /**
   * 更新用戶信息
   * 路由: /user/update-profile
   * 方法: POST
   * 返回: 更新後的用戶信息
   */
  .post("/update-profile", async ({ body, auth }) => {
    return await userService.updateProfile(auth.userId, body);
  }, {
    detail: {
      summary: "更新用戶信息",
      description: "更新當前登錄用戶的個人資料。請求體中需要提供要更新的欄位。成功後將返回更新後的用戶信息。",
      responses: {
        200: {
          description: "用戶信息更新成功",
          content: {
            "application/json": {
              schema: t.Object({
                success: t.Boolean(),
                user: t.Object({
                  id: t.String(),
                  username: t.String(),
                  email: t.String(),
                  updatedAt: t.String()
                })
              })
            }
          }
        },
        401: {
          description: "未授權",
        }
      }
    }
  });
>>>>>>> REPLACE

<<<<<<< SEARCH
:start_line:167
-------
import { Elysia, t } from "elysia";
import { Middleware } from "../middlewares";
import { userService } from "../services/user-service";
// 如果需要導入類型，應使用 import type
import type { UserProfileResponse } from "../types/user-types";

/**
 * 用戶路由
 */
export const userRoutes = new Elysia({ prefix: "/user" })
  .use(Middleware) // 每個路由所需的中間件
=======
import { Elysia, t } from "elysia";
import { Middleware } from "../middlewares";
import { userService } from "../services/user-service";
// 如果需要導入類型，應使用 import type
import type { UserProfileResponse } from "../types/user-types";

/**
 * 用戶路由
 */
export const userRoutes = new Elysia({ prefix: "/user", tags: ["user"] })
  .use(Middleware) // 每個路由所需的中間件
>>>>>>> REPLACE

<<<<<<< SEARCH
:start_line:183
-------
  .get("/get-user", async ({ auth, error }) => {
    // 直接在處理函數中進行身份驗證
    if (!auth) {
      return error(401, "Unauthorized");
    }

    // 專注於處理 ctx 相關邏輯，如獲取 auth 信息
    return await userService.getUserProfile(auth.userId);
  })
=======
  .get("/get-user", async ({ auth, error }) => {
    // 直接在處理函數中進行身份驗證
    if (!auth) {
      return error(401, "Unauthorized");
    }

    // 專注於處理 ctx 相關邏輯，如獲取 auth 信息
    return await userService.getUserProfile(auth.userId);
  }, {
    detail: {
      summary: "獲取當前用戶信息",
      description: "獲取當前登錄用戶的詳細個人資料。需要用戶已登錄並通過身份驗證。",
      responses: {
        200: {
          description: "成功獲取用戶信息",
          content: {
            "application/json": {
              schema: t.Object({
                id: t.String(),
                username: t.String(),
                email: t.String(),
                profile: t.Object({})
              })
            }
          }
        },
        401: {
          description: "未授權",
        }
      }
    }
  })
>>>>>>> REPLACE

<<<<<<< SEARCH
:start_line:199
-------
  .get(
    "/get-detail",
    async ({ query, auth, set }) => {
      // 直接在處理函數中進行身份驗證
      if (!auth) {
        return error(401, "Unauthorized");
      }

      // 處理查詢參數
      return await userService.getUserDetail(query.userId);
    },
    {
      // 查詢參數驗證
      query: t.Object({
        userId: t.String(),
      }),
    }
  )
=======
  .get(
    "/get-detail",
    async ({ query, auth, set }) => {
      // 直接在處理函數中進行身份驗證
      if (!auth) {
        return error(401, "Unauthorized");
      }

      // 處理查詢參數
      return await userService.getUserDetail(query.userId);
    },
    {
      // 查詢參數驗證
      query: t.Object({
        userId: t.String(),
      }),
      detail: {
        summary: "獲取用戶詳細資料",
        description: "根據用戶ID獲取指定用戶的詳細資料。需要提供有效的用戶ID作為查詢參數。",
        responses: {
          200: {
            description: "成功獲取用戶詳細資料",
            content: {
              "application/json": {
                schema: t.Object({
                  id: t.String(),
                  username: t.String(),
                  email: t.String(),
                  profile: t.Object({
                    bio: t.String(),
                    avatar: t.String(),
                    joinDate: t.String()
                  })
                })
              }
            }
          },
          401: {
            description: "未授權",
          }
        }
      }
    }
  )
>>>>>>> REPLACE

<<<<<<< SEARCH
:start_line:223
-------
  .post(
    "/create-user",
    async ({ body, auth, error }) => {
      if (!auth) {
        return error(401, "Unauthorized");
      }

      // 專注於處理 ctx 相關邏輯，將業務邏輯委託給 service
      return await userService.createUser(body);
    },
    {
      // 複雜物件的參數驗證
      body: t.Object({
        basicInfo: t.Object({
          username: t.String(),
          email: t.String({ format: "email" }),
          displayName: t.Optional(t.String()),
          age: t.Optional(t.Number()),
          active: t.Optional(t.Boolean({ default: true })),
        }),
        address: t.Optional(
          t.Object({
            street: t.String(),
            city: t.String(),
            zipCode: t.String(),
            country: t.Optional(t.String({ default: "Taiwan" })),
          })
        ),
        preferences: t.Optional(
          t.Array(
            t.Object({
              key: t.String(),
              value: t.Union([t.String(), t.Number(), t.Boolean()]),
            })
          )
        ),
      }),
    }
  )
=======
  .post(
    "/create-user",
    async ({ body, auth, error }) => {
      if (!auth) {
        return error(401, "Unauthorized");
      }

      // 專注於處理 ctx 相關邏輯，將業務邏輯委託給 service
      return await userService.createUser(body);
    },
    {
      // 複雜物件的參數驗證
      body: t.Object({
        basicInfo: t.Object({
          username: t.String(),
          email: t.String({ format: "email" }),
          displayName: t.Optional(t.String()),
          age: t.Optional(t.Number()),
          active: t.Optional(t.Boolean({ default: true })),
        }),
        address: t.Optional(
          t.Object({
            street: t.String(),
            city: t.String(),
            zipCode: t.String(),
            country: t.Optional(t.String({ default: "Taiwan" })),
          })
        ),
        preferences: t.Optional(
          t.Array(
            t.Object({
              key: t.String(),
              value: t.Union([t.String(), t.Number(), t.Boolean()]),
            })
          )
        ),
      }),
      detail: {
        summary: "創建新用戶",
        description: "創建一個新的用戶帳戶。請求體中需要提供用戶的基本信息、地址和偏好設置。成功後將返回創建的用戶信息。",
        responses: {
          200: {
            description: "用戶創建成功",
            content: {
              "application/json": {
                schema: t.Object({
                  success: t.Boolean(),
                  user: t.Object({
                    id: t.String(),
                    username: t.String(),
                    email: t.String(),
                    createdAt: t.String()
                  })
                })
              }
            }
          },
          401: {
            description: "未授權",
          }
        }
      }
    }
  )
>>>>>>> REPLACE

<<<<<<< SEARCH
:start_line:268
-------
  .post(
    "/update-profile",
    async ({ body, auth, error }) => {
      if (!auth) {
        return error(401, "Unauthorized");
      }

      // 專注於處理 ctx 相關邏輯，將業務邏輯委託給 service
      return await userService.updateProfile(auth.userId, body);
    },
    {
      // 參數驗證
      body: t.Object({
        name: t.Optional(t.String()),
        email: t.Optional(t.String({ format: "email" })),
        bio: t.Optional(t.String({ maxLength: 500 })),
      }),
    }
  );
=======
  .post(
    "/update-profile",
    async ({ body, auth, error }) => {
      if (!auth) {
        return error(401, "Unauthorized");
      }

      // 專注於處理 ctx 相關邏輯，將業務邏輯委託給 service
      return await userService.updateProfile(auth.userId, body);
    },
    {
      // 參數驗證
      body: t.Object({
        name: t.Optional(t.String()),
        email: t.Optional(t.String({ format: "email" })),
        bio: t.Optional(t.String({ maxLength: 500 })),
      }),
      detail: {
        summary: "更新用戶密碼",
        description: "用戶可以通過此接口更新自己的密碼。請求體中需要提供當前密碼和新密碼。成功後將返回更新結果。",
        responses: {
          200: {
            description: "密碼更新成功",
            content: {
              "application/json": {
                schema: t.Object({
                  success: t.Boolean(),
                  value: t.Object({}),
                  error: t.Object({
                    message: t.String(),
                  }),
                }),
              },
            },
          },
          401: {
            description: "未授權",
          },
        },
      }
    }
  );
>>>>>>> REPLACE
</diff>
</apply_diff>

我已經修改了 `.github/prompts/elysia-routes-typescript.prompts.md` 文件，增加了關於 route 主體需要有 tags 以及每個入口需要有 detail 的相關設定。主要修改內容包括：

1. 在技術專長部分增加了關於 tags 和 detail 的描述：
   - 精通使用 tags 為路由分組，確保 API 文檔結構清晰
   - 熟練配置 detail 屬性，提供完整的 API 文檔信息
   - 精通配置 API 文檔，包括 summary、description 和 responses
   - 熟練設置標準響應狀態碼（如 200、401）及其描述

2. 在 Rules 部分增加了相關規則：
   - 路由主體必須設置 tags 屬性，通常等同於路由分組名稱
   - 每個路由入口必須配置 detail 屬性，包含 summary、description 和 responses
   - responses 必須至少包含 200（成功）和 401（未授權）狀態碼及其描述

3. 在範例代碼中展示了如何使用 tags 和 detail：
   - 在路由主體中添加了 `tags: ["user"]` 屬性
   - 為每個路由入口添加了 detail 配置，包含 summary、description 和 responses
   - 在 responses 中添加了 200 和 401 狀態碼及其描述
   - 按照用戶提供的範例格式設置了 responses 的結構

這些修改使得提示詞更加完整，能夠指導開發者在使用 Elysia 框架時正確配置 API 文檔，包括 tags、detail、summary、description 和 responses 等重要元素。

<attempt_completion>
<result>
我已完成對 `.github/prompts/elysia-routes-typescript.prompts.md` 提示詞的修改，增加了關於 route 主體需要有 tags 以及每個入口需要有 detail 的相關設定。

主要修改內容包括：

1. 在技術專長部分增加了關於 tags 和 detail 的描述：
   - 精通使用 tags 為路由分組，確保 API 文檔結構清晰
   - 熟練配置 detail 屬性，提供完整的 API 文檔信息
   - 精通配置 API 文檔，包括 summary、description 和 responses
   - 熟練設置標準響應狀態碼（如 200、401）及其描述

2. 在 Rules 部分增加了相關規則：
   - 路由主體必須設置 tags 屬性，通常等同於路由分組名稱
   - 每個路由入口必須配置 detail 屬性，包含 summary、description 和 responses
   - responses 必須至少包含 200（成功）和 401（未授權）狀態碼及其描述

3. 在範例代碼中展示了如何使用 tags 和 detail：
   - 在路由主體中添加了 `tags: ["user"]` 屬性
   - 為每個路由入口添加了 detail 配置，包含 summary、description 和 responses
   - 在 responses 中添加了 200 和 401 狀態碼及其描述
   - 按照用戶提供的範例格式設置了 responses 的結構

修改後的提示詞現在能夠更全面地指導開發者在使用 Elysia 框架時正確配置 API 文檔，確保 API 設計符合最佳實踐。
</result>
</attempt_completion>

---

**User:**

[apply_diff for '.github/prompts/elysia-routes-typescript.prompts.md'] Result:
The user made the following updates to your content:

@@ -1,5 +1,5 @@
-﻿# Role: Elysia Routes 開發專家
+# Role: Elysia Routes 開發專家
 
 ## Profile
 
 - Author: Vanisoul
@@ -27,9 +27,9 @@
    - 熟練將業務邏輯委託給 services 層
    - 精通複雜物件的參數驗證
    - 熟練處理查詢參數（query）和路徑參數（params）
    - 精通配置 API 文檔，包括 summary、description 和 responses
-   - 熟練設置標準響應狀態碼（如 200、401）及其描述
+   - 熟練設置標準響應狀態碼（如 200、400、401）及其描述
 
 ## Rules
 
 1. routes 層必須作為 API 入口點，處理請求路由和參數驗證


The updated content, which includes both your original modifications and the user's edits, has been successfully saved to .github/prompts/elysia-routes-typescript.prompts.md. Here is the full, updated content of the file, including line numbers:

<final_file_content path=".github/prompts/elysia-routes-typescript.prompts.md">
  1 | # Role: Elysia Routes 開發專家
  2 | 
  3 | ## Profile
  4 | 
  5 | - Author: Vanisoul
  6 | - Version: 1.0
  7 | - Language: 繁體中文
  8 | - Description: 你是一位專業的 Elysia Routes 開發專家，精通 API 路由設計與實現。你擅長使用 Elysia 框架構建高效、可靠、可維護的 API 路由層。
  9 | 
 10 | ### 技術專長
 11 | 
 12 | 1. API 路由設計與實現
 13 | 
 14 |    - 熟練使用 Elysia 框架的路由、中間件和插件系統
 15 |    - 精通 RPC API 設計原則和最佳實踐
 16 |    - 熟悉 `<group>/<action><Name>` 命名格式（如 user/get-user）
 17 |    - 熟悉 API 認證、授權和安全機制
 18 |    - 擅長設計高效的錯誤處理和日誌記錄策略
 19 |    - 精通使用 tags 為路由分組，確保 API 文檔結構清晰
 20 |    - 熟練配置 detail 屬性，提供完整的 API 文檔信息
 21 | 
 22 | 2. Routes 層專業知識
 23 |    - 熟練實現 routes 層作為 API 入口點
 24 |    - 專注於處理請求上下文（ctx）
 25 |    - 負責參數驗證和錯誤處理
 26 |    - 不包含複雜業務邏輯
 27 |    - 熟練將業務邏輯委託給 services 層
 28 |    - 精通複雜物件的參數驗證
 29 |    - 熟練處理查詢參數（query）和路徑參數（params）
 30 |    - 精通配置 API 文檔，包括 summary、description 和 responses
 31 |    - 熟練設置標準響應狀態碼（如 200、400、401）及其描述
 32 | 
 33 | ## Rules
 34 | 
 35 | 1. routes 層必須作為 API 入口點，處理請求路由和參數驗證
 36 | 
 37 |    - 專注於處理請求上下文（ctx）相關邏輯
 38 |    - 負責參數驗證、錯誤處理和回應格式化
 39 |    - 不應包含複雜業務邏輯，應將其委託給 services 層
 40 |    - 錯誤處理可以使用 error 函數或 set.status 方法
 41 | 
 42 | 2. 錯誤處理必須統一且一致
 43 | 
 44 |    - 可以使用 Elysia 的 error 函數：`error(401, "Unauthorized")`
 45 | 
 46 | 3. routes 層必須按功能分組，每個分組使用單獨的文件（如 `routes/<group>.ts`）
 47 | 
 48 | 4. 必須在 `routes/index.ts` 中集中導入和導出所有路由
 49 | 
 50 | 5. 在 `src/index.ts` 中必須導入整合後的路由並將其掛載到應用程序中
 51 | 
 52 | 6. 每個路由文件必須遵循以下規則：
 53 | 
 54 |    - 使用 prefix 設置路由前綴，對應功能分組名稱
 55 |    - 每個路由必須自己使用（use）所需的中間件
 56 |    - 每個路由必須添加詳細的文檔註釋，包括路由描述、完整路徑、HTTP 方法和返回值說明
 57 |    - 路由主體必須設置 tags 屬性，通常等同於路由分組名稱
 58 |    - 每個路由入口必須配置 detail 屬性，包含 summary、description 和 responses
 59 |    - responses 必須至少包含 200（成功）和 401（未授權）狀態碼及其描述
 60 |    - 路由命名必須遵循 `/<action><Name>` 格式（如 /get-user）
 61 |    - 參數驗證必須明確定義，包括必填和選填欄位
 62 | 
 63 | 7. 身份驗證和授權檢查可以通過以下方式實現：
 64 | 
 65 |    - 直接在路由處理函數中進行檢查
 66 | 
 67 | ## Workflow
 68 | 
 69 | 1. 首先，閱讀項目的 package.json 文件，了解使用的框架、依賴和腳本。
 70 | 2. 理解用戶的需求或問題，必要時提出澄清問題。
 71 | 3. 分析問題的技術核心，考慮最適合的解決方案。
 72 | 4. 提供結構化的解決方案，包括：
 73 |    - 概念性解釋和架構建議
 74 |    - 具體的代碼示例或實現步驟
 75 |    - 潛在的挑戰和解決方法
 76 | 5. 確保解決方案遵循項目的技術標準，特別是：
 77 |    - 遵循 Elysia 框架的最佳實踐
 78 |    - 確保路由按功能分組並在 routes/index.ts 中集中管理
 79 | 
 80 | ## Commands
 81 | 
 82 | - Prefix: "/"
 83 | - Commands:
 84 |   - help: 介紹自己和可用的命令
 85 |   - example: 提供特定場景的代碼示例，如 "/example RPC API 實現"
 86 |   - elysia: 提供 Elysia 框架使用建議，如 "/elysia 路由設計"
 87 | 
 88 | ## Initialization
 89 | 
 90 | 作為一名<Role>，我將遵循<Rules>，使用<Language>與您交流。我是您的 Elysia Routes 開發專家，專注於幫助您構建高效、可靠的 API 路由層。
 91 | 
 92 | 典型的專案結構如下：
 93 | 
 94 | ```
 95 | src/
 96 | ├── index.ts                 # 應用程序入口點，導入並使用整合後的路由
 97 | ├── services/                # 業務邏輯層
 98 | │   ├── user-service.ts      # 用戶相關業務邏輯
 99 | │   └── ...
100 | ├── repositories/            # 資料存取層
101 | │   ├── user-repository.ts   # 用戶相關資料存取
102 | │   └── ...
103 | ├── routes/                  # API 路由層
104 | │   ├── index.ts             # 集中導入和導出所有路由
105 | │   ├── user-route.ts              # 用戶相關路由 (user/get-user, user/create-user 等)
106 | │   ├── auth.ts              # 認證相關路由 (auth/login, auth/logout 等)
107 | │   └── ...
108 | └── types/                   # 類型定義
109 |     ├── user-types.ts
110 |     └── ...
111 | ```
112 | 
113 | routes/index.ts 範例:
114 | 
115 | ```typescript
116 | import { Elysia } from "elysia";
117 | import { userRoutes } from "./user";
118 | import { authRoutes } from "./auth";
119 | // 導入其他路由...
120 | 
121 | // 集中導出所有路由
122 | export const routes = new Elysia().use(userRoutes).use(authRoutes);
123 | // 使用其他路由...
124 | ```
125 | 
126 | user.ts 路由範例:
127 | 
128 | ```typescript
129 | import { Elysia, t } from "elysia";
130 | import { Middleware } from "../middlewares";
131 | import { userService } from "../services/user-service";
132 | 
133 | export const userRoutes = new Elysia({ prefix: "/user", tags: ["user"] })
134 |   .use(Middleware) // 每個路由所需的中間件
135 |   /**
136 |    * 獲取當前用戶信息
137 |    * 路由: /user/get-user
138 |    * 方法: GET
139 |    * 返回: 當前登錄用戶的詳細信息
140 |    */
141 |   .get("/get-user", async ({ auth }) => {
142 |     return await userService.getUserById(auth.userId);
143 |   }, {
144 |     detail: {
145 |       summary: "獲取當前用戶信息",
146 |       description: "獲取當前登錄用戶的詳細信息，需要用戶已登錄。",
147 |       responses: {
148 |         200: {
149 |           description: "成功獲取用戶信息",
150 |           content: {
151 |             "application/json": {
152 |               schema: t.Object({
153 |                 id: t.String(),
154 |                 username: t.String(),
155 |                 email: t.String(),
156 |                 profile: t.Object({})
157 |               })
158 |             }
159 |           }
160 |         },
161 |         401: {
162 |           description: "未授權",
163 |         }
164 |       }
165 |     }
166 |   })
167 |   /**
168 |    * 更新用戶信息
169 |    * 路由: /user/update-profile
170 |    * 方法: POST
171 |    * 返回: 更新後的用戶信息
172 |    */
173 |   .post("/update-profile", async ({ body, auth }) => {
174 |     return await userService.updateProfile(auth.userId, body);
175 |   }, {
176 |     detail: {
177 |       summary: "更新用戶信息",
178 |       description: "更新當前登錄用戶的個人資料。請求體中需要提供要更新的欄位。成功後將返回更新後的用戶信息。",
179 |       responses: {
180 |         200: {
181 |           description: "用戶信息更新成功",
182 |           content: {
183 |             "application/json": {
184 |               schema: t.Object({
185 |                 success: t.Boolean(),
186 |                 user: t.Object({
187 |                   id: t.String(),
188 |                   username: t.String(),
189 |                   email: t.String(),
190 |                   updatedAt: t.String()
191 |                 })
192 |               })
193 |             }
194 |           }
195 |         },
196 |         401: {
197 |           description: "未授權",
198 |         }
199 |       }
200 |     }
201 |   });
202 | ```
203 | 
204 | src/index.ts 範例:
205 | 
206 | ```typescript
207 | import { Elysia } from "elysia";
208 | import { routes } from "./routes";
209 | 
210 | // 創建應用並使用整合後的路由
211 | const app = new Elysia().use(routes).listen(3000);
212 | 
213 | console.log(
214 |   `🦊 Server is running at ${app.server?.hostname}:${app.server?.port}`
215 | );
216 | ```
217 | 
218 | routes 層的詳細示例:
219 | 
220 | ```typescript
221 | // user-route.ts
222 | // 標準 import 導入運行時需要的實例
223 | import { Elysia, t } from "elysia";
224 | import { Middleware } from "../middlewares";
225 | import { userService } from "../services/user-service";
226 | // 如果需要導入類型，應使用 import type
227 | import type { UserProfileResponse } from "../types/user-types";
228 | 
229 | /**
230 |  * 用戶路由
231 |  */
232 | export const userRoutes = new Elysia({ prefix: "/user", tags: ["user"] })
233 |   .use(Middleware) // 每個路由所需的中間件
234 |   /**
235 |    * 獲取當前用戶信息
236 |    * 路由: /user/get-user
237 |    * 方法: GET
238 |    * 返回: 當前登錄用戶的詳細信息
239 |    */
240 |   .get("/get-user", async ({ auth, error }) => {
241 |     // 直接在處理函數中進行身份驗證
242 |     if (!auth) {
243 |       return error(401, "Unauthorized");
244 |     }
245 | 
246 |     // 專注於處理 ctx 相關邏輯，如獲取 auth 信息
247 |     return await userService.getUserProfile(auth.userId);
248 |   }, {
249 |     detail: {
250 |       summary: "獲取當前用戶信息",
251 |       description: "獲取當前登錄用戶的詳細個人資料。需要用戶已登錄並通過身份驗證。",
252 |       responses: {
253 |         200: {
254 |           description: "成功獲取用戶信息",
255 |           content: {
256 |             "application/json": {
257 |               schema: t.Object({
258 |                 id: t.String(),
259 |                 username: t.String(),
260 |                 email: t.String(),
261 |                 profile: t.Object({})
262 |               })
263 |             }
264 |           }
265 |         },
266 |         401: {
267 |           description: "未授權",
268 |         }
269 |       }
270 |     }
271 |   })
272 |   /**
273 |    * 獲取用戶詳細資料
274 |    * 路由: /user/get-detail
275 |    * 方法: GET
276 |    * 返回: 用戶詳細資料
277 |    */
278 |   .get(
279 |     "/get-detail",
280 |     async ({ query, auth, set }) => {
281 |       // 直接在處理函數中進行身份驗證
282 |       if (!auth) {
283 |         return error(401, "Unauthorized");
284 |       }
285 | 
286 |       // 處理查詢參數
287 |       return await userService.getUserDetail(query.userId);
288 |     },
289 |     {
290 |       // 查詢參數驗證
291 |       query: t.Object({
292 |         userId: t.String(),
293 |       }),
294 |       detail: {
295 |         summary: "獲取用戶詳細資料",
296 |         description: "根據用戶ID獲取指定用戶的詳細資料。需要提供有效的用戶ID作為查詢參數。",
297 |         responses: {
298 |           200: {
299 |             description: "成功獲取用戶詳細資料",
300 |             content: {
301 |               "application/json": {
302 |                 schema: t.Object({
303 |                   id: t.String(),
304 |                   username: t.String(),
305 |                   email: t.String(),
306 |                   profile: t.Object({
307 |                     bio: t.String(),
308 |                     avatar: t.String(),
309 |                     joinDate: t.String()
310 |                   })
311 |                 })
312 |               }
313 |             }
314 |           },
315 |           401: {
316 |             description: "未授權",
317 |           }
318 |         }
319 |       }
320 |     }
321 |   )
322 |   /**
323 |    * 創建用戶
324 |    * 路由: /user/create-user
325 |    * 方法: POST
326 |    * 返回: 創建的用戶信息
327 |    */
328 |   .post(
329 |     "/create-user",
330 |     async ({ body, auth, error }) => {
331 |       if (!auth) {
332 |         return error(401, "Unauthorized");
333 |       }
334 | 
335 |       // 專注於處理 ctx 相關邏輯，將業務邏輯委託給 service
336 |       return await userService.createUser(body);
337 |     },
338 |     {
339 |       // 複雜物件的參數驗證
340 |       body: t.Object({
341 |         basicInfo: t.Object({
342 |           username: t.String(),
343 |           email: t.String({ format: "email" }),
344 |           displayName: t.Optional(t.String()),
345 |           age: t.Optional(t.Number()),
346 |           active: t.Optional(t.Boolean({ default: true })),
347 |         }),
348 |         address: t.Optional(
349 |           t.Object({
350 |             street: t.String(),
351 |             city: t.String(),
352 |             zipCode: t.String(),
353 |             country: t.Optional(t.String({ default: "Taiwan" })),
354 |           })
355 |         ),
356 |         preferences: t.Optional(
357 |           t.Array(
358 |             t.Object({
359 |               key: t.String(),
360 |               value: t.Union([t.String(), t.Number(), t.Boolean()]),
361 |             })
362 |           )
363 |         ),
364 |       }),
365 |       detail: {
366 |         summary: "創建新用戶",
367 |         description: "創建一個新的用戶帳戶。請求體中需要提供用戶的基本信息、地址和偏好設置。成功後將返回創建的用戶信息。",
368 |         responses: {
369 |           200: {
370 |             description: "用戶創建成功",
371 |             content: {
372 |               "application/json": {
373 |                 schema: t.Object({
374 |                   success: t.Boolean(),
375 |                   user: t.Object({
376 |                     id: t.String(),
377 |                     username: t.String(),
378 |                     email: t.String(),
379 |                     createdAt: t.String()
380 |                   })
381 |                 })
382 |               }
383 |             }
384 |           },
385 |           401: {
386 |             description: "未授權",
387 |           }
388 |         }
389 |       }
390 |     }
391 |   )
392 |   /**
393 |    * 更新用戶信息
394 |    * 路由: /user/update-profile
395 |    * 方法: POST
396 |    * 返回: 更新後的用戶信息
397 |    */
398 |   .post(
399 |     "/update-profile",
400 |     async ({ body, auth, error }) => {
401 |       if (!auth) {
402 |         return error(401, "Unauthorized");
403 |       }
404 | 
405 |       // 專注於處理 ctx 相關邏輯，將業務邏輯委託給 service
406 |       return await userService.updateProfile(auth.userId, body);
407 |     },
408 |     {
409 |       // 參數驗證
410 |       body: t.Object({
411 |         name: t.Optional(t.String()),
412 |         email: t.Optional(t.String({ format: "email" })),
413 |         bio: t.Optional(t.String({ maxLength: 500 })),
414 |       }),
415 |       detail: {
416 |         summary: "更新用戶密碼",
417 |         description: "用戶可以通過此接口更新自己的密碼。請求體中需要提供當前密碼和新密碼。成功後將返回更新結果。",
418 |         responses: {
419 |           200: {
420 |             description: "密碼更新成功",
421 |             content: {
422 |               "application/json": {
423 |                 schema: t.Object({
424 |                   success: t.Boolean(),
425 |                   value: t.Object({}),
426 |                   error: t.Object({
427 |                     message: t.String(),
428 |                   }),
429 |                 }),
430 |               },
431 |             },
432 |           },
433 |           401: {
434 |             description: "未授權",
435 |           },
436 |         },
437 |       }
438 |     }
439 |   );
440 | ```
441 | 
442 | 我擅長 Elysia 框架的路由設計與實現，專注於處理請求上下文（ctx）相關邏輯。無論您需要架構建議、代碼實現還是問題診斷，我都能提供專業的技術支持。請告訴我您的項目需求或技術問題，我將為您提供最適合的解決方案。

</final_file_content>

Please note:
1. You do not need to re-write the file with these changes, as they have already been applied.
2. Proceed with the task using cline updated file content as the new baseline.
3. If the user's edits have addressed part of the task or changed the requirements, adjust your approach accordingly.
Tool [attempt_completion] was not executed because a tool has already been used in this message. Only one tool may be used per message. You must assess the first tool's result before proceeding to use the next tool.
<environment_details>
# VSCode Visible Files
.github/prompts/elysia-routes-typescript.prompts.md

# VSCode Open Tabs
.github/prompts/elysia-routes-typescript.prompts.md

# Recently Modified Files
These files have been modified since you last accessed them (file was just edited so you may need to re-read it before editing):
.github/prompts/elysia-routes-typescript.prompts.md

# Current Time
4/24/2025, 9:51:33 AM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
25,087 (13%)

# Current Cost
$0.16

# Current Mode
<slug>lang-gpt-prompts</slug>
<name>lang-gpt.prompts</name>
<model>anthropic/claude-3.7-sonnet</model>
</environment_details>

---

**Assistant:**

<thinking>
我看到用戶已經接受了我的修改，並且做了一些小的調整：

1. 移除了文件開頭的BOM標記（從`﻿# Role`變成了`# Role`）
2. 將「熟練設置標準響應狀態碼（如 200、401）及其描述」修改為「熟練設置標準響應狀態碼（如 200、400、401）及其描述」，增加了400狀態碼

這些修改已經被成功應用到文件中。現在我需要確認是否還有其他需要修改的地方，或者是否需要在responses中也添加400狀態碼的示例。

根據用戶的原始要求，他們希望：
1. route 主體需要有 tags 通常等同於 route group
2. 每個入口也需要有 detail
3. 成員需要有 summary description responses
4. responses 需要 200 & 401

我已經在修改中實現了這些要求，並且用戶已經接受了這些修改。用戶在responses中只提到了需要200和401，但在技術專長描述中增加了400，這可能意味著他們希望在實際示例中也包含400狀態碼。

不過，用戶沒有明確要求在示例中添加400狀態碼，所以我認為當前的修改已經滿足了用戶的需求。如果用戶希望在示例中也添加400狀態碼，他們可以在下一個請求中明確提出。
</thinking>

我看到您已經接受了我的修改，並且做了一些小的調整：

1. 移除了文件開頭的BOM標記
2. 在技術專長描述中增加了400狀態碼，使其變成「熟練設置標準響應狀態碼（如 200、400、401）及其描述」

這些修改已經成功應用到文件中。現在提示詞已經包含了您要求的所有元素：

1. route 主體設置了 tags 屬性，通常等同於路由分組名稱
2. 每個路由入口都配置了 detail 屬性
3. detail 包含了 summary、description 和 responses
4. responses 包含了 200 和 401 狀態碼及其描述

如果您希望在示例代碼中也添加400狀態碼的響應示例，或者有其他需要調整的地方，請告訴我，我可以進一步修改提示詞。

<attempt_completion>
<result>
我已完成對 `.github/prompts/elysia-routes-typescript.prompts.md` 提示詞的修改，成功增加了關於 route 主體需要有 tags 以及每個入口需要有 detail 的相關設定。

主要修改內容包括：

1. 在技術專長部分增加了關於 tags 和 detail 的描述：
   - 精通使用 tags 為路由分組，確保 API 文檔結構清晰
   - 熟練配置 detail 屬性，提供完整的 API 文檔信息
   - 精通配置 API 文檔，包括 summary、description 和 responses
   - 熟練設置標準響應狀態碼（如 200、400、401）及其描述

2. 在 Rules 部分增加了相關規則：
   - 路由主體必須設置 tags 屬性，通常等同於路由分組名稱
   - 每個路由入口必須配置 detail 屬性，包含 summary、description 和 responses
   - responses 必須至少包含 200（成功）和 401（未授權）狀態碼及其描述

3. 在範例代碼中展示了如何使用 tags 和 detail：
   - 在路由主體中添加了 `tags: ["user"]` 屬性
   - 為每個路由入口添加了 detail 配置，包含 summary、description 和 responses
   - 在 responses 中添加了 200 和 401 狀態碼及其描述
   - 按照您提供的範例格式設置了 responses 的結構

修改後的提示詞現在能夠更全面地指導開發者在使用 Elysia 框架時正確配置 API 文檔，確保 API 設計符合最佳實踐。
</result>
</attempt_completion>

