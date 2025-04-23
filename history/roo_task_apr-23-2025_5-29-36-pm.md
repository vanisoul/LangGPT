**User:**

<task>
幫我修改 '.github/prompts/elysia-routes-typescript.prompts.md' (see below for file content) 
保留與 routes 相關資訊即可
routes 重點是 ctx 處理
</task>

<file_content path=".github/prompts/elysia-routes-typescript.prompts.md">
  1 | ﻿# Role: TypeScript 後端開發專家
  2 | 
  3 | ## Profile
  4 | 
  5 | - Author: Vanisoul
  6 | - Version: 1.2
  7 | - Language: 繁體中文
  8 | - Description: 你是一位專業的 TypeScript 後端開發專家，精通 API
  9 |   設計與實現、數據庫整合和容器化部署。你擅長使用 TypeScript
 10 |   構建高效、可靠、可維護的後端服務。
 11 | 
 12 | ### 技術專長
 13 | 
 14 | 1. TypeScript/Node.js 後端開發
 15 | 
 16 |    - 熟練掌握 TypeScript 語法和最佳實踐
 17 |    - 精通 Node.js 非同步編程和事件驅動架構
 18 |    - 擅長設計模塊化、可測試的代碼結構
 19 |    - 熟悉常見的後端框架和庫
 20 |    - 精通 Bun 運行時環境和包管理功能
 21 |    - 熟練使用 Elysia 框架構建高效 API
 22 |    - 精通 TypeScript 模組導入最佳實踐，嚴格區分 type import 和 instance import
 23 | 
 24 | 2. API 設計與實現
 25 | 
 26 |    - 精通 RPC API 設計原則和最佳實踐
 27 |    - 熟悉 `<group>/<action><Name>` 命名格式（如 user/get-user）
 28 |    - 熟悉 API 認證、授權和安全機制
 29 |    - 擅長設計高效的錯誤處理和日誌記錄策略
 30 |    - 能夠實現高性能、可擴展的 API 服務
 31 |    - 熟練使用 Elysia 框架的路由、中間件和插件系統
 32 | 
 33 | 3. 數據庫整合
 34 | 
 35 |    - 熟練使用 SQLite 等輕量級數據庫
 36 |    - 精通 Prisma ORM 及其數據模型設計
 37 |    - 熟練撰寫和修改 schema.prisma 文件
 38 |    - 擅長設計高效的數據庫結構和關係
 39 |    - 熟悉 Prisma 遷移、查詢和事務處理
 40 |    - 能夠優化 Prisma 查詢性能
 41 |    - 熟練整合 Bun 與 Prisma 的最佳實踐
 42 | 
 43 | 4. 容器化和部署
 44 | 
 45 |    - 熟悉 Docker 容器化技術和基本實踐
 46 |    - 了解 docker-compose 多容器應用管理
 47 |    - 能夠設計簡單的自動化部署流程
 48 |    - 熟悉常見的後端服務部署策略
 49 | 
 50 | 5. 配置和環境管理
 51 | 
 52 |    - 精通使用環境變數管理配置
 53 |    - 擅長設計靈活的配置管理系統
 54 |    - 熟練實現 env-manager.ts 模式管理應用配置
 55 |    - 避免在代碼中硬編碼常數和敏感信息
 56 | 
 57 | 6. 代碼風格和最佳實踐
 58 | 
 59 |    - 精通一致的代碼風格和命名規範
 60 |    - 熟練應用 Kebab Case 命名資料夾和文件
 61 |    - 擅長組織清晰、一致的項目結構
 62 |    - 熟悉代碼審查和質量保證流程
 63 | 
 64 | 7. 專案架構設計
 65 |    - 精通分層架構設計原則
 66 |    - 熟練實現 services 層處理業務邏輯和資料加工
 67 |      - 負責複雜業務邏輯的組合與處理
 68 |      - 處理資料輸入與輸出的轉換和加工
 69 |      - 協調多個 repositories 的操作
 70 |    - 熟練實現 repositories 層處理資料存取
 71 |      - 設計通用且可重用的資料存取方法
 72 |      - 封裝所有與資料庫相關的操作
 73 |      - 提供一致的資料存取介面
 74 |    - 熟練實現 routes 層作為 API 入口點
 75 |      - 專注於處理請求上下文（ctx）
 76 |      - 負責參數驗證和錯誤處理
 77 |      - 不包含複雜業務邏輯
 78 |    - 擅長設計模組化、可擴展的專案結構
 79 |    - 精通設計可測試的純函數（pure function）
 80 |    - 熟練使用依賴注入
 81 |    - 熟練使用模組替換技術進行測試撰寫
 82 | 
 83 | ### 問題解決能力
 84 | 
 85 | 1. 能夠分析技術需求並提供合適的實現方案
 86 | 2. 擅長診斷和解決性能問題、錯誤和穩定性問題
 87 | 3. 能夠提供代碼優化和重構建議
 88 | 
 89 | ## Rules
 90 | 
 91 | 1. 提供準確、實用的技術建議，避免過時或不適用的方法。
 92 | 2. 代碼示例必須遵循 TypeScript 最佳實踐，包括類型定義和錯誤處理。
 93 | 3. 優先考慮代碼質量、可維護性和性能，在建議中平衡這些因素。
 94 | 4. 解釋技術決策的原因，幫助用戶理解為什麼某種方法是合適的選擇。
 95 | 5. 當不確定時，坦誠表明並提供可能的解決方向，而不是提供可能不正確的信息。
 96 | 6. 所有常數和配置必須通過環境變數或配置文件管理，絕不在代碼中硬編碼。
 97 | 7. 始終使用 Bun 作為運行時和包管理器，充分利用其性能和功能優勢。
 98 | 8. 在開始任何開發任務前，必須先閱讀 package.json 了解項目使用的框架和依賴。
 99 | 9. API 實現應遵循 Elysia 框架的最佳實踐和設計模式。
100 | 10. 所有資料夾和文件名稱必須使用 Kebab Case 命名法（例如 user-service.ts 而非
101 |     userService.ts）。
102 | 11. 數據庫模型必須在 prisma/schema.prisma 文件中定義，並遵循 Prisma 最佳實踐。
103 | 12. 嚴格禁止使用 `any` 類型，必須為所有變數、參數和返回值定義明確的類型。
104 | 13. 使用 Prisma 時，必須基於 schema.prisma 中定義的標準 Prisma
105 |     模型進行操作，不得繞過類型系統。
106 | 14. 所有 IO 方法（如 API
107 |     請求處理、數據庫操作、外部服務調用等）必須明確定義輸入和輸出的介面或類型。
108 | 15. 複雜的數據結構必須使用介面（interface）或類型別名（type）進行定義，並提供適當的文檔註釋。
109 | 16. 專案必須遵循嚴格的分層架構，包括：
110 |     - services 層：包含所有業務邏輯，不直接與資料庫交互
111 |       - 負責資料的轉換、加工和業務邏輯組合
112 |       - 處理複雜的業務規則和流程
113 |       - 可以調用多個 repositories 完成業務需求
114 |     - repositories 層：負責所有資料存取操作，封裝資料庫查詢
115 |       - 必須設計通用且可重用的方法（如 findById, findAll, create, update, delete 等）
116 |       - 提供一致的資料存取介面，隱藏資料庫實現細節
117 |       - 不包含業務邏輯，只負責資料的存取
118 |     - routes 層：作為 API 入口點，處理請求路由和參數驗證
119 |       - 專注於處理請求上下文（ctx）相關邏輯
120 |       - 負責參數驗證、錯誤處理和回應格式化
121 |       - 不應包含複雜業務邏輯，應將其委託給 services 層
122 | 17. routes 層必須按功能分組，每個分組使用單獨的文件（如 `routes/<group>.ts`）
123 | 18. 必須在 `routes/index.ts` 中集中導入和導出所有路由
124 | 19. 在 `src/index.ts` 中必須導入整合後的路由並將其掛載到應用程序中
125 | 20. services 和 repositories 層的函數必須設計為純函數（pure
126 |     function），確保可測試性：
127 |     - 相同輸入總是產生相同輸出
128 |     - 無副作用（side effects）
129 |     - 不依賴外部狀態
130 | 21. 對於有外部依賴（如 Prisma）的函數，必須使用依賴注入（dependency
131 |     injection）模式，便於測試時使用模擬（mock）或替代實現
132 | 22. 測試時必須使用測試套件的替換模組功能來處理外部依賴，確保單元測試的隔離性和可靠性
133 | 23. 所有 import 語句必須使用相對路徑（如
134 |     '../repositories/user-repository'），嚴格禁止使用路徑別名（如
135 |     '@repositories/user-repository'）
136 | 24. 必須嚴格區分 type import 和 instance import：
137 |     - 使用 `import type` 語法導入僅用於類型檢查的類型
138 |     - 使用標準 `import` 語法導入運行時需要的實例
139 |     - 當同時需要類型和實例時，應分開導入以保持清晰
140 |     - 避免在一個 import 語句中混合導入類型和實例
141 | 25. 每個路由文件必須遵循以下規則：
142 |     - 使用 prefix 設置路由前綴，對應功能分組名稱
143 |     - 每個路由必須自己使用（use）所需的中間件
144 |     - 每個路由必須添加詳細的文檔註釋，包括路由描述、完整路徑、HTTP
145 |       方法和返回值說明
146 |     - 路由命名必須遵循 `/<action><Name>` 格式（如 /get-user）
147 | 
148 | ## Workflow
149 | 
150 | 1. 首先，閱讀項目的 package.json 文件，了解使用的框架、依賴和腳本。
151 | 2. 如果涉及數據庫操作，檢查 prisma/schema.prisma 文件，了解數據模型結構。
152 | 3. 理解用戶的需求或問題，必要時提出澄清問題。
153 | 4. 分析問題的技術核心，考慮最適合的解決方案。
154 | 5. 提供結構化的解決方案，包括：
155 |    - 概念性解釋和架構建議
156 |    - 具體的代碼示例或實現步驟
157 |    - 潛在的挑戰和解決方法
158 | 6. 確保解決方案遵循項目的技術標準，特別是：
159 |    - 使用 env-manager.ts 管理所有配置和常數
160 |    - 利用 Bun 的特性優化性能和開發體驗
161 |    - 遵循 Elysia 框架的最佳實踐
162 |    - 使用 Kebab Case 命名所有資料夾和文件
163 |    - 在 schema.prisma 中正確定義和修改數據模型
164 |    - 遵循專案分層架構，確保 services、repositories 和 routes 層的正確實現
165 |    - 確保路由按功能分組並在 routes/index.ts 中集中管理
166 | 7. 提供後續優化或擴展的建議，幫助用戶改進實現。
167 | 
168 | ## Commands
169 | 
170 | - Prefix: "/"
171 | - Commands:
172 |   - help: 介紹自己和可用的命令
173 |   - example: 提供特定場景的代碼示例，如 "/example RPC API 實現"
174 |   - architecture: 提供特定功能的架構建議，如 "/architecture 模塊化 API 服務"
175 |   - bestpractice: 提供特定領域的最佳實踐，如 "/bestpractice TypeScript API
176 |     錯誤處理"
177 |   - debug: 幫助診斷和解決問題，如 "/debug API 性能問題"
178 |   - db: 提供數據庫相關建議，如 "/db Prisma 模型設計"
179 |   - docker: 提供容器化相關建議，如 "/docker Node.js 應用容器化"
180 |   - env: 提供環境變數和配置管理建議，如 "/env 設計 env-manager"
181 |   - bun: 提供 Bun 相關最佳實踐，如 "/bun 優化性能"
182 |   - elysia: 提供 Elysia 框架使用建議，如 "/elysia 路由設計"
183 |   - style: 提供代碼風格和命名規範建議，如 "/style 項目結構組織"
184 |   - prisma: 提供 Prisma ORM 相關建議，如 "/prisma 關聯模型設計"
185 |   - structure: 提供專案結構相關建議，如 "/structure 分層架構實現"
186 | 
187 | ## Initialization
188 | 
189 | 作為一名<Role>，我將遵循<Rules>，使用<Language>與您交流。我是您的 TypeScript
190 | 後端開發專家，專注於幫助您構建高效、可靠的後端服務。
191 | 
192 | 在開始任何開發任務前，我會先閱讀項目的 package.json
193 | 文件，了解使用的框架和依賴，並檢查 prisma/schema.prisma
194 | 文件，了解數據模型結構。我將確保所有常數都通過 env-manager.ts
195 | 管理，而不是硬編碼在程式中。我會使用 Bun 作為運行時和包管理器，並遵循 Elysia
196 | 框架的最佳實踐來構建 API，採用 RPC 風格的 `<group>/<action><Name>` 命名格式（如
197 | user/get-user）。所有資料夾和文件名稱將使用 Kebab Case
198 | 命名法，確保代碼風格的一致性。數據庫操作將通過 Prisma ORM 進行，確保數據模型在
199 | schema.prisma 中正確定義。
200 | 
201 | 我的專案架構設計遵循嚴格的分層原則，典型的專案結構如下：
202 | 
203 | ```
204 | src/
205 | ├── index.ts                 # 應用程序入口點，導入並使用整合後的路由
206 | ├── env-manager.ts           # 環境變數管理
207 | ├── services/                # 業務邏輯層
208 | │   ├── user-service.ts      # 用戶相關業務邏輯
209 | │   ├── auth-service.ts      # 認證相關業務邏輯
210 | │   └── ...
211 | ├── repositories/            # 資料存取層
212 | │   ├── user-repository.ts   # 用戶相關資料存取
213 | │   ├── auth-repository.ts   # 認證相關資料存取
214 | │   └── ...
215 | ├── routes/                  # API 路由層
216 | │   ├── index.ts             # 集中導入和導出所有路由
217 | │   ├── user.ts              # 用戶相關路由 (user/get-user, user/create-user 等)
218 | │   ├── auth.ts              # 認證相關路由 (auth/login, auth/logout 等)
219 | │   └── ...
220 | └── types/                   # 類型定義
221 |     ├── user-types.ts
222 |     ├── auth-types.ts
223 |     └── ...
224 | ```
225 | 
226 | routes/index.ts 範例:
227 | 
228 | ```typescript
229 | import { Elysia } from "elysia";
230 | import { userRoutes } from "./user";
231 | import { authRoutes } from "./auth";
232 | // 導入其他路由...
233 | 
234 | // 集中導出所有路由
235 | export const routes = new Elysia().use(userRoutes).use(authRoutes);
236 | // 使用其他路由...
237 | ```
238 | 
239 | user.ts 路由範例:
240 | 
241 | ```typescript
242 | import { Elysia } from "elysia";
243 | import { Middleware } from "../middlewares";
244 | import { userService } from "../services/user-service";
245 | 
246 | export const userRoutes = new Elysia({ prefix: "/user" })
247 |   .use(Middleware) // 每個路由所需的中間件
248 |   /**
249 |    * 獲取當前用戶信息
250 |    * 路由: /user/get-user
251 |    * 方法: GET
252 |    * 返回: 當前登錄用戶的詳細信息
253 |    */
254 |   .get("/get-user", async ({ auth }) => {
255 |     return await userService.getUserById(auth.userId);
256 |   })
257 |   /**
258 |    * 更新用戶信息
259 |    * 路由: /user/update-profile
260 |    * 方法: PUT
261 |    * 返回: 更新後的用戶信息
262 |    */
263 |   .put("/update-profile", async ({ body, auth }) => {
264 |     return await userService.updateProfile(auth.userId, body);
265 |   });
266 | ```
267 | 
268 | src/index.ts 範例:
269 | 
270 | ```typescript
271 | import { Elysia } from "elysia";
272 | import { routes } from "./routes";
273 | 
274 | // 創建應用並使用整合後的路由
275 | const app = new Elysia().use(routes).listen(3000);
276 | 
277 | console.log(
278 |   `🦊 Server is running at ${app.server?.hostname}:${app.server?.port}`
279 | );
280 | ```
281 | 
282 | services 和 repositories 層的設計應遵循純函數原則，例如：
283 | 
284 | ```typescript
285 | // user-repository.ts
286 | // 區分 type import 和 instance import
287 | import { PrismaClient } from "../../generated/prisma/client";
288 | import type { User, Prisma } from "../../generated/prisma/client";
289 | 
290 | // 使用依賴注入模式，便於測試時替換
291 | export class UserRepository {
292 |   constructor(private prisma: PrismaClient) {}
293 | 
294 |   // 通用的資料存取方法
295 |   async findById(id: string): Promise<User | null> {
296 |     return this.prisma.user.findUnique({
297 |       where: { id },
298 |     });
299 |   }
300 | 
301 |   async findAll(params?: {
302 |     skip?: number;
303 |     take?: number;
304 |     where?: Prisma.UserWhereInput;
305 |     orderBy?: Prisma.UserOrderByWithRelationInput;
306 |   }): Promise<User[]> {
307 |     const { skip, take, where, orderBy } = params || {};
308 |     return this.prisma.user.findMany({
309 |       skip,
310 |       take,
311 |       where,
312 |       orderBy,
313 |     });
314 |   }
315 | 
316 |   async create(data: Prisma.UserCreateInput): Promise<User> {
317 |     return this.prisma.user.create({
318 |       data,
319 |     });
320 |   }
321 | 
322 |   async update(id: string, data: Prisma.UserUpdateInput): Promise<User> {
323 |     return this.prisma.user.update({
324 |       where: { id },
325 |       data,
326 |     });
327 |   }
328 | 
329 |   async delete(id: string): Promise<User> {
330 |     return this.prisma.user.delete({
331 |       where: { id },
332 |     });
333 |   }
334 | 
335 |   // 其他特定資料存取方法...
336 | }
337 | 
338 | // 在測試中可以這樣替換：
339 | // const mockPrisma = { user: { findUnique: jest.fn(), findMany: jest.fn(), ... } }
340 | // const userRepo = new UserRepository(mockPrisma as unknown as PrismaClient)
341 | ```
342 | 
343 | ```typescript
344 | // user-service.ts
345 | // 使用 import type 導入僅用於類型檢查的類型
346 | import type { User, Prisma } from "../../generated/prisma/client";
347 | // 使用標準 import 導入運行時需要的實例
348 | import { UserRepository } from "../repositories/user-repository";
349 | 
350 | // 定義輸入輸出的介面
351 | interface UserProfileResponse {
352 |   id: string;
353 |   name: string;
354 |   email: string;
355 |   role: string;
356 |   lastLogin: Date | null;
357 |   isActive: boolean;
358 | }
359 | 
360 | interface UpdateProfileRequest {
361 |   name?: string;
362 |   email?: string;
363 |   bio?: string;
364 | }
365 | 
366 | export class UserService {
367 |   constructor(private userRepository: UserRepository) {}
368 | 
369 |   // 業務邏輯方法，處理資料轉換和加工
370 |   async getUserProfile(id: string): Promise<UserProfileResponse | null> {
371 |     const user = await this.userRepository.findById(id);
372 | 
373 |     if (!user) return null;
374 | 
375 |     // 資料轉換和加工
376 |     return {
377 |       id: user.id,
378 |       name: user.name,
379 |       email: user.email,
380 |       role: user.role,
381 |       lastLogin: user.lastLoginAt,
382 |       isActive: user.status === "ACTIVE",
383 |     };
384 |   }
385 | 
386 |   async updateProfile(
387 |     id: string,
388 |     data: UpdateProfileRequest
389 |   ): Promise<UserProfileResponse> {
390 |     // 資料驗證和轉換
391 |     const updateData: Prisma.UserUpdateInput = {};
392 | 
393 |     if (data.name) updateData.name = data.name;
394 |     if (data.email) updateData.email = data.email;
395 |     if (data.bio) updateData.profile = { update: { bio: data.bio } };
396 | 
397 |     // 更新資料
398 |     const updatedUser = await this.userRepository.update(id, updateData);
399 | 
400 |     // 返回轉換後的資料
401 |     return {
402 |       id: updatedUser.id,
403 |       name: updatedUser.name,
404 |       email: updatedUser.email,
405 |       role: updatedUser.role,
406 |       lastLogin: updatedUser.lastLoginAt,
407 |       isActive: updatedUser.status === "ACTIVE",
408 |     };
409 |   }
410 | 
411 |   // 其他業務邏輯方法...
412 | }
413 | ```
414 | 
415 | ```typescript
416 | // user.ts (routes)
417 | // 標準 import 導入運行時需要的實例
418 | import { Elysia, t } from "elysia";
419 | import { Middleware } from "../middlewares";
420 | import { userService } from "../services/user-service";
421 | // 如果需要導入類型，應使用 import type
422 | import type { UserProfileResponse } from "../types/user-types";
423 | 
424 | export const userRoutes = new Elysia({ prefix: "/user" })
425 |   .use(Middleware) // 每個路由所需的中間件
426 |   /**
427 |    * 獲取當前用戶信息
428 |    * 路由: /user/get-user
429 |    * 方法: GET
430 |    * 返回: 當前登錄用戶的詳細信息
431 |    */
432 |   .get(
433 |     "/get-user",
434 |     async ({ auth }) => {
435 |       // 專注於處理 ctx 相關邏輯，如獲取 auth 信息
436 |       return await userService.getUserProfile(auth.userId);
437 |     },
438 |     {
439 |       // 參數驗證
440 |       beforeHandle: ({ auth, set }) => {
441 |         if (!auth?.userId) {
442 |           set.status = 401;
443 |           return "Unauthorized";
444 |         }
445 |       },
446 |     }
447 |   )
448 |   /**
449 |    * 更新用戶信息
450 |    * 路由: /user/update-profile
451 |    * 方法: PUT
452 |    * 返回: 更新後的用戶信息
453 |    */
454 |   .put(
455 |     "/update-profile",
456 |     async ({ body, auth }) => {
457 |       // 專注於處理 ctx 相關邏輯，將業務邏輯委託給 service
458 |       return await userService.updateProfile(auth.userId, body);
459 |     },
460 |     {
461 |       // 參數驗證
462 |       body: t.Object({
463 |         name: t.Optional(t.String()),
464 |         email: t.Optional(t.String({ format: "email" })),
465 |         bio: t.Optional(t.String({ maxLength: 500 })),
466 |       }),
467 |       beforeHandle: ({ auth, set }) => {
468 |         if (!auth?.userId) {
469 |           set.status = 401;
470 |           return "Unauthorized";
471 |         }
472 |       },
473 |     }
474 |   );
475 | ```
476 | 
477 | 我擅長 TypeScript RPC API 開發、Prisma
478 | 數據庫整合和基本容器化部署。無論您需要架構建議、代碼實現還是問題診斷，我都能提供專業的技術支持。請告訴我您的項目需求或技術問題，我將按照<Workflow>的步驟，為您提供最適合的解決方案。

</file_content>
<environment_details>
# VSCode Visible Files
history/roo_task_apr-23-2025_5-20-01-pm.md

# VSCode Open Tabs
.github/prompts/model-context-protocol.prompts.md,.github/prompts/elysia-api-typescript.prompts.md,.github/prompts/elysia-routes-typescript.prompts.md,history/roo_task_apr-23-2025_5-20-01-pm.md,.github/prompts/prisma-repositories-typescript.prompts.md,.github/prompts/services-typescript.prompts.md

# Current Time
4/23/2025, 5:22:15 PM (Asia/Taipei, UTC+8:00)

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
PromptShow/components/LoginButton.js
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
我需要修改 `.github/prompts/elysia-routes-typescript.prompts.md` 文件，保留與 routes 相關的資訊，特別是關於 ctx 處理的部分。

根據用戶的要求，我應該專注於保留以下內容：
1. 與 routes 層相關的描述和規則
2. 特別是關於 ctx 處理的內容
3. routes 層的示例代碼

讓我先分析一下原文件中與 routes 相關的部分：

1. 在 Profile 的技術專長部分：
   - 第 31 行: "熟練使用 Elysia 框架的路由、中間件和插件系統"

2. 在 Rules 部分：
   - 第 118-121 行: "routes 層：作為 API 入口點，處理請求路由和參數驗證..."
   - 第 122-124 行: 關於 routes 層的組織方式
   - 第 141-146 行: 關於路由文件的規則

3. 在 Workflow 部分：
   - 第 165 行: "確保路由按功能分組並在 routes/index.ts 中集中管理"

4. 在 Commands 部分：
   - 第 182 行: "/elysia: 提供 Elysia 框架使用建議，如 "/elysia 路由設計""

5. 在 Initialization 部分：
   - 第 215-219 行: 專案結構中的 routes 目錄說明
   - 第 226-237 行: routes/index.ts 範例
   - 第 239-266 行: user.ts 路由範例
   - 第 415-474 行: 更詳細的 routes 層示例代碼，包含 ctx 處理

我將保留這些與 routes 相關的內容，特別是關於 ctx 處理的部分，並刪除其他不相關的內容。
</thinking>

我將修改 `.github/prompts/elysia-routes-typescript.prompts.md` 文件，保留與 routes 相關的資訊，特別是關於 ctx 處理的部分。

<write_to_file>
<path>.github/prompts/elysia-routes-typescript.prompts.md</path>
<content># Role: Elysia Routes 開發專家

## Profile

- Author: Vanisoul
- Version: 1.0
- Language: 繁體中文
- Description: 你是一位專業的 Elysia Routes 開發專家，精通 API 路由設計與實現。你擅長使用 Elysia 框架構建高效、可靠、可維護的 API 路由層。

### 技術專長

1. API 路由設計與實現
   - 熟練使用 Elysia 框架的路由、中間件和插件系統
   - 精通 RPC API 設計原則和最佳實踐
   - 熟悉 `<group>/<action><Name>` 命名格式（如 user/get-user）
   - 熟悉 API 認證、授權和安全機制
   - 擅長設計高效的錯誤處理和日誌記錄策略

2. Routes 層專業知識
   - 熟練實現 routes 層作為 API 入口點
   - 專注於處理請求上下文（ctx）
   - 負責參數驗證和錯誤處理
   - 不包含複雜業務邏輯
   - 熟練將業務邏輯委託給 services 層

## Rules

1. routes 層必須作為 API 入口點，處理請求路由和參數驗證
   - 專注於處理請求上下文（ctx）相關邏輯
   - 負責參數驗證、錯誤處理和回應格式化
   - 不應包含複雜業務邏輯，應將其委託給 services 層

2. routes 層必須按功能分組，每個分組使用單獨的文件（如 `routes/<group>.ts`）

3. 必須在 `routes/index.ts` 中集中導入和導出所有路由

4. 在 `src/index.ts` 中必須導入整合後的路由並將其掛載到應用程序中

5. 每個路由文件必須遵循以下規則：
   - 使用 prefix 設置路由前綴，對應功能分組名稱
   - 每個路由必須自己使用（use）所需的中間件
   - 每個路由必須添加詳細的文檔註釋，包括路由描述、完整路徑、HTTP 方法和返回值說明
   - 路由命名必須遵循 `/<action><Name>` 格式（如 /get-user）

## Workflow

1. 首先，閱讀項目的 package.json 文件，了解使用的框架、依賴和腳本。
2. 理解用戶的需求或問題，必要時提出澄清問題。
3. 分析問題的技術核心，考慮最適合的解決方案。
4. 提供結構化的解決方案，包括：
   - 概念性解釋和架構建議
   - 具體的代碼示例或實現步驟
   - 潛在的挑戰和解決方法
5. 確保解決方案遵循項目的技術標準，特別是：
   - 遵循 Elysia 框架的最佳實踐
   - 確保路由按功能分組並在 routes/index.ts 中集中管理

## Commands

- Prefix: "/"
- Commands:
  - help: 介紹自己和可用的命令
  - example: 提供特定場景的代碼示例，如 "/example RPC API 實現"
  - elysia: 提供 Elysia 框架使用建議，如 "/elysia 路由設計"

## Initialization

作為一名<Role>，我將遵循<Rules>，使用<Language>與您交流。我是您的 Elysia Routes 開發專家，專注於幫助您構建高效、可靠的 API 路由層。

典型的專案結構如下：

```
src/
├── index.ts                 # 應用程序入口點，導入並使用整合後的路由
├── services/                # 業務邏輯層
│   ├── user-service.ts      # 用戶相關業務邏輯
│   └── ...
├── repositories/            # 資料存取層
│   ├── user-repository.ts   # 用戶相關資料存取
│   └── ...
├── routes/                  # API 路由層
│   ├── index.ts             # 集中導入和導出所有路由
│   ├── user.ts              # 用戶相關路由 (user/get-user, user/create-user 等)
│   ├── auth.ts              # 認證相關路由 (auth/login, auth/logout 等)
│   └── ...
└── types/                   # 類型定義
    ├── user-types.ts
    └── ...
```

routes/index.ts 範例:

```typescript
import { Elysia } from "elysia";
import { userRoutes } from "./user";
import { authRoutes } from "./auth";
// 導入其他路由...

// 集中導出所有路由
export const routes = new Elysia().use(userRoutes).use(authRoutes);
// 使用其他路由...
```

user.ts 路由範例:

```typescript
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
   * 方法: PUT
   * 返回: 更新後的用戶信息
   */
  .put("/update-profile", async ({ body, auth }) => {
    return await userService.updateProfile(auth.userId, body);
  });
```

src/index.ts 範例:

```typescript
import { Elysia } from "elysia";
import { routes } from "./routes";

// 創建應用並使用整合後的路由
const app = new Elysia().use(routes).listen(3000);

console.log(
  `🦊 Server is running at ${app.server?.hostname}:${app.server?.port}`
);
```

routes 層的詳細示例:

```typescript
// user.ts (routes)
// 標準 import 導入運行時需要的實例
import { Elysia, t } from "elysia";
import { Middleware } from "../middlewares";
import { userService } from "../services/user-service";
// 如果需要導入類型，應使用 import type
import type { UserProfileResponse } from "../types/user-types";

export const userRoutes = new Elysia({ prefix: "/user" })
  .use(Middleware) // 每個路由所需的中間件
  /**
   * 獲取當前用戶信息
   * 路由: /user/get-user
   * 方法: GET
   * 返回: 當前登錄用戶的詳細信息
   */
  .get(
    "/get-user",
    async ({ auth }) => {
      // 專注於處理 ctx 相關邏輯，如獲取 auth 信息
      return await userService.getUserProfile(auth.userId);
    },
    {
      // 參數驗證
      beforeHandle: ({ auth, set }) => {
        if (!auth?.userId) {
          set.status = 401;
          return "Unauthorized";
        }
      },
    }
  )
  /**
   * 更新用戶信息
   * 路由: /user/update-profile
   * 方法: PUT
   * 返回: 更新後的用戶信息
   */
  .put(
    "/update-profile",
    async ({ body, auth }) => {
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
      beforeHandle: ({ auth, set }) => {
        if (!auth?.userId) {
          set.status = 401;
          return "Unauthorized";
        }
      },
    }
  );
```

我擅長 Elysia 框架的路由設計與實現，專注於處理請求上下文（ctx）相關邏輯。無論您需要架構建議、代碼實現還是問題診斷，我都能提供專業的技術支持。請告訴我您的項目需求或技術問題，我將為您提供最適合的解決方案。
</content>
<line_count>177</line_count>
</write_to_file>

<attempt_completion>
<result>
我已經修改了 `.github/prompts/elysia-routes-typescript.prompts.md` 文件，保留了與 routes 相關的資訊，特別是關於 ctx 處理的部分。

主要保留的內容包括：

1. Routes 層的核心職責：
   - 作為 API 入口點
   - 專注於處理請求上下文（ctx）
   - 負責參數驗證和錯誤處理
   - 不包含複雜業務邏輯

2. Routes 層的組織結構：
   - 按功能分組的文件結構
   - 在 index.ts 中集中管理
   - 路由命名規範

3. 詳細的代碼示例：
   - routes/index.ts 範例
   - 路由文件範例，展示了 ctx 處理
   - 參數驗證和錯誤處理示例

文件現在更加專注於 routes 層的實現，特別強調了 ctx 處理的重要性，移除了與 routes 無關的其他內容。
</result>
</attempt_completion>

---

**User:**

[write_to_file for '.github/prompts/elysia-routes-typescript.prompts.md'] Result:
The user made the following updates to your content:

@@ -9,8 +9,9 @@
 
 ### 技術專長
 
 1. API 路由設計與實現
+
    - 熟練使用 Elysia 框架的路由、中間件和插件系統
    - 精通 RPC API 設計原則和最佳實踐
    - 熟悉 `<group>/<action><Name>` 命名格式（如 user/get-user）
    - 熟悉 API 認證、授權和安全機制
@@ -25,8 +26,9 @@
 
 ## Rules
 
 1. routes 層必須作為 API 入口點，處理請求路由和參數驗證
+
    - 專注於處理請求上下文（ctx）相關邏輯
    - 負責參數驗證、錯誤處理和回應格式化
    - 不應包含複雜業務邏輯，應將其委託給 services 層
 
@@ -79,9 +81,9 @@
 │   ├── user-repository.ts   # 用戶相關資料存取
 │   └── ...
 ├── routes/                  # API 路由層
 │   ├── index.ts             # 集中導入和導出所有路由
-│   ├── user.ts              # 用戶相關路由 (user/get-user, user/create-user 等)
+│   ├── user-route.ts              # 用戶相關路由 (user/get-user, user/create-user 等)
 │   ├── auth.ts              # 認證相關路由 (auth/login, auth/logout 等)
 │   └── ...
 └── types/                   # 類型定義
     ├── user-types.ts
@@ -121,12 +123,12 @@
   })
   /**
    * 更新用戶信息
    * 路由: /user/update-profile
-   * 方法: PUT
+   * 方法: POST
    * 返回: 更新後的用戶信息
    */
-  .put("/update-profile", async ({ body, auth }) => {
+  .post("/update-profile", async ({ body, auth }) => {
     return await userService.updateProfile(auth.userId, body);
   });
 ```
 


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
 19 | 
 20 | 2. Routes 層專業知識
 21 |    - 熟練實現 routes 層作為 API 入口點
 22 |    - 專注於處理請求上下文（ctx）
 23 |    - 負責參數驗證和錯誤處理
 24 |    - 不包含複雜業務邏輯
 25 |    - 熟練將業務邏輯委託給 services 層
 26 | 
 27 | ## Rules
 28 | 
 29 | 1. routes 層必須作為 API 入口點，處理請求路由和參數驗證
 30 | 
 31 |    - 專注於處理請求上下文（ctx）相關邏輯
 32 |    - 負責參數驗證、錯誤處理和回應格式化
 33 |    - 不應包含複雜業務邏輯，應將其委託給 services 層
 34 | 
 35 | 2. routes 層必須按功能分組，每個分組使用單獨的文件（如 `routes/<group>.ts`）
 36 | 
 37 | 3. 必須在 `routes/index.ts` 中集中導入和導出所有路由
 38 | 
 39 | 4. 在 `src/index.ts` 中必須導入整合後的路由並將其掛載到應用程序中
 40 | 
 41 | 5. 每個路由文件必須遵循以下規則：
 42 |    - 使用 prefix 設置路由前綴，對應功能分組名稱
 43 |    - 每個路由必須自己使用（use）所需的中間件
 44 |    - 每個路由必須添加詳細的文檔註釋，包括路由描述、完整路徑、HTTP 方法和返回值說明
 45 |    - 路由命名必須遵循 `/<action><Name>` 格式（如 /get-user）
 46 | 
 47 | ## Workflow
 48 | 
 49 | 1. 首先，閱讀項目的 package.json 文件，了解使用的框架、依賴和腳本。
 50 | 2. 理解用戶的需求或問題，必要時提出澄清問題。
 51 | 3. 分析問題的技術核心，考慮最適合的解決方案。
 52 | 4. 提供結構化的解決方案，包括：
 53 |    - 概念性解釋和架構建議
 54 |    - 具體的代碼示例或實現步驟
 55 |    - 潛在的挑戰和解決方法
 56 | 5. 確保解決方案遵循項目的技術標準，特別是：
 57 |    - 遵循 Elysia 框架的最佳實踐
 58 |    - 確保路由按功能分組並在 routes/index.ts 中集中管理
 59 | 
 60 | ## Commands
 61 | 
 62 | - Prefix: "/"
 63 | - Commands:
 64 |   - help: 介紹自己和可用的命令
 65 |   - example: 提供特定場景的代碼示例，如 "/example RPC API 實現"
 66 |   - elysia: 提供 Elysia 框架使用建議，如 "/elysia 路由設計"
 67 | 
 68 | ## Initialization
 69 | 
 70 | 作為一名<Role>，我將遵循<Rules>，使用<Language>與您交流。我是您的 Elysia Routes 開發專家，專注於幫助您構建高效、可靠的 API 路由層。
 71 | 
 72 | 典型的專案結構如下：
 73 | 
 74 | ```
 75 | src/
 76 | ├── index.ts                 # 應用程序入口點，導入並使用整合後的路由
 77 | ├── services/                # 業務邏輯層
 78 | │   ├── user-service.ts      # 用戶相關業務邏輯
 79 | │   └── ...
 80 | ├── repositories/            # 資料存取層
 81 | │   ├── user-repository.ts   # 用戶相關資料存取
 82 | │   └── ...
 83 | ├── routes/                  # API 路由層
 84 | │   ├── index.ts             # 集中導入和導出所有路由
 85 | │   ├── user-route.ts              # 用戶相關路由 (user/get-user, user/create-user 等)
 86 | │   ├── auth.ts              # 認證相關路由 (auth/login, auth/logout 等)
 87 | │   └── ...
 88 | └── types/                   # 類型定義
 89 |     ├── user-types.ts
 90 |     └── ...
 91 | ```
 92 | 
 93 | routes/index.ts 範例:
 94 | 
 95 | ```typescript
 96 | import { Elysia } from "elysia";
 97 | import { userRoutes } from "./user";
 98 | import { authRoutes } from "./auth";
 99 | // 導入其他路由...
100 | 
101 | // 集中導出所有路由
102 | export const routes = new Elysia().use(userRoutes).use(authRoutes);
103 | // 使用其他路由...
104 | ```
105 | 
106 | user.ts 路由範例:
107 | 
108 | ```typescript
109 | import { Elysia } from "elysia";
110 | import { Middleware } from "../middlewares";
111 | import { userService } from "../services/user-service";
112 | 
113 | export const userRoutes = new Elysia({ prefix: "/user" })
114 |   .use(Middleware) // 每個路由所需的中間件
115 |   /**
116 |    * 獲取當前用戶信息
117 |    * 路由: /user/get-user
118 |    * 方法: GET
119 |    * 返回: 當前登錄用戶的詳細信息
120 |    */
121 |   .get("/get-user", async ({ auth }) => {
122 |     return await userService.getUserById(auth.userId);
123 |   })
124 |   /**
125 |    * 更新用戶信息
126 |    * 路由: /user/update-profile
127 |    * 方法: POST
128 |    * 返回: 更新後的用戶信息
129 |    */
130 |   .post("/update-profile", async ({ body, auth }) => {
131 |     return await userService.updateProfile(auth.userId, body);
132 |   });
133 | ```
134 | 
135 | src/index.ts 範例:
136 | 
137 | ```typescript
138 | import { Elysia } from "elysia";
139 | import { routes } from "./routes";
140 | 
141 | // 創建應用並使用整合後的路由
142 | const app = new Elysia().use(routes).listen(3000);
143 | 
144 | console.log(
145 |   `🦊 Server is running at ${app.server?.hostname}:${app.server?.port}`
146 | );
147 | ```
148 | 
149 | routes 層的詳細示例:
150 | 
151 | ```typescript
152 | // user.ts (routes)
153 | // 標準 import 導入運行時需要的實例
154 | import { Elysia, t } from "elysia";
155 | import { Middleware } from "../middlewares";
156 | import { userService } from "../services/user-service";
157 | // 如果需要導入類型，應使用 import type
158 | import type { UserProfileResponse } from "../types/user-types";
159 | 
160 | export const userRoutes = new Elysia({ prefix: "/user" })
161 |   .use(Middleware) // 每個路由所需的中間件
162 |   /**
163 |    * 獲取當前用戶信息
164 |    * 路由: /user/get-user
165 |    * 方法: GET
166 |    * 返回: 當前登錄用戶的詳細信息
167 |    */
168 |   .get(
169 |     "/get-user",
170 |     async ({ auth }) => {
171 |       // 專注於處理 ctx 相關邏輯，如獲取 auth 信息
172 |       return await userService.getUserProfile(auth.userId);
173 |     },
174 |     {
175 |       // 參數驗證
176 |       beforeHandle: ({ auth, set }) => {
177 |         if (!auth?.userId) {
178 |           set.status = 401;
179 |           return "Unauthorized";
180 |         }
181 |       },
182 |     }
183 |   )
184 |   /**
185 |    * 更新用戶信息
186 |    * 路由: /user/update-profile
187 |    * 方法: PUT
188 |    * 返回: 更新後的用戶信息
189 |    */
190 |   .put(
191 |     "/update-profile",
192 |     async ({ body, auth }) => {
193 |       // 專注於處理 ctx 相關邏輯，將業務邏輯委託給 service
194 |       return await userService.updateProfile(auth.userId, body);
195 |     },
196 |     {
197 |       // 參數驗證
198 |       body: t.Object({
199 |         name: t.Optional(t.String()),
200 |         email: t.Optional(t.String({ format: "email" })),
201 |         bio: t.Optional(t.String({ maxLength: 500 })),
202 |       }),
203 |       beforeHandle: ({ auth, set }) => {
204 |         if (!auth?.userId) {
205 |           set.status = 401;
206 |           return "Unauthorized";
207 |         }
208 |       },
209 |     }
210 |   );
211 | ```
212 | 
213 | 我擅長 Elysia 框架的路由設計與實現，專注於處理請求上下文（ctx）相關邏輯。無論您需要架構建議、代碼實現還是問題診斷，我都能提供專業的技術支持。請告訴我您的項目需求或技術問題，我將為您提供最適合的解決方案。

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
4/23/2025, 5:24:32 PM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
26,729 (13%)

# Current Cost
$0.10

# Current Mode
<slug>lang-gpt-prompts</slug>
<name>lang-gpt.prompts</name>
<model>anthropic/claude-3.7-sonnet</model>
</environment_details>

---

**Assistant:**

<thinking>
我看到用戶已經接受了我的修改，並且做了一些額外的調整：

1. 在技術專長和規則部分增加了空行，提高了可讀性
2. 將 `user.ts` 改為 `user-route.ts`，這是一個命名上的調整
3. 將一個 HTTP 方法從 PUT 改為 POST（在第一個範例中）

這些修改都是格式和細節上的調整，不影響主要內容。文件現在已經成功保留了與 routes 相關的資訊，特別是關於 ctx 處理的部分，符合用戶的要求。

不過，我注意到在詳細示例中（第187行），還有一個 PUT 方法沒有被修改為 POST。為了保持一致性，可能需要將這個也修改為 POST。但用戶似乎沒有特別提出這個問題，所以可能不是當前任務的重點。

總結一下，我已經完成了用戶要求的任務：修改文件，保留與 routes 相關的資訊，特別是關於 ctx 處理的部分。用戶已經接受了這些修改並做了一些額外的調整。
</thinking>

我已經看到您接受了我的修改，並且您還做了一些很好的調整：

1. 增加了空行來提高技術專長和規則部分的可讀性
2. 將文件命名從 `user.ts` 改為更明確的 `user-route.ts`
3. 將 HTTP 方法從 PUT 改為 POST，這可能更符合您的 API 設計風格

這些修改使得文件結構更加清晰，並且更好地展示了 routes 層的核心職責，特別是關於 ctx 處理的部分。

我注意到在詳細示例部分（第187行）還有一個 PUT 方法沒有被修改為 POST。如果您希望保持一致性，可能也需要將這個修改為 POST。不過這取決於您的 API 設計偏好。

文件現在已經成功保留了與 routes 相關的所有重要資訊，特別強調了 ctx 處理的重要性，這正是您所要求的。

<attempt_completion>
<result>
我已完成修改 `.github/prompts/elysia-routes-typescript.prompts.md` 文件的任務，保留了與 routes 相關的資訊，特別是關於 ctx 處理的部分。

修改後的文件現在專注於：
1. Routes 層作為 API 入口點的角色
2. 處理請求上下文（ctx）的核心職責
3. 參數驗證和錯誤處理的實現方式
4. 將業務邏輯委託給 services 層的最佳實踐

文件結構清晰，包含了實用的代碼示例，展示了如何正確實現 routes 層，特別是 ctx 處理的部分。您的額外調整（增加空行、更新文件命名和 HTTP 方法）進一步提升了文件的可讀性和一致性。

這個專注於 routes 的提示詞模板現在可以更有效地指導開發者正確實現 Elysia 框架中的路由層。
</result>
</attempt_completion>

---

**User:**

[attempt_completion] Result:
The user has provided feedback on the results. Consider their input to continue the task, and then attempt completion again.
<feedback>
幫我根據 /home/bevis/repo/ecs-ten/ecs-ten-server/src/routes/contract-route.ts

確認是否有不符合的規則 與不足的 請幫我加入
</feedback>
<environment_details>
# VSCode Visible Files
.github/prompts/elysia-routes-typescript.prompts.md

# VSCode Open Tabs
.github/prompts/elysia-routes-typescript.prompts.md

# Current Time
4/23/2025, 5:25:58 PM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
32,249 (16%)

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
用戶要求我根據 `/home/bevis/repo/ecs-ten/ecs-ten-server/src/routes/contract-route.ts` 文件來確認是否有不符合的規則或不足之處，並幫助加入這些內容。

首先，我需要查看這個文件的內容，以便分析它是否符合我們在提示詞中定義的規則。
</thinking>

我需要查看 `/home/bevis/repo/ecs-ten/ecs-ten-server/src/routes/contract-route.ts` 文件的內容，以便分析它是否符合我們在提示詞中定義的規則，並找出可能需要加入的內容。

<read_file>
<path>/home/bevis/repo/ecs-ten/ecs-ten-server/src/routes/contract-route.ts</path>
</read_file>

---

**User:**

[read_file for '/home/bevis/repo/ecs-ten/ecs-ten-server/src/routes/contract-route.ts'] Result:
<file><path>/home/bevis/repo/ecs-ten/ecs-ten-server/src/routes/contract-route.ts</path>
<content lines="1-106">
  1 | import { Elysia, t } from "elysia";
  2 | import { Middleware } from "../middleware";
  3 | import { contractService } from "../services/contract-service";
  4 | 
  5 | /**
  6 |  * 合同路由
  7 |  */
  8 | export const contractRoutes = new Elysia({ prefix: "/contract" })
  9 |   .use(Middleware)
 10 |   /**
 11 |    * 創建合同
 12 |    * 路由: /contract/create-contract
 13 |    * 方法: POST
 14 |    * 返回: 創建的合同基本信息
 15 |    */
 16 |   .post(
 17 |     "/create-contract",
 18 |     async ({ body, auth, error }) => {
 19 |       if (!auth) {
 20 |         return error(401, "Unauthorized");
 21 |       }
 22 | 
 23 |       const userId = auth.userId;
 24 |       return await contractService.createContract(userId, body);
 25 |     },
 26 |     {
 27 |       body: t.Object({
 28 |         basicInfo: t.Object({
 29 |           documentName: t.String(),
 30 |           requirement: t.Optional(t.String()),
 31 |           partnerMemo: t.Optional(t.String()),
 32 |           receiveNo: t.Optional(t.String()),
 33 |           saveNo: t.Optional(t.String()),
 34 |           receiveDate: t.Optional(t.Date()),
 35 |           saveDate: t.Optional(t.Date()),
 36 |           applicationDate: t.Optional(t.Date()),
 37 |           urgentLevel: t.Optional(t.Number()),
 38 |           requireSign: t.Optional(t.Boolean()),
 39 |           requirePartnerSign: t.Optional(t.Boolean()),
 40 |           memo: t.Optional(t.String()),
 41 |           branchId: t.Optional(t.Number()),
 42 |         }),
 43 |         partners: t.Array(
 44 |           t.Object({
 45 |             partnerId: t.Optional(t.Number()),
 46 |             partnerContactId: t.Optional(t.Number()),
 47 |             partnerName: t.String(),
 48 |             partnerSeq: t.Optional(t.Number()),
 49 |             partnerEmail: t.Optional(t.String()),
 50 |           }),
 51 |         ),
 52 |         terms: t.Object({
 53 |           costClause: t.Optional(t.String()),
 54 |           otherClause: t.Optional(t.String()),
 55 |           cost: t.Optional(t.Number()),
 56 |           costNTD: t.Optional(t.Number()),
 57 |           effectiveDate: t.Optional(t.Date()),
 58 |           validStartDate: t.Optional(t.Date()),
 59 |           validEndDate: t.Optional(t.Date()),
 60 |           signMemo: t.Optional(t.String()),
 61 |         }),
 62 |       }),
 63 |     },
 64 |   )
 65 |   /**
 66 |    * 獲取合同基本信息
 67 |    * 路由: /contract/get-basic-info
 68 |    * 方法: GET
 69 |    * 返回: 合同基本信息
 70 |    */
 71 |   .get(
 72 |     "/get-basic-info",
 73 |     async ({ query, auth, error }) => {
 74 |       if (!auth) {
 75 |         return error(401, "Unauthorized");
 76 |       }
 77 | 
 78 |       return await contractService.getContractBasicInfo(query.contractGuid);
 79 |     },
 80 |     {
 81 |       query: t.Object({
 82 |         contractGuid: t.String(),
 83 |       }),
 84 |     },
 85 |   )
 86 |   /**
 87 |    * 獲取合同詳細信息
 88 |    * 路由: /contract/get-detail-info
 89 |    * 方法: GET
 90 |    * 返回: 合同詳細信息
 91 |    */
 92 |   .get(
 93 |     "/get-detail-info",
 94 |     async ({ query, auth, error }) => {
 95 |       if (!auth) {
 96 |         return error(401, "Unauthorized");
 97 |       }
 98 | 
 99 |       return await contractService.getContractDetailInfo(query.contractGuid);
100 |     },
101 |     {
102 |       query: t.Object({
103 |         contractGuid: t.String(),
104 |       }),
105 |     },
106 |   );
</content>
</file>
<environment_details>
# VSCode Visible Files
.github/prompts/elysia-routes-typescript.prompts.md

# VSCode Open Tabs
.github/prompts/elysia-routes-typescript.prompts.md

# Current Time
4/23/2025, 5:26:31 PM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
32,769 (16%)

# Current Cost
$0.28

# Current Mode
<slug>lang-gpt-prompts</slug>
<name>lang-gpt.prompts</name>
<model>anthropic/claude-3.7-sonnet</model>
</environment_details>

---

**Assistant:**

<thinking>
現在我已經看到了 `/home/bevis/repo/ecs-ten/ecs-ten-server/src/routes/contract-route.ts` 文件的內容。我需要分析這個文件是否符合我們在提示詞中定義的規則，並找出可能需要加入的內容。

讓我對照我們的規則來檢查：

1. **routes 層作為 API 入口點，處理請求路由和參數驗證**
   - 文件確實作為 API 入口點
   - 有處理請求上下文 (ctx) 相關邏輯
   - 有參數驗證 (使用 t.Object 等)
   - 有錯誤處理 (使用 error(401, "Unauthorized"))
   - 將業務邏輯委託給 services 層 (使用 contractService)

2. **routes 層按功能分組，每個分組使用單獨的文件**
   - 文件名為 contract-route.ts，符合功能分組

3. **路由文件規則**
   - 使用 prefix 設置路由前綴 (prefix: "/contract")
   - 每個路由使用所需的中間件 (.use(Middleware))
   - 每個路由添加詳細的文檔註釋 (包括路由描述、完整路徑、HTTP 方法和返回值說明)
   - 路由命名遵循 `/<action><Name>` 格式 (/create-contract, /get-basic-info, /get-detail-info)

不符合或不足的地方：

1. **錯誤處理方式不一致**：
   - 文件中使用 `error(401, "Unauthorized")` 而不是在我們提示詞中示例的 `set.status = 401; return "Unauthorized"`
   - 這不是問題，只是實現方式不同，但可能需要在提示詞中提及這兩種方式

2. **缺少 beforeHandle 使用**：
   - 文件中直接在路由處理函數中進行身份驗證，而不是使用 beforeHandle
   - 這也不是問題，只是實現方式不同，但可能需要在提示詞中提及這兩種方式

3. **缺少更複雜的參數驗證示例**：
   - 文件中有很複雜的參數驗證結構，特別是在 create-contract 路由中
   - 我們的提示詞中可以加入更複雜的參數驗證示例

4. **缺少錯誤處理的最佳實踐**：
   - 可以在提示詞中加入更多關於錯誤處理的最佳實踐

5. **缺少查詢參數處理的示例**：
   - 文件中使用了查詢參數 (query)，但我們的提示詞中沒有相關示例

基於以上分析，我將更新提示詞，加入這些不足的部分。
</thinking>

根據 `/home/bevis/repo/ecs-ten/ecs-ten-server/src/routes/contract-route.ts` 文件的內容，我發現以下幾點需要在提示詞中加入或調整：

<apply_diff>
<path>.github/prompts/elysia-routes-typescript.prompts.md</path>
<diff>
<<<<<<< SEARCH
:start_line:20
-------
2. Routes 層專業知識
   - 熟練實現 routes 層作為 API 入口點
   - 專注於處理請求上下文（ctx）
   - 負責參數驗證和錯誤處理
   - 不包含複雜業務邏輯
   - 熟練將業務邏輯委託給 services 層
=======
2. Routes 層專業知識
   - 熟練實現 routes 層作為 API 入口點
   - 專注於處理請求上下文（ctx）
   - 負責參數驗證和錯誤處理
   - 不包含複雜業務邏輯
   - 熟練將業務邏輯委託給 services 層
   - 精通複雜物件的參數驗證
   - 熟練處理查詢參數（query）和路徑參數（params）
>>>>>>> REPLACE

<<<<<<< SEARCH
:start_line:31
-------
   - 專注於處理請求上下文（ctx）相關邏輯
   - 負責參數驗證、錯誤處理和回應格式化
   - 不應包含複雜業務邏輯，應將其委託給 services 層
=======
   - 專注於處理請求上下文（ctx）相關邏輯
   - 負責參數驗證、錯誤處理和回應格式化
   - 不應包含複雜業務邏輯，應將其委託給 services 層
   - 錯誤處理可以使用 error 函數或 set.status 方法

2. 錯誤處理必須統一且一致
   
   - 可以使用 Elysia 的 error 函數：`error(401, "Unauthorized")`
   - 或使用 set.status 方法：`set.status = 401; return "Unauthorized"`
   - 在同一專案中應選擇其中一種方式並一致使用
>>>>>>> REPLACE

<<<<<<< SEARCH
:start_line:41
-------
5. 每個路由文件必須遵循以下規則：
   - 使用 prefix 設置路由前綴，對應功能分組名稱
   - 每個路由必須自己使用（use）所需的中間件
   - 每個路由必須添加詳細的文檔註釋，包括路由描述、完整路徑、HTTP 方法和返回值說明
   - 路由命名必須遵循 `/<action><Name>` 格式（如 /get-user）
=======
5. 每個路由文件必須遵循以下規則：
   - 使用 prefix 設置路由前綴，對應功能分組名稱
   - 每個路由必須自己使用（use）所需的中間件
   - 每個路由必須添加詳細的文檔註釋，包括路由描述、完整路徑、HTTP 方法和返回值說明
   - 路由命名必須遵循 `/<action><Name>` 格式（如 /get-user）
   - 參數驗證必須明確定義，包括必填和選填欄位

6. 身份驗證和授權檢查可以通過以下方式實現：
   
   - 使用 beforeHandle 鉤子函數進行預處理
   - 或直接在路由處理函數中進行檢查
   - 在同一專案中應選擇其中一種方式並一致使用
>>>>>>> REPLACE

<<<<<<< SEARCH
:start_line:149
-------
routes 層的詳細示例:

```typescript
// user.ts (routes)
// 標準 import 導入運行時需要的實例
import { Elysia, t } from "elysia";
import { Middleware } from "../middlewares";
import { userService } from "../services/user-service";
// 如果需要導入類型，應使用 import type
import type { UserProfileResponse } from "../types/user-types";

export const userRoutes = new Elysia({ prefix: "/user" })
  .use(Middleware) // 每個路由所需的中間件
  /**
   * 獲取當前用戶信息
   * 路由: /user/get-user
   * 方法: GET
   * 返回: 當前登錄用戶的詳細信息
   */
  .get(
    "/get-user",
    async ({ auth }) => {
      // 專注於處理 ctx 相關邏輯，如獲取 auth 信息
      return await userService.getUserProfile(auth.userId);
    },
    {
      // 參數驗證
      beforeHandle: ({ auth, set }) => {
        if (!auth?.userId) {
          set.status = 401;
          return "Unauthorized";
        }
      },
    }
  )
  /**
   * 更新用戶信息
   * 路由: /user/update-profile
   * 方法: PUT
   * 返回: 更新後的用戶信息
   */
  .put(
    "/update-profile",
    async ({ body, auth }) => {
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
      beforeHandle: ({ auth, set }) => {
        if (!auth?.userId) {
          set.status = 401;
          return "Unauthorized";
        }
      },
    }
  );
```
=======
routes 層的詳細示例:

```typescript
// user-route.ts
// 標準 import 導入運行時需要的實例
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
  /**
   * 獲取當前用戶信息
   * 路由: /user/get-user
   * 方法: GET
   * 返回: 當前登錄用戶的詳細信息
   */
  .get(
    "/get-user",
    async ({ auth, error }) => {
      // 方法一：直接在處理函數中進行身份驗證
      if (!auth) {
        return error(401, "Unauthorized");
      }
      
      // 專注於處理 ctx 相關邏輯，如獲取 auth 信息
      return await userService.getUserProfile(auth.userId);
    }
  )
  /**
   * 獲取用戶詳細資料
   * 路由: /user/get-detail
   * 方法: GET
   * 返回: 用戶詳細資料
   */
  .get(
    "/get-detail",
    async ({ query, auth, set }) => {
      // 方法二：使用 beforeHandle 進行身份驗證（在下方配置）
      // 處理查詢參數
      return await userService.getUserDetail(query.userId);
    },
    {
      // 查詢參數驗證
      query: t.Object({
        userId: t.String(),
      }),
      // 使用 beforeHandle 進行預處理
      beforeHandle: ({ auth, set }) => {
        if (!auth?.userId) {
          set.status = 401;
          return "Unauthorized";
        }
      },
    }
  )
  /**
   * 創建用戶
   * 路由: /user/create-user
   * 方法: POST
   * 返回: 創建的用戶信息
   */
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
        address: t.Optional(t.Object({
          street: t.String(),
          city: t.String(),
          zipCode: t.String(),
          country: t.Optional(t.String({ default: "Taiwan" })),
        })),
        preferences: t.Optional(t.Array(
          t.Object({
            key: t.String(),
            value: t.Union([t.String(), t.Number(), t.Boolean()]),
          })
        )),
      }),
    }
  )
  /**
   * 更新用戶信息
   * 路由: /user/update-profile
   * 方法: POST
   * 返回: 更新後的用戶信息
   */
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
```
>>>>>>> REPLACE
</diff>
</apply_diff>

<attempt_completion>
<result>
根據分析 `/home/bevis/repo/ecs-ten/ecs-ten-server/src/routes/contract-route.ts` 文件，我已經更新了 `.github/prompts/elysia-routes-typescript.prompts.md` 提示詞，加入了以下重要內容：

1. **擴展了 Routes 層專業知識**：
   - 增加了「精通複雜物件的參數驗證」
   - 增加了「熟練處理查詢參數（query）和路徑參數（params）」

2. **增加了錯誤處理的多種方式**：
   - 說明了可以使用 Elysia 的 error 函數：`error(401, "Unauthorized")`
   - 或使用 set.status 方法：`set.status = 401; return "Unauthorized"`
   - 強調在同一專案中應選擇其中一種方式並一致使用

3. **增加了身份驗證和授權檢查的多種實現方式**：
   - 使用 beforeHandle 鉤子函數進行預處理
   - 或直接在路由處理函數中進行檢查
   - 強調在同一專案中應選擇其中一種方式並一致使用

4. **完全更新了示例代碼**：
   - 增加了更多路由示例，包括處理查詢參數的示例
   - 展示了兩種不同的身份驗證方式
   - 增加了複雜物件的參數驗證示例，包括嵌套物件和陣列
   - 更新了文件命名和註釋風格，與實際項目保持一致

這些更新使提示詞更加全面，能夠更好地指導開發者實現符合實際項目需求的 Elysia 路由層。特別是關於 ctx 處理的部分，現在有了更詳細的示例和最佳實踐建議。
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
@@ -35,32 +35,29 @@
    - 不應包含複雜業務邏輯，應將其委託給 services 層
    - 錯誤處理可以使用 error 函數或 set.status 方法
 
 2. 錯誤處理必須統一且一致
-   
+
    - 可以使用 Elysia 的 error 函數：`error(401, "Unauthorized")`
-   - 或使用 set.status 方法：`set.status = 401; return "Unauthorized"`
-   - 在同一專案中應選擇其中一種方式並一致使用
 
-2. routes 層必須按功能分組，每個分組使用單獨的文件（如 `routes/<group>.ts`）
+3. routes 層必須按功能分組，每個分組使用單獨的文件（如 `routes/<group>.ts`）
 
-3. 必須在 `routes/index.ts` 中集中導入和導出所有路由
+4. 必須在 `routes/index.ts` 中集中導入和導出所有路由
 
-4. 在 `src/index.ts` 中必須導入整合後的路由並將其掛載到應用程序中
+5. 在 `src/index.ts` 中必須導入整合後的路由並將其掛載到應用程序中
 
-5. 每個路由文件必須遵循以下規則：
+6. 每個路由文件必須遵循以下規則：
+
    - 使用 prefix 設置路由前綴，對應功能分組名稱
    - 每個路由必須自己使用（use）所需的中間件
    - 每個路由必須添加詳細的文檔註釋，包括路由描述、完整路徑、HTTP 方法和返回值說明
    - 路由命名必須遵循 `/<action><Name>` 格式（如 /get-user）
    - 參數驗證必須明確定義，包括必填和選填欄位
 
-6. 身份驗證和授權檢查可以通過以下方式實現：
-   
-   - 使用 beforeHandle 鉤子函數進行預處理
-   - 或直接在路由處理函數中進行檢查
-   - 在同一專案中應選擇其中一種方式並一致使用
+7. 身份驗證和授權檢查可以通過以下方式實現：
 
+   - 直接在路由處理函數中進行檢查
+
 ## Workflow
 
 1. 首先，閱讀項目的 package.json 文件，了解使用的框架、依賴和腳本。
 2. 理解用戶的需求或問題，必要時提出澄清問題。
@@ -183,20 +180,17 @@
    * 路由: /user/get-user
    * 方法: GET
    * 返回: 當前登錄用戶的詳細信息
    */
-  .get(
-    "/get-user",
-    async ({ auth, error }) => {
-      // 方法一：直接在處理函數中進行身份驗證
-      if (!auth) {
-        return error(401, "Unauthorized");
-      }
-      
-      // 專注於處理 ctx 相關邏輯，如獲取 auth 信息
-      return await userService.getUserProfile(auth.userId);
+  .get("/get-user", async ({ auth, error }) => {
+    // 直接在處理函數中進行身份驗證
+    if (!auth) {
+      return error(401, "Unauthorized");
     }
-  )
+
+    // 專注於處理 ctx 相關邏輯，如獲取 auth 信息
+    return await userService.getUserProfile(auth.userId);
+  })
   /**
    * 獲取用戶詳細資料
    * 路由: /user/get-detail
    * 方法: GET
@@ -204,24 +198,21 @@
    */
   .get(
     "/get-detail",
     async ({ query, auth, set }) => {
-      // 方法二：使用 beforeHandle 進行身份驗證（在下方配置）
+      // 直接在處理函數中進行身份驗證
+      if (!auth) {
+        return error(401, "Unauthorized");
+      }
+
       // 處理查詢參數
       return await userService.getUserDetail(query.userId);
     },
     {
       // 查詢參數驗證
       query: t.Object({
         userId: t.String(),
       }),
-      // 使用 beforeHandle 進行預處理
-      beforeHandle: ({ auth, set }) => {
-        if (!auth?.userId) {
-          set.status = 401;
-          return "Unauthorized";
-        }
-      },
     }
   )
   /**
    * 創建用戶
@@ -234,9 +225,9 @@
     async ({ body, auth, error }) => {
       if (!auth) {
         return error(401, "Unauthorized");
       }
-      
+
       // 專注於處理 ctx 相關邏輯，將業務邏輯委託給 service
       return await userService.createUser(body);
     },
     {
@@ -248,20 +239,24 @@
           displayName: t.Optional(t.String()),
           age: t.Optional(t.Number()),
           active: t.Optional(t.Boolean({ default: true })),
         }),
-        address: t.Optional(t.Object({
-          street: t.String(),
-          city: t.String(),
-          zipCode: t.String(),
-          country: t.Optional(t.String({ default: "Taiwan" })),
-        })),
-        preferences: t.Optional(t.Array(
+        address: t.Optional(
           t.Object({
-            key: t.String(),
-            value: t.Union([t.String(), t.Number(), t.Boolean()]),
+            street: t.String(),
+            city: t.String(),
+            zipCode: t.String(),
+            country: t.Optional(t.String({ default: "Taiwan" })),
           })
-        )),
+        ),
+        preferences: t.Optional(
+          t.Array(
+            t.Object({
+              key: t.String(),
+              value: t.Union([t.String(), t.Number(), t.Boolean()]),
+            })
+          )
+        ),
       }),
     }
   )
   /**
@@ -275,9 +270,9 @@
     async ({ body, auth, error }) => {
       if (!auth) {
         return error(401, "Unauthorized");
       }
-      
+
       // 專注於處理 ctx 相關邏輯，將業務邏輯委託給 service
       return await userService.updateProfile(auth.userId, body);
     },
     {


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
4/23/2025, 5:29:13 PM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
38,753 (19%)

# Current Cost
$0.36

# Current Mode
<slug>lang-gpt-prompts</slug>
<name>lang-gpt.prompts</name>
<model>anthropic/claude-3.7-sonnet</model>
</environment_details>

---

**Assistant:**

<thinking>
我看到用戶已經接受了我的修改，並且做了一些額外的調整：

1. 移除了 BOM 字符（從 `﻿# Role` 改為 `# Role`）
2. 簡化了錯誤處理的選項，只保留了 `error(401, "Unauthorized")` 方式
3. 調整了規則的編號順序
4. 簡化了身份驗證的選項，只保留了直接在路由處理函數中進行檢查的方式
5. 改進了代碼示例的格式和結構，使其更加清晰
6. 在 get-detail 路由中添加了直接身份驗證的代碼
7. 調整了複雜物件參數驗證的格式，使其更加清晰

這些修改使得提示詞更加符合用戶實際項目中的實踐。現在我需要確認是否還有其他需要調整的地方。
</thinking>

我看到您已經接受了我的修改，並且做了一些很好的調整，使提示詞更加符合您實際項目中的實踐：

1. 簡化了錯誤處理，只保留 `error(401, "Unauthorized")` 方式，這與您的 contract-route.ts 文件中的做法一致
2. 調整了身份驗證方式，只保留直接在路由處理函數中進行檢查的方式
3. 改進了代碼示例的格式和結構，使其更加清晰易讀
4. 調整了複雜物件參數驗證的格式，使其更符合實際編碼風格

這些修改使得提示詞更加精確和實用。現在提示詞已經很好地反映了您在 contract-route.ts 中的實踐，包括：

- 路由前綴設置 (`prefix: "/contract"`)
- 中間件使用 (`.use(Middleware)`)
- 詳細的文檔註釋 (包括路由描述、路徑、HTTP 方法和返回值說明)
- 路由命名格式 (`/create-contract`, `/get-basic-info`, `/get-detail-info`)
- 直接在路由處理函數中進行身份驗證 (`if (!auth) { return error(401, "Unauthorized"); }`)
- 複雜物件的參數驗證 (使用嵌套的 t.Object 結構)
- 查詢參數處理 (使用 query 參數)

提示詞現在完全符合您的實際開發實踐，特別是關於 ctx 處理的部分。

<attempt_completion>
<result>
我已經根據 `/home/bevis/repo/ecs-ten/ecs-ten-server/src/routes/contract-route.ts` 文件分析並更新了 `.github/prompts/elysia-routes-typescript.prompts.md` 提示詞。

您的調整使提示詞更加符合實際項目中的實踐：

1. 簡化了錯誤處理，統一使用 `error(401, "Unauthorized")` 方式
2. 保留了直接在路由處理函數中進行身份驗證的方式，移除了 beforeHandle 方式
3. 改進了代碼示例的格式和結構，使其更加清晰易讀
4. 調整了複雜物件參數驗證的格式，使其更符合實際編碼風格

現在提示詞完全符合您在 contract-route.ts 中的實際開發實踐，包括：

- 路由前綴設置 (`prefix: "/contract"`)
- 中間件使用 (`.use(Middleware)`)
- 詳細的文檔註釋
- 標準的路由命名格式
- 直接在路由處理函數中進行身份驗證
- 複雜物件的參數驗證
- 查詢參數處理

這個更新後的提示詞將能夠更好地指導開發者按照您的標準實現 Elysia 路由層，特別是在處理請求上下文（ctx）方面。
</result>
</attempt_completion>

