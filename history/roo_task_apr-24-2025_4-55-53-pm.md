**User:**

<task>
使用 ecs swagger api 取得

POST
/ContractAccess/CreateContractAccess

建立 contract-access route
</task>
<environment_details>
# VSCode Visible Files


# VSCode Open Tabs


# Current Time
4/24/2025, 4:50:37 PM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
(Not available)

# Current Cost
$0.00

# Current Mode
<slug>elysia-routes-typescript-prompts</slug>
<name>elysia-routes-typescript.prompts</name>
<model>openai/gpt-4.1</model>


# Current Workspace Directory (/home/bevis/repo/ecs-ten/ecs-ten-server) Files
.env
.env.example
.windsurfrules
bun.lock
justfile
package-lock.json
package.json
README-task-master.md
README.md
swagger.json
taskmaster-plan.md
tsconfig.json
generated/
generated/prisma/
generated/prisma/client.d.ts
generated/prisma/client.js
generated/prisma/default.d.ts
generated/prisma/default.js
generated/prisma/edge.d.ts
generated/prisma/edge.js
generated/prisma/index-browser.js
generated/prisma/index.d.ts
generated/prisma/index.js
generated/prisma/libquery_engine-debian-openssl-3.0.x.so.node
generated/prisma/package.json
generated/prisma/schema.prisma
generated/prisma/wasm.d.ts
generated/prisma/wasm.js
generated/prisma/runtime/
generated/prisma/runtime/edge-esm.js
generated/prisma/runtime/edge.js
generated/prisma/runtime/index-browser.d.ts
generated/prisma/runtime/index-browser.js
generated/prisma/runtime/library.d.ts
generated/prisma/runtime/library.js
generated/prisma/runtime/react-native.js
generated/prisma/runtime/wasm.js
http/
http/contracts.http
keys/
keys/private/
keys/private/cluster.pkcs8.pem
keys/public/
keys/public/cluster.spki.pem
prisma/
prisma/schema.prisma
scripts/
scripts/example_prd.txt
scripts/prd.txt
src/
src/env-manager.ts
src/generate-jwt.ts
src/index.ts
src/prisma-client.ts
src/middleware/
src/middleware/auth.ts
src/middleware/error.ts
src/middleware/index.ts
src/middleware/jwt.ts
src/middleware/logger.ts
src/repositories/
src/repositories/contract-repository.ts
src/repositories/user-repository.ts
src/routes/
src/routes/auth-route.ts
src/routes/contract-route.ts
src/routes/contracts-route.ts
src/routes/index.ts
src/routes/user-route.ts
src/routes/users-route.ts
src/services/
src/services/auth-service.ts
src/services/contract-service-define.ts
src/services/contract-service.ts
src/services/user-service-define.ts
src/services/user-service.ts
src/types/
src/types/contract-types.ts
src/types/general-types.ts
src/types/user-types.ts
src/utils/
src/utils/file-utility.ts
src/utils/password-util.ts
tasks/
tasks/task_001.txt
tasks/task_002.txt
tasks/task_003.txt
tasks/task_004.txt
tasks/task_005.txt
tasks/task_006.txt
tasks/task_007.txt
tasks/task_008.txt
tasks/task_009.txt
tasks/task_010.txt
tasks/task_011.txt
tasks/task_012.txt
tasks/task_013.txt
tasks/task_014.txt
tasks/task_015.txt
tasks/task_016.txt
tasks/task_017.txt
tasks/task_018.txt
tasks/task_019.txt
tasks/task_020.txt
tasks/tasks.json
</environment_details>

---

**Assistant:**

<thinking>
1. 目標：根據 ECS Swagger API，為 POST /ContractAccess/CreateContractAccess 建立 contract-access 路由。
2. 步驟：
  - 取得 /ContractAccess/CreateContractAccess 的 swagger 定義，確認 request body 與 response schema。
  - 建立 src/routes/contract-access-route.ts，實作 /contract-access/create-contract-access 路由（POST）。
  - 路由需符合 Elysia Routes 標準：prefix、tags、summary、description、responses、參數驗證、回應格式。
  - 檢查 src/routes/index.ts 是否有整合新路由。
3. 目前專案尚未有 contract-access 相關 route，需新建檔案。
4. 需先取得 swagger 定義細節。
</thinking>

<use_mcp_tool>
<server_name>ecs-api-swagger</server_name>
<tool_name>getEndpointDetail</tool_name>
<arguments>
{
  "path": "/ContractAccess/CreateContractAccess",
  "method": "POST"
}
</arguments>
</use_mcp_tool>

---

**User:**

[use_mcp_tool for 'ecs-api-swagger'] Result:
{
  "path": "/ContractAccess/CreateContractAccess",
  "method": "POST",
  "description": "創建合約調閱申請 - 提交一個新的合約調閱權限申請",
  "parameters": [],
  "requestBody": {
    "description": "調閱申請的詳細資料，包含申請人、調閱時間段和調閱原因等",
    "content": {
      "application/json": {
        "schema": {
          "type": "object",
          "properties": {
            "applicantLoginId": {
              "type": "string",
              "description": "申請人登入ID",
              "nullable": true
            },
            "contractAccessType": {
              "enum": [
                "Online",
                "Paper",
                "Copy",
                "Other"
              ],
              "type": "string"
            },
            "startAccessDateUtc": {
              "type": "string",
              "description": "開始調閱日期（UTC格式）",
              "nullable": true
            },
            "endAccessDateUtc": {
              "type": "string",
              "description": "結束調閱日期（UTC格式）",
              "nullable": true
            },
            "accessRequestMemo": {
              "type": "string",
              "description": "被調閱的合約資訊",
              "nullable": true
            },
            "accessReason": {
              "type": "string",
              "description": "調閱原因",
              "nullable": true
            }
          },
          "additionalProperties": false,
          "description": "創建合約調閱申請請求模型 - 包含申請調閱合約的必要資訊"
        }
      },
      "text/json": {
        "schema": {
          "type": "object",
          "properties": {
            "applicantLoginId": {
              "type": "string",
              "description": "申請人登入ID",
              "nullable": true
            },
            "contractAccessType": {
              "enum": [
                "Online",
                "Paper",
                "Copy",
                "Other"
              ],
              "type": "string"
            },
            "startAccessDateUtc": {
              "type": "string",
              "description": "開始調閱日期（UTC格式）",
              "nullable": true
            },
            "endAccessDateUtc": {
              "type": "string",
              "description": "結束調閱日期（UTC格式）",
              "nullable": true
            },
            "accessRequestMemo": {
              "type": "string",
              "description": "被調閱的合約資訊",
              "nullable": true
            },
            "accessReason": {
              "type": "string",
              "description": "調閱原因",
              "nullable": true
            }
          },
          "additionalProperties": false,
          "description": "創建合約調閱申請請求模型 - 包含申請調閱合約的必要資訊"
        }
      },
      "application/*+json": {
        "schema": {
          "type": "object",
          "properties": {
            "applicantLoginId": {
              "type": "string",
              "description": "申請人登入ID",
              "nullable": true
            },
            "contractAccessType": {
              "enum": [
                "Online",
                "Paper",
                "Copy",
                "Other"
              ],
              "type": "string"
            },
            "startAccessDateUtc": {
              "type": "string",
              "description": "開始調閱日期（UTC格式）",
              "nullable": true
            },
            "endAccessDateUtc": {
              "type": "string",
              "description": "結束調閱日期（UTC格式）",
              "nullable": true
            },
            "accessRequestMemo": {
              "type": "string",
              "description": "被調閱的合約資訊",
              "nullable": true
            },
            "accessReason": {
              "type": "string",
              "description": "調閱原因",
              "nullable": true
            }
          },
          "additionalProperties": false,
          "description": "創建合約調閱申請請求模型 - 包含申請調閱合約的必要資訊"
        }
      }
    }
  },
  "responses": {
    "200": {
      "description": "OK",
      "content": {
        "application/json": {
          "schema": {
            "type": "object",
            "properties": {
              "success": {
                "type": "boolean"
              },
              "value": {
                "type": "object",
                "properties": {
                  "applyNo": {
                    "type": "string",
                    "description": "申請編號",
                    "nullable": true
                  },
                  "contractGuid": {
                    "type": "string",
                    "description": "合約GUID識別碼",
                    "nullable": true
                  }
                },
                "additionalProperties": false,
                "description": "創建合約調閱申請響應模型 - 包含新創建的申請結果"
              },
              "error": {
                "type": "object",
                "properties": {
                  "message": {
                    "type": "string",
                    "nullable": true
                  }
                },
                "additionalProperties": false
              }
            },
            "additionalProperties": false
          }
        }
      }
    }
  },
  "tags": [
    "ContractAccess"
  ]
}
<environment_details>
# VSCode Visible Files


# VSCode Open Tabs


# Current Time
4/24/2025, 4:50:46 PM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
21,758 (2%)

# Current Cost
$0.04

# Current Mode
<slug>elysia-routes-typescript-prompts</slug>
<name>elysia-routes-typescript.prompts</name>
<model>openai/gpt-4.1</model>
</environment_details>

---

**Assistant:**

<thinking>
1. 已取得 /ContractAccess/CreateContractAccess 的 swagger 定義，確認 request body 與 response schema。
2. 需建立 src/routes/contract-access-route.ts，實作 POST /contract-access/create-contract-access。
3. 需設計 body schema，contractAccessType 需用 const 物件代替 enum。
4. 回應格式需符合 { success, value, error } 標準。
5. 需於 src/routes/index.ts 匯入並掛載新路由。
6. 需於 services 層建立 stub function（如 contractAccessService.createContractAccess），但本次僅專注於 routes 層，service 可先假設已存在。
</thinking>

以下為 contract-access-route.ts 的內容設計：

```typescript
import { Elysia, t } from "elysia";
import { authMiddleware } from "../middleware";
import { contractAccessService } from "../services/contract-service"; // 假設 service 已有對應 function

// 以 const 物件代替 enum
export const CONTRACT_ACCESS_TYPE = {
  Online: "Online",
  Paper: "Paper",
  Copy: "Copy",
  Other: "Other",
} as const;

/**
 * 合約調閱申請路由
 */
export const contractAccessRoutes = new Elysia({
  prefix: "/contract-access",
  detail: {
    tags: ["ContractAccess"],
  },
})
  .use(authMiddleware)
  /**
   * 創建合約調閱申請
   * 路由: /contract-access/create-contract-access
   * 方法: POST
   * 返回: 新創建的合約調閱申請結果
   */
  .post(
    "/create-contract-access",
    async ({ body, auth, error }) => {
      if (!auth) {
        return {
          success: false,
          error: { message: "Unauthorized" },
        };
      }
      try {
        // 將業務邏輯委託給 service
        const result = await contractAccessService.createContractAccess({
          ...body,
          applicantLoginId: body.applicantLoginId ?? auth.loginId,
        });
        return {
          success: true,
          value: result,
        };
      } catch (err) {
        return {
          success: false,
          error: { message: err.message || "Failed to create contract access" },
        };
      }
    },
    {
      body: t.Object({
        applicantLoginId: t.Optional(t.String()),
        contractAccessType: t.Union([
          t.Literal(CONTRACT_ACCESS_TYPE.Online),
          t.Literal(CONTRACT_ACCESS_TYPE.Paper),
          t.Literal(CONTRACT_ACCESS_TYPE.Copy),
          t.Literal(CONTRACT_ACCESS_TYPE.Other),
        ]),
        startAccessDateUtc: t.Optional(t.String()),
        endAccessDateUtc: t.Optional(t.String()),
        accessRequestMemo: t.Optional(t.String()),
        accessReason: t.Optional(t.String()),
      }),
      detail: {
        summary: "創建合約調閱申請",
        description: "提交一個新的合約調閱權限申請，需登入授權。",
        tags: ["ContractAccess"],
        responses: {
          200: {
            description: "成功創建合約調閱申請",
            content: {
              "application/json": {
                schema: t.Object({
                  success: t.Boolean(),
                  value: t.Object({
                    applyNo: t.Optional(t.String()),
                    contractGuid: t.Optional(t.String()),
                  }),
                }),
              },
            },
          },
          400: {
            description: "請求錯誤",
            content: {
              "application/json": {
                schema: t.Object({
                  success: t.Boolean(),
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
    }
  );
```

接下來將此內容寫入 src/routes/contract-access-route.ts。

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


# VSCode Open Tabs


# Current Time
4/24/2025, 4:50:58 PM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
23,936 (2%)

# Current Cost
$0.07

# Current Mode
<slug>elysia-routes-typescript-prompts</slug>
<name>elysia-routes-typescript.prompts</name>
<model>openai/gpt-4.1</model>
</environment_details>

---

**Assistant:**

<write_to_file>
<path>src/routes/contract-access-route.ts</path>
<content>
import { Elysia, t } from "elysia";
import { authMiddleware } from "../middleware";
import { contractAccessService } from "../services/contract-service"; // 假設 service 已有對應 function

// 以 const 物件代替 enum
export const CONTRACT_ACCESS_TYPE = {
  Online: "Online",
  Paper: "Paper",
  Copy: "Copy",
  Other: "Other",
} as const;

/**
 * 合約調閱申請路由
 */
export const contractAccessRoutes = new Elysia({
  prefix: "/contract-access",
  detail: {
    tags: ["ContractAccess"],
  },
})
  .use(authMiddleware)
  /**
   * 創建合約調閱申請
   * 路由: /contract-access/create-contract-access
   * 方法: POST
   * 返回: 新創建的合約調閱申請結果
   */
  .post(
    "/create-contract-access",
    async ({ body, auth, error }) => {
      if (!auth) {
        return {
          success: false,
          error: { message: "Unauthorized" },
        };
      }
      try {
        // 將業務邏輯委託給 service
        const result = await contractAccessService.createContractAccess({
          ...body,
          applicantLoginId: body.applicantLoginId ?? auth.loginId,
        });
        return {
          success: true,
          value: result,
        };
      } catch (err: any) {
        return {
          success: false,
          error: { message: err.message || "Failed to create contract access" },
        };
      }
    },
    {
      body: t.Object({
        applicantLoginId: t.Optional(t.String()),
        contractAccessType: t.Union([
          t.Literal(CONTRACT_ACCESS_TYPE.Online),
          t.Literal(CONTRACT_ACCESS_TYPE.Paper),
          t.Literal(CONTRACT_ACCESS_TYPE.Copy),
          t.Literal(CONTRACT_ACCESS_TYPE.Other),
        ]),
        startAccessDateUtc: t.Optional(t.String()),
        endAccessDateUtc: t.Optional(t.String()),
        accessRequestMemo: t.Optional(t.String()),
        accessReason: t.Optional(t.String()),
      }),
      detail: {
        summary: "創建合約調閱申請",
        description: "提交一個新的合約調閱權限申請，需登入授權。",
        tags: ["ContractAccess"],
        responses: {
          200: {
            description: "成功創建合約調閱申請",
            content: {
              "application/json": {
                schema: t.Object({
                  success: t.Boolean(),
                  value: t.Object({
                    applyNo: t.Optional(t.String()),
                    contractGuid: t.Optional(t.String()),
                  }),
                }),
              },
            },
          },
          400: {
            description: "請求錯誤",
            content: {
              "application/json": {
                schema: t.Object({
                  success: t.Boolean(),
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
    }
  );
</content>
<line_count>70</line_count>
</write_to_file>

---

**User:**

[write_to_file for 'src/routes/contract-access-route.ts'] Result:
The user made the following updates to your content:

@@ -1,7 +1,7 @@
 import { Elysia, t } from "elysia";
-import { authMiddleware } from "../middleware";
-import { contractAccessService } from "../services/contract-service"; // 假設 service 已有對應 function
+import { Middleware } from "../middleware";
+import { contractAccessService } from "../services/contract-access-service"; // 假設 service 已有對應 function
 
 // 以 const 物件代替 enum
 export const CONTRACT_ACCESS_TYPE = {
   Online: "Online",
@@ -18,9 +18,9 @@
   detail: {
     tags: ["ContractAccess"],
   },
 })
-  .use(authMiddleware)
+  .use(Middleware)
   /**
    * 創建合約調閱申請
    * 路由: /contract-access/create-contract-access
    * 方法: POST


The updated content, which includes both your original modifications and the user's edits, has been successfully saved to src/routes/contract-access-route.ts. Here is the full, updated content of the file, including line numbers:

<final_file_content path="src/routes/contract-access-route.ts">
  1 | import { Elysia, t } from "elysia";
  2 | import { Middleware } from "../middleware";
  3 | import { contractAccessService } from "../services/contract-access-service"; // 假設 service 已有對應 function
  4 | 
  5 | // 以 const 物件代替 enum
  6 | export const CONTRACT_ACCESS_TYPE = {
  7 |   Online: "Online",
  8 |   Paper: "Paper",
  9 |   Copy: "Copy",
 10 |   Other: "Other",
 11 | } as const;
 12 | 
 13 | /**
 14 |  * 合約調閱申請路由
 15 |  */
 16 | export const contractAccessRoutes = new Elysia({
 17 |   prefix: "/contract-access",
 18 |   detail: {
 19 |     tags: ["ContractAccess"],
 20 |   },
 21 | })
 22 |   .use(Middleware)
 23 |   /**
 24 |    * 創建合約調閱申請
 25 |    * 路由: /contract-access/create-contract-access
 26 |    * 方法: POST
 27 |    * 返回: 新創建的合約調閱申請結果
 28 |    */
 29 |   .post(
 30 |     "/create-contract-access",
 31 |     async ({ body, auth, error }) => {
 32 |       if (!auth) {
 33 |         return {
 34 |           success: false,
 35 |           error: { message: "Unauthorized" },
 36 |         };
 37 |       }
 38 |       try {
 39 |         // 將業務邏輯委託給 service
 40 |         const result = await contractAccessService.createContractAccess({
 41 |           ...body,
 42 |           applicantLoginId: body.applicantLoginId ?? auth.loginId,
 43 |         });
 44 |         return {
 45 |           success: true,
 46 |           value: result,
 47 |         };
 48 |       } catch (err: any) {
 49 |         return {
 50 |           success: false,
 51 |           error: { message: err.message || "Failed to create contract access" },
 52 |         };
 53 |       }
 54 |     },
 55 |     {
 56 |       body: t.Object({
 57 |         applicantLoginId: t.Optional(t.String()),
 58 |         contractAccessType: t.Union([
 59 |           t.Literal(CONTRACT_ACCESS_TYPE.Online),
 60 |           t.Literal(CONTRACT_ACCESS_TYPE.Paper),
 61 |           t.Literal(CONTRACT_ACCESS_TYPE.Copy),
 62 |           t.Literal(CONTRACT_ACCESS_TYPE.Other),
 63 |         ]),
 64 |         startAccessDateUtc: t.Optional(t.String()),
 65 |         endAccessDateUtc: t.Optional(t.String()),
 66 |         accessRequestMemo: t.Optional(t.String()),
 67 |         accessReason: t.Optional(t.String()),
 68 |       }),
 69 |       detail: {
 70 |         summary: "創建合約調閱申請",
 71 |         description: "提交一個新的合約調閱權限申請，需登入授權。",
 72 |         tags: ["ContractAccess"],
 73 |         responses: {
 74 |           200: {
 75 |             description: "成功創建合約調閱申請",
 76 |             content: {
 77 |               "application/json": {
 78 |                 schema: t.Object({
 79 |                   success: t.Boolean(),
 80 |                   value: t.Object({
 81 |                     applyNo: t.Optional(t.String()),
 82 |                     contractGuid: t.Optional(t.String()),
 83 |                   }),
 84 |                 }),
 85 |               },
 86 |             },
 87 |           },
 88 |           400: {
 89 |             description: "請求錯誤",
 90 |             content: {
 91 |               "application/json": {
 92 |                 schema: t.Object({
 93 |                   success: t.Boolean(),
 94 |                   error: t.Object({
 95 |                     message: t.String(),
 96 |                   }),
 97 |                 }),
 98 |               },
 99 |             },
100 |           },
101 |           401: {
102 |             description: "未授權",
103 |           },
104 |         },
105 |       },
106 |     }
107 |   );

</final_file_content>

Please note:
1. You do not need to re-write the file with these changes, as they have already been applied.
2. Proceed with the task using cline updated file content as the new baseline.
3. If the user's edits have addressed part of the task or changed the requirements, adjust your approach accordingly.

New problems detected after saving the file:
src/routes/contract-access-route.ts
- [biome Error] 48 |       } catch (err: any) { : Unexpected any. Specify a different type.
- [ts Error] 3 | import { contractAccessService } from "../services/contract-access-service"; // 假設 service 已有對應 function : Cannot find module '../services/contract-access-service' or its corresponding type declarations.
- [ts Error] 42 |           applicantLoginId: body.applicantLoginId ?? auth.loginId, : Property 'loginId' does not exist on type '{ readonly userId: number; readonly user: string; }'.
<environment_details>
# VSCode Visible Files
src/routes/contract-access-route.ts

# VSCode Open Tabs
src/routes/contract-access-route.ts

# Current Time
4/24/2025, 4:51:42 PM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
24,986 (2%)

# Current Cost
$0.08

# Current Mode
<slug>elysia-routes-typescript-prompts</slug>
<name>elysia-routes-typescript.prompts</name>
<model>openai/gpt-4.1</model>
</environment_details>
[TASK RESUMPTION] This task was interrupted just now. It may or may not be complete, so please reassess the task context. Be aware that the project state may have changed since then. If the task has not been completed, retry the last step before interruption and proceed with completing the task.

Note: If you previously attempted a tool use that the user did not provide a result for, you should assume the tool use was not successful and assess whether you should retry. If the last tool was a browser_action, the browser has been closed and you must launch a new browser if needed.

IMPORTANT: If the last tool use was a write_to_file that was interrupted, the file was reverted back to its original state before the interrupted edit, and you do NOT need to re-read the file as you already have its up-to-date contents.

New instructions for task continuation:
<user_message>
繼續建立 contract access service
</user_message>
<environment_details>
# VSCode Visible Files
src/routes/contract-access-route.ts

# VSCode Open Tabs
src/routes/contract-access-route.ts

# Current Time
4/24/2025, 4:51:59 PM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
24,986 (2%)

# Current Cost
$0.08

# Current Mode
<slug>services-typescript-prompts</slug>
<name>services-typescript.prompts</name>
<model>openai/gpt-4.1</model>


# Current Workspace Directory (/home/bevis/repo/ecs-ten/ecs-ten-server) Files
.env
.env.example
.windsurfrules
bun.lock
justfile
package-lock.json
package.json
README-task-master.md
README.md
swagger.json
taskmaster-plan.md
tsconfig.json
generated/
generated/prisma/
generated/prisma/client.d.ts
generated/prisma/client.js
generated/prisma/default.d.ts
generated/prisma/default.js
generated/prisma/edge.d.ts
generated/prisma/edge.js
generated/prisma/index-browser.js
generated/prisma/index.d.ts
generated/prisma/index.js
generated/prisma/libquery_engine-debian-openssl-3.0.x.so.node
generated/prisma/package.json
generated/prisma/schema.prisma
generated/prisma/wasm.d.ts
generated/prisma/wasm.js
generated/prisma/runtime/
generated/prisma/runtime/edge-esm.js
generated/prisma/runtime/edge.js
generated/prisma/runtime/index-browser.d.ts
generated/prisma/runtime/index-browser.js
generated/prisma/runtime/library.d.ts
generated/prisma/runtime/library.js
generated/prisma/runtime/react-native.js
generated/prisma/runtime/wasm.js
http/
http/contracts.http
keys/
keys/private/
keys/private/cluster.pkcs8.pem
keys/public/
keys/public/cluster.spki.pem
prisma/
prisma/schema.prisma
scripts/
scripts/example_prd.txt
scripts/prd.txt
src/
src/env-manager.ts
src/generate-jwt.ts
src/index.ts
src/prisma-client.ts
src/middleware/
src/middleware/auth.ts
src/middleware/error.ts
src/middleware/index.ts
src/middleware/jwt.ts
src/middleware/logger.ts
src/repositories/
src/repositories/contract-repository.ts
src/repositories/user-repository.ts
src/routes/
src/routes/auth-route.ts
src/routes/contract-access-route.ts
src/routes/contract-route.ts
src/routes/contracts-route.ts
src/routes/index.ts
src/routes/user-route.ts
src/routes/users-route.ts
src/services/
src/services/auth-service.ts
src/services/contract-service-define.ts
src/services/contract-service.ts
src/services/user-service-define.ts
src/services/user-service.ts
src/types/
src/types/contract-types.ts
src/types/general-types.ts
src/types/user-types.ts
src/utils/
src/utils/file-utility.ts
src/utils/password-util.ts
tasks/
tasks/task_001.txt
tasks/task_002.txt
tasks/task_003.txt
tasks/task_004.txt
tasks/task_005.txt
tasks/task_006.txt
tasks/task_007.txt
tasks/task_008.txt
tasks/task_009.txt
tasks/task_010.txt
tasks/task_011.txt
tasks/task_012.txt
tasks/task_013.txt
tasks/task_014.txt
tasks/task_015.txt
tasks/task_016.txt
tasks/task_017.txt
tasks/task_018.txt
tasks/task_019.txt
tasks/task_020.txt
tasks/tasks.json
</environment_details>

---

**Assistant:**

<thinking>
1. 需建立 src/services/contract-access-service.ts，實作 createContractAccess 方法，並導出單例。
2. 需依據 swagger 定義設計 input/output 型別，並依規則放於 src/types/contract-types.ts。
3. 需依賴 contract-repository，進行資料儲存（可 stub）。
4. 需符合服務層最佳實踐：純函數、依賴注入、錯誤處理、JSDoc。
5. contractAccessType 需用 const 物件代替 enum。
6. 回傳格式需為 { applyNo, contractGuid }。
7. 需先檢查 src/types/contract-types.ts 是否已有型別定義，若無則補上。
</thinking>

<read_file>
<path>src/types/contract-types.ts</path>
</read_file>

---

**User:**

[read_file for 'src/types/contract-types.ts'] Result:
The user denied this operation and provided the following feedback:
<feedback>
你應該根據 contract access route 的使用 直接建立即可
</feedback>
<environment_details>
# VSCode Visible Files
src/routes/contract-access-route.ts

# VSCode Open Tabs
src/routes/contract-access-route.ts

# Current Time
4/24/2025, 4:52:46 PM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
26,073 (2%)

# Current Cost
$0.14

# Current Mode
<slug>services-typescript-prompts</slug>
<name>services-typescript.prompts</name>
<model>openai/gpt-4.1</model>
</environment_details>

---

**Assistant:**

<thinking>
1. 依據 contract-access-route 的需求，直接在 service 檔案中定義 input/output 型別。
2. contractAccessService 需實作 createContractAccess，並導出單例。
3. 需 stub contractRepository，並以依賴注入方式設計，方便未來擴充。
4. 嚴格型別、JSDoc、錯誤處理、純函數設計。
5. contractAccessType 用 const 物件。
6. 回傳 { applyNo, contractGuid }。
</thinking>

<write_to_file>
<path>src/services/contract-access-service.ts</path>
<content>
import type { ContractRepository } from "../repositories/contract-repository";

/**
 * 合約調閱申請類型常數
 */
export const CONTRACT_ACCESS_TYPE = {
  Online: "Online",
  Paper: "Paper",
  Copy: "Copy",
  Other: "Other",
} as const;

/**
 * 創建合約調閱申請的輸入型別
 */
export interface CreateContractAccessInput {
  applicantLoginId?: string;
  contractAccessType: typeof CONTRACT_ACCESS_TYPE[keyof typeof CONTRACT_ACCESS_TYPE];
  startAccessDateUtc?: string;
  endAccessDateUtc?: string;
  accessRequestMemo?: string;
  accessReason?: string;
}

/**
 * 創建合約調閱申請的回應型別
 */
export interface CreateContractAccessResult {
  applyNo?: string;
  contractGuid?: string;
}

/**
 * 合約調閱申請服務
 */
export class ContractAccessService {
  private contractRepository: ContractRepository;

  constructor(deps: { contractRepository: ContractRepository }) {
    this.contractRepository = deps.contractRepository;
  }

  /**
   * 創建合約調閱申請
   * @param input 創建申請的資料
   * @returns 申請結果
   * @throws Error 當儲存失敗時
   */
  async createContractAccess(
    input: CreateContractAccessInput
  ): Promise<CreateContractAccessResult> {
    try {
      // 實際應用應調用 repository 儲存資料
      // 這裡僅 stub 回傳假資料
      // const saved = await this.contractRepository.createContractAccess(input);
      // return { applyNo: saved.applyNo, contractGuid: saved.contractGuid };

      // stub 假資料
      return {
        applyNo: "CA20250424001",
        contractGuid: "dummy-guid-123456",
      };
    } catch (error) {
      // 可擴充 log
      throw new Error("Failed to create contract access");
    }
  }
}

// 假設已實作 contractRepository
import { contractRepository } from "../repositories/contract-repository";
export const contractAccessService = new ContractAccessService({ contractRepository });
</content>
<line_count>56</line_count>
</write_to_file>

---

**User:**

[write_to_file for 'src/services/contract-access-service.ts'] Result:
The content was successfully saved to src/services/contract-access-service.ts.
<environment_details>
# VSCode Visible Files
src/services/contract-access-service.ts

# VSCode Open Tabs
src/routes/contract-access-route.ts,src/services/contract-access-service.ts

# Current Time
4/24/2025, 4:53:33 PM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
26,887 (3%)

# Current Cost
$0.16

# Current Mode
<slug>services-typescript-prompts</slug>
<name>services-typescript.prompts</name>
<model>openai/gpt-4.1</model>
</environment_details>
[TASK RESUMPTION] This task was interrupted 1 minute ago. It may or may not be complete, so please reassess the task context. Be aware that the project state may have changed since then. If the task has not been completed, retry the last step before interruption and proceed with completing the task.

Note: If you previously attempted a tool use that the user did not provide a result for, you should assume the tool use was not successful and assess whether you should retry. If the last tool was a browser_action, the browser has been closed and you must launch a new browser if needed.

New instructions for task continuation:
<user_message>
讀取 service 我已修改過
並且以此建立 contractAccessRepository
</user_message>
<environment_details>
# VSCode Visible Files
src/services/contract-access-service.ts

# VSCode Open Tabs
src/routes/contract-access-route.ts,src/services/contract-access-service.ts

# Current Time
4/24/2025, 4:55:16 PM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
26,887 (3%)

# Current Cost
$0.16

# Current Mode
<slug>prisma-repositories-typescript-prompts</slug>
<name>prisma-repositories-typescript.prompts</name>
<model>openai/gpt-4.1</model>


# Current Workspace Directory (/home/bevis/repo/ecs-ten/ecs-ten-server) Files
.env
.env.example
.windsurfrules
bun.lock
justfile
package-lock.json
package.json
README-task-master.md
README.md
swagger.json
taskmaster-plan.md
tsconfig.json
generated/
generated/prisma/
generated/prisma/client.d.ts
generated/prisma/client.js
generated/prisma/default.d.ts
generated/prisma/default.js
generated/prisma/edge.d.ts
generated/prisma/edge.js
generated/prisma/index-browser.js
generated/prisma/index.d.ts
generated/prisma/index.js
generated/prisma/libquery_engine-debian-openssl-3.0.x.so.node
generated/prisma/package.json
generated/prisma/schema.prisma
generated/prisma/wasm.d.ts
generated/prisma/wasm.js
generated/prisma/runtime/
generated/prisma/runtime/edge-esm.js
generated/prisma/runtime/edge.js
generated/prisma/runtime/index-browser.d.ts
generated/prisma/runtime/index-browser.js
generated/prisma/runtime/library.d.ts
generated/prisma/runtime/library.js
generated/prisma/runtime/react-native.js
generated/prisma/runtime/wasm.js
http/
http/contracts.http
keys/
keys/private/
keys/private/cluster.pkcs8.pem
keys/public/
keys/public/cluster.spki.pem
prisma/
prisma/schema.prisma
scripts/
scripts/example_prd.txt
scripts/prd.txt
src/
src/env-manager.ts
src/generate-jwt.ts
src/index.ts
src/prisma-client.ts
src/middleware/
src/middleware/auth.ts
src/middleware/error.ts
src/middleware/index.ts
src/middleware/jwt.ts
src/middleware/logger.ts
src/repositories/
src/repositories/contract-repository.ts
src/repositories/user-repository.ts
src/routes/
src/routes/auth-route.ts
src/routes/contract-access-route.ts
src/routes/contract-route.ts
src/routes/contracts-route.ts
src/routes/index.ts
src/routes/user-route.ts
src/routes/users-route.ts
src/services/
src/services/auth-service.ts
src/services/contract-access-service.ts
src/services/contract-service-define.ts
src/services/contract-service.ts
src/services/user-service-define.ts
src/services/user-service.ts
src/types/
src/types/contract-types.ts
src/types/general-types.ts
src/types/user-types.ts
src/utils/
src/utils/file-utility.ts
src/utils/password-util.ts
tasks/
tasks/task_001.txt
tasks/task_002.txt
tasks/task_003.txt
tasks/task_004.txt
tasks/task_005.txt
tasks/task_006.txt
tasks/task_007.txt
tasks/task_008.txt
tasks/task_009.txt
tasks/task_010.txt
tasks/task_011.txt
tasks/task_012.txt
tasks/task_013.txt
tasks/task_014.txt
tasks/task_015.txt
tasks/task_016.txt
tasks/task_017.txt
tasks/task_018.txt
tasks/task_019.txt
tasks/task_020.txt
tasks/tasks.json
</environment_details>

---

**Assistant:**

<thinking>
1. 需建立 src/repositories/contract-access-repository.ts，實作 contractAccessRepository，封裝所有合約調閱申請的資料存取。
2. 需依據 service 的 createContractAccess input/output 設計 repository 方法 createContractAccess。
3. 需依賴 prisma client，並以依賴注入方式設計，便於測試與擴充。
4. 需檢查 prisma/schema.prisma 是否已有 contract access 相關 model，若無則需提醒補上。
5. 嚴格型別、JSDoc、錯誤處理、單例導出。
</thinking>

<read_file>
<path>prisma/schema.prisma</path>
</read_file>

---

**User:**

[read_file for 'prisma/schema.prisma'] Result:
<file><path>prisma/schema.prisma</path>
<content lines="1-4002">
   1 | generator client {
   2 |   provider        = "prisma-client-js"
   3 |   output          = "../generated/prisma"
   4 |   previewFeatures = ["multiSchema"]
   5 | }
   6 | 
   7 | datasource db {
   8 |   provider = "sqlserver"
   9 |   url      = env("DATABASE_URL")
  10 |   schemas  = ["code", "data", "dbo", "join"]
  11 | }
  12 | 
  13 | /// The underlying table does not contain a valid unique identifier and can therefore currently not be handled by Prisma Client.
  14 | model TempContractCustomizedField {
  15 |   applyNo    String?   @map("ApplyNo") @db.NVarChar(450)
  16 |   contractId Int?      @map("ContractId")
  17 |   txt01      String?   @map("Txt01") @db.NVarChar(450)
  18 |   txt02      String?   @map("Txt02") @db.NVarChar(450)
  19 |   txt03      String?   @map("Txt03") @db.NVarChar(450)
  20 |   txt04      String?   @map("Txt04") @db.NVarChar(450)
  21 |   txt05      String?   @map("Txt05") @db.NVarChar(450)
  22 |   txt06      String?   @map("Txt06") @db.NVarChar(450)
  23 |   txt07      String?   @map("Txt07") @db.NVarChar(450)
  24 |   txt08      String?   @map("Txt08") @db.NVarChar(450)
  25 |   txt09      String?   @map("Txt09") @db.NVarChar(450)
  26 |   txt10      String?   @map("Txt10") @db.NVarChar(450)
  27 |   txt11      String?   @map("Txt11") @db.NVarChar(450)
  28 |   txt12      String?   @map("Txt12") @db.NVarChar(450)
  29 |   txt13      String?   @map("Txt13") @db.NVarChar(450)
  30 |   txt14      String?   @map("Txt14") @db.NVarChar(450)
  31 |   txt15      String?   @map("Txt15") @db.NVarChar(450)
  32 |   txt16      String?   @map("Txt16") @db.NVarChar(450)
  33 |   txt17      String?   @map("Txt17") @db.NVarChar(450)
  34 |   txt18      String?   @map("Txt18") @db.NVarChar(450)
  35 |   txt19      String?   @map("Txt19") @db.NVarChar(450)
  36 |   txt20      String?   @map("Txt20") @db.NVarChar(450)
  37 |   memo01     String?   @map("Memo01") @db.NVarChar(Max)
  38 |   memo02     String?   @map("Memo02") @db.NVarChar(Max)
  39 |   memo03     String?   @map("Memo03") @db.NVarChar(Max)
  40 |   memo04     String?   @map("Memo04") @db.NVarChar(Max)
  41 |   memo05     String?   @map("Memo05") @db.NVarChar(Max)
  42 |   memo06     String?   @map("Memo06") @db.NVarChar(Max)
  43 |   memo07     String?   @map("Memo07") @db.NVarChar(Max)
  44 |   memo08     String?   @map("Memo08") @db.NVarChar(Max)
  45 |   memo09     String?   @map("Memo09") @db.NVarChar(Max)
  46 |   memo10     String?   @map("Memo10") @db.NVarChar(Max)
  47 |   memo11     String?   @map("Memo11") @db.NVarChar(Max)
  48 |   memo12     String?   @map("Memo12") @db.NVarChar(Max)
  49 |   memo13     String?   @map("Memo13") @db.NVarChar(Max)
  50 |   memo14     String?   @map("Memo14") @db.NVarChar(Max)
  51 |   memo15     String?   @map("Memo15") @db.NVarChar(Max)
  52 |   memo16     String?   @map("Memo16") @db.NVarChar(Max)
  53 |   memo17     String?   @map("Memo17") @db.NVarChar(Max)
  54 |   memo18     String?   @map("Memo18") @db.NVarChar(Max)
  55 |   memo19     String?   @map("Memo19") @db.NVarChar(Max)
  56 |   memo20     String?   @map("Memo20") @db.NVarChar(Max)
  57 |   checkBox01 String?   @map("CheckBox01") @db.NVarChar(Max)
  58 |   checkBox02 String?   @map("CheckBox02") @db.NVarChar(Max)
  59 |   checkBox03 String?   @map("CheckBox03") @db.NVarChar(Max)
  60 |   checkBox04 String?   @map("CheckBox04") @db.NVarChar(Max)
  61 |   checkBox05 String?   @map("CheckBox05") @db.NVarChar(Max)
  62 |   checkBox06 String?   @map("CheckBox06") @db.NVarChar(Max)
  63 |   checkBox07 String?   @map("CheckBox07") @db.NVarChar(Max)
  64 |   checkBox08 String?   @map("CheckBox08") @db.NVarChar(Max)
  65 |   checkBox09 String?   @map("CheckBox09") @db.NVarChar(Max)
  66 |   checkBox10 String?   @map("CheckBox10") @db.NVarChar(Max)
  67 |   checkBox11 String?   @map("CheckBox11") @db.NVarChar(Max)
  68 |   checkBox12 String?   @map("CheckBox12") @db.NVarChar(Max)
  69 |   checkBox13 String?   @map("CheckBox13") @db.NVarChar(Max)
  70 |   checkBox14 String?   @map("CheckBox14") @db.NVarChar(Max)
  71 |   checkBox15 String?   @map("CheckBox15") @db.NVarChar(Max)
  72 |   checkBox16 String?   @map("CheckBox16") @db.NVarChar(Max)
  73 |   checkBox17 String?   @map("CheckBox17") @db.NVarChar(Max)
  74 |   checkBox18 String?   @map("CheckBox18") @db.NVarChar(Max)
  75 |   checkBox19 String?   @map("CheckBox19") @db.NVarChar(Max)
  76 |   checkBox20 String?   @map("CheckBox20") @db.NVarChar(Max)
  77 |   select01   String?   @map("Select01") @db.NVarChar(Max)
  78 |   select02   String?   @map("Select02") @db.NVarChar(Max)
  79 |   select03   String?   @map("Select03") @db.NVarChar(Max)
  80 |   select04   String?   @map("Select04") @db.NVarChar(Max)
  81 |   select05   String?   @map("Select05") @db.NVarChar(Max)
  82 |   select06   String?   @map("Select06") @db.NVarChar(Max)
  83 |   select07   String?   @map("Select07") @db.NVarChar(Max)
  84 |   select08   String?   @map("Select08") @db.NVarChar(Max)
  85 |   select09   String?   @map("Select09") @db.NVarChar(Max)
  86 |   select10   String?   @map("Select10") @db.NVarChar(Max)
  87 |   select11   String?   @map("Select11") @db.NVarChar(Max)
  88 |   select12   String?   @map("Select12") @db.NVarChar(Max)
  89 |   select13   String?   @map("Select13") @db.NVarChar(Max)
  90 |   select14   String?   @map("Select14") @db.NVarChar(Max)
  91 |   select15   String?   @map("Select15") @db.NVarChar(Max)
  92 |   select16   String?   @map("Select16") @db.NVarChar(Max)
  93 |   select17   String?   @map("Select17") @db.NVarChar(Max)
  94 |   select18   String?   @map("Select18") @db.NVarChar(Max)
  95 |   select19   String?   @map("Select19") @db.NVarChar(Max)
  96 |   select20   String?   @map("Select20") @db.NVarChar(Max)
  97 |   int01      Int?      @map("Int01")
  98 |   int02      Int?      @map("Int02")
  99 |   int03      Int?      @map("Int03")
 100 |   int04      Int?      @map("Int04")
 101 |   int05      Int?      @map("Int05")
 102 |   int06      Int?      @map("Int06")
 103 |   int07      Int?      @map("Int07")
 104 |   int08      Int?      @map("Int08")
 105 |   int09      Int?      @map("Int09")
 106 |   int10      Int?      @map("Int10")
 107 |   int11      Int?      @map("Int11")
 108 |   int12      Int?      @map("Int12")
 109 |   int13      Int?      @map("Int13")
 110 |   int14      Int?      @map("Int14")
 111 |   int15      Int?      @map("Int15")
 112 |   int16      Int?      @map("Int16")
 113 |   int17      Int?      @map("Int17")
 114 |   int18      Int?      @map("Int18")
 115 |   int19      Int?      @map("Int19")
 116 |   int20      Int?      @map("Int20")
 117 |   double01   Decimal?  @map("Double01") @db.Decimal(18, 8)
 118 |   double02   Decimal?  @map("Double02") @db.Decimal(18, 8)
 119 |   double03   Decimal?  @map("Double03") @db.Decimal(18, 8)
 120 |   double04   Decimal?  @map("Double04") @db.Decimal(18, 8)
 121 |   double05   Decimal?  @map("Double05") @db.Decimal(18, 8)
 122 |   double06   Decimal?  @map("Double06") @db.Decimal(18, 8)
 123 |   double07   Decimal?  @map("Double07") @db.Decimal(18, 8)
 124 |   double08   Decimal?  @map("Double08") @db.Decimal(18, 8)
 125 |   double09   Decimal?  @map("Double09") @db.Decimal(18, 8)
 126 |   double10   Decimal?  @map("Double10") @db.Decimal(18, 8)
 127 |   double11   Decimal?  @map("Double11") @db.Decimal(18, 8)
 128 |   double12   Decimal?  @map("Double12") @db.Decimal(18, 8)
 129 |   double13   Decimal?  @map("Double13") @db.Decimal(18, 8)
 130 |   double14   Decimal?  @map("Double14") @db.Decimal(18, 8)
 131 |   double15   Decimal?  @map("Double15") @db.Decimal(18, 8)
 132 |   double16   Decimal?  @map("Double16") @db.Decimal(18, 8)
 133 |   double17   Decimal?  @map("Double17") @db.Decimal(18, 8)
 134 |   double18   Decimal?  @map("Double18") @db.Decimal(18, 8)
 135 |   double19   Decimal?  @map("Double19") @db.Decimal(18, 8)
 136 |   double20   Decimal?  @map("Double20") @db.Decimal(18, 8)
 137 |   date01     DateTime? @map("Date01") @db.DateTime
 138 |   date02     DateTime? @map("Date02") @db.DateTime
 139 |   date03     DateTime? @map("Date03") @db.DateTime
 140 |   date04     DateTime? @map("Date04") @db.DateTime
 141 |   date05     DateTime? @map("Date05") @db.DateTime
 142 |   date06     DateTime? @map("Date06") @db.DateTime
 143 |   date07     DateTime? @map("Date07") @db.DateTime
 144 |   date08     DateTime? @map("Date08") @db.DateTime
 145 |   date09     DateTime? @map("Date09") @db.DateTime
 146 |   date10     DateTime? @map("Date10") @db.DateTime
 147 |   radio01    String?   @map("Radio01") @db.NVarChar(450)
 148 |   radio02    String?   @map("Radio02") @db.NVarChar(450)
 149 |   radio03    String?   @map("Radio03") @db.NVarChar(450)
 150 |   radio04    String?   @map("Radio04") @db.NVarChar(450)
 151 |   radio05    String?   @map("Radio05") @db.NVarChar(450)
 152 |   radio06    String?   @map("Radio06") @db.NVarChar(450)
 153 |   radio07    String?   @map("Radio07") @db.NVarChar(450)
 154 |   radio08    String?   @map("Radio08") @db.NVarChar(450)
 155 |   radio09    String?   @map("Radio09") @db.NVarChar(450)
 156 |   radio10    String?   @map("Radio10") @db.NVarChar(450)
 157 |   txt21      String?   @map("Txt21") @db.NVarChar(450)
 158 |   txt22      String?   @map("Txt22") @db.NVarChar(450)
 159 |   txt23      String?   @map("Txt23") @db.NVarChar(450)
 160 |   txt24      String?   @map("Txt24") @db.NVarChar(450)
 161 |   txt25      String?   @map("Txt25") @db.NVarChar(450)
 162 |   txt26      String?   @map("Txt26") @db.NVarChar(450)
 163 |   txt27      String?   @map("Txt27") @db.NVarChar(450)
 164 |   txt28      String?   @map("Txt28") @db.NVarChar(450)
 165 |   txt29      String?   @map("Txt29") @db.NVarChar(450)
 166 |   txt30      String?   @map("Txt30") @db.NVarChar(450)
 167 | 
 168 |   @@map("_temp_ContractCustomizedField")
 169 |   @@ignore
 170 |   @@schema("dbo")
 171 | }
 172 | 
 173 | model ActingAgent {
 174 |   sn          Int          @id(map: "PK_ActingUser") @default(autoincrement()) @map("Sn")
 175 |   actingId    Int?         @map("ActingID")
 176 |   userId      Int?         @map("UserID")
 177 |   user        User?        @relation(fields: [userId], references: [userId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ActingAgent_User")
 178 |   actingEntry ActingEntry? @relation(fields: [actingId], references: [actingId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ActingUser_ActingEntry")
 179 | 
 180 |   @@index([actingId], map: "IX_ActingAgent_ActingID")
 181 |   @@index([sn], map: "IX_ActingAgent_Sn")
 182 |   @@index([userId], map: "IX_ActingAgent_UserID")
 183 |   @@schema("join")
 184 | }
 185 | 
 186 | model ActingContract {
 187 |   sn          Int          @id(map: "PK_ActingContract") @default(autoincrement()) @map("Sn")
 188 |   actingId    Int?         @map("ActingID")
 189 |   contractId  Int?         @map("ContractID")
 190 |   actingEntry ActingEntry? @relation(fields: [actingId], references: [actingId], onDelete: Cascade, map: "FK_ActingContract_ActingEntry")
 191 |   contract    Contract?    @relation(fields: [contractId], references: [contractId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ActingContract_Contract")
 192 | 
 193 |   @@index([actingId], map: "IX_ActingContract_ActingID")
 194 |   @@index([contractId], map: "IX_ActingContract_ContractID")
 195 |   @@schema("join")
 196 | }
 197 | 
 198 | model ActingEntry {
 199 |   actingId            Int              @id(map: "PK_ActingEntry") @default(autoincrement()) @map("ActingID")
 200 |   userId              Int?             @map("UserID")
 201 |   validStartDate      DateTime?        @map("ValidStartDate") @db.DateTime
 202 |   validEndDate        DateTime?        @map("ValidEndDate") @db.DateTime
 203 |   reason              String?          @map("Reason") @db.NVarChar(Max)
 204 |   isVaild             Boolean?         @default(true, map: "DF_ActingEntry_IsVaild") @map("IsVaild")
 205 |   isActingAllContract Boolean?         @default(false, map: "DF_ActingEntry_IsActingAllContract") @map("IsActingAllContract")
 206 |   createdUserId       Int?             @map("CreatedUserID")
 207 |   createType          Int?             @map("CreateType")
 208 |   actingAgents        ActingAgent[]
 209 |   actingContracts     ActingContract[]
 210 |   user                User?            @relation(fields: [userId], references: [userId], onDelete: Cascade, map: "FK_ActingEntry_User")
 211 | 
 212 |   @@index([actingId], map: "IX_ActingEntry_ActingID")
 213 |   @@index([createdUserId], map: "IX_ActingEntry_CreatedUserID")
 214 |   @@index([createType], map: "IX_ActingEntry_CreateType")
 215 |   @@index([userId], map: "IX_ActingEntry_UserID")
 216 |   @@index([validEndDate], map: "IX_ActingEntry_ValidEndDate")
 217 |   @@index([validStartDate], map: "IX_ActingEntry_ValidStartDate")
 218 |   @@schema("data")
 219 | }
 220 | 
 221 | model ApiLog {
 222 |   sn         Int      @id(map: "PK_ContractCustomizedField") @default(autoincrement()) @map("Sn")
 223 |   userId     Int?     @map("UserID")
 224 |   uri        String?  @map("Uri") @db.NVarChar(Max)
 225 |   body       String?  @map("Body") @db.NVarChar(Max)
 226 |   response   String?  @map("Response") @db.NVarChar(Max)
 227 |   createDate DateTime @default(now(), map: "DF_ApiLog_CreateDate") @map("CreateDate") @db.DateTime
 228 |   user       User?    @relation(fields: [userId], references: [userId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ApiLog_User")
 229 | 
 230 |   @@schema("dbo")
 231 | }
 232 | 
 233 | model Attachment {
 234 |   attachmentId                         Int                                   @id(map: "PK_Attachment") @default(autoincrement()) @map("AttachmentID")
 235 |   filePath                             String?                               @map("FilePath") @db.NVarChar(Max)
 236 |   version                              Int?                                  @default(1, map: "DF_Attachment_Version") @map("Version")
 237 |   createDate                           DateTime?                             @default(now(), map: "DF_Attachment_CreateDate") @map("CreateDate") @db.DateTime
 238 |   userId                               Int?                                  @map("UserID")
 239 |   fileName                             String?                               @map("FileName") @db.NVarChar(Max)
 240 |   fileSize                             Int?                                  @map("FileSize")
 241 |   description                          String?                               @map("Description") @db.NVarChar(Max)
 242 |   type                                 String?                               @map("Type") @db.NVarChar(125)
 243 |   fileTypeId                           Int?                                  @map("FileTypeID")
 244 |   extension                            String?                               @map("Extension") @db.NVarChar(125)
 245 |   disable                              Boolean?                              @default(false, map: "DF_Attachment_Disable") @map("Disable")
 246 |   baseAttachmentId                     Int?                                  @map("BaseAttachmentID")
 247 |   originalWordPath                     String?                               @map("OriginalWordPath") @db.NVarChar(Max)
 248 |   originalTempFileName                 String?                               @map("OriginalTempFileName") @db.NVarChar(50)
 249 |   fileHash                             String?                               @map("FileHash") @db.NVarChar(Max)
 250 |   attachment                           Attachment?                           @relation("AttachmentToAttachment", fields: [baseAttachmentId], references: [attachmentId], onDelete: NoAction, onUpdate: NoAction, map: "FK_Attachment_Attachment")
 251 |   otherAttachments                     Attachment[]                          @relation("AttachmentToAttachment")
 252 |   fileType                             FileType?                             @relation(fields: [fileTypeId], references: [sn], onDelete: NoAction, onUpdate: NoAction, map: "FK_Attachment_FileType")
 253 |   user                                 User?                                 @relation(fields: [userId], references: [userId], onDelete: Cascade, map: "FK_Attachment_User")
 254 |   attachmentBips                       AttachmentBip[]
 255 |   attachmentCertifieds                 AttachmentCertified[]
 256 |   attachmentGuid                       AttachmentGuid?
 257 |   contractAttachments                  ContractAttachment[]
 258 |   contractFileTemplateAttachments      ContractFileTemplateAttachment[]
 259 |   contractFileTemplateExtraAttachments ContractFileTemplateExtraAttachment[]
 260 |   envelopeAttachments                  EnvelopeAttachment[]
 261 |   eventAttachments                     EventAttachment[]
 262 |   otherExaminerAttachments             OtherExaminerAttachment[]
 263 |   otherExaminerConfigAttachments       OtherExaminerConfigAttachment[]
 264 |   signAttachments                      SignAttachment[]
 265 | 
 266 |   @@index([attachmentId], map: "IX_Attachment_AttachmentID")
 267 |   @@index([baseAttachmentId], map: "IX_Attachment_BaseAttachmentID")
 268 |   @@index([createDate], map: "IX_Attachment_CreateDate")
 269 |   @@index([disable], map: "IX_Attachment_Disable")
 270 |   @@index([extension], map: "IX_Attachment_Extension")
 271 |   @@index([fileSize], map: "IX_Attachment_FileSize")
 272 |   @@index([fileTypeId], map: "IX_Attachment_FileTypeID")
 273 |   @@index([originalTempFileName], map: "IX_Attachment_OriginalTempFileName")
 274 |   @@index([type], map: "IX_Attachment_Type")
 275 |   @@index([userId], map: "IX_Attachment_UserID")
 276 |   @@index([version], map: "IX_Attachment_Version")
 277 |   @@schema("data")
 278 | }
 279 | 
 280 | model AttachmentBip {
 281 |   sn            Int        @id(map: "PK_AttachmentBIPInfo") @default(autoincrement()) @map("SN")
 282 |   attachmentId  Int        @map("AttachmentID")
 283 |   certificateId String?    @map("CertificateId") @db.NVarChar(450)
 284 |   attachment    Attachment @relation(fields: [attachmentId], references: [attachmentId], onUpdate: NoAction, map: "FK_AttachmentBIP_Attachment")
 285 | 
 286 |   @@index([attachmentId], map: "IX_AttachmentBIP_AttachmentID")
 287 |   @@index([certificateId], map: "IX_AttachmentBIP_CertificateId")
 288 |   @@map("AttachmentBIP")
 289 |   @@schema("join")
 290 | }
 291 | 
 292 | model AttachmentCertified {
 293 |   sn                   Int                 @id(map: "PK_AttachmentPDF") @default(autoincrement()) @map("SN")
 294 |   attachmentId         Int?                @map("AttachmentID")
 295 |   filePath             String?             @map("FilePath") @db.NVarChar(Max)
 296 |   userId               Int?                @map("UserID")
 297 |   fileName             String?             @map("FileName") @db.NVarChar(Max)
 298 |   fileSize             Int?                @map("FileSize")
 299 |   extension            String?             @map("Extension") @db.NVarChar(125)
 300 |   createDate           DateTime            @default(now(), map: "DF_AttachmentPDF_CreateDate") @map("CreateDate") @db.DateTime
 301 |   version              Int?                @default(0, map: "DF_AttachmentCertified_Version") @map("Version")
 302 |   signAttachmentInfoSn Int?                @map("SignAttachmentInfoSn")
 303 |   signAttachmentInfo   SignAttachmentInfo? @relation(fields: [signAttachmentInfoSn], references: [sn], onDelete: NoAction, onUpdate: NoAction, map: "FK_AttachmentCertified_SignAttachmentInfo")
 304 |   attachment           Attachment?         @relation(fields: [attachmentId], references: [attachmentId], onDelete: Cascade, onUpdate: NoAction, map: "FK_AttachmentPDF_Attachment")
 305 |   user                 User?               @relation(fields: [userId], references: [userId], onDelete: NoAction, onUpdate: NoAction, map: "FK_AttachmentPDF_User")
 306 | 
 307 |   @@index([attachmentId], map: "IX_AttachmentCertified_AttachmentID")
 308 |   @@index([createDate], map: "IX_AttachmentCertified_CreateDate")
 309 |   @@index([extension], map: "IX_AttachmentCertified_Extension")
 310 |   @@index([fileSize], map: "IX_AttachmentCertified_FileSize")
 311 |   @@index([signAttachmentInfoSn], map: "IX_AttachmentCertified_SignAttachmentInfoSn")
 312 |   @@index([userId], map: "IX_AttachmentCertified_UserID")
 313 |   @@index([version], map: "IX_AttachmentCertified_Version")
 314 |   @@schema("data")
 315 | }
 316 | 
 317 | model AttachmentGuid {
 318 |   attachmentId Int        @id(map: "PK_AttachmentGuid") @map("AttachmentID")
 319 |   guid         String     @map("Guid") @db.NVarChar(200)
 320 |   attachment   Attachment @relation(fields: [attachmentId], references: [attachmentId], onDelete: Cascade, onUpdate: NoAction, map: "FK_AttachmentGuid_Attachment")
 321 | 
 322 |   @@index([guid], map: "IX_AttachmentGuid_Guid")
 323 |   @@schema("join")
 324 | }
 325 | 
 326 | model AttachmentWatermark {
 327 |   sn                    Int                  @id(map: "PK_AttachmentWatermark") @default(autoincrement()) @map("SN")
 328 |   watermarkSetting      String?              @map("WatermarkSettings") @db.Xml
 329 |   watermarkSettingsJson String?              @map("WatermarkSettingsJson") @db.NVarChar(Max)
 330 |   signAttachmentInfos   SignAttachmentInfo[]
 331 | 
 332 |   @@schema("join")
 333 | }
 334 | 
 335 | model Authority {
 336 |   authorityId                                                      Int                                  @id(map: "PK_Authority") @map("AuthorityID")
 337 |   name                                                             String?                              @map("Name") @db.NVarChar(125)
 338 |   seq                                                              Int?                                 @map("Seq")
 339 |   groupId                                                          Int?                                 @map("GroupID")
 340 |   disable                                                          Boolean?                             @default(false, map: "DF_Authority_Disable") @map("Disable")
 341 |   authorityGroup                                                   AuthorityGroup?                      @relation(fields: [groupId], references: [groupId], onDelete: Cascade, map: "FK_Authority_AuthorityGroup")
 342 |   examStageExamStageViewAuthorityIdToAuthorities                   ExamStage[]                          @relation("ExamStage_ViewAuthorityIDToAuthority")
 343 |   examStageExamStageEditAuthorityIdToAuthorities                   ExamStage[]                          @relation("ExamStage_EditAuthorityIDToAuthority")
 344 |   examStageAuthorityExamStageAuthorityEditAuthorityIdToAuthorities ExamStageAuthority[]                 @relation("ExamStageAuthority_EditAuthorityIDToAuthority")
 345 |   examStageAuthorityExamStageAuthorityViewAuthorityIdToAuthorities ExamStageAuthority[]                 @relation("ExamStageAuthority_ViewAuthorityIDToAuthority")
 346 |   userAuthorities                                                  UserAuthority[]
 347 |   userContractAuthorities                                          UserContractAuthority[]
 348 |   userContractAuthorityForDepartments                              UserContractAuthorityForDepartment[]
 349 | 
 350 |   @@index([authorityId], map: "IX_Authority_AuthorityID")
 351 |   @@index([disable], map: "IX_Authority_Disable")
 352 |   @@index([groupId], map: "IX_Authority_GroupID")
 353 |   @@index([name], map: "IX_Authority_Name")
 354 |   @@index([seq], map: "IX_Authority_Seq")
 355 |   @@schema("code")
 356 | }
 357 | 
 358 | model AuthorityChangeLog {
 359 |   sn           Int      @id(map: "PK_AuthorityChangeLog") @default(autoincrement()) @map("Sn")
 360 |   loginSn      Int      @map("LoginSn")
 361 |   changingUser String   @map("ChangingUser") @db.NVarChar(225)
 362 |   changingItem String   @map("ChangingItem") @db.NVarChar(Max)
 363 |   changingDate DateTime @map("ChangingDate") @db.DateTime
 364 |   loginLog     LoginLog @relation(fields: [loginSn], references: [sn], onUpdate: NoAction, map: "FK_AuthorityChangeLog_LoginLog")
 365 | 
 366 |   @@index([changingDate], map: "IX_AuthorityChangeLog_ChangingDate")
 367 |   @@index([changingUser], map: "IX_AuthorityChangeLog_ChangingUser")
 368 |   @@index([loginSn], map: "IX_AuthorityChangeLog_LoginSn")
 369 |   @@schema("data")
 370 | }
 371 | 
 372 | model AuthorityGroup {
 373 |   groupId             Int         @id(map: "PK_AuthorityGroup") @map("GroupID")
 374 |   name                String?     @map("Name") @db.NVarChar(125)
 375 |   seq                 Int?        @map("Seq")
 376 |   examStageId         Int?        @map("ExamStageID")
 377 |   disable             Boolean?    @default(false, map: "DF_AuthorityGroup_Disable") @map("Disable")
 378 |   contractFlowGroupId Int?        @map("ContractFlowGroupID")
 379 |   authorities         Authority[]
 380 | 
 381 |   @@index([contractFlowGroupId], map: "IX_AuthorityGroup_ContractFlowGroupID")
 382 |   @@index([examStageId], map: "IX_AuthorityGroup_ContractFlowSeq")
 383 |   @@index([groupId], map: "IX_AuthorityGroup_GroupID")
 384 |   @@index([name], map: "IX_AuthorityGroup_Name")
 385 |   @@index([seq], map: "IX_AuthorityGroup_Seq")
 386 |   @@schema("code")
 387 | }
 388 | 
 389 | model Classification {
 390 |   sn                      Int                      @id(map: "PK_Classification") @default(autoincrement()) @map("SN")
 391 |   name                    String                   @map("Name") @db.NVarChar(Max)
 392 |   parentSn                Int?                     @map("ParentSN")
 393 |   createDate              DateTime?                @default(now(), map: "DF_Classification_CreateDate") @map("CreateDate") @db.DateTime
 394 |   isEnable                Boolean                  @default(true, map: "DF_Classification_IsEnable") @map("IsEnable")
 395 |   contractClassifications ContractClassification[]
 396 | 
 397 |   @@schema("code")
 398 | }
 399 | 
 400 | model CloseStage {
 401 |   closeStageId Int        @id(map: "PK_CloseStage") @default(autoincrement()) @map("CloseStageID")
 402 |   name         String?    @map("Name") @db.NVarChar(450)
 403 |   systemDefine Boolean?   @map("SystemDefine")
 404 |   disable      Boolean?   @map("Disable")
 405 |   seq          Int?       @map("Seq")
 406 |   contracts    Contract[]
 407 | 
 408 |   @@index([name], map: "IX_CloseStage_Name")
 409 |   @@index([seq], map: "IX_CloseStage_Seq")
 410 |   @@schema("code")
 411 | }
 412 | 
 413 | model CloseStatus {
 414 |   sn           Int      @id(map: "PK_CloseStatus") @default(autoincrement()) @map("Sn")
 415 |   name         String?  @map("Name") @db.NVarChar(125)
 416 |   systemDefine Boolean? @map("SystemDefine")
 417 |   disable      Boolean? @map("Disable")
 418 | 
 419 |   @@index([name], map: "IX_CloseStatus_Name")
 420 |   @@schema("code")
 421 | }
 422 | 
 423 | model CompanyList {
 424 |   companyId   Int     @id(map: "PK_CompanyList") @default(autoincrement()) @map("CompanyID")
 425 |   companyType String? @map("CompanyType") @db.NVarChar(50)
 426 |   companyName String? @map("CompanyName") @db.NVarChar(50)
 427 | 
 428 |   @@index([companyName], map: "IX_CompanyList_CompanyName")
 429 |   @@index([companyType], map: "IX_CompanyList_CompanyType")
 430 |   @@schema("data")
 431 | }
 432 | 
 433 | model Contract {
 434 |   contractId                                                             Int                      @id(map: "PK_Contract") @default(autoincrement()) @map("ContractID")
 435 |   documentName                                                           String?                  @map("DocumentName") @db.NVarChar(255)
 436 |   recorderId                                                             Int?                     @map("RecorderID")
 437 |   createDate                                                             DateTime?                @default(now(), map: "DF_Contract_CreateDate") @map("CreateDate") @db.DateTime
 438 |   branchId                                                               Int?                     @map("BranchID")
 439 |   requirement                                                            String?                  @map("Requirement") @db.NVarChar(Max)
 440 |   provisionDate                                                          DateTime?                @map("ProvisionDate") @db.DateTime
 441 |   partnerMemo                                                            String?                  @map("PartnerMemo") @db.NVarChar(Max)
 442 |   receiveNo                                                              String?                  @map("ReceiveNo") @db.NVarChar(255)
 443 |   saveNo                                                                 String?                  @map("SaveNo") @db.NVarChar(255)
 444 |   receiveDate                                                            DateTime?                @map("ReceiveDate") @db.DateTime
 445 |   saveDate                                                               DateTime?                @map("SaveDate") @db.DateTime
 446 |   applicationDate                                                        DateTime?                @map("ApplicationDate") @db.DateTime
 447 |   urgentLevel                                                            Int?                     @default(0, map: "DF_Contract_UrgentLevel") @map("UrgentLevel")
 448 |   requireSign                                                            Boolean?                 @default(false, map: "DF_Contract_RequireSign") @map("RequireSign")
 449 |   requirePartnerSign                                                     Boolean?                 @default(false, map: "DF_Contract_RequirePartnerSign") @map("RequirePartnerSign")
 450 |   signTypeId                                                             Int?                     @map("SignTypeID")
 451 |   currentStageId                                                         Int?                     @map("CurrentStageID")
 452 |   backStageId                                                            Int?                     @map("BackStageID")
 453 |   exchangeTypeId                                                         Int?                     @map("ExchangeTypeID")
 454 |   costClause                                                             String?                  @map("CostClause") @db.NVarChar(Max)
 455 |   otherClause                                                            String?                  @map("OtherClause") @db.NVarChar(Max)
 456 |   costNtd                                                                Decimal?                 @map("CostNTD") @db.Decimal(18, 2)
 457 |   cost                                                                   Decimal?                 @map("Cost") @db.Decimal(18, 2)
 458 |   memo                                                                   String?                  @map("Memo") @db.NVarChar(Max)
 459 |   effectiveDate                                                          DateTime?                @map("EffectiveDate") @db.DateTime
 460 |   validStartDate                                                         DateTime?                @map("ValidStartDate") @db.DateTime
 461 |   validEndDate                                                           DateTime?                @map("ValidEndDate") @db.DateTime
 462 |   signMemo                                                               String?                  @map("SignMemo") @db.NVarChar(Max)
 463 |   documentNo                                                             String?                  @map("DocumentNo") @db.NVarChar(Max)
 464 |   lastSendMailDate                                                       DateTime?                @map("LastSendMailDate") @db.DateTime
 465 |   alertExtend                                                            Boolean?                 @map("AlertExtend")
 466 |   alertEmail                                                             String?                  @map("AlertEmails") @db.NVarChar(255)
 467 |   companySignId                                                          Int?                     @map("CompanySignID")
 468 |   applyNo                                                                String?                  @map("ApplyNo") @db.NVarChar(255)
 469 |   alertBeginDate                                                         DateTime?                @map("AlertBeginDate") @db.DateTime
 470 |   alertPeriod                                                            Int?                     @map("AlertPeriod")
 471 |   autoExtend                                                             Boolean?                 @map("AutoExtend")
 472 |   extendYear                                                             Int?                     @map("ExtendYear")
 473 |   extendMonth                                                            Int?                     @map("ExtendMonth")
 474 |   finalCost                                                              Decimal?                 @map("FinalCost") @db.Decimal(18, 2)
 475 |   alertCcEmail                                                           String?                  @map("AlertCCEmails") @db.NVarChar(255)
 476 |   alertBccEmail                                                          String?                  @map("AlertBCCEmails") @db.NVarChar(255)
 477 |   needCost                                                               Boolean?                 @map("NeedCost")
 478 |   finalCostExchangeTypeId                                                Int?                     @map("FinalCostExchangeTypeID")
 479 |   finalCostNtd                                                           Decimal?                 @map("FinalCostNTD") @db.Decimal(18, 2)
 480 |   alertEndDate                                                           DateTime?                @map("AlertEndDate") @db.DateTime
 481 |   closeMemo                                                              String?                  @map("CloseMemo") @db.NVarChar(Max)
 482 |   closeStageId                                                           Int?                     @map("CloseStageID")
 483 |   autoRenewDeadline                                                      Boolean?                 @map("AutoRenewDeadline")
 484 |   autoRenewNewDate                                                       Boolean?                 @map("AutoRenewNewDate")
 485 |   autoRenewValidEndDate                                                  DateTime?                @map("AutoRenewValidEndDate") @db.DateTime
 486 |   closeCaseBeforeMonth                                                   Int?                     @map("CloseCaseBeforeMonth")
 487 |   closeCaseBeforeDay                                                     Int?                     @map("CloseCaseBeforeDay")
 488 |   extendWithoutNotice                                                    Boolean?                 @map("ExtendWithoutNotice")
 489 |   extendPeriodYear                                                       Int?                     @map("ExtendPeriodYear")
 490 |   extendPeriodMonth                                                      Int?                     @map("ExtendPeriodMonth")
 491 |   autoCircleCount                                                        Int?                     @map("AutoCircleCount")
 492 |   terminationWithoutNotice                                               Boolean?                 @map("TerminationWithoutNotice")
 493 |   isAlert                                                                Boolean?                 @map("IsAlert")
 494 |   notifyBeforeDay                                                        Int?                     @map("NotifyBeforeDay")
 495 |   notifyDay                                                              Int?                     @map("NotifyDay")
 496 |   closeMailToSelect                                                      Int?                     @map("CloseMailToSelect")
 497 |   closeMailToOther                                                       String?                  @map("CloseMailToOther") @db.NVarChar(450)
 498 |   closeCcMailToSelect                                                    Int?                     @map("CloseCCMailToSelect")
 499 |   closeCcMailToOther                                                     String?                  @map("CloseCCMailToOther") @db.NVarChar(450)
 500 |   closeBccMailToSelect                                                   Int?                     @map("CloseBCCMailToSelect")
 501 |   closeBccMailToOther                                                    String?                  @map("CloseBCCMailToOther") @db.NVarChar(450)
 502 |   txt01                                                                  String?                  @map("Txt01") @db.NVarChar(450)
 503 |   txt02                                                                  String?                  @map("Txt02") @db.NVarChar(450)
 504 |   txt03                                                                  String?                  @map("Txt03") @db.NVarChar(450)
 505 |   txt04                                                                  String?                  @map("Txt04") @db.NVarChar(450)
 506 |   txt05                                                                  String?                  @map("Txt05") @db.NVarChar(450)
 507 |   txt06                                                                  String?                  @map("Txt06") @db.NVarChar(450)
 508 |   txt07                                                                  String?                  @map("Txt07") @db.NVarChar(450)
 509 |   txt08                                                                  String?                  @map("Txt08") @db.NVarChar(450)
 510 |   txt09                                                                  String?                  @map("Txt09") @db.NVarChar(450)
 511 |   txt10                                                                  String?                  @map("Txt10") @db.NVarChar(450)
 512 |   memo01                                                                 String?                  @map("Memo01") @db.NVarChar(Max)
 513 |   memo02                                                                 String?                  @map("Memo02") @db.NVarChar(Max)
 514 |   memo03                                                                 String?                  @map("Memo03") @db.NVarChar(Max)
 515 |   memo04                                                                 String?                  @map("Memo04") @db.NVarChar(Max)
 516 |   memo05                                                                 String?                  @map("Memo05") @db.NVarChar(Max)
 517 |   memo06                                                                 String?                  @map("Memo06") @db.NVarChar(Max)
 518 |   memo07                                                                 String?                  @map("Memo07") @db.NVarChar(Max)
 519 |   memo08                                                                 String?                  @map("Memo08") @db.NVarChar(Max)
 520 |   memo09                                                                 String?                  @map("Memo09") @db.NVarChar(Max)
 521 |   memo10                                                                 String?                  @map("Memo10") @db.NVarChar(Max)
 522 |   memo11                                                                 String?                  @map("Memo11") @db.NVarChar(Max)
 523 |   memo12                                                                 String?                  @map("Memo12") @db.NVarChar(Max)
 524 |   memo13                                                                 String?                  @map("Memo13") @db.NVarChar(Max)
 525 |   memo14                                                                 String?                  @map("Memo14") @db.NVarChar(Max)
 526 |   memo15                                                                 String?                  @map("Memo15") @db.NVarChar(Max)
 527 |   radio01                                                                String?                  @map("Radio01") @db.NVarChar(2000)
 528 |   radio02                                                                String?                  @map("Radio02") @db.NVarChar(2000)
 529 |   radio03                                                                String?                  @map("Radio03") @db.NVarChar(2000)
 530 |   radio04                                                                String?                  @map("Radio04") @db.NVarChar(2000)
 531 |   radio05                                                                String?                  @map("Radio05") @db.NVarChar(2000)
 532 |   checkBox01                                                             String?                  @map("CheckBox01") @db.NVarChar(2000)
 533 |   checkBox02                                                             String?                  @map("CheckBox02") @db.NVarChar(2000)
 534 |   checkBox03                                                             String?                  @map("CheckBox03") @db.NVarChar(2000)
 535 |   checkBox04                                                             String?                  @map("CheckBox04") @db.NVarChar(2000)
 536 |   checkBox05                                                             String?                  @map("CheckBox05") @db.NVarChar(2000)
 537 |   select01                                                               String?                  @map("Select01") @db.NVarChar(2000)
 538 |   select02                                                               String?                  @map("Select02") @db.NVarChar(2000)
 539 |   select03                                                               String?                  @map("Select03") @db.NVarChar(2000)
 540 |   select04                                                               String?                  @map("Select04") @db.NVarChar(2000)
 541 |   select05                                                               String?                  @map("Select05") @db.NVarChar(2000)
 542 |   int01                                                                  Int?                     @map("Int01")
 543 |   int02                                                                  Int?                     @map("Int02")
 544 |   int03                                                                  Int?                     @map("Int03")
 545 |   int04                                                                  Int?                     @map("Int04")
 546 |   int05                                                                  Int?                     @map("Int05")
 547 |   double01                                                               Decimal?                 @map("Double01") @db.Decimal(18, 8)
 548 |   double02                                                               Decimal?                 @map("Double02") @db.Decimal(18, 8)
 549 |   double03                                                               Decimal?                 @map("Double03") @db.Decimal(18, 8)
 550 |   double04                                                               Decimal?                 @map("Double04") @db.Decimal(18, 8)
 551 |   double05                                                               Decimal?                 @map("Double05") @db.Decimal(18, 8)
 552 |   date01                                                                 DateTime?                @map("Date01") @db.DateTime
 553 |   date02                                                                 DateTime?                @map("Date02") @db.DateTime
 554 |   date03                                                                 DateTime?                @map("Date03") @db.DateTime
 555 |   date04                                                                 DateTime?                @map("Date04") @db.DateTime
 556 |   date05                                                                 DateTime?                @map("Date05") @db.DateTime
 557 |   date06                                                                 DateTime?                @map("Date06") @db.DateTime
 558 |   date07                                                                 DateTime?                @map("Date07") @db.DateTime
 559 |   date08                                                                 DateTime?                @map("Date08") @db.DateTime
 560 |   date09                                                                 DateTime?                @map("Date09") @db.DateTime
 561 |   date10                                                                 DateTime?                @map("Date10") @db.DateTime
 562 |   contractModuleSn                                                       Int?                     @map("ContractModuleSN")
 563 |   finalCostExchangeRate                                                  Decimal?                 @map("FinalCostExchangeRate") @db.Decimal(10, 2)
 564 |   durationOtherMsg                                                       String?                  @map("DurationOtherMsg") @db.NVarChar(Max)
 565 |   applicantDepartmentId                                                  Int?                     @map("ApplicantDepartmentID")
 566 |   contractCost                                                           Int?                     @map("ContractCost")
 567 |   costOtherText                                                          String?                  @map("CostOtherText") @db.NVarChar(450)
 568 |   validOtherType                                                         Int?                     @map("ValidOtherType")
 569 |   validOtherTypeMemo                                                     String?                  @map("ValidOtherTypeMemo") @db.NVarChar(450)
 570 |   autoExtendContract                                                     Int?                     @map("AutoExtendContract")
 571 |   autoExtendLimited                                                      Int?                     @map("AutoExtendLimited")
 572 |   autoExtendLimitedFrequency                                             Int?                     @map("AutoExtendLimitedFrequency")
 573 |   autoExtendFrequency                                                    Int?                     @map("AutoExtendFrequency")
 574 |   validDurationType                                                      Int?                     @default(0, map: "DF_Contract_ValidDurationType") @map("ValidDurationType")
 575 |   lastAutoExtendDate                                                     DateTime?                @map("LastAutoExtendDate") @db.DateTime
 576 |   countrySn                                                              Int?                     @map("CountrySn")
 577 |   actingContracts                                                        ActingContract[]
 578 |   closeStage                                                             CloseStage?              @relation(fields: [closeStageId], references: [closeStageId], onDelete: NoAction, onUpdate: NoAction, map: "FK_Contract_CloseStage")
 579 |   countryCode                                                            CountryCode?             @relation(fields: [countrySn], references: [sn], onDelete: NoAction, onUpdate: NoAction, map: "FK_Contract_CountrySn_CountryCode_Sn")
 580 |   departmentContractBranchIdToDepartment                                 Department?              @relation("Contract_BranchIDToDepartment", fields: [branchId], references: [departmentId], onDelete: NoAction, onUpdate: NoAction, map: "FK_Contract_Department")
 581 |   departmentContractApplicantDepartmentIdToDepartment                    Department?              @relation("Contract_ApplicantDepartmentIDToDepartment", fields: [applicantDepartmentId], references: [departmentId], onDelete: NoAction, onUpdate: NoAction, map: "FK_Contract_Department1")
 582 |   urgentLevelContractUrgentLevelToUrgentLevel                            UrgentLevel?             @relation("Contract_UrgentLevelToUrgentLevel", fields: [urgentLevel], references: [urgentLevelId], onDelete: NoAction, onUpdate: NoAction, map: "FK_Contract_UrgentLevel")
 583 |   user                                                                   User?                    @relation(fields: [recorderId], references: [userId], onDelete: NoAction, onUpdate: NoAction, map: "FK_Contract_User")
 584 |   contractAccessRelatedContractAccessRelatedMainContractIdToContracts    ContractAccessRelated[]  @relation("ContractAccessRelated_MainContractIDToContract")
 585 |   contractAccessRelatedContractAccessRelatedRelatedContractIdToContracts ContractAccessRelated[]  @relation("ContractAccessRelated_RelatedContractIDToContract")
 586 |   contractAmount                                                         JoinContractAmount?
 587 |   contractAttachments                                                    ContractAttachment[]
 588 |   contractClassifications                                                ContractClassification[]
 589 |   contractCustom                                                         ContractCustom?
 590 |   contractCustomizedField                                                ContractCustomizedField?
 591 |   contractEnvelopes                                                      ContractEnvelope[]
 592 |   contractEvents                                                         ContractEvent[]
 593 |   contractExaminers                                                      ContractExaminer[]
 594 |   contractExamStageInfo                                                  ContractExamStageInfo?
 595 |   contractExtendInfo                                                     ContractExtendInfo?
 596 |   contractGuid                                                           ContractGuid?
 597 |   contractHistories                                                      ContractHistory[]
 598 |   contractMailLogs                                                       ContractMailLog[]
 599 |   contractMessageBoards                                                  ContractMessageBoard[]
 600 |   contractOtherNotifies                                                  ContractOtherNotify[]
 601 |   contractPartners                                                       ContractPartner[]
 602 |   contractRequireSigns                                                   ContractRequireSign[]
 603 |   contractStampDuties                                                    ContractStampDuty[]
 604 |   contractTypes                                                          JoinContractType[]       @ignore
 605 |   contractViewTemp                                                       ContractViewTemp?
 606 |   ltcLogs                                                                LtcLog[]
 607 |   partnerSignLogs                                                        PartnerSignLog[]
 608 |   projectContracts                                                       ProjectContract[]
 609 |   relatedContractRelatedContractContractIdToContracts                    RelatedContract[]        @relation("RelatedContract_ContractIDToContract")
 610 |   relatedContractRelatedContractRelatedContractIdToContracts             RelatedContract[]        @relation("RelatedContract_RelatedContractIDToContract")
 611 |   tempPartners                                                           TempPartner[]
 612 |   userContractAuthorities                                                UserContractAuthority[]
 613 | 
 614 |   @@index([alertBccEmail], map: "IX_Contract_AlertBCCEmails")
 615 |   @@index([alertBeginDate], map: "IX_Contract_AlertBeginDate")
 616 |   @@index([alertCcEmail], map: "IX_Contract_AlertCCEmails")
 617 |   @@index([alertEmail], map: "IX_Contract_AlertEmails")
 618 |   @@index([alertEndDate], map: "IX_Contract_AlertEndDate")
 619 |   @@index([alertPeriod], map: "IX_Contract_AlertPeriod")
 620 |   @@index([applicantDepartmentId], map: "IX_Contract_ApplicantDepartment")
 621 |   @@index([applicationDate], map: "IX_Contract_ApplicationDate")
 622 |   @@index([applyNo], map: "IX_Contract_ApplyNo")
 623 |   @@index([autoCircleCount], map: "IX_Contract_AutoCircleCount")
 624 |   @@index([autoExtendContract], map: "IX_Contract_AutoExtendContract")
 625 |   @@index([autoExtendFrequency], map: "IX_Contract_AutoExtendFrequency")
 626 |   @@index([autoExtendLimited], map: "IX_Contract_AutoExtendLimited")
 627 |   @@index([autoExtendLimitedFrequency], map: "IX_Contract_AutoExtendLimitedFrequency")
 628 |   @@index([autoRenewValidEndDate], map: "IX_Contract_AutoRenewValidEndDate")
 629 |   @@index([backStageId], map: "IX_Contract_BackStageID")
 630 |   @@index([branchId], map: "IX_Contract_BranchID")
 631 |   @@index([closeBccMailToOther], map: "IX_Contract_CloseBCCMailToOther")
 632 |   @@index([closeBccMailToSelect], map: "IX_Contract_CloseBCCMailToSelect")
 633 |   @@index([closeCaseBeforeDay], map: "IX_Contract_CloseCaseBeforeDay")
 634 |   @@index([closeCaseBeforeMonth], map: "IX_Contract_CloseCaseBeforeMonth")
 635 |   @@index([closeCcMailToOther], map: "IX_Contract_CloseCCMailToOther")
 636 |   @@index([closeCcMailToSelect], map: "IX_Contract_CloseCCMailToSelect")
 637 |   @@index([closeMailToOther], map: "IX_Contract_CloseMailToOther")
 638 |   @@index([closeMailToSelect], map: "IX_Contract_CloseMailToSelect")
 639 |   @@index([closeStageId], map: "IX_Contract_CloseStageID")
 640 |   @@index([companySignId], map: "IX_Contract_CompanySignID")
 641 |   @@index([contractCost], map: "IX_CONTRACT_CONTRACTCOST")
 642 |   @@index([contractId], map: "IX_Contract_ContractID")
 643 |   @@index([contractModuleSn], map: "IX_Contract_ContractModuleSN")
 644 |   @@index([cost], map: "IX_Contract_Cost")
 645 |   @@index([costNtd], map: "IX_Contract_CostNTD")
 646 |   @@index([costOtherText], map: "IX_Contract_CostOtherText")
 647 |   @@index([createDate], map: "IX_Contract_CreateDate")
 648 |   @@index([currentStageId], map: "IX_Contract_CurrentStageID")
 649 |   @@index([date01], map: "IX_Contract_Date01")
 650 |   @@index([date02], map: "IX_Contract_Date02")
 651 |   @@index([date03], map: "IX_Contract_Date03")
 652 |   @@index([date04], map: "IX_Contract_Date04")
 653 |   @@index([date05], map: "IX_Contract_Date05")
 654 |   @@index([date06], map: "IX_Contract_Date06")
 655 |   @@index([date07], map: "IX_Contract_Date07")
 656 |   @@index([date08], map: "IX_Contract_Date08")
 657 |   @@index([date09], map: "IX_Contract_Date09")
 658 |   @@index([date10], map: "IX_Contract_Date10")
 659 |   @@index([documentName], map: "IX_Contract_DocumentName")
 660 |   @@index([double01], map: "IX_Contract_Double01")
 661 |   @@index([double02], map: "IX_Contract_Double02")
 662 |   @@index([double03], map: "IX_Contract_Double03")
 663 |   @@index([double04], map: "IX_Contract_Double04")
 664 |   @@index([double05], map: "IX_Contract_Double05")
 665 |   @@index([effectiveDate], map: "IX_Contract_EffectiveDate")
 666 |   @@index([exchangeTypeId], map: "IX_Contract_ExchangeTypeID")
 667 |   @@index([extendMonth], map: "IX_Contract_ExtendMonth")
 668 |   @@index([extendPeriodMonth], map: "IX_Contract_ExtendPeriodMonth")
 669 |   @@index([extendPeriodYear], map: "IX_Contract_ExtendPeriodYear")
 670 |   @@index([extendYear], map: "IX_Contract_ExtendYear")
 671 |   @@index([finalCost], map: "IX_Contract_FinalCost")
 672 |   @@index([finalCostExchangeRate], map: "IX_Contract_FinalCostExchangeRate")
 673 |   @@index([finalCostExchangeTypeId], map: "IX_Contract_FinalCostExchangeTypeID")
 674 |   @@index([finalCostNtd], map: "IX_Contract_FinalCostNTD")
 675 |   @@index([int01], map: "IX_Contract_Int01")
 676 |   @@index([int02], map: "IX_Contract_Int02")
 677 |   @@index([int03], map: "IX_Contract_Int03")
 678 |   @@index([int04], map: "IX_Contract_Int04")
 679 |   @@index([int05], map: "IX_Contract_Int05")
 680 |   @@index([lastAutoExtendDate], map: "IX_Contract_LastAutoExtendDate")
 681 |   @@index([lastSendMailDate], map: "IX_Contract_LastSendMailDate")
 682 |   @@index([notifyBeforeDay], map: "IX_Contract_NotifyBeforeDay")
 683 |   @@index([notifyDay], map: "IX_Contract_NotifyDay")
 684 |   @@index([provisionDate], map: "IX_Contract_ProvisionDate")
 685 |   @@index([receiveDate], map: "IX_Contract_ReceiveDate")
 686 |   @@index([receiveNo], map: "IX_Contract_ReceiveNo")
 687 |   @@index([recorderId], map: "IX_Contract_RecorderID")
 688 |   @@index([requirePartnerSign], map: "IX_Contract_RequirePartnerSign")
 689 |   @@index([requireSign], map: "IX_Contract_RequireSign")
 690 |   @@index([saveDate], map: "IX_Contract_SaveDate")
 691 |   @@index([saveNo], map: "IX_Contract_SaveNo")
 692 |   @@index([signTypeId], map: "IX_Contract_SignTypeID")
 693 |   @@index([txt01], map: "IX_Contract_Txt01")
 694 |   @@index([txt02], map: "IX_Contract_Txt02")
 695 |   @@index([txt03], map: "IX_Contract_Txt03")
 696 |   @@index([txt04], map: "IX_Contract_Txt04")
 697 |   @@index([txt05], map: "IX_Contract_Txt05")
 698 |   @@index([txt06], map: "IX_Contract_Txt06")
 699 |   @@index([txt07], map: "IX_Contract_Txt07")
 700 |   @@index([txt08], map: "IX_Contract_Txt08")
 701 |   @@index([txt09], map: "IX_Contract_Txt09")
 702 |   @@index([txt10], map: "IX_Contract_Txt10")
 703 |   @@index([urgentLevel], map: "IX_Contract_UrgentLevel")
 704 |   @@index([validDurationType], map: "IX_Contract_ValidDurationType")
 705 |   @@index([validEndDate], map: "IX_Contract_ValidEndDate")
 706 |   @@index([validOtherType], map: "IX_Contract_ValidOtherType")
 707 |   @@index([validOtherTypeMemo], map: "IX_Contract_ValidOtherTypeMemo")
 708 |   @@index([validStartDate], map: "IX_Contract_ValidStartDate")
 709 |   @@schema("data")
 710 | }
 711 | 
 712 | model ContractAccessRelated {
 713 |   sn                                                       Int       @id(map: "PK_ContractAccessRelated") @default(autoincrement()) @map("SN")
 714 |   mainContractId                                           Int?      @map("MainContractID")
 715 |   relatedContractId                                        Int?      @map("RelatedContractID")
 716 |   createDateTime                                           DateTime  @map("CreateDateTime") @db.DateTime
 717 |   txt01                                                    String?   @map("Txt01") @db.NVarChar(450)
 718 |   txt02                                                    String?   @map("Txt02") @db.NVarChar(450)
 719 |   txt03                                                    String?   @map("Txt03") @db.NVarChar(450)
 720 |   txt04                                                    String?   @map("Txt04") @db.NVarChar(450)
 721 |   contractContractAccessRelatedMainContractIdToContract    Contract? @relation("ContractAccessRelated_MainContractIDToContract", fields: [mainContractId], references: [contractId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractAccessRelated_Contract")
 722 |   contractContractAccessRelatedRelatedContractIdToContract Contract? @relation("ContractAccessRelated_RelatedContractIDToContract", fields: [relatedContractId], references: [contractId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractAccessRelated_Contract1")
 723 | 
 724 |   @@index([createDateTime], map: "IX_ContractAccessRelated_CreateDateTime")
 725 |   @@index([mainContractId], map: "IX_ContractAccessRelated_MainContractID")
 726 |   @@index([relatedContractId], map: "IX_ContractAccessRelated_RelatedContractID")
 727 |   @@index([txt01], map: "IX_ContractAccessRelated_Txt01")
 728 |   @@index([txt02], map: "IX_ContractAccessRelated_Txt02")
 729 |   @@index([txt03], map: "IX_ContractAccessRelated_Txt03")
 730 |   @@index([txt04], map: "IX_ContractAccessRelated_Txt04")
 731 |   @@schema("join")
 732 | }
 733 | 
 734 | model ContractAccessType {
 735 |   sn                  Int                  @id(map: "PK_ContractAccessType_SN") @default(autoincrement()) @map("SN")
 736 |   name                String               @map("Name") @db.NVarChar(300)
 737 |   seq                 Int                  @map("Seq")
 738 |   enable              Boolean              @map("Enable")
 739 |   contractExtendInfos ContractExtendInfo[]
 740 | 
 741 |   @@index([name], map: "IX_ContractAccessType_Name")
 742 |   @@index([seq], map: "IX_ContractAccessType_Seq")
 743 |   @@schema("code")
 744 | }
 745 | 
 746 | /// The underlying table does not contain a valid unique identifier and can therefore currently not be handled by Prisma Client.
 747 | model CodeContractAmount {
 748 |   contractAmountId Int                  @id @default(autoincrement()) @map("ContractAmountID")
 749 |   amountItem       String               @map("AmountItem") @db.NVarChar(250)
 750 |   disable          Boolean              @default(false, map: "DF_ContractAmount_Disable") @map("Disable")
 751 |   systemDefine     Boolean              @default(false, map: "DF_ContractAmount_SystemDefine") @map("SystemDefine")
 752 |   contractAmounts  JoinContractAmount[]
 753 | 
 754 |   @@index([amountItem], map: "IX_ContractAmount_AmountItem")
 755 |   @@map("ContractAmount")
 756 |   @@ignore
 757 |   @@schema("code")
 758 | }
 759 | 
 760 | model JoinContractAmount {
 761 |   sn               Int                 @id(map: "PK_ContractAmount_1") @default(autoincrement()) @map("SN")
 762 |   contractId       Int                 @unique(map: "UC_ContractAmount_ContractID") @map("ContractID")
 763 |   contractAmountId Int?                @map("ContractAmountID")
 764 |   exchangeTypeId   Int?                @map("ExchangeTypeID")
 765 |   cost             Decimal?            @map("Cost") @db.Decimal(18, 2)
 766 |   costNtd          Decimal?            @map("CostNTD") @db.Decimal(18, 2)
 767 |   exchangeRate     Decimal?            @map("ExchangeRate") @db.Decimal(10, 2)
 768 |   tax              Int?                @map("Tax")
 769 |   payPeriod        String?             @map("PayPeriod") @db.NVarChar(450)
 770 |   contract         Contract            @relation(fields: [contractId], references: [contractId], onDelete: Cascade, map: "FK_ContractAmount_Contract")
 771 |   contractAmount   CodeContractAmount? @relation(fields: [contractAmountId], references: [contractAmountId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractAmount_ContractAmount") @ignore
 772 |   exchange         Exchange?           @relation(fields: [exchangeTypeId], references: [sn], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractAmount_Exchange")
 773 | 
 774 |   @@map("ContractAmount")
 775 |   @@schema("join")
 776 | }
 777 | 
 778 | model ContractAttachment {
 779 |   sn                     Int         @id(map: "PK_ContractAttachment") @default(autoincrement()) @map("Sn")
 780 |   attachmentId           Int?        @map("AttachmentID")
 781 |   contractId             Int?        @map("ContractID")
 782 |   examStageId            Int?        @map("ExamStageID")
 783 |   examinerSn             Int?        @map("ExaminerSn")
 784 |   contractFileTemplateSn Int?        @map("ContractFileTemplateSN")
 785 |   attachment             Attachment? @relation(fields: [attachmentId], references: [attachmentId], onDelete: Cascade, map: "FK_ContractAttachment_Attachment")
 786 |   contract               Contract?   @relation(fields: [contractId], references: [contractId], onDelete: Cascade, map: "FK_ContractAttachment_Contract")
 787 | 
 788 |   @@index([attachmentId], map: "IX_ContractAttachment_AttachmentID")
 789 |   @@index([contractFileTemplateSn], map: "IX_ContractAttachment_ContractFileTemplateSN")
 790 |   @@index([contractId], map: "IX_ContractAttachment_ContractID")
 791 |   @@index([examinerSn], map: "IX_ContractAttachment_ExaminerSn")
 792 |   @@index([examStageId], map: "IX_ContractAttachment_ExamStageID")
 793 |   @@schema("join")
 794 | }
 795 | 
 796 | model ContractAttachmentStatus {
 797 |   sn           Int     @id(map: "PK_ContractAttachmentStatus") @default(autoincrement()) @map("Sn")
 798 |   attachmentId Int     @map("AttachmentId")
 799 |   contractId   Int     @map("ContractId")
 800 |   isDelete     Boolean @map("IsDelete")
 801 | 
 802 |   @@index([attachmentId], map: "IX_ContractAttachmentStatus_AttachmentId")
 803 |   @@index([contractId], map: "IX_ContractAttachmentStatus_ContractId")
 804 |   @@schema("join")
 805 | }
 806 | 
 807 | model ContractClassification {
 808 |   sn               Int            @id(map: "PK_ContractClassification") @default(autoincrement()) @map("SN")
 809 |   contractId       Int            @map("ContractID")
 810 |   classificationSn Int            @map("ClassificationSN")
 811 |   classification   Classification @relation(fields: [classificationSn], references: [sn], onDelete: Cascade, map: "FK_ContractClassification_ClassificationSN_Classification_SN")
 812 |   contract         Contract       @relation(fields: [contractId], references: [contractId], onDelete: Cascade, map: "FK_ContractClassification_ContractID_Contract_ContractID")
 813 | 
 814 |   @@index([classificationSn], map: "IX_ContractClassification_ClassificationSN")
 815 |   @@index([contractId], map: "IX_ContractClassification_ContractID")
 816 |   @@schema("join")
 817 | }
 818 | 
 819 | model ContractCurrentExaminerTemp {
 820 |   sn         Int     @id(map: "PK_ContractCurrentExaminerTemp") @default(autoincrement()) @map("SN")
 821 |   contractId Int     @map("ContractID")
 822 |   userId     Int     @map("UserID")
 823 |   examType   String? @map("ExamType") @db.NVarChar(50)
 824 | 
 825 |   @@index([contractId], map: "IX_ContractCurrentExaminerTemp_ContractID")
 826 |   @@index([examType], map: "IX_ContractCurrentExaminerTemp_ExamType")
 827 |   @@index([userId], map: "IX_ContractCurrentExaminerTemp_UserID")
 828 |   @@schema("dbo")
 829 | }
 830 | 
 831 | model ContractCustom {
 832 |   contractId            Int          @id(map: "PK_ContractCustom_ContractID") @map("ContractID")
 833 |   applicableField       Boolean?     @map("ApplicableField")
 834 |   whoPaymentField       String?      @map("WhoPaymentField") @db.NVarChar(100)
 835 |   otherPaymentField     String?      @map("OtherPaymentField") @db.NVarChar(200)
 836 |   countryCodeSn         Int?         @map("CountryCodeSn")
 837 |   siteCodeSn            Int?         @map("SiteCodeSn")
 838 |   businessComment       String?      @map("BusinessComment") @db.NVarChar(Max)
 839 |   companyCode           String?      @map("CompanyCode") @db.NVarChar(200)
 840 |   companyType1          String?      @map("CompanyType1") @db.NVarChar(50)
 841 |   yearField             String?      @map("YearField") @db.NVarChar(50)
 842 |   countryField          String?      @map("CountryField") @db.NVarChar(50)
 843 |   companyType2          String?      @map("CompanyType2") @db.NVarChar(50)
 844 |   cusProductProjectName String?      @map("Cus_ProductProjectName") @db.NVarChar(450)
 845 |   needSignature         Boolean?     @map("NeedSignature")
 846 |   contract              Contract     @relation(fields: [contractId], references: [contractId], onDelete: Cascade, map: "FK_ContractCustom_Contract")
 847 |   countryCode           CountryCode? @relation(fields: [countryCodeSn], references: [sn], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractCustom_CountryCode")
 848 |   siteCode              SiteCode?    @relation(fields: [siteCodeSn], references: [sn], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractCustom_SiteCode")
 849 | 
 850 |   @@index([companyCode], map: "IX_ContractCustom_CompanyCode")
 851 |   @@index([companyType1], map: "IX_ContractCustom_CompanyType1")
 852 |   @@index([companyType2], map: "IX_ContractCustom_CompanyType2")
 853 |   @@index([countryCodeSn], map: "IX_ContractCustom_CountryCodeSn")
 854 |   @@index([countryField], map: "IX_ContractCustom_CountryField")
 855 |   @@index([cusProductProjectName], map: "IX_ContractCustom_Cus_ProductProjectName")
 856 |   @@index([otherPaymentField], map: "IX_ContractCustom_OtherPaymentField")
 857 |   @@index([siteCodeSn], map: "IX_ContractCustom_SiteCodeSn")
 858 |   @@index([whoPaymentField], map: "IX_ContractCustom_WhoPaymentField")
 859 |   @@index([yearField], map: "IX_ContractCustom_YearField")
 860 |   @@schema("data")
 861 | }
 862 | 
 863 | model ContractCustomizedField {
 864 |   contractId Int       @id(map: "PK_ContractCustomizedField") @map("ContractId")
 865 |   txt01      String?   @map("Txt01") @db.NVarChar(Max)
 866 |   txt02      String?   @map("Txt02") @db.NVarChar(Max)
 867 |   txt03      String?   @map("Txt03") @db.NVarChar(Max)
 868 |   txt04      String?   @map("Txt04") @db.NVarChar(Max)
 869 |   txt05      String?   @map("Txt05") @db.NVarChar(Max)
 870 |   txt06      String?   @map("Txt06") @db.NVarChar(Max)
 871 |   txt07      String?   @map("Txt07") @db.NVarChar(Max)
 872 |   txt08      String?   @map("Txt08") @db.NVarChar(Max)
 873 |   txt09      String?   @map("Txt09") @db.NVarChar(Max)
 874 |   txt10      String?   @map("Txt10") @db.NVarChar(Max)
 875 |   txt11      String?   @map("Txt11") @db.NVarChar(Max)
 876 |   txt12      String?   @map("Txt12") @db.NVarChar(Max)
 877 |   txt13      String?   @map("Txt13") @db.NVarChar(Max)
 878 |   txt14      String?   @map("Txt14") @db.NVarChar(Max)
 879 |   txt15      String?   @map("Txt15") @db.NVarChar(Max)
 880 |   txt16      String?   @map("Txt16") @db.NVarChar(Max)
 881 |   txt17      String?   @map("Txt17") @db.NVarChar(Max)
 882 |   txt18      String?   @map("Txt18") @db.NVarChar(Max)
 883 |   txt19      String?   @map("Txt19") @db.NVarChar(Max)
 884 |   txt20      String?   @map("Txt20") @db.NVarChar(Max)
 885 |   memo01     String?   @map("Memo01") @db.NVarChar(Max)
 886 |   memo02     String?   @map("Memo02") @db.NVarChar(Max)
 887 |   memo03     String?   @map("Memo03") @db.NVarChar(Max)
 888 |   memo04     String?   @map("Memo04") @db.NVarChar(Max)
 889 |   memo05     String?   @map("Memo05") @db.NVarChar(Max)
 890 |   memo06     String?   @map("Memo06") @db.NVarChar(Max)
 891 |   memo07     String?   @map("Memo07") @db.NVarChar(Max)
 892 |   memo08     String?   @map("Memo08") @db.NVarChar(Max)
 893 |   memo09     String?   @map("Memo09") @db.NVarChar(Max)
 894 |   memo10     String?   @map("Memo10") @db.NVarChar(Max)
 895 |   memo11     String?   @map("Memo11") @db.NVarChar(Max)
 896 |   memo12     String?   @map("Memo12") @db.NVarChar(Max)
 897 |   memo13     String?   @map("Memo13") @db.NVarChar(Max)
 898 |   memo14     String?   @map("Memo14") @db.NVarChar(Max)
 899 |   memo15     String?   @map("Memo15") @db.NVarChar(Max)
 900 |   memo16     String?   @map("Memo16") @db.NVarChar(Max)
 901 |   memo17     String?   @map("Memo17") @db.NVarChar(Max)
 902 |   memo18     String?   @map("Memo18") @db.NVarChar(Max)
 903 |   memo19     String?   @map("Memo19") @db.NVarChar(Max)
 904 |   memo20     String?   @map("Memo20") @db.NVarChar(Max)
 905 |   checkBox01 String?   @map("CheckBox01") @db.NVarChar(Max)
 906 |   checkBox02 String?   @map("CheckBox02") @db.NVarChar(Max)
 907 |   checkBox03 String?   @map("CheckBox03") @db.NVarChar(Max)
 908 |   checkBox04 String?   @map("CheckBox04") @db.NVarChar(Max)
 909 |   checkBox05 String?   @map("CheckBox05") @db.NVarChar(Max)
 910 |   checkBox06 String?   @map("CheckBox06") @db.NVarChar(Max)
 911 |   checkBox07 String?   @map("CheckBox07") @db.NVarChar(Max)
 912 |   checkBox08 String?   @map("CheckBox08") @db.NVarChar(Max)
 913 |   checkBox09 String?   @map("CheckBox09") @db.NVarChar(Max)
 914 |   checkBox10 String?   @map("CheckBox10") @db.NVarChar(Max)
 915 |   checkBox11 String?   @map("CheckBox11") @db.NVarChar(Max)
 916 |   checkBox12 String?   @map("CheckBox12") @db.NVarChar(Max)
 917 |   checkBox13 String?   @map("CheckBox13") @db.NVarChar(Max)
 918 |   checkBox14 String?   @map("CheckBox14") @db.NVarChar(Max)
 919 |   checkBox15 String?   @map("CheckBox15") @db.NVarChar(Max)
 920 |   checkBox16 String?   @map("CheckBox16") @db.NVarChar(Max)
 921 |   checkBox17 String?   @map("CheckBox17") @db.NVarChar(Max)
 922 |   checkBox18 String?   @map("CheckBox18") @db.NVarChar(Max)
 923 |   checkBox19 String?   @map("CheckBox19") @db.NVarChar(Max)
 924 |   checkBox20 String?   @map("CheckBox20") @db.NVarChar(Max)
 925 |   select01   String?   @map("Select01") @db.NVarChar(Max)
 926 |   select02   String?   @map("Select02") @db.NVarChar(Max)
 927 |   select03   String?   @map("Select03") @db.NVarChar(Max)
 928 |   select04   String?   @map("Select04") @db.NVarChar(Max)
 929 |   select05   String?   @map("Select05") @db.NVarChar(Max)
 930 |   select06   String?   @map("Select06") @db.NVarChar(Max)
 931 |   select07   String?   @map("Select07") @db.NVarChar(Max)
 932 |   select08   String?   @map("Select08") @db.NVarChar(Max)
 933 |   select09   String?   @map("Select09") @db.NVarChar(Max)
 934 |   select10   String?   @map("Select10") @db.NVarChar(Max)
 935 |   select11   String?   @map("Select11") @db.NVarChar(Max)
 936 |   select12   String?   @map("Select12") @db.NVarChar(Max)
 937 |   select13   String?   @map("Select13") @db.NVarChar(Max)
 938 |   select14   String?   @map("Select14") @db.NVarChar(Max)
 939 |   select15   String?   @map("Select15") @db.NVarChar(Max)
 940 |   select16   String?   @map("Select16") @db.NVarChar(Max)
 941 |   select17   String?   @map("Select17") @db.NVarChar(Max)
 942 |   select18   String?   @map("Select18") @db.NVarChar(Max)
 943 |   select19   String?   @map("Select19") @db.NVarChar(Max)
 944 |   select20   String?   @map("Select20") @db.NVarChar(Max)
 945 |   int01      Int?      @map("Int01")
 946 |   int02      Int?      @map("Int02")
 947 |   int03      Int?      @map("Int03")
 948 |   int04      Int?      @map("Int04")
 949 |   int05      Int?      @map("Int05")
 950 |   int06      Int?      @map("Int06")
 951 |   int07      Int?      @map("Int07")
 952 |   int08      Int?      @map("Int08")
 953 |   int09      Int?      @map("Int09")
 954 |   int10      Int?      @map("Int10")
 955 |   int11      Int?      @map("Int11")
 956 |   int12      Int?      @map("Int12")
 957 |   int13      Int?      @map("Int13")
 958 |   int14      Int?      @map("Int14")
 959 |   int15      Int?      @map("Int15")
 960 |   int16      Int?      @map("Int16")
 961 |   int17      Int?      @map("Int17")
 962 |   int18      Int?      @map("Int18")
 963 |   int19      Int?      @map("Int19")
 964 |   int20      Int?      @map("Int20")
 965 |   double01   Decimal?  @map("Double01") @db.Decimal(18, 8)
 966 |   double02   Decimal?  @map("Double02") @db.Decimal(18, 8)
 967 |   double03   Decimal?  @map("Double03") @db.Decimal(18, 8)
 968 |   double04   Decimal?  @map("Double04") @db.Decimal(18, 8)
 969 |   double05   Decimal?  @map("Double05") @db.Decimal(18, 8)
 970 |   double06   Decimal?  @map("Double06") @db.Decimal(18, 8)
 971 |   double07   Decimal?  @map("Double07") @db.Decimal(18, 8)
 972 |   double08   Decimal?  @map("Double08") @db.Decimal(18, 8)
 973 |   double09   Decimal?  @map("Double09") @db.Decimal(18, 8)
 974 |   double10   Decimal?  @map("Double10") @db.Decimal(18, 8)
 975 |   double11   Decimal?  @map("Double11") @db.Decimal(18, 8)
 976 |   double12   Decimal?  @map("Double12") @db.Decimal(18, 8)
 977 |   double13   Decimal?  @map("Double13") @db.Decimal(18, 8)
 978 |   double14   Decimal?  @map("Double14") @db.Decimal(18, 8)
 979 |   double15   Decimal?  @map("Double15") @db.Decimal(18, 8)
 980 |   double16   Decimal?  @map("Double16") @db.Decimal(18, 8)
 981 |   double17   Decimal?  @map("Double17") @db.Decimal(18, 8)
 982 |   double18   Decimal?  @map("Double18") @db.Decimal(18, 8)
 983 |   double19   Decimal?  @map("Double19") @db.Decimal(18, 8)
 984 |   double20   Decimal?  @map("Double20") @db.Decimal(18, 8)
 985 |   date01     DateTime? @map("Date01") @db.DateTime
 986 |   date02     DateTime? @map("Date02") @db.DateTime
 987 |   date03     DateTime? @map("Date03") @db.DateTime
 988 |   date04     DateTime? @map("Date04") @db.DateTime
 989 |   date05     DateTime? @map("Date05") @db.DateTime
 990 |   date06     DateTime? @map("Date06") @db.DateTime
 991 |   date07     DateTime? @map("Date07") @db.DateTime
 992 |   date08     DateTime? @map("Date08") @db.DateTime
 993 |   date09     DateTime? @map("Date09") @db.DateTime
 994 |   date10     DateTime? @map("Date10") @db.DateTime
 995 |   radio01    String?   @map("Radio01") @db.NVarChar(450)
 996 |   radio02    String?   @map("Radio02") @db.NVarChar(450)
 997 |   radio03    String?   @map("Radio03") @db.NVarChar(450)
 998 |   radio04    String?   @map("Radio04") @db.NVarChar(450)
 999 |   radio05    String?   @map("Radio05") @db.NVarChar(450)
1000 |   radio06    String?   @map("Radio06") @db.NVarChar(450)
1001 |   radio07    String?   @map("Radio07") @db.NVarChar(450)
1002 |   radio08    String?   @map("Radio08") @db.NVarChar(450)
1003 |   radio09    String?   @map("Radio09") @db.NVarChar(450)
1004 |   radio10    String?   @map("Radio10") @db.NVarChar(450)
1005 |   txt21      String?   @map("Txt21") @db.NVarChar(Max)
1006 |   txt22      String?   @map("Txt22") @db.NVarChar(Max)
1007 |   txt23      String?   @map("Txt23") @db.NVarChar(Max)
1008 |   txt24      String?   @map("Txt24") @db.NVarChar(Max)
1009 |   txt25      String?   @map("Txt25") @db.NVarChar(Max)
1010 |   txt26      String?   @map("Txt26") @db.NVarChar(Max)
1011 |   txt27      String?   @map("Txt27") @db.NVarChar(Max)
1012 |   txt28      String?   @map("Txt28") @db.NVarChar(Max)
1013 |   txt29      String?   @map("Txt29") @db.NVarChar(Max)
1014 |   txt30      String?   @map("Txt30") @db.NVarChar(Max)
1015 |   txt31      String?   @map("Txt31") @db.NVarChar(450)
1016 |   txt32      String?   @map("Txt32") @db.NVarChar(450)
1017 |   txt33      String?   @map("Txt33") @db.NVarChar(450)
1018 |   txt34      String?   @map("Txt34") @db.NVarChar(450)
1019 |   txt35      String?   @map("Txt35") @db.NVarChar(450)
1020 |   contract   Contract  @relation(fields: [contractId], references: [contractId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractCustomizedField_Contract")
1021 | 
1022 |   @@index([date01], map: "IX_ContractCustomizedField_Date01")
1023 |   @@index([date02], map: "IX_ContractCustomizedField_Date02")
1024 |   @@index([date03], map: "IX_ContractCustomizedField_Date03")
1025 |   @@index([date04], map: "IX_ContractCustomizedField_Date04")
1026 |   @@index([date05], map: "IX_ContractCustomizedField_Date05")
1027 |   @@index([date06], map: "IX_ContractCustomizedField_Date06")
1028 |   @@index([date07], map: "IX_ContractCustomizedField_Date07")
1029 |   @@index([date08], map: "IX_ContractCustomizedField_Date08")
1030 |   @@index([date09], map: "IX_ContractCustomizedField_Date09")
1031 |   @@index([date10], map: "IX_ContractCustomizedField_Date10")
1032 |   @@index([double01], map: "IX_ContractCustomizedField_Double01")
1033 |   @@index([double02], map: "IX_ContractCustomizedField_Double02")
1034 |   @@index([double03], map: "IX_ContractCustomizedField_Double03")
1035 |   @@index([double04], map: "IX_ContractCustomizedField_Double04")
1036 |   @@index([double05], map: "IX_ContractCustomizedField_Double05")
1037 |   @@index([double06], map: "IX_ContractCustomizedField_Double06")
1038 |   @@index([double07], map: "IX_ContractCustomizedField_Double07")
1039 |   @@index([double08], map: "IX_ContractCustomizedField_Double08")
1040 |   @@index([double09], map: "IX_ContractCustomizedField_Double09")
1041 |   @@index([double10], map: "IX_ContractCustomizedField_Double10")
1042 |   @@index([double11], map: "IX_ContractCustomizedField_Double11")
1043 |   @@index([double12], map: "IX_ContractCustomizedField_Double12")
1044 |   @@index([double13], map: "IX_ContractCustomizedField_Double13")
1045 |   @@index([double14], map: "IX_ContractCustomizedField_Double14")
1046 |   @@index([double15], map: "IX_ContractCustomizedField_Double15")
1047 |   @@index([double16], map: "IX_ContractCustomizedField_Double16")
1048 |   @@index([double17], map: "IX_ContractCustomizedField_Double17")
1049 |   @@index([double18], map: "IX_ContractCustomizedField_Double18")
1050 |   @@index([double19], map: "IX_ContractCustomizedField_Double19")
1051 |   @@index([double20], map: "IX_ContractCustomizedField_Double20")
1052 |   @@index([int01], map: "IX_ContractCustomizedField_Int01")
1053 |   @@index([int02], map: "IX_ContractCustomizedField_Int02")
1054 |   @@index([int03], map: "IX_ContractCustomizedField_Int03")
1055 |   @@index([int04], map: "IX_ContractCustomizedField_Int04")
1056 |   @@index([int05], map: "IX_ContractCustomizedField_Int05")
1057 |   @@index([int06], map: "IX_ContractCustomizedField_Int06")
1058 |   @@index([int07], map: "IX_ContractCustomizedField_Int07")
1059 |   @@index([int08], map: "IX_ContractCustomizedField_Int08")
1060 |   @@index([int09], map: "IX_ContractCustomizedField_Int09")
1061 |   @@index([int10], map: "IX_ContractCustomizedField_Int10")
1062 |   @@index([int11], map: "IX_ContractCustomizedField_Int11")
1063 |   @@index([int12], map: "IX_ContractCustomizedField_Int12")
1064 |   @@index([int13], map: "IX_ContractCustomizedField_Int13")
1065 |   @@index([int14], map: "IX_ContractCustomizedField_Int14")
1066 |   @@index([int15], map: "IX_ContractCustomizedField_Int15")
1067 |   @@index([int16], map: "IX_ContractCustomizedField_Int16")
1068 |   @@index([int17], map: "IX_ContractCustomizedField_Int17")
1069 |   @@index([int18], map: "IX_ContractCustomizedField_Int18")
1070 |   @@index([int19], map: "IX_ContractCustomizedField_Int19")
1071 |   @@index([int20], map: "IX_ContractCustomizedField_Int20")
1072 |   @@index([radio01], map: "IX_ContractCustomizedField_Radio01")
1073 |   @@index([radio02], map: "IX_ContractCustomizedField_Radio02")
1074 |   @@index([radio03], map: "IX_ContractCustomizedField_Radio03")
1075 |   @@index([radio04], map: "IX_ContractCustomizedField_Radio04")
1076 |   @@index([radio05], map: "IX_ContractCustomizedField_Radio05")
1077 |   @@index([radio06], map: "IX_ContractCustomizedField_Radio06")
1078 |   @@index([radio07], map: "IX_ContractCustomizedField_Radio07")
1079 |   @@index([radio08], map: "IX_ContractCustomizedField_Radio08")
1080 |   @@index([radio09], map: "IX_ContractCustomizedField_Radio09")
1081 |   @@index([radio10], map: "IX_ContractCustomizedField_Radio10")
1082 |   @@index([txt31], map: "IX_ContractCustomizedField_Txt31")
1083 |   @@index([txt32], map: "IX_ContractCustomizedField_Txt32")
1084 |   @@index([txt33], map: "IX_ContractCustomizedField_Txt33")
1085 |   @@index([txt34], map: "IX_ContractCustomizedField_Txt34")
1086 |   @@index([txt35], map: "IX_ContractCustomizedField_Txt35")
1087 |   @@schema("join")
1088 | }
1089 | 
1090 | model ContractCustomizedFieldForSearch {
1091 |   contractId                            Int                               @id(map: "PK_ContractCustomizedFieldViewTemp") @map("ContractId")
1092 |   txt01                                 String?                           @map("Txt01") @db.NVarChar(450)
1093 |   txt02                                 String?                           @map("Txt02") @db.NVarChar(450)
1094 |   txt03                                 String?                           @map("Txt03") @db.NVarChar(450)
1095 |   txt04                                 String?                           @map("Txt04") @db.NVarChar(450)
1096 |   txt05                                 String?                           @map("Txt05") @db.NVarChar(450)
1097 |   txt06                                 String?                           @map("Txt06") @db.NVarChar(450)
1098 |   txt07                                 String?                           @map("Txt07") @db.NVarChar(450)
1099 |   txt08                                 String?                           @map("Txt08") @db.NVarChar(450)
1100 |   txt09                                 String?                           @map("Txt09") @db.NVarChar(450)
1101 |   txt10                                 String?                           @map("Txt10") @db.NVarChar(450)
1102 |   txt11                                 String?                           @map("Txt11") @db.NVarChar(450)
1103 |   txt12                                 String?                           @map("Txt12") @db.NVarChar(450)
1104 |   txt13                                 String?                           @map("Txt13") @db.NVarChar(450)
1105 |   txt14                                 String?                           @map("Txt14") @db.NVarChar(450)
1106 |   txt15                                 String?                           @map("Txt15") @db.NVarChar(450)
1107 |   txt16                                 String?                           @map("Txt16") @db.NVarChar(450)
1108 |   txt17                                 String?                           @map("Txt17") @db.NVarChar(450)
1109 |   txt18                                 String?                           @map("Txt18") @db.NVarChar(450)
1110 |   txt19                                 String?                           @map("Txt19") @db.NVarChar(450)
1111 |   txt20                                 String?                           @map("Txt20") @db.NVarChar(450)
1112 |   memo01                                String?                           @map("Memo01") @db.NVarChar(Max)
1113 |   memo02                                String?                           @map("Memo02") @db.NVarChar(Max)
1114 |   memo03                                String?                           @map("Memo03") @db.NVarChar(Max)
1115 |   memo04                                String?                           @map("Memo04") @db.NVarChar(Max)
1116 |   memo05                                String?                           @map("Memo05") @db.NVarChar(Max)
1117 |   memo06                                String?                           @map("Memo06") @db.NVarChar(Max)
1118 |   memo07                                String?                           @map("Memo07") @db.NVarChar(Max)
1119 |   memo08                                String?                           @map("Memo08") @db.NVarChar(Max)
1120 |   memo09                                String?                           @map("Memo09") @db.NVarChar(Max)
1121 |   memo10                                String?                           @map("Memo10") @db.NVarChar(Max)
1122 |   memo11                                String?                           @map("Memo11") @db.NVarChar(Max)
1123 |   memo12                                String?                           @map("Memo12") @db.NVarChar(Max)
1124 |   memo13                                String?                           @map("Memo13") @db.NVarChar(Max)
1125 |   memo14                                String?                           @map("Memo14") @db.NVarChar(Max)
1126 |   memo15                                String?                           @map("Memo15") @db.NVarChar(Max)
1127 |   memo16                                String?                           @map("Memo16") @db.NVarChar(Max)
1128 |   memo17                                String?                           @map("Memo17") @db.NVarChar(Max)
1129 |   memo18                                String?                           @map("Memo18") @db.NVarChar(Max)
1130 |   memo19                                String?                           @map("Memo19") @db.NVarChar(Max)
1131 |   memo20                                String?                           @map("Memo20") @db.NVarChar(Max)
1132 |   checkBox01                            String?                           @map("CheckBox01") @db.NVarChar(Max)
1133 |   checkBox02                            String?                           @map("CheckBox02") @db.NVarChar(Max)
1134 |   checkBox03                            String?                           @map("CheckBox03") @db.NVarChar(Max)
1135 |   checkBox04                            String?                           @map("CheckBox04") @db.NVarChar(Max)
1136 |   checkBox05                            String?                           @map("CheckBox05") @db.NVarChar(Max)
1137 |   checkBox06                            String?                           @map("CheckBox06") @db.NVarChar(Max)
1138 |   checkBox07                            String?                           @map("CheckBox07") @db.NVarChar(Max)
1139 |   checkBox08                            String?                           @map("CheckBox08") @db.NVarChar(Max)
1140 |   checkBox09                            String?                           @map("CheckBox09") @db.NVarChar(Max)
1141 |   checkBox10                            String?                           @map("CheckBox10") @db.NVarChar(Max)
1142 |   checkBox11                            String?                           @map("CheckBox11") @db.NVarChar(Max)
1143 |   checkBox12                            String?                           @map("CheckBox12") @db.NVarChar(Max)
1144 |   checkBox13                            String?                           @map("CheckBox13") @db.NVarChar(Max)
1145 |   checkBox14                            String?                           @map("CheckBox14") @db.NVarChar(Max)
1146 |   checkBox15                            String?                           @map("CheckBox15") @db.NVarChar(Max)
1147 |   checkBox16                            String?                           @map("CheckBox16") @db.NVarChar(Max)
1148 |   checkBox17                            String?                           @map("CheckBox17") @db.NVarChar(Max)
1149 |   checkBox18                            String?                           @map("CheckBox18") @db.NVarChar(Max)
1150 |   checkBox19                            String?                           @map("CheckBox19") @db.NVarChar(Max)
1151 |   checkBox20                            String?                           @map("CheckBox20") @db.NVarChar(Max)
1152 |   select01                              String?                           @map("Select01") @db.NVarChar(Max)
1153 |   select02                              String?                           @map("Select02") @db.NVarChar(Max)
1154 |   select03                              String?                           @map("Select03") @db.NVarChar(Max)
1155 |   select04                              String?                           @map("Select04") @db.NVarChar(Max)
1156 |   select05                              String?                           @map("Select05") @db.NVarChar(Max)
1157 |   select06                              String?                           @map("Select06") @db.NVarChar(Max)
1158 |   select07                              String?                           @map("Select07") @db.NVarChar(Max)
1159 |   select08                              String?                           @map("Select08") @db.NVarChar(Max)
1160 |   select09                              String?                           @map("Select09") @db.NVarChar(Max)
1161 |   select10                              String?                           @map("Select10") @db.NVarChar(Max)
1162 |   select11                              String?                           @map("Select11") @db.NVarChar(Max)
1163 |   select12                              String?                           @map("Select12") @db.NVarChar(Max)
1164 |   select13                              String?                           @map("Select13") @db.NVarChar(Max)
1165 |   select14                              String?                           @map("Select14") @db.NVarChar(Max)
1166 |   select15                              String?                           @map("Select15") @db.NVarChar(Max)
1167 |   select16                              String?                           @map("Select16") @db.NVarChar(Max)
1168 |   select17                              String?                           @map("Select17") @db.NVarChar(Max)
1169 |   select18                              String?                           @map("Select18") @db.NVarChar(Max)
1170 |   select19                              String?                           @map("Select19") @db.NVarChar(Max)
1171 |   select20                              String?                           @map("Select20") @db.NVarChar(Max)
1172 |   int01                                 Int?                              @map("Int01")
1173 |   int02                                 Int?                              @map("Int02")
1174 |   int03                                 Int?                              @map("Int03")
1175 |   int04                                 Int?                              @map("Int04")
1176 |   int05                                 Int?                              @map("Int05")
1177 |   int06                                 Int?                              @map("Int06")
1178 |   int07                                 Int?                              @map("Int07")
1179 |   int08                                 Int?                              @map("Int08")
1180 |   int09                                 Int?                              @map("Int09")
1181 |   int10                                 Int?                              @map("Int10")
1182 |   int11                                 Int?                              @map("Int11")
1183 |   int12                                 Int?                              @map("Int12")
1184 |   int13                                 Int?                              @map("Int13")
1185 |   int14                                 Int?                              @map("Int14")
1186 |   int15                                 Int?                              @map("Int15")
1187 |   int16                                 Int?                              @map("Int16")
1188 |   int17                                 Int?                              @map("Int17")
1189 |   int18                                 Int?                              @map("Int18")
1190 |   int19                                 Int?                              @map("Int19")
1191 |   int20                                 Int?                              @map("Int20")
1192 |   double01                              Decimal?                          @map("Double01") @db.Decimal(18, 8)
1193 |   double02                              Decimal?                          @map("Double02") @db.Decimal(18, 8)
1194 |   double03                              Decimal?                          @map("Double03") @db.Decimal(18, 8)
1195 |   double04                              Decimal?                          @map("Double04") @db.Decimal(18, 8)
1196 |   double05                              Decimal?                          @map("Double05") @db.Decimal(18, 8)
1197 |   double06                              Decimal?                          @map("Double06") @db.Decimal(18, 8)
1198 |   double07                              Decimal?                          @map("Double07") @db.Decimal(18, 8)
1199 |   double08                              Decimal?                          @map("Double08") @db.Decimal(18, 8)
1200 |   double09                              Decimal?                          @map("Double09") @db.Decimal(18, 8)
1201 |   double10                              Decimal?                          @map("Double10") @db.Decimal(18, 8)
1202 |   double11                              Decimal?                          @map("Double11") @db.Decimal(18, 8)
1203 |   double12                              Decimal?                          @map("Double12") @db.Decimal(18, 8)
1204 |   double13                              Decimal?                          @map("Double13") @db.Decimal(18, 8)
1205 |   double14                              Decimal?                          @map("Double14") @db.Decimal(18, 8)
1206 |   double15                              Decimal?                          @map("Double15") @db.Decimal(18, 8)
1207 |   double16                              Decimal?                          @map("Double16") @db.Decimal(18, 8)
1208 |   double17                              Decimal?                          @map("Double17") @db.Decimal(18, 8)
1209 |   double18                              Decimal?                          @map("Double18") @db.Decimal(18, 8)
1210 |   double19                              Decimal?                          @map("Double19") @db.Decimal(18, 8)
1211 |   double20                              Decimal?                          @map("Double20") @db.Decimal(18, 8)
1212 |   date01                                DateTime?                         @map("Date01") @db.DateTime
1213 |   date02                                DateTime?                         @map("Date02") @db.DateTime
1214 |   date03                                DateTime?                         @map("Date03") @db.DateTime
1215 |   date04                                DateTime?                         @map("Date04") @db.DateTime
1216 |   date05                                DateTime?                         @map("Date05") @db.DateTime
1217 |   date06                                DateTime?                         @map("Date06") @db.DateTime
1218 |   date07                                DateTime?                         @map("Date07") @db.DateTime
1219 |   date08                                DateTime?                         @map("Date08") @db.DateTime
1220 |   date09                                DateTime?                         @map("Date09") @db.DateTime
1221 |   date10                                DateTime?                         @map("Date10") @db.DateTime
1222 |   radio01                               String?                           @map("Radio01") @db.NVarChar(450)
1223 |   radio02                               String?                           @map("Radio02") @db.NVarChar(450)
1224 |   radio03                               String?                           @map("Radio03") @db.NVarChar(450)
1225 |   radio04                               String?                           @map("Radio04") @db.NVarChar(450)
1226 |   radio05                               String?                           @map("Radio05") @db.NVarChar(450)
1227 |   radio06                               String?                           @map("Radio06") @db.NVarChar(450)
1228 |   radio07                               String?                           @map("Radio07") @db.NVarChar(450)
1229 |   radio08                               String?                           @map("Radio08") @db.NVarChar(450)
1230 |   radio09                               String?                           @map("Radio09") @db.NVarChar(450)
1231 |   radio10                               String?                           @map("Radio10") @db.NVarChar(450)
1232 |   txt21                                 String?                           @map("Txt21") @db.NVarChar(450)
1233 |   txt22                                 String?                           @map("Txt22") @db.NVarChar(450)
1234 |   txt23                                 String?                           @map("Txt23") @db.NVarChar(450)
1235 |   txt24                                 String?                           @map("Txt24") @db.NVarChar(450)
1236 |   txt25                                 String?                           @map("Txt25") @db.NVarChar(450)
1237 |   txt26                                 String?                           @map("Txt26") @db.NVarChar(450)
1238 |   txt27                                 String?                           @map("Txt27") @db.NVarChar(450)
1239 |   txt28                                 String?                           @map("Txt28") @db.NVarChar(450)
1240 |   txt29                                 String?                           @map("Txt29") @db.NVarChar(450)
1241 |   txt30                                 String?                           @map("Txt30") @db.NVarChar(450)
1242 |   txt31                                 String?                           @map("Txt31") @db.NVarChar(450)
1243 |   txt32                                 String?                           @map("Txt32") @db.NVarChar(450)
1244 |   txt33                                 String?                           @map("Txt33") @db.NVarChar(450)
1245 |   txt34                                 String?                           @map("Txt34") @db.NVarChar(450)
1246 |   txt35                                 String?                           @map("Txt35") @db.NVarChar(450)
1247 |   contractCustomizedFieldForSearch      ContractCustomizedFieldForSearch  @relation("ContractCustomizedFieldForSearchToContractCustomizedFieldForSearch", fields: [contractId], references: [contractId], onUpdate: NoAction, map: "FK_ContractCustomizedFieldViewTemp_ContractCustomizedField")
1248 |   otherContractCustomizedFieldForSearch ContractCustomizedFieldForSearch? @relation("ContractCustomizedFieldForSearchToContractCustomizedFieldForSearch")
1249 | 
1250 |   @@index([date01], map: "IX_ContractCustomizedFieldForSearch_Date01")
1251 |   @@index([date02], map: "IX_ContractCustomizedFieldForSearch_Date02")
1252 |   @@index([date03], map: "IX_ContractCustomizedFieldForSearch_Date03")
1253 |   @@index([date04], map: "IX_ContractCustomizedFieldForSearch_Date04")
1254 |   @@index([date05], map: "IX_ContractCustomizedFieldForSearch_Date05")
1255 |   @@index([date06], map: "IX_ContractCustomizedFieldForSearch_Date06")
1256 |   @@index([date07], map: "IX_ContractCustomizedFieldForSearch_Date07")
1257 |   @@index([date08], map: "IX_ContractCustomizedFieldForSearch_Date08")
1258 |   @@index([date09], map: "IX_ContractCustomizedFieldForSearch_Date09")
1259 |   @@index([date10], map: "IX_ContractCustomizedFieldForSearch_Date10")
1260 |   @@index([double01], map: "IX_ContractCustomizedFieldForSearch_Double01")
1261 |   @@index([double02], map: "IX_ContractCustomizedFieldForSearch_Double02")
1262 |   @@index([double03], map: "IX_ContractCustomizedFieldForSearch_Double03")
1263 |   @@index([double04], map: "IX_ContractCustomizedFieldForSearch_Double04")
1264 |   @@index([double05], map: "IX_ContractCustomizedFieldForSearch_Double05")
1265 |   @@index([double06], map: "IX_ContractCustomizedFieldForSearch_Double06")
1266 |   @@index([double07], map: "IX_ContractCustomizedFieldForSearch_Double07")
1267 |   @@index([double08], map: "IX_ContractCustomizedFieldForSearch_Double08")
1268 |   @@index([double09], map: "IX_ContractCustomizedFieldForSearch_Double09")
1269 |   @@index([double10], map: "IX_ContractCustomizedFieldForSearch_Double10")
1270 |   @@index([double11], map: "IX_ContractCustomizedFieldForSearch_Double11")
1271 |   @@index([double12], map: "IX_ContractCustomizedFieldForSearch_Double12")
1272 |   @@index([double13], map: "IX_ContractCustomizedFieldForSearch_Double13")
1273 |   @@index([double14], map: "IX_ContractCustomizedFieldForSearch_Double14")
1274 |   @@index([double15], map: "IX_ContractCustomizedFieldForSearch_Double15")
1275 |   @@index([double16], map: "IX_ContractCustomizedFieldForSearch_Double16")
1276 |   @@index([double17], map: "IX_ContractCustomizedFieldForSearch_Double17")
1277 |   @@index([double18], map: "IX_ContractCustomizedFieldForSearch_Double18")
1278 |   @@index([double19], map: "IX_ContractCustomizedFieldForSearch_Double19")
1279 |   @@index([double20], map: "IX_ContractCustomizedFieldForSearch_Double20")
1280 |   @@index([int01], map: "IX_ContractCustomizedFieldForSearch_Int01")
1281 |   @@index([int02], map: "IX_ContractCustomizedFieldForSearch_Int02")
1282 |   @@index([int03], map: "IX_ContractCustomizedFieldForSearch_Int03")
1283 |   @@index([int04], map: "IX_ContractCustomizedFieldForSearch_Int04")
1284 |   @@index([int05], map: "IX_ContractCustomizedFieldForSearch_Int05")
1285 |   @@index([int06], map: "IX_ContractCustomizedFieldForSearch_Int06")
1286 |   @@index([int07], map: "IX_ContractCustomizedFieldForSearch_Int07")
1287 |   @@index([int08], map: "IX_ContractCustomizedFieldForSearch_Int08")
1288 |   @@index([int09], map: "IX_ContractCustomizedFieldForSearch_Int09")
1289 |   @@index([int10], map: "IX_ContractCustomizedFieldForSearch_Int10")
1290 |   @@index([int11], map: "IX_ContractCustomizedFieldForSearch_Int11")
1291 |   @@index([int12], map: "IX_ContractCustomizedFieldForSearch_Int12")
1292 |   @@index([int13], map: "IX_ContractCustomizedFieldForSearch_Int13")
1293 |   @@index([int14], map: "IX_ContractCustomizedFieldForSearch_Int14")
1294 |   @@index([int15], map: "IX_ContractCustomizedFieldForSearch_Int15")
1295 |   @@index([int16], map: "IX_ContractCustomizedFieldForSearch_Int16")
1296 |   @@index([int17], map: "IX_ContractCustomizedFieldForSearch_Int17")
1297 |   @@index([int18], map: "IX_ContractCustomizedFieldForSearch_Int18")
1298 |   @@index([int19], map: "IX_ContractCustomizedFieldForSearch_Int19")
1299 |   @@index([int20], map: "IX_ContractCustomizedFieldForSearch_Int20")
1300 |   @@index([radio01], map: "IX_ContractCustomizedFieldForSearch_Radio01")
1301 |   @@index([radio02], map: "IX_ContractCustomizedFieldForSearch_Radio02")
1302 |   @@index([radio03], map: "IX_ContractCustomizedFieldForSearch_Radio03")
1303 |   @@index([radio04], map: "IX_ContractCustomizedFieldForSearch_Radio04")
1304 |   @@index([radio05], map: "IX_ContractCustomizedFieldForSearch_Radio05")
1305 |   @@index([radio06], map: "IX_ContractCustomizedFieldForSearch_Radio06")
1306 |   @@index([radio07], map: "IX_ContractCustomizedFieldForSearch_Radio07")
1307 |   @@index([radio08], map: "IX_ContractCustomizedFieldForSearch_Radio08")
1308 |   @@index([radio09], map: "IX_ContractCustomizedFieldForSearch_Radio09")
1309 |   @@index([radio10], map: "IX_ContractCustomizedFieldForSearch_Radio10")
1310 |   @@index([txt01], map: "IX_ContractCustomizedFieldForSearch_Txt01")
1311 |   @@index([txt02], map: "IX_ContractCustomizedFieldForSearch_Txt02")
1312 |   @@index([txt03], map: "IX_ContractCustomizedFieldForSearch_Txt03")
1313 |   @@index([txt04], map: "IX_ContractCustomizedFieldForSearch_Txt04")
1314 |   @@index([txt05], map: "IX_ContractCustomizedFieldForSearch_Txt05")
1315 |   @@index([txt06], map: "IX_ContractCustomizedFieldForSearch_Txt06")
1316 |   @@index([txt07], map: "IX_ContractCustomizedFieldForSearch_Txt07")
1317 |   @@index([txt08], map: "IX_ContractCustomizedFieldForSearch_Txt08")
1318 |   @@index([txt09], map: "IX_ContractCustomizedFieldForSearch_Txt09")
1319 |   @@index([txt10], map: "IX_ContractCustomizedFieldForSearch_Txt10")
1320 |   @@index([txt11], map: "IX_ContractCustomizedFieldForSearch_Txt11")
1321 |   @@index([txt12], map: "IX_ContractCustomizedFieldForSearch_Txt12")
1322 |   @@index([txt13], map: "IX_ContractCustomizedFieldForSearch_Txt13")
1323 |   @@index([txt14], map: "IX_ContractCustomizedFieldForSearch_Txt14")
1324 |   @@index([txt15], map: "IX_ContractCustomizedFieldForSearch_Txt15")
1325 |   @@index([txt16], map: "IX_ContractCustomizedFieldForSearch_Txt16")
1326 |   @@index([txt17], map: "IX_ContractCustomizedFieldForSearch_Txt17")
1327 |   @@index([txt18], map: "IX_ContractCustomizedFieldForSearch_Txt18")
1328 |   @@index([txt19], map: "IX_ContractCustomizedFieldForSearch_Txt19")
1329 |   @@index([txt20], map: "IX_ContractCustomizedFieldForSearch_Txt20")
1330 |   @@index([txt21], map: "IX_ContractCustomizedFieldForSearch_Txt21")
1331 |   @@index([txt23], map: "IX_ContractCustomizedFieldForSearch_Txt22")
1332 |   @@index([txt23], map: "IX_ContractCustomizedFieldForSearch_Txt23")
1333 |   @@index([txt24], map: "IX_ContractCustomizedFieldForSearch_Txt24")
1334 |   @@index([txt25], map: "IX_ContractCustomizedFieldForSearch_Txt25")
1335 |   @@index([txt26], map: "IX_ContractCustomizedFieldForSearch_Txt26")
1336 |   @@index([txt27], map: "IX_ContractCustomizedFieldForSearch_Txt27")
1337 |   @@index([txt28], map: "IX_ContractCustomizedFieldForSearch_Txt28")
1338 |   @@index([txt29], map: "IX_ContractCustomizedFieldForSearch_Txt29")
1339 |   @@index([txt30], map: "IX_ContractCustomizedFieldForSearch_Txt30")
1340 |   @@index([txt31], map: "IX_ContractCustomizedFieldForSearch_Txt31")
1341 |   @@index([txt32], map: "IX_ContractCustomizedFieldForSearch_Txt32")
1342 |   @@index([txt33], map: "IX_ContractCustomizedFieldForSearch_Txt33")
1343 |   @@index([txt34], map: "IX_ContractCustomizedFieldForSearch_Txt34")
1344 |   @@index([txt35], map: "IX_ContractCustomizedFieldForSearch_Txt35")
1345 |   @@schema("join")
1346 | }
1347 | 
1348 | model ContractEnvelope {
1349 |   sn            Int          @id(map: "PK_ContractEnvelopes") @default(autoincrement())
1350 |   contractId    Int
1351 |   envelopesGuid String       @db.NVarChar(255)
1352 |   contract      Contract     @relation(fields: [contractId], references: [contractId], onUpdate: NoAction, map: "FK_ContractEnvelopes_Contract")
1353 |   envelopeInfo  EnvelopeInfo @relation(fields: [envelopesGuid], references: [envelopesGuid], onUpdate: NoAction, map: "FK_ContractEnvelopes_EnvelopeInfo")
1354 | 
1355 |   @@map("ContractEnvelopes")
1356 |   @@schema("dbo")
1357 | }
1358 | 
1359 | model ContractEvent {
1360 |   sn         Int       @id(map: "PK_Event_1") @default(autoincrement()) @map("Sn")
1361 |   eventId    Int?      @map("EventID")
1362 |   contractId Int?      @map("ContractID")
1363 |   contract   Contract? @relation(fields: [contractId], references: [contractId], onDelete: Cascade, map: "FK_Event_Contract")
1364 |   event      Event?    @relation(fields: [eventId], references: [eventId], onDelete: Cascade, map: "FK_Event_Event")
1365 | 
1366 |   @@index([contractId], map: "IX_ContractEvent_ContractID")
1367 |   @@index([eventId], map: "IX_ContractEvent_EventID")
1368 |   @@schema("join")
1369 | }
1370 | 
1371 | model ContractExaminer {
1372 |   sn                   Int                   @id(map: "PK_ContractExaminer") @default(autoincrement()) @map("Sn")
1373 |   contractId           Int                   @map("ContractID")
1374 |   examStageId          Int                   @map("ExamStageID")
1375 |   examStatusId         Int                   @map("ExamStatusID")
1376 |   userId               Int?                  @map("UserID")
1377 |   examMemo             String?               @map("ExamMemo") @db.NVarChar(Max)
1378 |   assignDate           DateTime?             @default(now(), map: "DF_ContractExaminer_AssignDate") @map("AssignDate") @db.DateTime
1379 |   examDate             DateTime?             @default(now(), map: "DF_ContractExaminer_ExamDate") @map("ExamDate") @db.DateTime
1380 |   reAssign             Boolean?              @default(false, map: "DF_ContractExaminer_ReExam") @map("ReAssign")
1381 |   type                 Int?                  @default(0, map: "DF_ContractExaminer_SignStage") @map("Type")
1382 |   signType             Int?                  @map("SignType")
1383 |   signer               String?               @map("Signer") @db.NVarChar(125)
1384 |   stayDate             DateTime?             @map("StayDate") @db.DateTime
1385 |   completeHour         Decimal?              @map("CompleteHours") @db.Decimal(10, 2)
1386 |   noticeOther          String?               @map("NoticeOthers") @db.NVarChar(Max)
1387 |   examSeq              Int                   @default(1, map: "DF_ContractExaminer_ExamSeq") @map("ExamSeq")
1388 |   examStageSeq         Int?                  @map("ExamStageSeq")
1389 |   contract             Contract              @relation(fields: [contractId], references: [contractId], onDelete: Cascade, map: "FK_ContractExaminer_Contract")
1390 |   examStage            ExamStage             @relation(fields: [examStageId], references: [examStageId], onDelete: Cascade, map: "FK_ContractExaminer_ExamStage")
1391 |   examStatus           ExamStatus            @relation(fields: [examStatusId], references: [examStatusId], onUpdate: NoAction, map: "FK_ContractExaminer_ExamStatus")
1392 |   user                 User?                 @relation(fields: [userId], references: [userId], onDelete: Cascade, map: "FK_ContractExaminer_User")
1393 |   otherExaminers       OtherExaminer[]
1394 |   otherExaminerConfigs OtherExaminerConfig[]
1395 | 
1396 |   @@index([sn], map: "IX_ContractExaminer")
1397 |   @@index([assignDate], map: "IX_ContractExaminer_AssignDate")
1398 |   @@index([completeHour], map: "IX_ContractExaminer_CompleteHours")
1399 |   @@index([contractId], map: "IX_ContractExaminer_ContractID")
1400 |   @@index([examDate], map: "IX_ContractExaminer_ExamDate")
1401 |   @@index([examSeq], map: "IX_ContractExaminer_ExamSeq")
1402 |   @@index([examStageId], map: "IX_ContractExaminer_ExamStageID")
1403 |   @@index([examStageSeq], map: "IX_ContractExaminer_ExamStageSeq")
1404 |   @@index([examStatusId], map: "IX_ContractExaminer_ExamStatusID")
1405 |   @@index([reAssign], map: "IX_ContractExaminer_ReAssign")
1406 |   @@index([signer], map: "IX_ContractExaminer_Signer")
1407 |   @@index([signType], map: "IX_ContractExaminer_SignType")
1408 |   @@index([sn], map: "IX_ContractExaminer_Sn")
1409 |   @@index([stayDate], map: "IX_ContractExaminer_StayDate")
1410 |   @@index([type], map: "IX_ContractExaminer_Type")
1411 |   @@index([userId], map: "IX_ContractExaminer_UserID")
1412 |   @@schema("data")
1413 | }
1414 | 
1415 | model ContractExamStageInfo {
1416 |   contractId                      Int      @id(map: "PK__Contract__C90D3409525B4127") @map("ContractID")
1417 |   attributionRight                Int?     @map("AttributionRights")
1418 |   attributionRightsText           String?  @map("AttributionRightsText") @db.NVarChar(Max)
1419 |   confidentialityRequirement      Int?     @map("ConfidentialityRequirements")
1420 |   confidentialityRequirementsText String?  @map("ConfidentialityRequirementsText") @db.NVarChar(Max)
1421 |   noInfringementGuarantee         Int?     @map("NoInfringementGuarantee")
1422 |   noInfringementGuaranteeText     String?  @map("NoInfringementGuaranteeText") @db.NVarChar(Max)
1423 |   infringementInvestigation       Int?     @map("InfringementInvestigation")
1424 |   infringementInvestigationText   String?  @map("InfringementInvestigationText") @db.NVarChar(Max)
1425 |   contract                        Contract @relation(fields: [contractId], references: [contractId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractExamStageInfo_ContractID")
1426 | 
1427 |   @@index([attributionRight], map: "IX_ContractExamStageInfo_AttributionRights")
1428 |   @@index([confidentialityRequirement], map: "IX_ContractExamStageInfo_ConfidentialityRequirements")
1429 |   @@index([infringementInvestigation], map: "IX_ContractExamStageInfo_InfringementInvestigation")
1430 |   @@index([noInfringementGuarantee], map: "IX_ContractExamStageInfo_NoInfringementGuarantee")
1431 |   @@schema("join")
1432 | }
1433 | 
1434 | model ContractExtendInfo {
1435 |   contractId             Int                @id(map: "PK_ContractExtendInfo") @map("ContractID")
1436 |   contractAccessTypeSn   Int                @map("ContractAccessTypeSN")
1437 |   contractAccessTypeMemo String?            @map("ContractAccessTypeMemo") @db.NVarChar(Max)
1438 |   accessStartDate        DateTime           @map("AccessStartDate") @db.DateTime
1439 |   accessEndDate          DateTime?          @map("AccessEndDate") @db.DateTime
1440 |   contractAccessDescript String?            @map("ContractAccessDescript") @db.NVarChar(Max)
1441 |   contractAccessReason   String?            @map("ContractAccessReason") @db.NVarChar(Max)
1442 |   searchStartDate        DateTime?          @map("SearchStartDate") @db.DateTime
1443 |   searchEndDate          DateTime?          @map("SearchEndDate") @db.DateTime
1444 |   recede                 Boolean?           @map("Recede")
1445 |   contract               Contract           @relation(fields: [contractId], references: [contractId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractExtendInfo_Contract")
1446 |   contractAccessType     ContractAccessType @relation(fields: [contractAccessTypeSn], references: [sn], onUpdate: NoAction, map: "FK_ContractExtendInfo_ContractAccessType")
1447 | 
1448 |   @@index([accessEndDate], map: "IX_ContractExtendInfo_AccessEndDate")
1449 |   @@index([accessStartDate], map: "IX_ContractExtendInfo_AccessStartDate")
1450 |   @@index([contractAccessTypeSn], map: "IX_ContractExtendInfo_ContractAccessTypeSN")
1451 |   @@index([searchEndDate], map: "IX_ContractExtendInfo_SearchEndDate")
1452 |   @@index([searchStartDate], map: "IX_ContractExtendInfo_SearchStartDate")
1453 |   @@schema("data")
1454 | }
1455 | 
1456 | model ContractFileTemplate {
1457 |   sn                                        Int                                       @id(map: "PK_ContractFileTemplate") @default(autoincrement()) @map("SN")
1458 |   templateName                              String                                    @map("TemplateName") @db.NVarChar(Max)
1459 |   contractFileTemplateTypeSn                Int                                       @map("ContractFileTemplateTypeSN")
1460 |   isOpen                                    Boolean                                   @default(true, map: "DF_ContractFileTemplate_IsOpen") @map("IsOpen")
1461 |   remark                                    String?                                   @map("Remark") @db.NVarChar(Max)
1462 |   userId                                    Int                                       @map("UserID")
1463 |   createDate                                DateTime                                  @default(now(), map: "DF_ContractFileTemplate_CreacteDate") @map("CreateDate") @db.DateTime
1464 |   isOnlineEditMode                          Boolean                                   @default(false, map: "DF_ContractFileTemplate_IsOnlineEditMode") @map("IsOnlineEditMode")
1465 |   contractFileTemplateType                  ContractFileTemplateType                  @relation(fields: [contractFileTemplateTypeSn], references: [sn], onUpdate: NoAction, map: "FK_ContractFileTemplate_ContractFileTemplateType")
1466 |   user                                      User                                      @relation(fields: [userId], references: [userId], onUpdate: NoAction, map: "FK_ContractFileTemplate_User")
1467 |   contractFileTemplateAttachments           ContractFileTemplateAttachment[]
1468 |   contractFileTemplateDepartmentAuthorities ContractFileTemplateDepartmentAuthority[]
1469 |   contractFileTemplateExtraAttachments      ContractFileTemplateExtraAttachment[]
1470 |   contractFileTemplateUserAuthorities       ContractFileTemplateUserAuthority[]
1471 | 
1472 |   @@index([contractFileTemplateTypeSn], map: "IX_ContractFileTemplate_ContractFileTemplateTypeSN")
1473 |   @@index([createDate], map: "IX_ContractFileTemplate_CreateDate")
1474 |   @@index([userId], map: "IX_ContractFileTemplate_UserID")
1475 |   @@schema("data")
1476 | }
1477 | 
1478 | model ContractFileTemplateAttachment {
1479 |   sn                     Int                  @id(map: "PK_ContractFileTemplateAttachment") @default(autoincrement()) @map("SN")
1480 |   contractFileTemplateSn Int                  @map("ContractFileTemplateSN")
1481 |   attachmentId           Int                  @map("AttachmentID")
1482 |   templateConfig         String?              @map("TemplateConfig") @db.NVarChar(Max)
1483 |   isFrontEnd             Boolean              @default(false, map: "DF_ContractFileTemplateAttachment_IsEND") @map("IsFrontEnd")
1484 |   attachment             Attachment           @relation(fields: [attachmentId], references: [attachmentId], onUpdate: NoAction, map: "FK_ContractFileTemplateAttachment_Attachment")
1485 |   contractFileTemplate   ContractFileTemplate @relation(fields: [contractFileTemplateSn], references: [sn], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractFileTemplateAttachment_ContractFileTemplate")
1486 | 
1487 |   @@index([attachmentId], map: "IX_ContractFileTemplateAttachment_AttachmentID")
1488 |   @@index([contractFileTemplateSn], map: "IX_ContractFileTemplateAttachment_ContractFileTemplateSN")
1489 |   @@schema("join")
1490 | }
1491 | 
1492 | model ContractFileTemplateDepartmentAuthority {
1493 |   sn                     Int                  @id(map: "PK_ContractFileTemplateDepartmentAuthority") @default(autoincrement()) @map("SN")
1494 |   contractFileTemplateSn Int                  @map("ContractFileTemplateSN")
1495 |   departmentId           Int?                 @map("DepartmentID")
1496 |   createDate             DateTime             @map("CreateDate") @db.DateTime
1497 |   createUserId           Int                  @map("CreateUserID")
1498 |   contractFileTemplate   ContractFileTemplate @relation(fields: [contractFileTemplateSn], references: [sn], onDelete: Cascade, map: "FK_ContractFileTemplateDepartmentAuthority_ContractFileTemplateDepartmentAuthority")
1499 |   department             Department?          @relation(fields: [departmentId], references: [departmentId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractFileTemplateDepartmentAuthority_Department")
1500 | 
1501 |   @@index([contractFileTemplateSn], map: "IX_ContractFileTemplateDepartmentAuthority_ContractFileTemplateSN")
1502 |   @@index([createDate], map: "IX_ContractFileTemplateDepartmentAuthority_CreateDate")
1503 |   @@index([createUserId], map: "IX_ContractFileTemplateDepartmentAuthority_CreateUserID")
1504 |   @@index([departmentId], map: "IX_ContractFileTemplateDepartmentAuthority_DepartmentID")
1505 |   @@schema("join")
1506 | }
1507 | 
1508 | model ContractFileTemplateExtraAttachment {
1509 |   sn                     Int                  @id(map: "PK_ContractFileTemplateExtraAttachment") @default(autoincrement()) @map("SN")
1510 |   contractFileTemplateSn Int                  @map("ContractFileTemplateSN")
1511 |   attachmentId           Int                  @map("AttachmentID")
1512 |   templateConfig         String?              @map("TemplateConfig") @db.NVarChar(Max)
1513 |   attachment             Attachment           @relation(fields: [attachmentId], references: [attachmentId], onUpdate: NoAction, map: "FK_ContractFileTemplateExtraAttachment_Attachment")
1514 |   contractFileTemplate   ContractFileTemplate @relation(fields: [contractFileTemplateSn], references: [sn], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractFileTemplateExtraAttachment_ContractFileTemplate")
1515 | 
1516 |   @@index([attachmentId], map: "IX_ContractFileTemplateExtraAttachment_AttachmentID")
1517 |   @@index([contractFileTemplateSn], map: "IX_ContractFileTemplateExtraAttachment_ContractFileTemplateSN")
1518 |   @@schema("join")
1519 | }
1520 | 
1521 | model ContractFileTemplateType {
1522 |   sn                    Int                    @id(map: "PK_ContractFileTemplateType") @default(autoincrement()) @map("SN")
1523 |   name                  String                 @map("Name") @db.NVarChar(Max)
1524 |   parentSn              Int?                   @map("ParentSN")
1525 |   createDate            DateTime?              @default(now(), map: "DF_ContractFileTemplateType_CreateDate") @map("CreateDate") @db.DateTime
1526 |   isEnable              Boolean                @default(true, map: "DF_ContractFileTemplateType_Visable") @map("IsEnable")
1527 |   contractFileTemplates ContractFileTemplate[]
1528 | 
1529 |   @@index([createDate], map: "IX_ContractFileTemplateType_CreateDate")
1530 |   @@index([parentSn], map: "IX_ContractFileTemplateType_ParentSN")
1531 |   @@schema("data")
1532 | }
1533 | 
1534 | model ContractFileTemplateUserAuthority {
1535 |   sn                     Int                  @id(map: "PK_ContractFileTemplateUserAuthority") @default(autoincrement()) @map("SN")
1536 |   contractFileTemplateSn Int                  @map("ContractFileTemplateSN")
1537 |   userId                 Int                  @map("UserID")
1538 |   createDate             DateTime             @map("CreateDate") @db.DateTime
1539 |   createUserId           Int                  @map("CreateUserID")
1540 |   contractFileTemplate   ContractFileTemplate @relation(fields: [contractFileTemplateSn], references: [sn], onDelete: Cascade, map: "FK_ContractFileTemplateUserAuthority_ContractFileTemplateUserAuthority")
1541 |   user                   User                 @relation(fields: [userId], references: [userId], onUpdate: NoAction, map: "FK_ContractFileTemplateUserAuthority_User")
1542 | 
1543 |   @@index([contractFileTemplateSn], map: "IX_ContractFileTemplateUserAuthority_ContractFileTemplateSN")
1544 |   @@index([createDate], map: "IX_ContractFileTemplateUserAuthority_CreateDate")
1545 |   @@index([createUserId], map: "IX_ContractFileTemplateUserAuthority_CreateUserID")
1546 |   @@index([userId], map: "IX_ContractFileTemplateUserAuthority_UserID")
1547 |   @@schema("join")
1548 | }
1549 | 
1550 | model ContractFlow {
1551 |   contractFlowId                Int                 @id(map: "PK_ContractFlow") @default(autoincrement()) @map("ContractFlowID")
1552 |   contractTypeId                Int                 @map("ContractTypeID")
1553 |   urgentLevelId                 Int                 @map("UrgentLevelID")
1554 |   disable                       Boolean?            @default(false, map: "DF_ContractFlow_Disable") @map("Disable")
1555 |   frequency                     Int?                @map("Frequency")
1556 |   enableAssignCloseExaminerSync Boolean?            @map("EnableAssignCloseExaminerSync")
1557 |   txt01                         String?             @map("Txt01") @db.NVarChar(255)
1558 |   cusJson                       String?             @map("Cus_Json") @db.NVarChar(Max)
1559 |   contractType                  CodeContractType    @relation(fields: [contractTypeId], references: [contractTypeId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractFlow_ContractType") @ignore
1560 |   urgentLevel                   UrgentLevel         @relation(fields: [urgentLevelId], references: [urgentLevelId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractFlow_UrgentLevel")
1561 |   contractFlowStages            ContractFlowStage[]
1562 | 
1563 |   @@index([contractTypeId], map: "IX_ContractFlow_ContractTypeID")
1564 |   @@index([frequency], map: "IX_ContractFlow_Frequency")
1565 |   @@index([txt01], map: "IX_ContractFlow_Txt01")
1566 |   @@index([urgentLevelId], map: "IX_ContractFlow_UrgentLevelID")
1567 |   @@schema("join")
1568 | }
1569 | 
1570 | model ContractFlowCsDefaultDepartment {
1571 |   defaultDepartmentId           Int                            @id(map: "PK_ContractFlowCSDefaultDepartment") @default(autoincrement()) @map("DefaultDepartmentID")
1572 |   defaultExaminerId             Int?                           @map("DefaultExaminerID")
1573 |   departmentId                  Int?                           @map("DepartmentID")
1574 |   contractFlowCsDefaultExaminer ContractFlowCsDefaultExaminer? @relation(fields: [defaultExaminerId], references: [defaultExaminerId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractFlowCSDefaultDepartment_ContractFlowCSDefaultExaminer")
1575 | 
1576 |   @@index([defaultExaminerId], map: "IX_ContractFlowCSDefaultDepartment_DefaultExaminerID")
1577 |   @@index([departmentId], map: "IX_ContractFlowCSDefaultDepartment_DepartmentID")
1578 |   @@map("ContractFlowCSDefaultDepartment")
1579 |   @@schema("join")
1580 | }
1581 | 
1582 | model ContractFlowCsDefaultExaminer {
1583 |   defaultExaminerId                Int                               @id(map: "PK_ContractFlowCSDefaultExaminer") @default(autoincrement()) @map("DefaultExaminerID")
1584 |   contractTypeId                   Int?                              @map("ContractTypeID")
1585 |   userId                           Int?                              @map("UserID")
1586 |   urgentLevelId                    Int?                              @map("UrgentLevelID")
1587 |   requireMemo                      String?                           @map("RequireMemo") @db.NVarChar(Max)
1588 |   halt                             Boolean?                          @map("Halt")
1589 |   carbonNotify                     String?                           @map("CarbonNotify") @db.NVarChar(Max)
1590 |   deadline                         Int?                              @map("Deadline")
1591 |   alertPeriod                      Int?                              @map("AlertPeriod")
1592 |   sendReminderMail                 Boolean?                          @map("SendReminderMail")
1593 |   attachmentID                     String?                           @map("AttachmentIDs") @db.NVarChar(Max)
1594 |   roleUserId                       Int                               @default(0, map: "DF__ContractF__RoleU__2DB1C7EE") @map("RoleUserID")
1595 |   syncContractAttachment           Int                               @default(0, map: "DF_ContractFlowCSDefaultExaminer_SyncContractAttachment") @map("SyncContractAttachment")
1596 |   contractFlowCsDefaultDepartments ContractFlowCsDefaultDepartment[]
1597 |   contractType                     CodeContractType?                 @relation(fields: [contractTypeId], references: [contractTypeId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractFlowCSDefaultExaminer_ContractType") @ignore
1598 |   user                             User?                             @relation(fields: [userId], references: [userId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractFlowCSDefaultExaminer_User")
1599 |   contractFlowCsDefaultStages      ContractFlowCsDefaultStage[]
1600 | 
1601 |   @@index([alertPeriod], map: "IX_ContractFlowCSDefaultExaminer_AlertPeriod")
1602 |   @@index([contractTypeId], map: "IX_ContractFlowCSDefaultExaminer_ContractTypeID")
1603 |   @@index([deadline], map: "IX_ContractFlowCSDefaultExaminer_Deadline")
1604 |   @@index([roleUserId], map: "IX_ContractFlowCSDefaultExaminer_RoleUserID")
1605 |   @@index([urgentLevelId], map: "IX_ContractFlowCSDefaultExaminer_UrgentLevelID")
1606 |   @@index([userId], map: "IX_ContractFlowCSDefaultExaminer_UserID")
1607 |   @@map("ContractFlowCSDefaultExaminer")
1608 |   @@schema("join")
1609 | }
1610 | 
1611 | model ContractFlowCsDefaultStage {
1612 |   defaultStageId                Int                            @id(map: "PK_ContractFlowCSDefaultStage") @default(autoincrement()) @map("DefaultStageID")
1613 |   defaultExaminerId             Int?                           @map("DefaultExaminerID")
1614 |   examStageId                   Int?                           @map("ExamStageID")
1615 |   examStatusId                  Int?                           @map("ExamStatusID")
1616 |   contractFlowCsDefaultExaminer ContractFlowCsDefaultExaminer? @relation(fields: [defaultExaminerId], references: [defaultExaminerId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractFlowCSDefaultStage_ContractFlowCSDefaultExaminer")
1617 |   examStage                     ExamStage?                     @relation(fields: [examStageId], references: [examStageId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractFlowCSDefaultStage_ExamStage")
1618 | 
1619 |   @@index([defaultExaminerId], map: "IX_ContractFlowCSDefaultStage_DefaultExaminerID")
1620 |   @@index([examStageId], map: "IX_ContractFlowCSDefaultStage_ExamStageID")
1621 |   @@index([examStatusId], map: "IX_ContractFlowCSDefaultStage_ExamStatusID")
1622 |   @@map("ContractFlowCSDefaultStage")
1623 |   @@schema("join")
1624 | }
1625 | 
1626 | model ContractFlowDefaultDepartment {
1627 |   defaultDepartmentId         Int                         @id(map: "PK_ContractFlowDefaultDepartment") @default(autoincrement()) @map("DefaultDepartmentID")
1628 |   defaultExaminerId           Int                         @map("DefaultExaminerID")
1629 |   departmentId                Int?                        @map("DepartmentID")
1630 |   contractFlowDefaultExaminer ContractFlowDefaultExaminer @relation(fields: [defaultExaminerId], references: [defaultExaminerId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractFlowDefaultDepartment_ContractFlowDefaultExaminer")
1631 | 
1632 |   @@index([defaultExaminerId], map: "IX_ContractFlowDefaultDepartment_DefaultExaminerID")
1633 |   @@index([departmentId], map: "IX_ContractFlowDefaultDepartment_DepartmentID")
1634 |   @@schema("join")
1635 | }
1636 | 
1637 | model ContractFlowDefaultExaminer {
1638 |   defaultExaminerId              Int                             @id(map: "PK_ContractFlowDefaultExaminer") @default(autoincrement()) @map("DefaultExaminerID")
1639 |   contractFlowStageId            Int                             @map("ContractFlowStageID")
1640 |   userId                         Int?                            @map("UserID")
1641 |   cc                             String?                         @map("CC") @db.NVarChar(450)
1642 |   contractFlowDefaultDepartments ContractFlowDefaultDepartment[]
1643 |   contractFlowStage              ContractFlowStage               @relation(fields: [contractFlowStageId], references: [contractFlowStageId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractFlowDefaultExaminer_ContractFlowStage")
1644 |   user                           User?                           @relation(fields: [userId], references: [userId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractFlowDefaultExaminer_User")
1645 | 
1646 |   @@index([cc], map: "IX_ContractFlowDefaultExaminer_CC")
1647 |   @@index([contractFlowStageId], map: "IX_ContractFlowDefaultExaminer_ContractFlowStageID")
1648 |   @@index([userId], map: "IX_ContractFlowDefaultExaminer_UserID")
1649 |   @@schema("join")
1650 | }
1651 | 
1652 | model ContractFlowDefaultSyncStage {
1653 |   defaultExaminerId   Int                @id(map: "PK__Contract__0409ED6BF7036ECF") @default(autoincrement()) @map("DefaultExaminerID")
1654 |   contractFlowStageId Int?               @map("ContractFlowStageID")
1655 |   syncStageSn         Int?               @map("SyncStageSN")
1656 |   contractFlowStage   ContractFlowStage? @relation(fields: [contractFlowStageId], references: [contractFlowStageId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractFlowDefaultSyncStage_ContractFlowStageID")
1657 |   syncStage           SyncStage?         @relation(fields: [syncStageSn], references: [sn], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractFlowDefaultSyncStage_SyncStageSN")
1658 | 
1659 |   @@index([contractFlowStageId], map: "IX_ContractFlowDefaultSyncStage_ContractFlowStageID")
1660 |   @@index([syncStageSn], map: "IX_ContractFlowDefaultSyncStage_SyncStageSN")
1661 |   @@schema("join")
1662 | }
1663 | 
1664 | model ContractFlowStage {
1665 |   contractFlowStageId           Int                            @id(map: "PK_ContractFlowStage") @default(autoincrement()) @map("ContractFlowStageID")
1666 |   contractFlowId                Int?                           @map("ContractFlowID")
1667 |   examStageId                   Int?                           @map("ExamStageID")
1668 |   deadline                      Int?                           @default(10, map: "DF_ContractFlowStage_Deadline") @map("Deadline")
1669 |   contractFlowDefaultExaminers  ContractFlowDefaultExaminer[]
1670 |   contractFlowDefaultSyncStages ContractFlowDefaultSyncStage[]
1671 |   contractFlow                  ContractFlow?                  @relation(fields: [contractFlowId], references: [contractFlowId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractFlowStage_ContractFlow")
1672 |   examStage                     ExamStage?                     @relation(fields: [examStageId], references: [examStageId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractFlowStage_ExamStage")
1673 | 
1674 |   @@index([contractFlowId], map: "IX_ContractFlowStage_ContractFlowID")
1675 |   @@index([deadline], map: "IX_ContractFlowStage_Deadline")
1676 |   @@index([examStageId], map: "IX_ContractFlowStage_ExamStageID")
1677 |   @@schema("join")
1678 | }
1679 | 
1680 | model ContractGuid {
1681 |   contractId Int      @id(map: "PK_ContractGuid") @map("ContractID")
1682 |   guid       String   @map("Guid") @db.NVarChar(200)
1683 |   contract   Contract @relation(fields: [contractId], references: [contractId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractGuid_Contract")
1684 | 
1685 |   @@index([guid], map: "IX_ContractGuid_Guid")
1686 |   @@schema("join")
1687 | }
1688 | 
1689 | model ContractHistory {
1690 |   sn                                    Int                   @id(map: "PK_ContractHistory") @default(autoincrement()) @map("Sn")
1691 |   contractId                            Int?                  @map("ContractID")
1692 |   examUserId                            Int?                  @map("ExamUserID")
1693 |   assignUserId                          Int?                  @map("AssignUserID")
1694 |   examStageId                           Int?                  @map("ExamStageID")
1695 |   examStatusId                          Int?                  @map("ExamStatusID")
1696 |   examMemo                              String?               @map("ExamMemo") @db.NVarChar(Max)
1697 |   examDate                              DateTime?             @default(now(), map: "DF_ContractHistory_ExamDate") @map("ExamDate") @db.DateTime
1698 |   type                                  Int?                  @default(0, map: "DF_ContractHistory_Type") @map("Type")
1699 |   signPerson                            String?               @map("SignPerson") @db.NVarChar(Max)
1700 |   signDate                              DateTime?             @map("SignDate") @db.DateTime
1701 |   processDay                            Int?                  @map("ProcessDay")
1702 |   isProcess                             Boolean?              @map("IsProcess")
1703 |   assignDate                            DateTime?             @map("AssignDate") @db.DateTime
1704 |   contractExtendInfo                    String?               @map("ContractExtendInfo") @db.NVarChar(Max)
1705 |   originType                            Int?                  @map("OriginType")
1706 |   cusDatum                              String?               @map("Cus_Data") @db.NVarChar(Max)
1707 |   userContractHistoryAssignUserIdToUser User?                 @relation("ContractHistory_AssignUserIDToUser", fields: [assignUserId], references: [userId], onUpdate: SetNull, map: "FK_ContractHistory_AssignUser")
1708 |   contract                              Contract?             @relation(fields: [contractId], references: [contractId], onDelete: Cascade, map: "FK_ContractHistory_Contract")
1709 |   examStage                             ExamStage?            @relation(fields: [examStageId], references: [examStageId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractHistory_ExamStage")
1710 |   examStatus                            ExamStatus?           @relation(fields: [examStatusId], references: [examStatusId], onDelete: Cascade, map: "FK_ContractHistory_ExamStatus")
1711 |   userContractHistoryExamUserIdToUser   User?                 @relation("ContractHistory_ExamUserIDToUser", fields: [examUserId], references: [userId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractHistory_User")
1712 |   contractPartners                      ContractPartner[]
1713 |   contractRequireSigns                  ContractRequireSign[]
1714 | 
1715 |   @@index([assignDate], map: "IX_ContractHistory_AssignDate")
1716 |   @@index([assignUserId], map: "IX_ContractHistory_AssignUserID")
1717 |   @@index([contractId], map: "IX_ContractHistory_ContractID")
1718 |   @@index([examDate], map: "IX_ContractHistory_ExamDate")
1719 |   @@index([examStageId], map: "IX_ContractHistory_ExamStageID")
1720 |   @@index([examStatusId], map: "IX_ContractHistory_ExamStatusID")
1721 |   @@index([examUserId], map: "IX_ContractHistory_ExamUserID")
1722 |   @@index([originType], map: "IX_ContractHistory_OriginType")
1723 |   @@index([processDay], map: "IX_ContractHistory_ProcessDay")
1724 |   @@index([signDate], map: "IX_ContractHistory_SignDate")
1725 |   @@index([sn], map: "IX_ContractHistory_Sn")
1726 |   @@index([type], map: "IX_ContractHistory_Type")
1727 |   @@schema("data")
1728 | }
1729 | 
1730 | /// The underlying table does not contain a valid unique identifier and can therefore currently not be handled by Prisma Client.
1731 | model ContractLog {
1732 |   sn                     Int       @default(autoincrement()) @map("SN")
1733 |   contractId             Int       @map("ContractID")
1734 |   contractXml            String?   @map("ContractXml") @db.Xml
1735 |   loginUser              Int?      @map("LoginUser")
1736 |   createDate             DateTime? @default(now(), map: "DF_ContractLog_CreateDate") @map("CreateDate") @db.DateTime
1737 |   userAction             String?   @map("UserAction") @db.NVarChar(500)
1738 |   contractXmlCompression String?   @map("ContractXmlCompression") @db.NVarChar(Max)
1739 | 
1740 |   @@index([contractId], map: "IX_ContractLog_ContractID")
1741 |   @@index([createDate], map: "IX_ContractLog_CreateDate")
1742 |   @@index([loginUser], map: "IX_ContractLog_LoginUser")
1743 |   @@index([sn], map: "IX_ContractLog_SN")
1744 |   @@ignore
1745 |   @@schema("dbo")
1746 | }
1747 | 
1748 | model ContractMailLog {
1749 |   sn         Int       @id(map: "PK_ContractMailLog") @default(autoincrement()) @map("SN")
1750 |   contractId Int?      @map("ContractID")
1751 |   mailSn     Int?      @map("MailSn")
1752 |   contract   Contract? @relation(fields: [contractId], references: [contractId], onDelete: Cascade, map: "FK_ContractMailLog_Contract")
1753 |   mailLog    MailLog?  @relation(fields: [mailSn], references: [mailSn], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractMailLog_MailLog")
1754 | 
1755 |   @@index([contractId], map: "IX_ContractMailLog_ContractID")
1756 |   @@index([mailSn], map: "IX_ContractMailLog_MailSn")
1757 |   @@schema("join")
1758 | }
1759 | 
1760 | model ContractMessageBoard {
1761 |   sn             Int          @id(map: "PK__Contract__32151C443584B2E9") @default(autoincrement()) @map("Sn")
1762 |   contractId     Int          @map("ContractID")
1763 |   boardId        Int          @map("BoardID")
1764 |   memo           String?      @map("Memo") @db.NVarChar(Max)
1765 |   requestStageId Int          @map("RequestStageID")
1766 |   userId         Int          @map("UserID")
1767 |   memoDate       DateTime     @default(now(), map: "DF__ContractM__MemoD__45E94432") @map("MemoDate") @db.DateTime
1768 |   visible        Boolean?     @default(true, map: "DF__ContractM__Visib__46DD686B") @map("Visible")
1769 |   messageBoard   MessageBoard @relation(fields: [boardId], references: [boardId], onUpdate: NoAction, map: "FK__ContractM__Board__430CD787")
1770 |   contract       Contract     @relation(fields: [contractId], references: [contractId], onUpdate: NoAction, map: "FK__ContractM__Contr__4218B34E")
1771 |   examStage      ExamStage    @relation(fields: [requestStageId], references: [examStageId], onUpdate: NoAction, map: "FK__ContractM__Reque__4400FBC0")
1772 |   user           User         @relation(fields: [userId], references: [userId], onUpdate: NoAction, map: "FK__ContractM__UserI__44F51FF9")
1773 | 
1774 |   @@index([boardId], map: "IX_ContractMessageBoard_BoardID")
1775 |   @@index([contractId], map: "IX_ContractMessageBoard_ContractID")
1776 |   @@index([memoDate], map: "IX_ContractMessageBoard_MemoDate")
1777 |   @@index([requestStageId], map: "IX_ContractMessageBoard_RequestStageID")
1778 |   @@index([userId], map: "IX_ContractMessageBoard_UserID")
1779 |   @@schema("join")
1780 | }
1781 | 
1782 | model ContractModule {
1783 |   sn                   Int                  @id(map: "PK_ContractModule") @map("SN")
1784 |   moduleName           String?              @map("ModuleName") @db.NVarChar(Max)
1785 |   examStageAuthorities ExamStageAuthority[]
1786 | 
1787 |   @@schema("code")
1788 | }
1789 | 
1790 | model ContractNoCloseNotice {
1791 |   id                Int     @id(map: "PK_ContractNoCloseNoticeType") @default(autoincrement()) @map("ID")
1792 |   name              String  @map("Name") @db.NVarChar(200)
1793 |   positionLevelCode String? @map("PositionLevelCode") @db.NVarChar(200)
1794 |   seq               Int     @map("Seq")
1795 |   afterDay          Int?    @map("AfterDays")
1796 | 
1797 |   @@schema("code")
1798 | }
1799 | 
1800 | model ContractOtherNotify {
1801 |   sn              Int       @id(map: "PK_ContractOtherNotify") @default(autoincrement()) @map("Sn")
1802 |   contractId      Int       @map("ContractID")
1803 |   examStageId     Int       @map("ExamStageID")
1804 |   otherNotifyMail String?   @map("OtherNotifyMail") @db.NVarChar(Max)
1805 |   contract        Contract  @relation(fields: [contractId], references: [contractId], onDelete: Cascade, map: "FK_ContractOtherNotify_Contract")
1806 |   examStage       ExamStage @relation(fields: [examStageId], references: [examStageId], map: "FK_ContractOtherNotify_ExamStage")
1807 | 
1808 |   @@index([contractId], map: "IX_ContractOtherNotify_ContractID")
1809 |   @@index([examStageId], map: "IX_ContractOtherNotify_ExamStageID")
1810 |   @@schema("join")
1811 | }
1812 | 
1813 | model ContractPartner {
1814 |   sn                Int              @id(map: "PK_ContractPartner") @default(autoincrement()) @map("Sn")
1815 |   contractId        Int?             @map("ContractID")
1816 |   partnerContactId  Int?             @map("PartnerContactID")
1817 |   partnerId         Int?             @map("PartnerID")
1818 |   partnerSeq        Int?             @map("PartnerSeq")
1819 |   partnerName       String?          @map("PartnerName") @db.NVarChar(450)
1820 |   contractHistorySn Int?             @map("ContractHistorySn")
1821 |   partnerEmail      String?          @map("PartnerEmail") @db.NVarChar(255)
1822 |   contract          Contract?        @relation(fields: [contractId], references: [contractId], onDelete: Cascade, map: "FK_ContractPartner_Contract")
1823 |   contractHistory   ContractHistory? @relation(fields: [contractHistorySn], references: [sn], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractPartner_ContractHistory")
1824 |   partner           Partner?         @relation(fields: [partnerId], references: [partnerId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractPartner_Partner")
1825 |   partnerContact    PartnerContact?  @relation(fields: [partnerContactId], references: [partnerContactId], onDelete: Cascade, map: "FK_ContractPartner_PartnerContact")
1826 | 
1827 |   @@index([contractHistorySn], map: "IX_ContractPartner")
1828 |   @@index([contractId], map: "IX_ContractPartner_ContractID")
1829 |   @@index([partnerContactId], map: "IX_ContractPartner_PartnerContactID")
1830 |   @@index([partnerId], map: "IX_ContractPartner_PartnerID")
1831 |   @@index([partnerName], map: "IX_ContractPartner_PartnerName")
1832 |   @@index([partnerSeq], map: "IX_ContractPartner_PartnerSeq")
1833 |   @@index([sn], map: "IX_ContractPartner_Sn")
1834 |   @@schema("join")
1835 | }
1836 | 
1837 | model ContractRequireAttribute {
1838 |   sn               Int               @id(map: "PK_ContractRequireAttribute") @default(autoincrement()) @map("Sn")
1839 |   name             String?           @map("Name") @db.NVarChar(50)
1840 |   disable          Boolean?          @map("Disable")
1841 |   systemDefine     Boolean?          @map("SystemDefine")
1842 |   relatedContracts RelatedContract[]
1843 | 
1844 |   @@index([name], map: "IX_ContractRequireAttribute_Name")
1845 |   @@schema("code")
1846 | }
1847 | 
1848 | model ContractRequireSign {
1849 |   sn                Int              @id(map: "PK_ContractRequireSign") @default(autoincrement()) @map("SN")
1850 |   contractId        Int              @map("ContractID")
1851 |   signTypeId        Int              @map("SignTypeID")
1852 |   signPerson        String?          @map("SignPerson") @db.NVarChar(450)
1853 |   custodianUserId   Int?             @map("Custodian_UserID")
1854 |   contractHistorySn Int?             @map("ContractHistorySn")
1855 |   contract          Contract         @relation(fields: [contractId], references: [contractId], onDelete: Cascade, map: "FK_ContractRequireSign_Contract")
1856 |   contractHistory   ContractHistory? @relation(fields: [contractHistorySn], references: [sn], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractRequireSign_ContractHistory")
1857 |   signRequirement   SignRequirement  @relation(fields: [signTypeId], references: [signTypeId], onUpdate: NoAction, map: "FK_ContractRequireSign_SignRequirement")
1858 |   user              User?            @relation(fields: [custodianUserId], references: [userId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ContractRequireSign_User")
1859 | 
1860 |   @@index([contractHistorySn], map: "IX_ContractRequireSign_ContractHistorySn")
1861 |   @@index([contractId], map: "IX_ContractRequireSign_ContractID")
1862 |   @@index([custodianUserId], map: "IX_ContractRequireSign_Custodian_UserID")
1863 |   @@index([signPerson], map: "IX_ContractRequireSign_SignPerson")
1864 |   @@index([signTypeId], map: "IX_ContractRequireSign_SignTypeID")
1865 |   @@schema("join")
1866 | }
1867 | 
1868 | model ContractStampDuty {
1869 |   sn            Int       @id(map: "PK_ContractStampDuty") @default(autoincrement()) @map("SN")
1870 |   contractId    Int       @map("ContractID")
1871 |   stampDutyType Int       @map("StampDutyType")
1872 |   description   String?   @map("Description") @db.NVarChar(Max)
1873 |   contract      Contract  @relation(fields: [contractId], references: [contractId], onUpdate: NoAction, map: "FK_ContractStampDuty_Contract")
1874 |   stampDuty     StampDuty @relation(fields: [stampDutyType], references: [stampDutyType], onUpdate: NoAction, map: "FK_ContractStampDuty_StampDuty")
1875 | 
1876 |   @@index([contractId], map: "IX_ContractStampDuty_ContractID")
1877 |   @@index([stampDutyType], map: "IX_ContractStampDuty_StampDutyType")
1878 |   @@schema("dbo")
1879 | }
1880 | 
1881 | /// The underlying table does not contain a valid unique identifier and can therefore currently not be handled by Prisma Client.
1882 | model JoinContractType {
1883 |   sn             Int               @default(autoincrement()) @map("Sn")
1884 |   contractId     Int?              @map("ContractID")
1885 |   contractTypeId Int?              @map("ContractTypeID")
1886 |   contract       Contract?         @relation(fields: [contractId], references: [contractId], onDelete: Cascade, map: "FK_ContractType_Contract")
1887 |   contractType   CodeContractType? @relation(fields: [contractTypeId], references: [contractTypeId], onDelete: Cascade, map: "FK_ContractType_ContractType")
1888 | 
1889 |   @@map("ContractType")
1890 |   @@ignore
1891 |   @@schema("join")
1892 | }
1893 | 
1894 | /// The underlying table does not contain a valid unique identifier and can therefore currently not be handled by Prisma Client.
1895 | model CodeContractType {
1896 |   contractTypeId                 Int                             @id @default(autoincrement()) @map("ContractTypeID")
1897 |   contractTypeName               String?                         @map("ContractTypeName") @db.NVarChar(Max)
1898 |   disable                        Boolean?                        @default(false, map: "DF_ContractType_Disable") @map("Disable")
1899 |   systemDefine                   Boolean?                        @default(false, map: "DF_ContractType_SystemDefine") @map("SystemDefine")
1900 |   mainContractTypeId             Int?                            @map("MainContractTypeID")
1901 |   secret                         Boolean?                        @map("Secret")
1902 |   contractTypeCode               String?                         @map("ContractTypeCode") @db.NVarChar(50)
1903 |   seq                            Int?                            @default(9999, map: "DF_ContractType_Seq") @map("Seq")
1904 |   deadlineNotice                 Boolean?                        @default(false, map: "DF_ContractType_DeadlineNotice") @map("DeadlineNotice")
1905 |   enableAutoAssignExaminer       Boolean?                        @default(false, map: "DF_ContractType_EnableAutoAssignExaminer") @map("EnableAutoAssignExaminer")
1906 |   autoAssignExaminerPriority     Int?                            @default(1, map: "DF_ContractType_AutoAssignExaminerPriority") @map("AutoAssignExaminerPriority")
1907 |   enableContractCloseFileUpload  Boolean                         @default(false, map: "DF__ContractT__Enabl__3C34F16F") @map("EnableContractCloseFileUpload")
1908 |   contractTypeMemo               String?                         @map("ContractTypeMemo") @db.NVarChar(Max)
1909 |   priorityNumber                 Int?                            @map("PriorityNumber")
1910 |   txt01                          String?                         @map("Txt01") @db.NVarChar(Max)
1911 |   isPublic                       Boolean?
1912 |   contractFlows                  ContractFlow[]
1913 |   contractFlowCsDefaultExaminers ContractFlowCsDefaultExaminer[]
1914 |   contractTypes                  JoinContractType[]
1915 |   mainContractType               MainContractType?               @relation(fields: [mainContractTypeId], references: [mainContractTypeId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractType_MainContractType")
1916 |   contractTypeLanguages          ContractTypeLanguage[]
1917 |   contractTypeDepartments        ContractTypeDepartment[]
1918 | 
1919 |   @@map("ContractType")
1920 |   @@ignore
1921 |   @@schema("code")
1922 | }
1923 | 
1924 | model ContractTypeLanguage {
1925 |   sn             Int              @id(map: "PK_ContractType_SN") @default(autoincrement()) @map("SN")
1926 |   contractTypeId Int              @map("ContractTypeID")
1927 |   languageCode   String           @map("LanguageCode") @db.NVarChar(50)
1928 |   name           String?          @map("Name") @db.NVarChar(Max)
1929 |   contractType   CodeContractType @relation(fields: [contractTypeId], references: [contractTypeId], onUpdate: NoAction, map: "FK_ContractType_Language_ContractType_Language") @ignore
1930 | 
1931 |   @@index([languageCode], map: "IX_ContractType_Language")
1932 |   @@index([contractTypeId], map: "IX_Table_ContractTypeID")
1933 |   @@map("ContractType_Language")
1934 |   @@schema("join")
1935 | }
1936 | 
1937 | model ContractTypeDepartment {
1938 |   sn             Int              @id(map: "PK__Contract__32151C4404C3A5BF") @default(autoincrement()) @map("Sn")
1939 |   contractTypeId Int              @map("ContractTypeID")
1940 |   departmentId   Int              @map("DepartmentID")
1941 |   type           Int?             @default(1, map: "DF__ContractTy__Type__40C49C62") @map("Type")
1942 |   createUserId   Int              @map("CreateUserID")
1943 |   createDate     DateTime         @default(now(), map: "DF__ContractT__Creat__41B8C09B") @map("CreateDate") @db.DateTime
1944 |   enable         Boolean          @default(true, map: "DF__ContractT__Enabl__42ACE4D4") @map("Enable")
1945 |   contractType   CodeContractType @relation(fields: [contractTypeId], references: [contractTypeId], onUpdate: NoAction, map: "FK_ContractTypeDepartment_ContractTypeID") @ignore
1946 |   user           User             @relation(fields: [createUserId], references: [userId], onUpdate: NoAction, map: "FK_ContractTypeDepartment_CreateUserID")
1947 |   department     Department       @relation(fields: [departmentId], references: [departmentId], onUpdate: NoAction, map: "FK_ContractTypeDepartment_DepartmentID")
1948 | 
1949 |   @@index([contractTypeId], map: "IX_ContractTypeDepartment_ContractTypeID")
1950 |   @@index([createDate], map: "IX_ContractTypeDepartment_CreateDate")
1951 |   @@index([createUserId], map: "IX_ContractTypeDepartment_CreateUserID")
1952 |   @@index([departmentId], map: "IX_ContractTypeDepartment_DepartmentID")
1953 |   @@index([enable], map: "IX_ContractTypeDepartment_Enable")
1954 |   @@index([type], map: "IX_ContractTypeDepartment_Type")
1955 |   @@schema("code")
1956 | }
1957 | 
1958 | model ContractViewTemp {
1959 |   contractId                      Int       @id(map: "PK_ContractViewTemp") @map("ContractID")
1960 |   contractGuid                    String?   @map("ContractGUID") @db.NVarChar(200)
1961 |   validDuration                   String?   @map("ValidDuration") @db.NVarChar(50)
1962 |   documentName                    String?   @map("DocumentName") @db.NVarChar(450)
1963 |   contractFlowId                  Int?      @map("ContractFlowID")
1964 |   recorderId                      Int?      @map("RecorderID")
1965 |   createDate                      DateTime? @map("CreateDate") @db.DateTime
1966 |   branchId                        Int?      @map("BranchID")
1967 |   requirement                     String?   @map("Requirement") @db.NVarChar(Max)
1968 |   provisionDate                   DateTime? @map("ProvisionDate") @db.DateTime
1969 |   partnerMemo                     String?   @map("PartnerMemo") @db.NVarChar(Max)
1970 |   receiveNo                       String    @map("ReceiveNo") @db.NVarChar(50)
1971 |   saveNo                          String    @map("SaveNo") @db.NVarChar(50)
1972 |   receiveDate                     DateTime? @map("ReceiveDate") @db.DateTime
1973 |   saveDate                        DateTime? @map("SaveDate") @db.DateTime
1974 |   departmentName                  String?   @map("DepartmentName") @db.NVarChar(450)
1975 |   branchName                      String?   @map("BranchName") @db.NVarChar(450)
1976 |   recorderName                    String?   @map("RecorderName") @db.NVarChar(Max)
1977 |   recorderExt                     String    @map("RecorderExt") @db.NVarChar(50)
1978 |   recorderEmail                   String?   @map("RecorderEmail") @db.NVarChar(Max)
1979 |   recorderDepartment              String?   @map("RecorderDepartment") @db.NVarChar(450)
1980 |   partner                         String    @map("Partners") @db.NVarChar(Max)
1981 |   contact                         String    @map("Contacts") @db.NVarChar(Max)
1982 |   recorerNameWithExt              String?   @map("RecorerNameWithExt") @db.NVarChar(Max)
1983 |   applicationDate                 DateTime? @map("ApplicationDate") @db.DateTime
1984 |   urgentLevelId                   Int       @map("UrgentLevelID")
1985 |   urgentLevel                     String    @map("UrgentLevel") @db.NVarChar(450)
1986 |   requireSign                     Boolean?  @map("RequireSign")
1987 |   requirePartnerSign              Boolean?  @map("RequirePartnerSign")
1988 |   signTypeId                      Int?      @map("SignTypeID")
1989 |   departmentIdName                String?   @map("DepartmentIDName") @db.NVarChar(450)
1990 |   currentStageId                  Int?      @map("CurrentStageID")
1991 |   currentExaminerSn               Int?      @map("CurrentExaminerSn")
1992 |   currentExaminerId               Int?      @map("CurrentExaminerID")
1993 |   backStageId                     Int?      @map("BackStageID")
1994 |   exchangeTypeId                  Int?      @map("ExchangeTypeID")
1995 |   currency                        String?   @map("Currency") @db.NVarChar(Max)
1996 |   costClause                      String?   @map("CostClause") @db.NVarChar(Max)
1997 |   otherClause                     String?   @map("OtherClause") @db.NVarChar(Max)
1998 |   costNtd                         Decimal?  @map("CostNTD") @db.Decimal(18, 2)
1999 |   cost                            Decimal?  @map("Cost") @db.Decimal(18, 2)
2000 |   memo                            String?   @map("Memo") @db.NVarChar(Max)
2001 |   contractTypeName                String?   @map("ContractTypeNames") @db.NVarChar(Max)
2002 |   contractTypeSearch              String?   @map("ContractTypeSearch") @db.NVarChar(Max)
2003 |   currentStage                    String?   @map("CurrentStage") @db.NVarChar(450)
2004 |   currentStageIdList              String?   @map("CurrentStageIDList") @db.NVarChar(450)
2005 |   currentStatus                   String    @map("CurrentStatus") @db.NVarChar(Max)
2006 |   effectiveDate                   DateTime? @map("EffectiveDate") @db.DateTime
2007 |   validStartDate                  DateTime? @map("ValidStartDate") @db.DateTime
2008 |   validEndDate                    DateTime? @map("ValidEndDate") @db.DateTime
2009 |   signMemo                        String?   @map("SignMemo") @db.NVarChar(Max)
2010 |   currentExaminer                 String    @map("CurrentExaminer") @db.NVarChar(Max)
2011 |   currentHandler                  String    @map("CurrentHandler") @db.NVarChar(Max)
2012 |   examiner                        String    @map("Examiners") @db.NVarChar(Max)
2013 |   applicantName                   String    @map("ApplicantNames") @db.NVarChar(Max)
2014 |   fullName                        String    @map("FullName") @db.NVarChar(Max)
2015 |   directorExaminerName            String    @map("DirectorExaminerNames") @db.NVarChar(Max)
2016 |   firstExaminerName               String    @map("FirstExaminerNames") @db.NVarChar(Max)
2017 |   realExaminerName                String    @map("RealExaminerNames") @db.NVarChar(Max)
2018 |   headExaminerName                String    @map("HeadExaminerNames") @db.NVarChar(Max)
2019 |   bossExaminerName                String    @map("BossExaminerNames") @db.NVarChar(Max)
2020 |   signExaminerName                String    @map("SignExaminerNames") @db.NVarChar(Max)
2021 |   closeExaminerName               String?   @map("CloseExaminerNames") @db.NVarChar(Max)
2022 |   weekNo                          String?   @db.NVarChar(50)
2023 |   processStatus                   String?   @map("ProcessStatus") @db.NVarChar(Max)
2024 |   applicantDepartmentName         String?   @map("ApplicantDepartmentName") @db.NVarChar(450)
2025 |   applicantDepartmentId           Int?      @map("ApplicantDepartmentID")
2026 |   documentNo                      String?   @map("DocumentNo") @db.NVarChar(Max)
2027 |   lastSendMailDate                DateTime? @map("LastSendMailDate") @db.DateTime
2028 |   applicantParentDepartmentId     Int?      @map("ApplicantParentDepartmentID")
2029 |   recorderEmployeeId              String    @map("RecorderEmployeeID") @db.NVarChar(450)
2030 |   examUser                        String    @map("ExamUser") @db.NVarChar(Max)
2031 |   examDate                        DateTime? @map("ExamDate") @db.DateTime
2032 |   realExaminerNamesWithoutExt     String    @map("RealExaminerNamesWithoutExt") @db.NVarChar(Max)
2033 |   processDay                      Int?      @map("ProcessDay")
2034 |   factoryidname                   String?   @db.NVarChar(450)
2035 |   idname                          String?   @map("Idname") @db.NVarChar(450)
2036 |   alertExtend                     Boolean?  @map("AlertExtend")
2037 |   alertEmail                      String?   @map("AlertEmails") @db.NVarChar(450)
2038 |   alertCcEmail                    String?   @map("AlertCCEmails") @db.NVarChar(450)
2039 |   alertBccEmail                   String?   @map("AlertBCCEmails") @db.NVarChar(450)
2040 |   companySignId                   Int?      @map("CompanySignID")
2041 |   applyNo                         String?   @map("ApplyNo") @db.NVarChar(50)
2042 |   alertBeginDate                  DateTime? @map("AlertBeginDate") @db.DateTime
2043 |   alertEndDate                    DateTime? @map("AlertEndDate") @db.DateTime
2044 |   alertPeriod                     Int?      @map("AlertPeriod")
2045 |   autoExtend                      Boolean?  @map("AutoExtend")
2046 |   extendYear                      Int?      @map("ExtendYear")
2047 |   extendMonth                     Int?      @map("ExtendMonth")
2048 |   finalCostExchangeTypeId         Int?      @map("FinalCostExchangeTypeID")
2049 |   finalCostNtd                    Decimal?  @map("FinalCostNTD") @db.Decimal(18, 2)
2050 |   closeStatusId                   Int?      @map("CloseStatusID")
2051 |   closeStatus                     String?   @map("CloseStatus") @db.NVarChar(Max)
2052 |   shortName                       String?   @map("ShortName") @db.NVarChar(125)
2053 |   applicantSiteName               String?   @map("ApplicantSiteName") @db.NVarChar(255)
2054 |   cusProductProjectName           String?   @map("Cus_ProductProjectName") @db.NVarChar(450)
2055 |   closeMemo                       String?   @map("CloseMemo") @db.NVarChar(Max)
2056 |   closeStageId                    Int?      @map("CloseStageID")
2057 |   closeStage                      String?   @map("CloseStage") @db.NVarChar(450)
2058 |   autoRenewDeadline               Boolean?  @map("AutoRenewDeadline")
2059 |   autoRenewNewDate                Boolean?  @map("AutoRenewNewDate")
2060 |   autoRenewValidEndDate           DateTime? @map("AutoRenewValidEndDate") @db.DateTime
2061 |   closeCaseBeforeMonth            Int?      @map("CloseCaseBeforeMonth")
2062 |   closeCaseBeforeDay              Int?      @map("CloseCaseBeforeDay")
2063 |   extendWithoutNotice             Boolean?  @map("ExtendWithoutNotice")
2064 |   extendPeriodYear                Int?      @map("ExtendPeriodYear")
2065 |   extendPeriodMonth               Int?      @map("ExtendPeriodMonth")
2066 |   autoCircleCount                 Int?      @map("AutoCircleCount")
2067 |   terminationWithoutNotice        Boolean?  @map("TerminationWithoutNotice")
2068 |   companySign                     String?   @map("CompanySign") @db.NVarChar(Max)
2069 |   companySignIdList               String?   @map("CompanySignIDList") @db.NVarChar(Max)
2070 |   finalCost                       Decimal?  @map("FinalCost") @db.Decimal(18, 2)
2071 |   dispatcherExaminerName          String?   @map("DispatcherExaminerNames") @db.NVarChar(Max)
2072 |   batchReviewStatusId             Int?      @map("BatchReviewStatusID")
2073 |   currentStatusStageId            Int?      @map("CurrentStatusStageID")
2074 |   txt01                           String?   @map("Txt01") @db.NVarChar(Max)
2075 |   txt02                           String?   @map("Txt02") @db.NVarChar(Max)
2076 |   txt03                           String?   @map("Txt03") @db.NVarChar(Max)
2077 |   txt04                           String?   @map("Txt04") @db.NVarChar(Max)
2078 |   txt05                           String?   @map("Txt05") @db.NVarChar(Max)
2079 |   txt06                           String?   @map("Txt06") @db.NVarChar(Max)
2080 |   txt07                           String?   @map("Txt07") @db.NVarChar(Max)
2081 |   txt08                           String?   @map("Txt08") @db.NVarChar(Max)
2082 |   txt09                           String?   @map("Txt09") @db.NVarChar(Max)
2083 |   txt10                           String?   @map("Txt10") @db.NVarChar(Max)
2084 |   memo01                          String?   @map("Memo01") @db.NVarChar(Max)
2085 |   memo02                          String?   @map("Memo02") @db.NVarChar(Max)
2086 |   memo03                          String?   @map("Memo03") @db.NVarChar(Max)
2087 |   memo04                          String?   @map("Memo04") @db.NVarChar(Max)
2088 |   memo05                          String?   @map("Memo05") @db.NVarChar(Max)
2089 |   memo06                          String?   @map("Memo06") @db.NVarChar(Max)
2090 |   memo07                          String?   @map("Memo07") @db.NVarChar(Max)
2091 |   memo08                          String?   @map("Memo08") @db.NVarChar(Max)
2092 |   memo09                          String?   @map("Memo09") @db.NVarChar(Max)
2093 |   memo10                          String?   @map("Memo10") @db.NVarChar(Max)
2094 |   memo11                          String?   @map("Memo11") @db.NVarChar(Max)
2095 |   memo12                          String?   @map("Memo12") @db.NVarChar(Max)
2096 |   memo13                          String?   @map("Memo13") @db.NVarChar(Max)
2097 |   memo14                          String?   @map("Memo14") @db.NVarChar(Max)
2098 |   memo15                          String?   @map("Memo15") @db.NVarChar(Max)
2099 |   radio01                         String?   @map("Radio01") @db.NVarChar(Max)
2100 |   radio02                         String?   @map("Radio02") @db.NVarChar(Max)
2101 |   radio03                         String?   @map("Radio03") @db.NVarChar(Max)
2102 |   radio04                         String?   @map("Radio04") @db.NVarChar(Max)
2103 |   radio05                         String?   @map("Radio05") @db.NVarChar(Max)
2104 |   checkBox01                      String?   @map("CheckBox01") @db.NVarChar(Max)
2105 |   checkBox02                      String?   @map("CheckBox02") @db.NVarChar(Max)
2106 |   checkBox03                      String?   @map("CheckBox03") @db.NVarChar(Max)
2107 |   checkBox04                      String?   @map("CheckBox04") @db.NVarChar(Max)
2108 |   checkBox05                      String?   @map("CheckBox05") @db.NVarChar(Max)
2109 |   select01                        String?   @map("Select01") @db.NVarChar(Max)
2110 |   select02                        String?   @map("Select02") @db.NVarChar(Max)
2111 |   select03                        String?   @map("Select03") @db.NVarChar(Max)
2112 |   select04                        String?   @map("Select04") @db.NVarChar(Max)
2113 |   select05                        String?   @map("Select05") @db.NVarChar(Max)
2114 |   int01                           Int?      @map("Int01")
2115 |   int02                           Int?      @map("Int02")
2116 |   int03                           Int?      @map("Int03")
2117 |   int04                           Int?      @map("Int04")
2118 |   int05                           Int?      @map("Int05")
2119 |   double01                        Decimal?  @map("Double01") @db.Decimal(18, 8)
2120 |   double02                        Decimal?  @map("Double02") @db.Decimal(18, 8)
2121 |   double03                        Decimal?  @map("Double03") @db.Decimal(18, 8)
2122 |   double04                        Decimal?  @map("Double04") @db.Decimal(18, 8)
2123 |   double05                        Decimal?  @map("Double05") @db.Decimal(18, 8)
2124 |   date01                          DateTime? @map("Date01") @db.DateTime
2125 |   date02                          DateTime? @map("Date02") @db.DateTime
2126 |   date03                          DateTime? @map("Date03") @db.DateTime
2127 |   date04                          DateTime? @map("Date04") @db.DateTime
2128 |   date05                          DateTime? @map("Date05") @db.DateTime
2129 |   date06                          DateTime? @map("Date06") @db.DateTime
2130 |   date07                          DateTime? @map("Date07") @db.DateTime
2131 |   date08                          DateTime? @map("Date08") @db.DateTime
2132 |   date09                          DateTime? @map("Date09") @db.DateTime
2133 |   date10                          DateTime? @map("Date10") @db.DateTime
2134 |   combine01                       String?   @map("Combine01") @db.NVarChar(Max)
2135 |   combine02                       String?   @map("Combine02") @db.NVarChar(Max)
2136 |   combine03                       String?   @map("Combine03") @db.NVarChar(Max)
2137 |   combine04                       String?   @map("Combine04") @db.NVarChar(Max)
2138 |   combine05                       String?   @map("Combine05") @db.NVarChar(Max)
2139 |   allPartner                      String?   @map("AllPartners") @db.NVarChar(Max)
2140 |   contractModuleSn                Int?      @map("ContractModuleSN")
2141 |   finalCostExchangeRate           Decimal?  @map("FinalCostExchangeRate") @db.Decimal(10, 2)
2142 |   durationOtherMsg                String?   @map("DurationOtherMsg") @db.NVarChar(Max)
2143 |   autoExtendContract              Int?      @map("AutoExtendContract")
2144 |   autoExtendLimited               Int?      @map("AutoExtendLimited")
2145 |   autoExtendLimitedFrequency      Int?      @map("AutoExtendLimitedFrequency")
2146 |   autoExtendFrequency             Int?      @map("AutoExtendFrequency")
2147 |   lastAutoExtendDate              DateTime? @map("LastAutoExtendDate") @db.DateTime
2148 |   renewalPeriod                   String?   @map("RenewalPeriod") @db.NVarChar(50)
2149 |   extendFrequency                 String?   @map("ExtendFrequency") @db.NVarChar(50)
2150 |   signDemand                      String?   @map("SignDemand") @db.NVarChar(50)
2151 |   contractStampDutyName           String?   @map("ContractStampDutyName") @db.NVarChar(50)
2152 |   contractStampDuty               Int?      @map("ContractStampDuty")
2153 |   stampDutyDescription            String?   @map("StampDutyDescription") @db.NVarChar(Max)
2154 |   contractTypeCode                String?   @map("ContractTypeCode") @db.NVarChar(Max)
2155 |   attributionRight                Int?      @map("AttributionRights")
2156 |   attributionRightsText           String?   @map("AttributionRightsText") @db.NVarChar(Max)
2157 |   confidentialityRequirement      Int?      @map("ConfidentialityRequirements")
2158 |   confidentialityRequirementsText String?   @map("ConfidentialityRequirementsText") @db.NVarChar(Max)
2159 |   noInfringementGuarantee         Int?      @map("NoInfringementGuarantee")
2160 |   noInfringementGuaranteeText     String?   @map("NoInfringementGuaranteeText") @db.NVarChar(Max)
2161 |   infringementInvestigation       Int?      @map("InfringementInvestigation")
2162 |   infringementInvestigationText   String?   @map("InfringementInvestigationText") @db.NVarChar(Max)
2163 |   contractAccessTypeSn            Int?      @map("ContractAccessTypeSN")
2164 |   contractAccessTypeMemo          String?   @map("ContractAccessTypeMemo") @db.NVarChar(Max)
2165 |   accessStartDate                 DateTime? @map("AccessStartDate") @db.DateTime
2166 |   accessEndDate                   DateTime? @map("AccessEndDate") @db.DateTime
2167 |   contractAccessDescript          String?   @map("ContractAccessDescript") @db.NVarChar(Max)
2168 |   contractAccessReason            String?   @map("ContractAccessReason") @db.NVarChar(Max)
2169 |   searchStartDate                 DateTime? @map("SearchStartDate") @db.DateTime
2170 |   searchEndDate                   DateTime? @map("SearchEndDate") @db.DateTime
2171 |   contractAccessTypeName          String?   @map("ContractAccessTypeName") @db.NVarChar(450)
2172 |   lastModifyDate                  DateTime? @map("LastModifyDate") @db.DateTime
2173 |   myLatestSignDate                DateTime? @map("MyLatestSignDate") @db.DateTime
2174 |   partnerLatestSignDate           DateTime? @map("PartnerLatestSignDate") @db.DateTime
2175 |   newProcessDay                   Int?      @map("NewProcessDay")
2176 |   country                         String?   @map("Country") @db.NVarChar(200)
2177 |   classification                  String?   @map("Classifications") @db.NVarChar(Max)
2178 |   txt11                           String?   @map("Txt11") @db.NVarChar(Max)
2179 |   txt12                           String?   @map("Txt12") @db.NVarChar(Max)
2180 |   txt13                           String?   @map("Txt13") @db.NVarChar(Max)
2181 |   txt14                           String?   @map("Txt14") @db.NVarChar(Max)
2182 |   txt15                           String?   @map("Txt15") @db.NVarChar(Max)
2183 |   txt16                           String?   @map("Txt16") @db.NVarChar(Max)
2184 |   txt17                           String?   @map("Txt17") @db.NVarChar(Max)
2185 |   txt18                           String?   @map("Txt18") @db.NVarChar(Max)
2186 |   txt19                           String?   @map("Txt19") @db.NVarChar(Max)
2187 |   txt20                           String?   @map("Txt20") @db.NVarChar(Max)
2188 |   txt21                           String?   @map("Txt21") @db.NVarChar(Max)
2189 |   txt22                           String?   @map("Txt22") @db.NVarChar(Max)
2190 |   txt23                           String?   @map("Txt23") @db.NVarChar(Max)
2191 |   txt24                           String?   @map("Txt24") @db.NVarChar(Max)
2192 |   txt25                           String?   @map("Txt25") @db.NVarChar(Max)
2193 |   txt26                           String?   @map("Txt26") @db.NVarChar(Max)
2194 |   txt27                           String?   @map("Txt27") @db.NVarChar(Max)
2195 |   txt28                           String?   @map("Txt28") @db.NVarChar(Max)
2196 |   txt29                           String?   @map("Txt29") @db.NVarChar(Max)
2197 |   txt30                           String?   @map("Txt30") @db.NVarChar(Max)
2198 |   txt31                           String?   @map("Txt31") @db.NVarChar(Max)
2199 |   txt32                           String?   @map("Txt32") @db.NVarChar(Max)
2200 |   txt33                           String?   @map("Txt33") @db.NVarChar(Max)
2201 |   txt34                           String?   @map("Txt34") @db.NVarChar(Max)
2202 |   txt35                           String?   @map("Txt35") @db.NVarChar(Max)
2203 |   memo16                          String?   @map("Memo16") @db.NVarChar(Max)
2204 |   memo17                          String?   @map("Memo17") @db.NVarChar(Max)
2205 |   memo18                          String?   @map("Memo18") @db.NVarChar(Max)
2206 |   memo19                          String?   @map("Memo19") @db.NVarChar(Max)
2207 |   memo20                          String?   @map("Memo20") @db.NVarChar(Max)
2208 |   radio06                         String?   @map("Radio06") @db.NVarChar(Max)
2209 |   radio07                         String?   @map("Radio07") @db.NVarChar(Max)
2210 |   radio08                         String?   @map("Radio08") @db.NVarChar(Max)
2211 |   radio09                         String?   @map("Radio09") @db.NVarChar(Max)
2212 |   radio10                         String?   @map("Radio10") @db.NVarChar(Max)
2213 |   checkBox06                      String?   @map("CheckBox06") @db.NVarChar(Max)
2214 |   checkBox07                      String?   @map("CheckBox07") @db.NVarChar(Max)
2215 |   checkBox08                      String?   @map("CheckBox08") @db.NVarChar(Max)
2216 |   checkBox09                      String?   @map("CheckBox09") @db.NVarChar(Max)
2217 |   checkBox10                      String?   @map("CheckBox10") @db.NVarChar(Max)
2218 |   checkBox11                      String?   @map("CheckBox11") @db.NVarChar(Max)
2219 |   checkBox12                      String?   @map("CheckBox12") @db.NVarChar(Max)
2220 |   checkBox13                      String?   @map("CheckBox13") @db.NVarChar(Max)
2221 |   checkBox14                      String?   @map("CheckBox14") @db.NVarChar(Max)
2222 |   checkBox15                      String?   @map("CheckBox15") @db.NVarChar(Max)
2223 |   checkBox16                      String?   @map("CheckBox16") @db.NVarChar(Max)
2224 |   checkBox17                      String?   @map("CheckBox17") @db.NVarChar(Max)
2225 |   checkBox18                      String?   @map("CheckBox18") @db.NVarChar(Max)
2226 |   checkBox19                      String?   @map("CheckBox19") @db.NVarChar(Max)
2227 |   checkBox20                      String?   @map("CheckBox20") @db.NVarChar(Max)
2228 |   select06                        String?   @map("Select06") @db.NVarChar(Max)
2229 |   select07                        String?   @map("Select07") @db.NVarChar(Max)
2230 |   select08                        String?   @map("Select08") @db.NVarChar(Max)
2231 |   select09                        String?   @map("Select09") @db.NVarChar(Max)
2232 |   select10                        String?   @map("Select10") @db.NVarChar(Max)
2233 |   select11                        String?   @map("Select11") @db.NVarChar(Max)
2234 |   select12                        String?   @map("Select12") @db.NVarChar(Max)
2235 |   select13                        String?   @map("Select13") @db.NVarChar(Max)
2236 |   select14                        String?   @map("Select14") @db.NVarChar(Max)
2237 |   select15                        String?   @map("Select15") @db.NVarChar(Max)
2238 |   select16                        String?   @map("Select16") @db.NVarChar(Max)
2239 |   select17                        String?   @map("Select17") @db.NVarChar(Max)
2240 |   select18                        String?   @map("Select18") @db.NVarChar(Max)
2241 |   select19                        String?   @map("Select19") @db.NVarChar(Max)
2242 |   select20                        String?   @map("Select20") @db.NVarChar(Max)
2243 |   int06                           Int?      @map("Int06")
2244 |   int07                           Int?      @map("Int07")
2245 |   int08                           Int?      @map("Int08")
2246 |   int09                           Int?      @map("Int09")
2247 |   int10                           Int?      @map("Int10")
2248 |   int11                           Int?      @map("Int11")
2249 |   int12                           Int?      @map("Int12")
2250 |   int13                           Int?      @map("Int13")
2251 |   int14                           Int?      @map("Int14")
2252 |   int15                           Int?      @map("Int15")
2253 |   int16                           Int?      @map("Int16")
2254 |   int17                           Int?      @map("Int17")
2255 |   int18                           Int?      @map("Int18")
2256 |   int19                           Int?      @map("Int19")
2257 |   int20                           Int?      @map("Int20")
2258 |   double06                        Decimal?  @map("Double06") @db.Decimal(18, 8)
2259 |   double07                        Decimal?  @map("Double07") @db.Decimal(18, 8)
2260 |   double08                        Decimal?  @map("Double08") @db.Decimal(18, 8)
2261 |   double09                        Decimal?  @map("Double09") @db.Decimal(18, 8)
2262 |   double10                        Decimal?  @map("Double10") @db.Decimal(18, 8)
2263 |   double11                        Decimal?  @map("Double11") @db.Decimal(18, 8)
2264 |   double12                        Decimal?  @map("Double12") @db.Decimal(18, 8)
2265 |   double13                        Decimal?  @map("Double13") @db.Decimal(18, 8)
2266 |   double14                        Decimal?  @map("Double14") @db.Decimal(18, 8)
2267 |   double15                        Decimal?  @map("Double15") @db.Decimal(18, 8)
2268 |   double16                        Decimal?  @map("Double16") @db.Decimal(18, 8)
2269 |   double17                        Decimal?  @map("Double17") @db.Decimal(18, 8)
2270 |   double18                        Decimal?  @map("Double18") @db.Decimal(18, 8)
2271 |   double19                        Decimal?  @map("Double19") @db.Decimal(18, 8)
2272 |   double20                        Decimal?  @map("Double20") @db.Decimal(18, 8)
2273 |   contract                        Contract  @relation(fields: [contractId], references: [contractId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ContractViewTemp_Contract")
2274 | 
2275 |   @@index([accessEndDate], map: "IX_ContractViewTemp_AccessEndDate")
2276 |   @@index([accessStartDate], map: "IX_ContractViewTemp_AccessStartDate")
2277 |   @@index([alertBccEmail], map: "IX_ContractViewTemp_AlertBCCEmails")
2278 |   @@index([alertBeginDate], map: "IX_ContractViewTemp_AlertBeginDate")
2279 |   @@index([alertCcEmail], map: "IX_ContractViewTemp_AlertCCEmails")
2280 |   @@index([alertEmail], map: "IX_ContractViewTemp_AlertEmails")
2281 |   @@index([alertEndDate], map: "IX_ContractViewTemp_AlertEndDate")
2282 |   @@index([alertExtend], map: "IX_ContractViewTemp_AlertExtend")
2283 |   @@index([alertPeriod], map: "IX_ContractViewTemp_AlertPeriod")
2284 |   @@index([applicantDepartmentId], map: "IX_ContractViewTemp_ApplicantDepartmentID")
2285 |   @@index([applicantDepartmentName], map: "IX_ContractViewTemp_ApplicantDepartmentName")
2286 |   @@index([applicantParentDepartmentId], map: "IX_ContractViewTemp_ApplicantParentDepartmentID")
2287 |   @@index([applicantSiteName], map: "IX_ContractViewTemp_ApplicantSiteName")
2288 |   @@index([applicationDate], map: "IX_ContractViewTemp_ApplicationDate")
2289 |   @@index([applyNo], map: "IX_ContractViewTemp_ApplyNo")
2290 |   @@index([attributionRight], map: "IX_ContractViewTemp_AttributionRights")
2291 |   @@index([autoCircleCount], map: "IX_ContractViewTemp_AutoCircleCount")
2292 |   @@index([autoExtend], map: "IX_ContractViewTemp_AutoExtend")
2293 |   @@index([autoExtendContract], map: "IX_ContractViewTemp_AutoExtendContract")
2294 |   @@index([autoExtendFrequency], map: "IX_ContractViewTemp_AutoExtendFrequency")
2295 |   @@index([autoExtendLimited], map: "IX_ContractViewTemp_AutoExtendLimited")
2296 |   @@index([autoExtendLimitedFrequency], map: "IX_ContractViewTemp_AutoExtendLimitedFrequency")
2297 |   @@index([autoRenewDeadline], map: "IX_ContractViewTemp_AutoRenewDeadline")
2298 |   @@index([autoRenewNewDate], map: "IX_ContractViewTemp_AutoRenewNewDate")
2299 |   @@index([autoRenewValidEndDate], map: "IX_ContractViewTemp_AutoRenewValidEndDate")
2300 |   @@index([backStageId], map: "IX_ContractViewTemp_BackStageID")
2301 |   @@index([batchReviewStatusId], map: "IX_ContractViewTemp_BatchReviewStatusID")
2302 |   @@index([branchId], map: "IX_ContractViewTemp_BranchID")
2303 |   @@index([branchName], map: "IX_ContractViewTemp_BranchName")
2304 |   @@index([closeCaseBeforeDay], map: "IX_ContractViewTemp_CloseCaseBeforeDay")
2305 |   @@index([closeCaseBeforeMonth], map: "IX_ContractViewTemp_CloseCaseBeforeMonth")
2306 |   @@index([closeStage], map: "IX_ContractViewTemp_CloseStage")
2307 |   @@index([closeStageId], map: "IX_ContractViewTemp_CloseStageID")
2308 |   @@index([closeStatusId], map: "IX_ContractViewTemp_CloseStatusID")
2309 |   @@index([closeStatusId, contractModuleSn], map: "IX_ContractViewTemp_CloseStatusID_ContractModuleSN")
2310 |   @@index([companySignId], map: "IX_ContractViewTemp_CompanySignID")
2311 |   @@index([confidentialityRequirement], map: "IX_ContractViewTemp_ConfidentialityRequirements")
2312 |   @@index([contractAccessTypeName], map: "IX_ContractViewTemp_ContractAccessTypeName")
2313 |   @@index([contractAccessTypeSn], map: "IX_ContractViewTemp_ContractAccessTypeSN")
2314 |   @@index([contractFlowId], map: "IX_ContractViewTemp_ContractFlowID")
2315 |   @@index([contractGuid], map: "IX_ContractViewTemp_ContractGUID")
2316 |   @@index([contractModuleSn], map: "IX_ContractViewTemp_ContractModuleSN")
2317 |   @@index([contractStampDuty], map: "IX_ContractViewTemp_ContractStampDuty")
2318 |   @@index([contractStampDutyName], map: "IX_ContractViewTemp_ContractStampDutyName")
2319 |   @@index([cost], map: "IX_ContractViewTemp_Cost")
2320 |   @@index([costNtd], map: "IX_ContractViewTemp_CostNTD")
2321 |   @@index([country], map: "IX_ContractViewTemp_Country")
2322 |   @@index([createDate], map: "IX_ContractViewTemp_CreateDate")
2323 |   @@index([currentExaminerId], map: "IX_ContractViewTemp_CurrentExaminerID")
2324 |   @@index([currentExaminerSn], map: "IX_ContractViewTemp_CurrentExaminerSn")
2325 |   @@index([currentStage], map: "IX_ContractViewTemp_CurrentStage")
2326 |   @@index([currentStageId], map: "IX_ContractViewTemp_CurrentStageID")
2327 |   @@index([currentStageIdList], map: "IX_ContractViewTemp_CurrentStageIDList")
2328 |   @@index([currentStatusStageId], map: "IX_ContractViewTemp_CurrentStatusStageID")
2329 |   @@index([cusProductProjectName], map: "IX_ContractViewTemp_Cus_ProductProjectName")
2330 |   @@index([date01], map: "IX_ContractViewTemp_Date01")
2331 |   @@index([date02], map: "IX_ContractViewTemp_Date02")
2332 |   @@index([date03], map: "IX_ContractViewTemp_Date03")
2333 |   @@index([date04], map: "IX_ContractViewTemp_Date04")
2334 |   @@index([date05], map: "IX_ContractViewTemp_Date05")
2335 |   @@index([date06], map: "IX_ContractViewTemp_Date06")
2336 |   @@index([date07], map: "IX_ContractViewTemp_Date07")
2337 |   @@index([date08], map: "IX_ContractViewTemp_Date08")
2338 |   @@index([date09], map: "IX_ContractViewTemp_Date09")
2339 |   @@index([date10], map: "IX_ContractViewTemp_Date10")
2340 |   @@index([departmentIdName], map: "IX_ContractViewTemp_DepartmentIDName")
2341 |   @@index([departmentName], map: "IX_ContractViewTemp_DepartmentName")
2342 |   @@index([documentName], map: "IX_ContractViewTemp_DocumentName")
2343 |   @@index([double01], map: "IX_ContractViewTemp_Double01")
2344 |   @@index([double02], map: "IX_ContractViewTemp_Double02")
2345 |   @@index([double03], map: "IX_ContractViewTemp_Double03")
2346 |   @@index([double04], map: "IX_ContractViewTemp_Double04")
2347 |   @@index([double05], map: "IX_ContractViewTemp_Double05")
2348 |   @@index([double06], map: "IX_ContractViewTemp_Double06")
2349 |   @@index([double07], map: "IX_ContractViewTemp_Double07")
2350 |   @@index([double08], map: "IX_ContractViewTemp_Double08")
2351 |   @@index([double09], map: "IX_ContractViewTemp_Double09")
2352 |   @@index([double10], map: "IX_ContractViewTemp_Double10")
2353 |   @@index([double11], map: "IX_ContractViewTemp_Double11")
2354 |   @@index([double12], map: "IX_ContractViewTemp_Double12")
2355 |   @@index([double13], map: "IX_ContractViewTemp_Double13")
2356 |   @@index([double14], map: "IX_ContractViewTemp_Double14")
2357 |   @@index([double15], map: "IX_ContractViewTemp_Double15")
2358 |   @@index([double16], map: "IX_ContractViewTemp_Double16")
2359 |   @@index([double17], map: "IX_ContractViewTemp_Double17")
2360 |   @@index([double18], map: "IX_ContractViewTemp_Double18")
2361 |   @@index([double19], map: "IX_ContractViewTemp_Double19")
2362 |   @@index([double20], map: "IX_ContractViewTemp_Double20")
2363 |   @@index([effectiveDate], map: "IX_ContractViewTemp_EffectiveDate")
2364 |   @@index([examDate], map: "IX_ContractViewTemp_ExamDate")
2365 |   @@index([exchangeTypeId], map: "IX_ContractViewTemp_ExchangeTypeID")
2366 |   @@index([extendFrequency], map: "IX_ContractViewTemp_ExtendFrequency")
2367 |   @@index([extendMonth], map: "IX_ContractViewTemp_ExtendMonth")
2368 |   @@index([extendPeriodMonth], map: "IX_ContractViewTemp_ExtendPeriodMonth")
2369 |   @@index([extendPeriodYear], map: "IX_ContractViewTemp_ExtendPeriodYear")
2370 |   @@index([extendWithoutNotice], map: "IX_ContractViewTemp_ExtendWithoutNotice")
2371 |   @@index([extendYear], map: "IX_ContractViewTemp_ExtendYear")
2372 |   @@index([factoryidname], map: "IX_ContractViewTemp_factoryidname")
2373 |   @@index([finalCost], map: "IX_ContractViewTemp_FinalCost")
2374 |   @@index([finalCostExchangeRate], map: "IX_ContractViewTemp_FinalCostExchangeRate")
2375 |   @@index([finalCostExchangeTypeId], map: "IX_ContractViewTemp_FinalCostExchangeTypeID")
2376 |   @@index([finalCostNtd], map: "IX_ContractViewTemp_FinalCostNTD")
2377 |   @@index([idname], map: "IX_ContractViewTemp_Idname")
2378 |   @@index([infringementInvestigation], map: "IX_ContractViewTemp_InfringementInvestigation")
2379 |   @@index([int01], map: "IX_ContractViewTemp_Int01")
2380 |   @@index([int02], map: "IX_ContractViewTemp_Int02")
2381 |   @@index([int03], map: "IX_ContractViewTemp_Int03")
2382 |   @@index([int04], map: "IX_ContractViewTemp_Int04")
2383 |   @@index([int05], map: "IX_ContractViewTemp_Int05")
2384 |   @@index([int06], map: "IX_ContractViewTemp_Int06")
2385 |   @@index([int07], map: "IX_ContractViewTemp_Int07")
2386 |   @@index([int08], map: "IX_ContractViewTemp_Int08")
2387 |   @@index([int09], map: "IX_ContractViewTemp_Int09")
2388 |   @@index([int10], map: "IX_ContractViewTemp_Int10")
2389 |   @@index([int11], map: "IX_ContractViewTemp_Int11")
2390 |   @@index([int12], map: "IX_ContractViewTemp_Int12")
2391 |   @@index([int13], map: "IX_ContractViewTemp_Int13")
2392 |   @@index([int14], map: "IX_ContractViewTemp_Int14")
2393 |   @@index([int15], map: "IX_ContractViewTemp_Int15")
2394 |   @@index([int16], map: "IX_ContractViewTemp_Int16")
2395 |   @@index([int17], map: "IX_ContractViewTemp_Int17")
2396 |   @@index([int18], map: "IX_ContractViewTemp_Int18")
2397 |   @@index([int19], map: "IX_ContractViewTemp_Int19")
2398 |   @@index([int20], map: "IX_ContractViewTemp_Int20")
2399 |   @@index([lastAutoExtendDate], map: "IX_ContractViewTemp_LastAutoExtendDate")
2400 |   @@index([lastModifyDate], map: "IX_ContractViewTemp_LastModifyDate")
2401 |   @@index([lastSendMailDate], map: "IX_ContractViewTemp_LastSendMailDate")
2402 |   @@index([noInfringementGuarantee], map: "IX_ContractViewTemp_NoInfringementGuarantee")
2403 |   @@index([processDay], map: "IX_ContractViewTemp_ProcessDay")
2404 |   @@index([provisionDate], map: "IX_ContractViewTemp_ProvisionDate")
2405 |   @@index([receiveDate], map: "IX_ContractViewTemp_ReceiveDate")
2406 |   @@index([receiveNo], map: "IX_ContractViewTemp_ReceiveNo")
2407 |   @@index([recorderDepartment], map: "IX_ContractViewTemp_RecorderDepartment")
2408 |   @@index([recorderEmployeeId], map: "IX_ContractViewTemp_RecorderEmployeeID")
2409 |   @@index([recorderExt], map: "IX_ContractViewTemp_RecorderExt")
2410 |   @@index([recorderId], map: "IX_ContractViewTemp_RecorderID")
2411 |   @@index([renewalPeriod], map: "IX_ContractViewTemp_RenewalPeriod")
2412 |   @@index([requirePartnerSign], map: "IX_ContractViewTemp_RequirePartnerSign")
2413 |   @@index([requireSign], map: "IX_ContractViewTemp_RequireSign")
2414 |   @@index([saveDate], map: "IX_ContractViewTemp_SaveDate")
2415 |   @@index([saveNo], map: "IX_ContractViewTemp_SaveNo")
2416 |   @@index([searchEndDate], map: "IX_ContractViewTemp_SearchEndDate")
2417 |   @@index([searchStartDate], map: "IX_ContractViewTemp_SearchStartDate")
2418 |   @@index([shortName], map: "IX_ContractViewTemp_ShortName")
2419 |   @@index([signDemand], map: "IX_ContractViewTemp_SignDemand")
2420 |   @@index([signTypeId], map: "IX_ContractViewTemp_SignTypeID")
2421 |   @@index([terminationWithoutNotice], map: "IX_ContractViewTemp_TerminationWithoutNotice")
2422 |   @@index([urgentLevel], map: "IX_ContractViewTemp_UrgentLevel")
2423 |   @@index([urgentLevelId], map: "IX_ContractViewTemp_UrgentLevelID")
2424 |   @@index([validDuration], map: "IX_ContractViewTemp_ValidDuration")
2425 |   @@index([validEndDate], map: "IX_ContractViewTemp_ValidEndDate")
2426 |   @@index([validStartDate], map: "IX_ContractViewTemp_ValidStartDate")
2427 |   @@index([weekNo], map: "IX_ContractViewTemp_weekNo")
2428 |   @@schema("dbo")
2429 | }
2430 | 
2431 | model CountryCode {
2432 |   sn              Int              @id(map: "PK_CountryCode") @default(autoincrement()) @map("Sn")
2433 |   countryName     String           @map("CountryName") @db.NVarChar(350)
2434 |   countryEngName  String?          @map("CountryEngName") @db.NVarChar(350)
2435 |   code            String           @map("Code") @db.NVarChar(100)
2436 |   disable         Boolean?         @map("Disable")
2437 |   contracts       Contract[]
2438 |   contractCustoms ContractCustom[]
2439 | 
2440 |   @@index([code], map: "IX_CountryCode_Code")
2441 |   @@index([countryEngName], map: "IX_CountryCode_CountryEngName")
2442 |   @@index([countryName], map: "IX_CountryCode_CountryName")
2443 |   @@schema("code")
2444 | }
2445 | 
2446 | model CsExamResult {
2447 |   csExamResultId        Int                    @id(map: "PK_CSExamResult") @default(autoincrement()) @map("CSExamResultID")
2448 |   name                  String?                @map("Name") @db.NVarChar(125)
2449 |   systemDefine          Boolean?               @map("SystemDefine")
2450 |   disable               Boolean?               @map("Disable")
2451 |   resultSeq             Int?                   @map("ResultSeq")
2452 |   csExamResultLanguages CsExamResultLanguage[]
2453 |   otherExaminers        OtherExaminer[]
2454 | 
2455 |   @@index([name], map: "IX_CSExamResult_Name")
2456 |   @@index([resultSeq], map: "IX_CSExamResult_ResultSeq")
2457 |   @@map("CSExamResult")
2458 |   @@schema("code")
2459 | }
2460 | 
2461 | model CsExamResultLanguage {
2462 |   sn             Int          @id(map: "PK_CSExamResultLanguage") @default(autoincrement()) @map("Sn")
2463 |   csExamResultId Int          @map("CSExamResultID")
2464 |   languageCode   String       @map("LanguageCode") @db.VarChar(20)
2465 |   name           String?      @map("Name") @db.NVarChar(255)
2466 |   csExamResult   CsExamResult @relation(fields: [csExamResultId], references: [csExamResultId], onDelete: Cascade, map: "FK_CSExamResultLanguage_CSExamResult")
2467 | 
2468 |   @@index([csExamResultId], map: "IX_CSExamResultLanguage_CSExamResultID")
2469 |   @@index([languageCode], map: "IX_CSExamResultLanguage_LanguageCode")
2470 |   @@index([name], map: "IX_CSExamResultLanguage_Name")
2471 |   @@map("CSExamResultLanguage")
2472 |   @@schema("join")
2473 | }
2474 | 
2475 | model CustomExtendField {
2476 |   sn                Int     @id(map: "PK_CustomExtendField") @default(autoincrement()) @map("Sn")
2477 |   tableName         String  @map("TableName") @db.NVarChar(50)
2478 |   columnName        String  @map("ColumnName") @db.NVarChar(50)
2479 |   enable            Boolean @default(true, map: "DF_CustomExtendField_Enable") @map("Enable")
2480 |   displayName       String  @map("DisplayName") @db.NVarChar(255)
2481 |   languageXml       String? @map("LanguageXml") @db.Xml
2482 |   booleanSearchType String? @default("N'BooleanSearchText'", map: "DF_CustomExtendField_BooleanSearchType") @map("BooleanSearchType") @db.NVarChar(255)
2483 | 
2484 |   @@index([booleanSearchType], map: "IX_CustomExtendField_BooleanSearchType")
2485 |   @@index([columnName], map: "IX_CustomExtendField_ColumnName")
2486 |   @@index([displayName], map: "IX_CustomExtendField_DisplayName")
2487 |   @@index([tableName], map: "IX_CustomExtendField_TableName")
2488 |   @@schema("data")
2489 | }
2490 | 
2491 | model CustomizeField {
2492 |   customizeFieldSn Int      @id(map: "PK_CustomizeField") @default(autoincrement()) @map("CustomizeFieldSn")
2493 |   columnName       String   @map("ColumnName") @db.NVarChar(150)
2494 |   displayName      String   @map("DisplayName") @db.NVarChar(Max)
2495 |   defaultValue     String?  @map("DefaultValue") @db.NVarChar(Max)
2496 |   required         Boolean? @map("Required")
2497 |   option           String?  @map("Options") @db.NVarChar(450)
2498 |   digit            Int?     @map("Digit")
2499 |   timeVisible      Boolean? @map("TimeVisible")
2500 |   enabled          Boolean  @map("Enabled")
2501 |   showBlock        String?  @map("ShowBlock") @db.NVarChar(450)
2502 | 
2503 |   @@index([columnName], map: "IX_CustomizeField_ColumnName")
2504 |   @@index([digit], map: "IX_CustomizeField_Digit")
2505 |   @@index([option], map: "IX_CustomizeField_Options")
2506 |   @@index([showBlock], map: "IX_CustomizeField_ShowBlock")
2507 |   @@schema("dbo")
2508 | }
2509 | 
2510 | model DbVersionUpdateHistory {
2511 |   sn                Int       @id(map: "PK_DBVersionUpdateHistory_SN") @default(autoincrement()) @map("SN")
2512 |   version           String    @map("Version") @db.NVarChar(450)
2513 |   isCustomization   Boolean   @map("IsCustomization")
2514 |   filePath          String    @map("FilePath") @db.NVarChar(Max)
2515 |   sql               String    @map("SQL") @db.NVarChar(Max)
2516 |   lastUpdateStatus  String?   @map("LastUpdateStatus") @db.NVarChar(450)
2517 |   lastUpdateMessage String?   @map("LastUpdateMessage") @db.NVarChar(Max)
2518 |   lastUpdateDate    DateTime? @default(now(), map: "DF_DBVersionUpdateHistory_LastExecuteDate") @map("LastUpdateDate") @db.DateTime
2519 |   createDate        DateTime  @default(now(), map: "DF_DBVersionUpdateHistory_CreateDate") @map("CreateDate") @db.DateTime
2520 | 
2521 |   @@index([createDate], map: "IX_DBVersionUpdateHistory_CreateDate")
2522 |   @@index([lastUpdateStatus], map: "IX_DBVersionUpdateHistory_LastUpdateStatus")
2523 |   @@index([version], map: "IX_DBVersionUpdateHistory_Version")
2524 |   @@map("DBVersionUpdateHistory")
2525 |   @@schema("dbo")
2526 | }
2527 | 
2528 | model Department {
2529 |   departmentId                                          Int                                       @id(map: "PK_Department") @default(autoincrement()) @map("DepartmentID")
2530 |   name                                                  String?                                   @map("Name") @db.NVarChar(255)
2531 |   createDate                                            DateTime?                                 @map("CreateDate") @db.DateTime
2532 |   parentId                                              Int?                                      @map("ParentID")
2533 |   departmentIdName                                      String?                                   @map("DepartmentIDName") @db.NVarChar(125)
2534 |   englishName                                           String?                                   @map("EnglishName") @db.NVarChar(255)
2535 |   shortName                                             String?                                   @map("ShortName") @db.NVarChar(125)
2536 |   startDate                                             DateTime?                                 @map("StartDate") @db.DateTime
2537 |   endDate                                               DateTime?                                 @map("EndDate") @db.DateTime
2538 |   disable                                               Boolean?                                  @default(false, map: "DF_Department_Disable") @map("Disable")
2539 |   factoryIdName                                         String?                                   @map("FactoryIDName") @db.NVarChar(255)
2540 |   isVisable                                             Boolean                                   @default(true, map: "DF_Department_Visable") @map("IsVisable")
2541 |   txt01                                                 String?                                   @map("Txt01") @db.NVarChar(255)
2542 |   bool01                                                Boolean?
2543 |   deptLeaderId                                          Int?                                      @map("Dept_Leader_ID")
2544 |   exchangeTypeId                                        Int?                                      @map("ExchangeTypeID")
2545 |   cost                                                  Decimal?                                  @map("Cost") @db.Decimal(18, 2)
2546 |   contractContractBranchIdToDepartments                 Contract[]                                @relation("Contract_BranchIDToDepartment")
2547 |   contractContractApplicantDepartmentIdToDepartments    Contract[]                                @relation("Contract_ApplicantDepartmentIDToDepartment")
2548 |   contractFileTemplateDepartmentAuthorities             ContractFileTemplateDepartmentAuthority[]
2549 |   contractTypeDepartments                               ContractTypeDepartment[]
2550 |   department                                            Department?                               @relation("DepartmentToDepartment", fields: [parentId], references: [departmentId], onDelete: NoAction, onUpdate: NoAction, map: "FK_Department_Department")
2551 |   otherDepartments                                      Department[]                              @relation("DepartmentToDepartment")
2552 |   users                                                 User[]
2553 |   userContractAuthorityForDepartments                   UserContractAuthorityForDepartment[]
2554 |   userDepartmentUserDepartmentDepartmentIdToDepartments UserDepartment[]                          @relation("UserDepartment_DepartmentIDToDepartment")
2555 |   userDepartmentUserDepartmentBranchIdToDepartments     UserDepartment[]                          @relation("UserDepartment_BranchIDToDepartment")
2556 | 
2557 |   @@index([createDate], map: "IX_Department_CreateDate")
2558 |   @@index([departmentId], map: "IX_Department_DepartmentID")
2559 |   @@index([departmentIdName], map: "IX_Department_DepartmentIDName")
2560 |   @@index([deptLeaderId], map: "IX_Department_Dept_Leader_ID")
2561 |   @@index([disable], map: "IX_Department_Disable")
2562 |   @@index([endDate], map: "IX_Department_EndDate")
2563 |   @@index([englishName], map: "IX_Department_EnglishName")
2564 |   @@index([factoryIdName], map: "IX_Department_FactoryIDName")
2565 |   @@index([name], map: "IX_Department_Name")
2566 |   @@index([parentId], map: "IX_Department_ParentID")
2567 |   @@index([shortName], map: "IX_Department_ShortName")
2568 |   @@index([startDate], map: "IX_Department_StartDate")
2569 |   @@index([txt01], map: "IX_Department_Txt01")
2570 |   @@schema("data")
2571 | }
2572 | 
2573 | model DepartmentTemp {
2574 |   departmentId     Int       @id(map: "PK_DepartmentTemp") @map("DepartmentID")
2575 |   name             String?   @map("Name") @db.NVarChar(255)
2576 |   rootDepartment   String?   @map("RootDepartment") @db.NVarChar(255)
2577 |   fullName         String?   @map("FullName") @db.NVarChar(Max)
2578 |   fullDeptIdName   String?   @map("FullDeptIDName") @db.NVarChar(Max)
2579 |   parentName       String?   @map("ParentName") @db.NVarChar(Max)
2580 |   branchId         Int?      @map("BranchID")
2581 |   departmentIdName String?   @map("DepartmentIDName") @db.NVarChar(125)
2582 |   sysDepartmentId  String?   @map("SysDepartmentID") @db.VarChar(900)
2583 |   parentId         Int?      @map("ParentID")
2584 |   createDate       DateTime? @map("CreateDate") @db.DateTime
2585 |   englishName      String?   @map("EnglishName") @db.NVarChar(255)
2586 |   shortName        String?   @map("ShortName") @db.NVarChar(125)
2587 |   startDate        DateTime? @map("StartDate") @db.DateTime
2588 |   endDate          DateTime? @map("EndDate") @db.DateTime
2589 |   disable          Boolean?  @map("Disable")
2590 |   userCount        Int       @map("UserCount")
2591 |   factoryIdName    String?   @map("FactoryIDName") @db.NVarChar(255)
2592 |   isVisable        Boolean?  @map("IsVisable")
2593 |   bool01           Boolean?
2594 |   deptLeaderId     Int?      @map("Dept_Leader_ID")
2595 | 
2596 |   @@index([branchId], map: "IX_DepartmentTemp_BranchID")
2597 |   @@index([createDate], map: "IX_DepartmentTemp_CreateDate")
2598 |   @@index([departmentIdName], map: "IX_DepartmentTemp_DepartmentIDName")
2599 |   @@index([deptLeaderId], map: "IX_DepartmentTemp_Dept_Leader_ID")
2600 |   @@index([endDate], map: "IX_DepartmentTemp_EndDate")
2601 |   @@index([englishName], map: "IX_DepartmentTemp_EnglishName")
2602 |   @@index([factoryIdName], map: "IX_DepartmentTemp_FactoryIDName")
2603 |   @@index([name], map: "IX_DepartmentTemp_Name")
2604 |   @@index([parentId], map: "IX_DepartmentTemp_ParentID")
2605 |   @@index([rootDepartment], map: "IX_DepartmentTemp_RootDepartment")
2606 |   @@index([shortName], map: "IX_DepartmentTemp_ShortName")
2607 |   @@index([startDate], map: "IX_DepartmentTemp_StartDate")
2608 |   @@index([sysDepartmentId], map: "IX_DepartmentTemp_SysDepartmentID")
2609 |   @@index([userCount(sort: Desc)], map: "IX_DepartmentTemp_UserCount")
2610 |   @@schema("dbo")
2611 | }
2612 | 
2613 | model DirectorRule {
2614 |   directorRuleId   Int      @id(map: "PK_DirectorRule") @default(autoincrement()) @map("DirectorRuleID")
2615 |   directorRuleName String?  @map("DirectorRuleName") @db.NVarChar(255)
2616 |   directorRule     String?  @map("DirectorRule") @db.Xml
2617 |   systemDefine     Boolean? @default(false, map: "DF_DirectorRule_SystemDefine") @map("SystemDefine")
2618 | 
2619 |   @@index([directorRuleName], map: "IX_DirectorRule_DirectorRuleName")
2620 |   @@schema("dbo")
2621 | }
2622 | 
2623 | model Domain {
2624 |   domainId           Int      @id(map: "PK_Domain") @default(autoincrement()) @map("DomainID")
2625 |   domainType         String   @default("N'NTDomain'", map: "DF_Domain_DomainType") @map("DomainType") @db.NVarChar(255)
2626 |   domainName         String   @unique(map: "IX_Domain_DomainName") @map("DomainName") @db.NVarChar(255)
2627 |   serverName         String?  @map("ServerName") @db.NVarChar(255)
2628 |   path               String?  @map("Path") @db.NVarChar(Max)
2629 |   isNtlm             Boolean? @default(true, map: "DF_Domain_NTLM") @map("IsNTLM")
2630 |   isDefault          Boolean? @default(false, map: "DF_Domain_SystemDefine") @map("IsDefault")
2631 |   logOnUser          String?  @map("LogOnUser") @db.NVarChar(255)
2632 |   userPassword       String?  @map("UserPassword") @db.NVarChar(255)
2633 |   userIdColumnName   String?  @default("N'sAMAccountName'", map: "DF_Domain_UserIdColumnName") @map("UserIdColumnName") @db.NVarChar(255)
2634 |   userNameColumnName String?  @default("N'name'", map: "DF_Domain_UserNameColumnName") @map("UserNameColumnName") @db.NVarChar(255)
2635 |   userDeptColumnName String?  @default("N'department'", map: "DF_Domain_UserDeptColumnName") @map("UserDeptColumnName") @db.NVarChar(255)
2636 |   systemDefine       Boolean  @default(false, map: "DF_Domain_SystemDefine_1") @map("SystemDefine")
2637 |   isShow             Boolean  @default(true, map: "DF_Domain_isShow")
2638 |   isSsl              Boolean  @default(false, map: "DF_Domain_IsSSL") @map("IsSSL")
2639 | 
2640 |   @@index([domainType], map: "IX_Domain_DomainType")
2641 |   @@index([logOnUser], map: "IX_Domain_LogOnUser")
2642 |   @@index([serverName], map: "IX_Domain_ServerName")
2643 |   @@index([userDeptColumnName], map: "IX_Domain_UserDeptColumnName")
2644 |   @@index([userIdColumnName], map: "IX_Domain_UserIdColumnName")
2645 |   @@index([userNameColumnName], map: "IX_Domain_UserNameColumnName")
2646 |   @@index([userPassword], map: "IX_Domain_UserPassword")
2647 |   @@schema("dbo")
2648 | }
2649 | 
2650 | model EnvelopeAttachment {
2651 |   sn            Int          @id(map: "PK_EnvelopeAttachment") @default(autoincrement())
2652 |   envelopesGuid String       @db.NVarChar(255)
2653 |   attachmentId  Int
2654 |   attachment    Attachment   @relation(fields: [attachmentId], references: [attachmentId], onUpdate: NoAction, map: "FK_EnvelopeAttachment_AttachmentID")
2655 |   envelopeInfo  EnvelopeInfo @relation(fields: [envelopesGuid], references: [envelopesGuid], onUpdate: NoAction, map: "FK_EnvelopeAttachment_EnvelopeInfo")
2656 | 
2657 |   @@schema("dbo")
2658 | }
2659 | 
2660 | model EnvelopeInfo {
2661 |   envelopesGuid       String               @id(map: "PK_EnvelopeInfo") @db.NVarChar(255)
2662 |   envelopesStatus     String               @db.NVarChar(255)
2663 |   lastUpdate          DateTime?            @db.DateTime
2664 |   createDate          DateTime?            @default(now(), map: "DF__EnvelopeI__Creat__32B6742D") @map("CreateDate") @db.DateTime
2665 |   voidedReason        String?              @db.NVarChar(Max)
2666 |   contractEnvelopes   ContractEnvelope[]
2667 |   envelopeAttachments EnvelopeAttachment[]
2668 |   envelopeStages      EnvelopeStage[]
2669 | 
2670 |   @@index([envelopesStatus], map: "IX_EnvelopeInfo_envelopesStatus")
2671 |   @@schema("dbo")
2672 | }
2673 | 
2674 | model EnvelopeStage {
2675 |   sn                Int          @id(map: "PK_EnvelopeStage") @default(autoincrement())
2676 |   envelopesGuid     String       @db.NVarChar(255)
2677 |   type              String?      @db.NVarChar(50)
2678 |   signTitle         String?      @db.NVarChar(255)
2679 |   sealId            Int?
2680 |   partnerId         Int?
2681 |   recipientId       Int
2682 |   signerEmail       String?      @db.NVarChar(255)
2683 |   signerName        String?      @db.NVarChar(255)
2684 |   signerUserId      Int?
2685 |   signedDateTime    DateTime?    @db.DateTime
2686 |   signerSignStatus  String?      @db.NVarChar(50)
2687 |   declinedReason    String?      @db.NVarChar(Max)
2688 |   declinedDateTime  DateTime?    @db.DateTime
2689 |   deliveredDateTime DateTime?    @db.DateTime
2690 |   sentDateTime      DateTime?    @db.DateTime
2691 |   envelopeInfo      EnvelopeInfo @relation(fields: [envelopesGuid], references: [envelopesGuid], onDelete: Cascade, onUpdate: NoAction, map: "FK_EnvelopeStage_EnvelopeInfo")
2692 | 
2693 |   @@index([envelopesGuid], map: "IX_EnvelopeStage_envelopesGuid")
2694 |   @@index([signerSignStatus], map: "IX_EnvelopeStage_signerSignStatus")
2695 |   @@schema("dbo")
2696 | }
2697 | 
2698 | model Event {
2699 |   eventId                      Int                           @id(map: "PK_Event") @default(autoincrement()) @map("EventID")
2700 |   recorderId                   Int?                          @map("RecorderID")
2701 |   eventDate                    DateTime?                     @default(now(), map: "DF_Event_EventDate") @map("EventDate") @db.DateTime
2702 |   createDate                   DateTime?                     @default(now(), map: "DF_Event_CreateDate") @map("CreateDate") @db.DateTime
2703 |   alertDate                    DateTime?                     @map("AlertDate") @db.DateTime
2704 |   sendMail                     Boolean?                      @default(false, map: "DF_Event_SendMail") @map("SendMail")
2705 |   sendMailStartDate            DateTime?                     @map("SendMailStartDate") @db.DateTime
2706 |   sendMailEndDate              DateTime?                     @map("SendMailEndDate") @db.DateTime
2707 |   sendMailTerm                 Int?                          @map("SendMailTerm")
2708 |   traceItem                    String?                       @map("TraceItem") @db.NVarChar(Max)
2709 |   processStatus                String?                       @map("ProcessStatus") @db.NVarChar(Max)
2710 |   memo                         String?                       @map("Memo") @db.NVarChar(Max)
2711 |   lastSendMailDate             DateTime?                     @map("LastSendMailDate") @db.DateTime
2712 |   modifyDate                   DateTime?                     @map("ModifyDate") @db.DateTime
2713 |   modifyUserId                 Int?                          @map("ModifyUserID")
2714 |   sendedNotifyConfirmMail      Boolean?                      @map("SendedNotifyConfirmMail")
2715 |   createType                   Int?                          @map("CreateType")
2716 |   contractEvents               ContractEvent[]
2717 |   user                         User?                         @relation(fields: [recorderId], references: [userId], onDelete: NoAction, onUpdate: NoAction, map: "FK_Event_User")
2718 |   eventAttachments             EventAttachment[]
2719 |   eventSendMailExamStageLists  EventSendMailExamStageList[]
2720 |   eventSendMailLists           EventSendMailList[]
2721 |   eventSendMailOtherRolesLists EventSendMailOtherRolesList[]
2722 |   eventSendOtherMailLists      EventSendOtherMailList[]
2723 |   projectEvents                ProjectEvent[]
2724 | 
2725 |   @@index([alertDate], map: "IX_Event_AlertDate")
2726 |   @@index([createDate], map: "IX_Event_CreateDate")
2727 |   @@index([createType], map: "IX_EVENT_CREATETYPE")
2728 |   @@index([eventDate], map: "IX_Event_EventDate")
2729 |   @@index([lastSendMailDate], map: "IX_Event_LastSendMailDate")
2730 |   @@index([modifyDate], map: "IX_Event_ModifyDate")
2731 |   @@index([modifyUserId], map: "IX_Event_ModifyUserID")
2732 |   @@index([recorderId], map: "IX_Event_RecorderID")
2733 |   @@index([sendedNotifyConfirmMail], map: "IX_EVENT_SendedNotifyConfirmMail")
2734 |   @@index([sendMailEndDate], map: "IX_Event_SendMailEndDate")
2735 |   @@index([sendMailStartDate], map: "IX_Event_SendMailStartDate")
2736 |   @@index([sendMailTerm], map: "IX_Event_SendMailTerm")
2737 |   @@schema("data")
2738 | }
2739 | 
2740 | model EventAttachment {
2741 |   sn           Int         @id(map: "PK_EventAttachment") @default(autoincrement()) @map("Sn")
2742 |   attachmentId Int?        @map("AttachmentID")
2743 |   eventId      Int?        @map("EventID")
2744 |   attachment   Attachment? @relation(fields: [attachmentId], references: [attachmentId], onDelete: Cascade, map: "FK_EventAttachment_Attachment")
2745 |   event        Event?      @relation(fields: [eventId], references: [eventId], onDelete: Cascade, map: "FK_EventAttachment_Event")
2746 | 
2747 |   @@index([attachmentId], map: "IX_EventAttachment_AttachmentID")
2748 |   @@index([eventId], map: "IX_EventAttachment_EventID")
2749 |   @@schema("join")
2750 | }
2751 | 
2752 | model EventSendMailExamStageList {
2753 |   sn                                                      Int        @id(map: "PK__EventSen__32151C44F4F41280") @default(autoincrement()) @map("Sn")
2754 |   eventId                                                 Int?       @map("EventID")
2755 |   examStage                                               Int?       @map("ExamStage")
2756 |   type                                                    Int?       @map("Type")
2757 |   event                                                   Event?     @relation(fields: [eventId], references: [eventId], onDelete: Cascade, onUpdate: NoAction, map: "FK_EventSendMailExamStageList_EventID")
2758 |   examStageEventSendMailExamStageListExamStageToExamStage ExamStage? @relation("EventSendMailExamStageList_ExamStageToExamStage", fields: [examStage], references: [examStageId], onDelete: NoAction, onUpdate: NoAction, map: "FK_EventSendMailExamStageList_ExamStage")
2759 | 
2760 |   @@index([eventId], map: "IX_EventSendMailExamStageList_EventID")
2761 |   @@index([examStage], map: "IX_EventSendMailExamStageList_ExamStage")
2762 |   @@index([type], map: "IX_EventSendMailExamStageList_Type")
2763 |   @@schema("join")
2764 | }
2765 | 
2766 | model EventSendMailList {
2767 |   sn      Int    @id(map: "PK_EventSendMailList") @default(autoincrement()) @map("Sn")
2768 |   eventId Int?   @map("EventID")
2769 |   userId  Int?   @map("UserID")
2770 |   type    Int?   @default(1, map: "DF_EventSendMailList_Type") @map("Type")
2771 |   event   Event? @relation(fields: [eventId], references: [eventId], onDelete: Cascade, map: "FK_EventSendMailList_Event")
2772 |   user    User?  @relation(fields: [userId], references: [userId], onDelete: Cascade, map: "FK_EventSendMailList_User")
2773 | 
2774 |   @@index([eventId], map: "IX_EventSendMailList_EventID")
2775 |   @@index([type], map: "IX_EventSendMailList_Type")
2776 |   @@index([userId], map: "IX_EventSendMailList_UserID")
2777 |   @@schema("join")
2778 | }
2779 | 
2780 | model EventSendMailOtherRolesList {
2781 |   sn      Int    @id(map: "PK__EventSen__32151C44506123EF") @default(autoincrement()) @map("Sn")
2782 |   eventId Int?   @map("EventID")
2783 |   role    Int?   @map("Roles")
2784 |   type    Int?   @map("Type")
2785 |   event   Event? @relation(fields: [eventId], references: [eventId], onDelete: Cascade, onUpdate: NoAction, map: "FK_EventSendMailOtherRolesList_EventID")
2786 | 
2787 |   @@index([eventId], map: "IX_EventSendMailOtherRolesList_EventID")
2788 |   @@index([role], map: "IX_EventSendMailOtherRolesList_Roles")
2789 |   @@index([type], map: "IX_EventSendMailOtherRolesList_Type")
2790 |   @@schema("join")
2791 | }
2792 | 
2793 | model EventSendOtherMailList {
2794 |   sn         Int       @id(map: "PK_EventSendOtherMailList") @default(autoincrement()) @map("Sn")
2795 |   eventId    Int?      @map("EventID")
2796 |   type       Int?      @default(1, map: "DF_EventSendOtherMailList_Type") @map("Type")
2797 |   email      String?   @map("Email") @db.NVarChar(450)
2798 |   createdate DateTime? @default(now(), map: "DF_EventSendOtherMailList_createdate") @map("Createdate") @db.DateTime
2799 |   event      Event?    @relation(fields: [eventId], references: [eventId], onDelete: Cascade, map: "FK_EventSendOtherMailList_Event")
2800 | 
2801 |   @@index([createdate], map: "IX_EventSendOtherMailList_Createdate")
2802 |   @@index([email], map: "IX_EventSendOtherMailList_Email")
2803 |   @@index([eventId], map: "IX_EventSendOtherMailList_EventID")
2804 |   @@index([type], map: "IX_EventSendOtherMailList_Type")
2805 |   @@schema("join")
2806 | }
2807 | 
2808 | model EventStatus {
2809 |   sn                          Int       @id(map: "PK__EventSta__32151C448BD298DF") @default(autoincrement()) @map("Sn")
2810 |   eventType                   Int       @map("EventType")
2811 |   statusName                  String    @map("StatusName") @db.NVarChar(450)
2812 |   statusSimplifiedChineseName String?   @map("StatusSimplifiedChineseName") @db.NVarChar(1024)
2813 |   statusEnglishName           String?   @map("StatusEnglishName") @db.NVarChar(1024)
2814 |   statusJapaneseName          String?   @map("StatusJapaneseName") @db.NVarChar(1024)
2815 |   stopAlertMail               Boolean   @map("StopAlertMail")
2816 |   lastModifiedTime            DateTime? @map("LastModifiedTime") @db.DateTime
2817 |   modifiedByUserId            Int       @map("ModifiedByUserId")
2818 |   disable                     Boolean   @map("Disable")
2819 | 
2820 |   @@unique([eventType, statusName], map: "UC_EventType_StatusName")
2821 |   @@schema("dbo")
2822 | }
2823 | 
2824 | model ExaminerGroup {
2825 |   sn                   Int                   @id(map: "PK_FlowType") @default(autoincrement()) @map("Sn")
2826 |   groupId              Int                   @map("GroupId")
2827 |   parentGroupId        Int?                  @map("ParentGroupId")
2828 |   examType             String                @map("ExamType") @db.NVarChar(50)
2829 |   otherExaminerConfigs OtherExaminerConfig[]
2830 | 
2831 |   @@index([groupId], map: "IX_ExaminerGroup_GroupId")
2832 |   @@index([examType], map: "IX_FlowType_FlowType")
2833 |   @@index([parentGroupId], map: "IX_FlowType_ParentGroupId")
2834 |   @@schema("join")
2835 | }
2836 | 
2837 | model ExamResult {
2838 |   examResultId Int          @id(map: "PK_ExamResult") @default(autoincrement()) @map("ExamResultID")
2839 |   name         String?      @default("0", map: "DF_ExamResult_Name") @map("Name") @db.NVarChar(125)
2840 |   systemDefine Boolean?     @default(true, map: "DF_ExamResult_SystemDefine") @map("SystemDefine")
2841 |   disable      Boolean?     @default(false, map: "DF_ExamResult_Disable") @map("Disable")
2842 |   resultSeq    Int?         @map("ResultSeq")
2843 |   examStatuses ExamStatus[]
2844 | 
2845 |   @@index([disable], map: "IX_ExamResult_Disable")
2846 |   @@index([examResultId], map: "IX_ExamResult_ExamResultID")
2847 |   @@index([name], map: "IX_ExamResult_Name")
2848 |   @@index([resultSeq], map: "IX_ExamResult_ResultSeq")
2849 |   @@index([systemDefine], map: "IX_ExamResult_SystemDefine")
2850 |   @@schema("code")
2851 | }
2852 | 
2853 | /// The underlying table does not contain a valid unique identifier and can therefore currently not be handled by Prisma Client.
2854 | model ExamRule {
2855 |   ruleId   Int       @default(autoincrement()) @map("RuleID")
2856 |   ruleName String?   @map("RuleName") @db.NVarChar(255)
2857 |   disable  Boolean?  @default(true, map: "DF_ExamRule_Disable") @map("Disable")
2858 |   createOn DateTime? @default(now(), map: "DF_ExamRule_CreateOn") @map("CreateOn") @db.DateTime
2859 |   createBy String?   @map("CreateBy") @db.NVarChar(255)
2860 |   modifyOn DateTime? @default(now(), map: "DF_ExamRule_ModifyOn") @map("ModifyOn") @db.DateTime
2861 |   modifyBy String?   @map("ModifyBy") @db.NVarChar(255)
2862 | 
2863 |   @@index([createBy], map: "IX_ExamRule_CreateBy")
2864 |   @@index([createOn], map: "IX_ExamRule_CreateOn")
2865 |   @@index([modifyBy], map: "IX_ExamRule_ModifyBy")
2866 |   @@index([modifyOn], map: "IX_ExamRule_ModifyOn")
2867 |   @@index([ruleId], map: "IX_ExamRule_RuleID")
2868 |   @@index([ruleName], map: "IX_ExamRule_RuleName")
2869 |   @@ignore
2870 |   @@schema("dbo")
2871 | }
2872 | 
2873 | model ExamStage {
2874 |   examStageId                                                               Int                          @id(map: "PK_ExamStage") @default(autoincrement()) @map("ExamStageID")
2875 |   name                                                                      String?                      @map("Name") @db.NVarChar(125)
2876 |   systemDefine                                                              Boolean?                     @default(true, map: "DF_ExamStage_SystemDefine") @map("SystemDefine")
2877 |   disable                                                                   Boolean?                     @default(false, map: "DF_ExamStage_Disable") @map("Disable")
2878 |   defaultExamStatusId                                                       Int?                         @map("DefaultExamStatusID")
2879 |   examOnce                                                                  Boolean?                     @default(false, map: "DF_ExamStage_ExamOnce") @map("ExamOnce")
2880 |   examByOrder                                                               Boolean?                     @default(true, map: "DF_ExamStage_ExamByOrder") @map("ExamByOrder")
2881 |   processStatus                                                             String?                      @map("ProcessStatus") @db.NVarChar(125)
2882 |   backDescription                                                           String?                      @map("BackDescription") @db.NVarChar(125)
2883 |   roleUserId                                                                Int?                         @map("RoleUserID")
2884 |   viewAuthorityId                                                           Int?                         @map("ViewAuthorityID")
2885 |   editAuthorityId                                                           Int?                         @map("EditAuthorityID")
2886 |   optional                                                                  Boolean?                     @default(false, map: "DF_ExamStage_Optional") @map("Optional")
2887 |   canback                                                                   Boolean?                     @default(false, map: "DF_ExamStage_Canback") @map("Canback")
2888 |   examSeq                                                                   Int?                         @map("ExamSeq")
2889 |   general                                                                   Boolean?                     @default(true, map: "DF_ExamStage_GeneralFlow") @map("General")
2890 |   assignInContractAdd                                                       Boolean                      @default(false, map: "DF_ExamStage_AssignInContractAdd") @map("AssignInContractAdd")
2891 |   stageType                                                                 String?                      @map("StageType") @db.NVarChar(450)
2892 |   contractExaminers                                                         ContractExaminer[]
2893 |   contractFlowCsDefaultStages                                               ContractFlowCsDefaultStage[]
2894 |   contractFlowStages                                                        ContractFlowStage[]
2895 |   contractHistories                                                         ContractHistory[]
2896 |   contractMessageBoards                                                     ContractMessageBoard[]
2897 |   contractOtherNotifies                                                     ContractOtherNotify[]
2898 |   eventSendMailExamStageListEventSendMailExamStageListExamStageToExamStages EventSendMailExamStageList[] @relation("EventSendMailExamStageList_ExamStageToExamStage")
2899 |   authorityExamStageViewAuthorityIdToAuthority                              Authority?                   @relation("ExamStage_ViewAuthorityIDToAuthority", fields: [viewAuthorityId], references: [authorityId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ExamStage_Authority")
2900 |   authorityExamStageEditAuthorityIdToAuthority                              Authority?                   @relation("ExamStage_EditAuthorityIDToAuthority", fields: [editAuthorityId], references: [authorityId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ExamStage_Authority1")
2901 |   examStatusExamStageDefaultExamStatusIdToExamStatus                        ExamStatus?                  @relation("ExamStage_DefaultExamStatusIDToExamStatus", fields: [defaultExamStatusId], references: [examStatusId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ExamStage_ExamStatus")
2902 |   user                                                                      User?                        @relation(fields: [roleUserId], references: [userId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ExamStage_User")
2903 |   examStageAuthorities                                                      ExamStageAuthority[]
2904 |   examStatusExamStatusExamStageIdToExamStages                               ExamStatus[]                 @relation("ExamStatus_ExamStageIDToExamStage")
2905 |   messageBoardConfigs                                                       MessageBoardConfig[]
2906 |   syncStageSyncStageExamStageIdToExamStages                                 SyncStage[]                  @relation("SyncStage_ExamStageIDToExamStage")
2907 |   syncStageSyncStageSyncExamStageIdToExamStages                             SyncStage[]                  @relation("SyncStage_SyncExamStageIDToExamStage")
2908 | 
2909 |   @@index([backDescription], map: "IX_ExamStage_BackDescription")
2910 |   @@index([defaultExamStatusId], map: "IX_ExamStage_DefaultExamStatusID")
2911 |   @@index([disable], map: "IX_ExamStage_Disable")
2912 |   @@index([editAuthorityId], map: "IX_ExamStage_EditAuthorityID")
2913 |   @@index([examByOrder], map: "IX_ExamStage_ExamByOrder")
2914 |   @@index([examOnce], map: "IX_ExamStage_ExamOnce")
2915 |   @@index([examSeq], map: "IX_ExamStage_ExamSeq")
2916 |   @@index([examStageId], map: "IX_ExamStage_ExamStageID")
2917 |   @@index([name], map: "IX_ExamStage_Name")
2918 |   @@index([processStatus], map: "IX_ExamStage_ProcessStatus")
2919 |   @@index([roleUserId], map: "IX_ExamStage_RoleUserID")
2920 |   @@index([stageType], map: "IX_ExamStage_StageType")
2921 |   @@index([systemDefine], map: "IX_ExamStage_SystemDefine")
2922 |   @@index([viewAuthorityId], map: "IX_ExamStage_ViewAuthorityID")
2923 |   @@schema("code")
2924 | }
2925 | 
2926 | model ExamStageAuthority {
2927 |   sn                                                    Int            @id(map: "PK_ExamStage_SN") @default(autoincrement()) @map("SN")
2928 |   examStageId                                           Int            @map("ExamStageID")
2929 |   viewAuthorityId                                       Int?           @map("ViewAuthorityID")
2930 |   editAuthorityId                                       Int?           @map("EditAuthorityID")
2931 |   contractModuleSn                                      Int            @map("ContractModuleSN")
2932 |   contractModule                                        ContractModule @relation(fields: [contractModuleSn], references: [sn], onUpdate: NoAction, map: "FK_ExamStageAuthority_ContractModule")
2933 |   authorityExamStageAuthorityEditAuthorityIdToAuthority Authority?     @relation("ExamStageAuthority_EditAuthorityIDToAuthority", fields: [editAuthorityId], references: [authorityId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ExamStageAuthority_EditAuthorityID")
2934 |   examStage                                             ExamStage      @relation(fields: [examStageId], references: [examStageId], onUpdate: NoAction, map: "FK_ExamStageAuthority_ExamStage")
2935 |   authorityExamStageAuthorityViewAuthorityIdToAuthority Authority?     @relation("ExamStageAuthority_ViewAuthorityIDToAuthority", fields: [viewAuthorityId], references: [authorityId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ExamStageAuthority_ViewAuthorityID")
2936 | 
2937 |   @@index([contractModuleSn], map: "IX_ExamStageAuthority_ContractModuleSN")
2938 |   @@index([editAuthorityId], map: "IX_ExamStageAuthority_EditAuthorityID")
2939 |   @@index([examStageId], map: "IX_ExamStageAuthority_ExamStageID")
2940 |   @@index([viewAuthorityId], map: "IX_ExamStageAuthority_ViewAuthorityID")
2941 |   @@schema("code")
2942 | }
2943 | 
2944 | model ExamStageConfig {
2945 |   examStageId  Int       @id(map: "PK_ExamStageConfig") @map("ExamStageID")
2946 |   name         String?   @map("Name") @db.NVarChar(50)
2947 |   roleUserId   Int?      @map("RoleUserID")
2948 |   examSeq      Int?      @map("ExamSeq")
2949 |   createDate   DateTime? @map("CreateDate") @db.DateTime
2950 |   systemDefine Boolean?  @map("SystemDefine")
2951 |   stageType    String?   @map("StageType") @db.NVarChar(450)
2952 | 
2953 |   @@index([createDate], map: "IX_ExamStageConfig_CreateDate")
2954 |   @@index([examSeq], map: "IX_ExamStageConfig_ExamSeq")
2955 |   @@index([name], map: "IX_ExamStageConfig_Name")
2956 |   @@index([roleUserId], map: "IX_ExamStageConfig_RoleUserID")
2957 |   @@schema("code")
2958 | }
2959 | 
2960 | model ExamStatus {
2961 |   examStatusId                                        Int                   @id(map: "PK_ExamStatus") @default(autoincrement()) @map("ExamStatusID")
2962 |   name                                                String?               @map("Name") @db.NVarChar(125)
2963 |   examStageId                                         Int?                  @map("ExamStageID")
2964 |   examResultId                                        Int?                  @map("ExamResultID")
2965 |   systemDefine                                        Boolean?              @default(false, map: "DF_ExamStatus_SystemDefine") @map("SystemDefine")
2966 |   disable                                             Boolean?              @default(false, map: "DF_ExamStatus_Disable") @map("Disable")
2967 |   default                                             Boolean?              @default(true, map: "DF_ExamStatus_Default") @map("Default")
2968 |   editable                                            Boolean?              @default(true, map: "DF_ExamStatus_Editable") @map("Editable")
2969 |   contractExaminers                                   ContractExaminer[]
2970 |   contractHistories                                   ContractHistory[]
2971 |   examStageExamStageDefaultExamStatusIdToExamStatuses ExamStage[]           @relation("ExamStage_DefaultExamStatusIDToExamStatus")
2972 |   examResult                                          ExamResult?           @relation(fields: [examResultId], references: [examResultId], onDelete: Cascade, map: "FK_ExamStatus_ExamResult")
2973 |   examStageExamStatusExamStageIdToExamStage           ExamStage?            @relation("ExamStatus_ExamStageIDToExamStage", fields: [examStageId], references: [examStageId], onDelete: NoAction, onUpdate: NoAction, map: "FK_ExamStatus_ExamStage")
2974 |   examStatusLanguages                                 ExamStatusLanguage[]
2975 |   otherExaminerConfigs                                OtherExaminerConfig[]
2976 | 
2977 |   @@index([default], map: "IX_ExamStatus_Default")
2978 |   @@index([disable], map: "IX_ExamStatus_Disable")
2979 |   @@index([examResultId], map: "IX_ExamStatus_ExamResultID")
2980 |   @@index([examStageId], map: "IX_ExamStatus_ExamStageID")
2981 |   @@index([examStatusId], map: "IX_ExamStatus_ExamStatusID")
2982 |   @@index([name], map: "IX_ExamStatus_Name")
2983 |   @@index([systemDefine], map: "IX_ExamStatus_SystemDefine")
2984 |   @@schema("code")
2985 | }
2986 | 
2987 | model ExamStatusLanguage {
2988 |   sn           Int        @id(map: "PK_ExamStatusLanguage") @default(autoincrement()) @map("Sn")
2989 |   examStatusId Int        @map("ExamStatusID")
2990 |   languageCode String     @map("LanguageCode") @db.VarChar(20)
2991 |   name         String?    @map("Name") @db.NVarChar(255)
2992 |   examStatus   ExamStatus @relation(fields: [examStatusId], references: [examStatusId], onDelete: Cascade, map: "FK_ExamStatusLanguage_ExamStatus")
2993 | 
2994 |   @@index([examStatusId], map: "IX_ExamStatusLanguage_ExamStatusID")
2995 |   @@index([languageCode], map: "IX_ExamStatusLanguage_LanguageCode")
2996 |   @@index([name], map: "IX_ExamStatusLanguage_Name")
2997 |   @@schema("join")
2998 | }
2999 | 
3000 | model Exchange {
3001 |   sn              Int                  @id(map: "PK_Exchange") @default(autoincrement()) @map("Sn")
3002 |   currency        String?              @map("Currency") @db.NVarChar(125)
3003 |   name            String?              @map("Name") @db.NVarChar(125)
3004 |   tRate           Float?               @map("TRate")
3005 |   disable         Boolean?             @default(false, map: "DF_Exchange_Disable") @map("Disable")
3006 |   contractAmounts JoinContractAmount[]
3007 | 
3008 |   @@index([currency], map: "IX_Exchange_Currency")
3009 |   @@index([disable], map: "IX_Exchange_Disable")
3010 |   @@index([name], map: "IX_Exchange_Name")
3011 |   @@index([sn], map: "IX_Exchange_Sn")
3012 |   @@index([tRate], map: "IX_Exchange_TRate")
3013 |   @@schema("code")
3014 | }
3015 | 
3016 | model FileType {
3017 |   sn           Int          @id(map: "PK_FileType") @default(autoincrement()) @map("Sn")
3018 |   name         String?      @map("Name") @db.NVarChar(Max)
3019 |   disable      Boolean?     @default(false, map: "DF_FileType_Disable") @map("Disable")
3020 |   systemDefine Boolean?     @default(false, map: "DF_FileType_SystemDefine") @map("SystemDefine")
3021 |   seq          Int?         @map("Seq")
3022 |   attachments  Attachment[]
3023 | 
3024 |   @@index([disable], map: "IX_FileType_Disable")
3025 |   @@index([sn], map: "IX_FileType_Sn")
3026 |   @@index([seq], map: "IX_FILETYPE_SORT")
3027 |   @@index([systemDefine], map: "IX_FileType_SystemDefine")
3028 |   @@schema("code")
3029 | }
3030 | 
3031 | model ForumList {
3032 |   sn                Int               @id(map: "PK_ForumList") @default(autoincrement()) @map("Sn")
3033 |   userId            Int               @map("UserID")
3034 |   title             String            @map("Title") @db.NVarChar(450)
3035 |   content           String            @map("Content") @db.NVarChar(Max)
3036 |   createDate        DateTime          @map("CreateDate") @db.DateTime
3037 |   forumTopicReplies ForumTopicReply[]
3038 | 
3039 |   @@index([createDate], map: "IX_ForumList_CreateDate")
3040 |   @@index([title], map: "IX_ForumList_Title")
3041 |   @@index([userId], map: "IX_ForumList_UserID")
3042 |   @@schema("data")
3043 | }
3044 | 
3045 | model ForumReply {
3046 |   sn                Int               @id(map: "PK_ForumReply") @default(autoincrement()) @map("Sn")
3047 |   userId            Int?              @map("UserID")
3048 |   replyDate         DateTime?         @map("ReplyDate") @db.DateTime
3049 |   memo              String?           @map("Memo") @db.NVarChar(Max)
3050 |   forumTopicReplies ForumTopicReply[]
3051 | 
3052 |   @@index([replyDate], map: "IX_ForumReply_ReplyDate")
3053 |   @@index([userId], map: "IX_ForumReply_UserID")
3054 |   @@schema("data")
3055 | }
3056 | 
3057 | model ForumTopicReply {
3058 |   sn           Int        @id(map: "PK_ForumTopicReply") @default(autoincrement()) @map("Sn")
3059 |   forumListId  Int        @map("ForumListID")
3060 |   forumReplyId Int        @map("ForumReplyID")
3061 |   forumList    ForumList  @relation(fields: [forumListId], references: [sn], map: "FK_ForumTopicReply_ForumList")
3062 |   forumReply   ForumReply @relation(fields: [forumReplyId], references: [sn], map: "FK_ForumTopicReply_ForumReply")
3063 | 
3064 |   @@index([forumListId], map: "IX_ForumTopicReply_ForumListID")
3065 |   @@index([forumReplyId], map: "IX_ForumTopicReply_ForumReplyID")
3066 |   @@schema("join")
3067 | }
3068 | 
3069 | model LoginLog {
3070 |   sn                  Int                  @id(map: "PK_LoginLog") @default(autoincrement()) @map("Sn")
3071 |   userId              Int                  @map("UserID")
3072 |   ipAddress           String               @map("IPAddress") @db.NVarChar(125)
3073 |   loginDate           DateTime             @default(now(), map: "DF_LoginLog_LoginDate") @map("LoginDate") @db.DateTime
3074 |   logoutDate          DateTime?            @map("LogoutDate") @db.DateTime
3075 |   isSuccess           Boolean              @default(true, map: "DF_LoginLog_IsSuccess") @map("IsSuccess")
3076 |   authorityChangeLogs AuthorityChangeLog[]
3077 |   user                User                 @relation(fields: [userId], references: [userId], onDelete: Cascade, map: "FK_LoginLog_User")
3078 |   usingLogs           UsingLog[]
3079 | 
3080 |   @@index([ipAddress], map: "IX_LoginLog_IPAddress")
3081 |   @@index([loginDate], map: "IX_LoginLog_LoginDate")
3082 |   @@index([logoutDate], map: "IX_LoginLog_LogoutDate")
3083 |   @@index([userId], map: "IX_LoginLog_UserID")
3084 |   @@schema("data")
3085 | }
3086 | 
3087 | model LtcLog {
3088 |   sn         Int       @id(map: "PK_LTCLog") @default(autoincrement()) @map("Sn")
3089 |   contractId Int?      @map("ContractID")
3090 |   editUser   String    @map("EditUser") @db.NVarChar(250)
3091 |   modifyDate DateTime  @default(now(), map: "DF_LTCLog_ModifyDate") @map("ModifyDate") @db.DateTime
3092 |   methName   String    @map("MethName") @db.NVarChar(250)
3093 |   inputInfo  String?   @map("InputInfo") @db.NVarChar(Max)
3094 |   outputInfo String?   @map("OutputInfo") @db.NVarChar(Max)
3095 |   oldValue   String?   @map("OldValue") @db.NVarChar(Max)
3096 |   newValue   String?   @map("NewValue") @db.NVarChar(Max)
3097 |   status     String    @map("Status") @db.NVarChar(250)
3098 |   type       String    @map("Type") @db.NVarChar(250)
3099 |   memo       String?   @map("Memo") @db.NVarChar(Max)
3100 |   contract   Contract? @relation(fields: [contractId], references: [contractId], onDelete: NoAction, onUpdate: NoAction, map: "FK_LTCLog_Contract")
3101 | 
3102 |   @@index([contractId], map: "IX_LTCLog_ContractID")
3103 |   @@index([editUser], map: "IX_LTCLog_EditUser")
3104 |   @@index([methName], map: "IX_LTCLog_MethName")
3105 |   @@index([modifyDate], map: "IX_LTCLog_ModifyDate")
3106 |   @@index([status], map: "IX_LTCLog_Status")
3107 |   @@index([type], map: "IX_LTCLog_Type")
3108 |   @@map("LTCLog")
3109 |   @@schema("data")
3110 | }
3111 | 
3112 | model MailLog {
3113 |   mailSn           Int               @id(sort: Desc, map: "PK_MailLog") @default(autoincrement()) @map("MailSn")
3114 |   mailTitle        String?           @map("MailTitle") @db.NVarChar(Max)
3115 |   mailBody         String?           @map("MailBody") @db.NVarChar(Max)
3116 |   mailTo           String?           @map("MailTo") @db.NVarChar(Max)
3117 |   mailFrom         String?           @map("MailFrom") @db.NVarChar(500)
3118 |   isSuccess        Boolean?          @map("IsSuccess")
3119 |   isBodyHtml       Boolean?          @map("IsBodyHtml")
3120 |   sendDate         DateTime?         @map("SendDate") @db.DateTime
3121 |   createDate       DateTime?         @default(now(), map: "DF_MailLog_CreateDate") @map("CreateDate") @db.DateTime
3122 |   isReSend         Boolean?          @map("IsReSend")
3123 |   mailCc           String?           @map("MailCC") @db.NVarChar(Max)
3124 |   mailBcc          String?           @map("MailBCC") @db.NVarChar(Max)
3125 |   mailType         String?           @map("MailType") @db.NVarChar(Max)
3126 |   lastReSendDate   DateTime?         @map("LastReSendDate") @db.DateTime
3127 |   mailLogTypeSn    Int?              @map("MailLogTypeSN")
3128 |   autoErrorMsg     String?           @map("AutoErrorMsg") @db.NVarChar(Max)
3129 |   reSendErrorMsg   String?           @map("ReSendErrorMsg") @db.NVarChar(Max)
3130 |   contractMailLogs ContractMailLog[]
3131 |   mailLogType      MailLogType?      @relation(fields: [mailLogTypeSn], references: [mailLogTypeSn], onDelete: NoAction, onUpdate: NoAction, map: "FK_MailLog_MailLogType")
3132 | 
3133 |   @@index([createDate(sort: Desc)], map: "IX_MailLog_CreateDate")
3134 |   @@index([lastReSendDate], map: "IX_MailLog_LastReSendDate")
3135 |   @@index([mailLogTypeSn], map: "IX_MailLog_MailLogTypeSN")
3136 |   @@index([sendDate(sort: Desc)], map: "IX_MailLog_SendDate")
3137 |   @@schema("dbo")
3138 | }
3139 | 
3140 | model MailLogType {
3141 |   mailLogTypeSn Int       @id(map: "PK_MailLogType") @map("MailLogTypeSN")
3142 |   mailLogType   String?   @map("MailLogType") @db.NVarChar(100)
3143 |   mailLogs      MailLog[]
3144 | 
3145 |   @@index([mailLogType], map: "IX_MailLogType_MailLogType")
3146 |   @@schema("code")
3147 | }
3148 | 
3149 | model MailType {
3150 |   sn           Int      @id(map: "PK_MailType") @default(autoincrement()) @map("Sn")
3151 |   name         String?  @map("Name") @db.NVarChar(Max)
3152 |   disable      Boolean? @default(false, map: "DF_MailType_Disable") @map("Disable")
3153 |   systemDefine Boolean? @default(false, map: "DF_MailType_SystemDefine") @map("SystemDefine")
3154 | 
3155 |   @@schema("code")
3156 | }
3157 | 
3158 | model MainContractDepartment {
3159 |   sn                 Int @id(map: "PK_MainContractDepartment") @default(autoincrement()) @map("SN")
3160 |   mainContractTypeId Int @map("MainContractTypeID")
3161 |   departmentId       Int @map("DepartmentID")
3162 | 
3163 |   @@index([departmentId], map: "IX_MainContractDepartment_DepartmentID")
3164 |   @@index([mainContractTypeId], map: "IX_MainContractDepartment_MainContractTypeID")
3165 |   @@schema("join")
3166 | }
3167 | 
3168 | model MainContractType {
3169 |   mainContractTypeId        Int                        @id(map: "PK_MainContractType") @default(autoincrement()) @map("MainContractTypeID")
3170 |   mainContractTypeName      String?                    @map("MainContractTypeName") @db.NVarChar(Max)
3171 |   disable                   Boolean                    @default(false, map: "DF_MainContractType_Disable") @map("Disable")
3172 |   systemDefine              Boolean                    @default(false, map: "DF_MainContractType_SystemDefine") @map("SystemDefine")
3173 |   secret                    Boolean                    @default(false, map: "DF_MainContractType_Secret") @map("Secret")
3174 |   contractTypeCode          String?                    @map("ContractTypeCode") @db.NVarChar(50)
3175 |   seq                       Int?                       @default(9999, map: "DF_MainContractType_Seq") @map("Seq")
3176 |   mainContractTypeMemo      String?                    @map("MainContractTypeMemo") @db.NVarChar(Max)
3177 |   priorityNumber            Int?                       @map("PriorityNumber")
3178 |   contractTypes             CodeContractType[]         @ignore
3179 |   mainContractTypeLanguages MainContractTypeLanguage[]
3180 | 
3181 |   @@index([contractTypeCode], map: "IX_MainContractType_ContractTypeCode")
3182 |   @@index([seq], map: "IX_MainContractType_Seq")
3183 |   @@schema("code")
3184 | }
3185 | 
3186 | model MainContractTypeLanguage {
3187 |   sn                 Int              @id(map: "PK_Table_SN") @default(autoincrement()) @map("SN")
3188 |   mainContractTypeId Int              @map("MainContractTypeID")
3189 |   languageCode       String           @map("LanguageCode") @db.NVarChar(50)
3190 |   name               String?          @map("Name") @db.NVarChar(Max)
3191 |   mainContractType   MainContractType @relation(fields: [mainContractTypeId], references: [mainContractTypeId], onUpdate: NoAction, map: "FK_MainContractType_Language_MainContractType")
3192 | 
3193 |   @@index([languageCode], map: "IX_Table_LanguageCode")
3194 |   @@index([mainContractTypeId], map: "IX_Table_MainContractTypeID")
3195 |   @@map("MainContractType_Language")
3196 |   @@schema("join")
3197 | }
3198 | 
3199 | model Memo {
3200 |   type String  @id(map: "PK_Memo") @map("Type") @db.NVarChar(125)
3201 |   memo String? @map("Memo") @db.NVarChar(Max)
3202 | 
3203 |   @@index([type], map: "IX_Memo_Type")
3204 |   @@schema("code")
3205 | }
3206 | 
3207 | model MessageBoard {
3208 |   boardId               Int                    @id(map: "PK__MessageB__F9646BD2AE70F2C7") @default(autoincrement()) @map("BoardID")
3209 |   boardTitle            String?                @map("BoardTitle") @db.NVarChar(155)
3210 |   boardName             String?                @map("BoardName") @db.NVarChar(155)
3211 |   createDate            DateTime?              @default(now(), map: "DF__MessageBo__Creat__59063A47") @map("CreateDate") @db.DateTime
3212 |   enable                Boolean?               @default(true, map: "DF__MessageBo__Enabl__59FA5E80") @map("Enable")
3213 |   contractMessageBoards ContractMessageBoard[]
3214 |   messageBoardConfigs   MessageBoardConfig[]
3215 | 
3216 |   @@index([boardName], map: "IX_MessageBoard_BoardName")
3217 |   @@index([boardTitle], map: "IX_MessageBoard_BoardTitle")
3218 |   @@index([createDate], map: "IX_MessageBoard_CreateDate")
3219 |   @@schema("code")
3220 | }
3221 | 
3222 | model MessageBoardConfig {
3223 |   sn           Int          @id(map: "PK__MessageB__32151C44B245943F") @default(autoincrement()) @map("Sn")
3224 |   boardId      Int          @map("BoardID")
3225 |   examStageId  Int          @map("ExamStageID")
3226 |   createDate   DateTime?    @default(now(), map: "DF__MessageBo__Creat__54968AE5") @map("CreateDate") @db.DateTime
3227 |   seq          Int?         @map("Seq")
3228 |   enable       Boolean?     @default(true, map: "DF__MessageBo__Enabl__558AAF1E") @map("Enable")
3229 |   messageBoard MessageBoard @relation(fields: [boardId], references: [boardId], onUpdate: NoAction, map: "FK_MessageBoardConfig_BoardID")
3230 |   examStage    ExamStage    @relation(fields: [examStageId], references: [examStageId], onUpdate: NoAction, map: "FK_MessageBoardConfig_ExamStageID")
3231 | 
3232 |   @@index([boardId], map: "IX_MessageBoardConfig_BoardID")
3233 |   @@index([createDate], map: "IX_MessageBoardConfig_CreateDate")
3234 |   @@index([examStageId], map: "IX_MessageBoardConfig_ExamStageID")
3235 |   @@index([seq], map: "IX_MessageBoardConfig_Seq")
3236 |   @@schema("code")
3237 | }
3238 | 
3239 | model MessageLog {
3240 |   id        String   @id(map: "PK_MessageLogs") @db.Char(36)
3241 |   messageId String   @db.Char(36)
3242 |   client    String   @db.NVarChar(255)
3243 |   isSuccess Boolean
3244 |   error     String   @db.NVarChar(Max)
3245 |   payload   String   @db.NVarChar(Max)
3246 |   createdAt DateTime @db.DateTime
3247 |   message   Message  @relation(fields: [messageId], references: [id], onUpdate: NoAction, map: "FK_MessageLogs_Messages")
3248 | 
3249 |   @@map("MessageLogs")
3250 |   @@schema("dbo")
3251 | }
3252 | 
3253 | model Message {
3254 |   id          String       @id(map: "PK_Messages") @db.Char(36)
3255 |   topic       String       @db.NVarChar(255)
3256 |   originator  String       @db.NVarChar(255)
3257 |   payload     String       @db.NVarChar(Max)
3258 |   createdAt   DateTime     @db.DateTime
3259 |   messageLogs MessageLog[]
3260 | 
3261 |   @@map("Messages")
3262 |   @@schema("dbo")
3263 | }
3264 | 
3265 | model OtherContractAttachmentStatus {
3266 |   sn           Int     @id(map: "PK_OtherContractAttachmentStatus") @default(autoincrement()) @map("Sn")
3267 |   attachmentId Int     @map("AttachmentId")
3268 |   contractId   Int     @map("ContractId")
3269 |   isDelete     Boolean @map("IsDelete")
3270 | 
3271 |   @@index([attachmentId], map: "IX_OtherContractAttachmentStatus_AttachmentId")
3272 |   @@index([contractId], map: "IX_OtherContractAttachmentStatus_ContractId")
3273 |   @@schema("join")
3274 | }
3275 | 
3276 | model OtherExaminer {
3277 |   sn                                      Int                       @id(map: "PK_OtherExaminer") @default(autoincrement()) @map("Sn")
3278 |   examinerSn                              Int                       @map("ExaminerSn")
3279 |   userId                                  Int                       @map("UserID")
3280 |   requireMemo                             String?                   @map("RequireMemo") @db.NVarChar(Max)
3281 |   replyMemo                               String?                   @map("ReplyMemo") @db.NVarChar(Max)
3282 |   sentMail                                Boolean?                  @default(false, map: "DF_OtherExaminer_SentMail") @map("SentMail")
3283 |   replied                                 Boolean?                  @default(false, map: "DF_OtherExaminer_Replied") @map("Replied")
3284 |   assignDate                              DateTime?                 @default(now(), map: "DF_OtherExaminer_StayDate") @map("AssignDate") @db.DateTime
3285 |   examDate                                DateTime?                 @map("ExamDate") @db.DateTime
3286 |   halt                                    Boolean?                  @default(false, map: "DF_OtherExaminer_Halt") @map("Halt")
3287 |   carbonNotify                            String?                   @map("CarbonNotify") @db.NVarChar(Max)
3288 |   deadline                                Int?                      @map("Deadline")
3289 |   alertPeriod                             Int?                      @map("AlertPeriod")
3290 |   sendReminderMail                        Boolean?                  @default(false, map: "DF_OtherExaminer_SendReminderMail") @map("SendReminderMail")
3291 |   csExamResultId                          Int?                      @map("CSExamResultID")
3292 |   actualExamUserId                        Int?                      @map("ActualExamUserID")
3293 |   originalUserId                          Int?                      @map("OriginalUserID")
3294 |   groupId                                 Int?                      @map("GroupID")
3295 |   examStatusId                            Int?                      @map("ExamStatusID")
3296 |   contractExaminer                        ContractExaminer          @relation(fields: [examinerSn], references: [sn], onDelete: Cascade, map: "FK_OtherExaminer_ContractExaminer")
3297 |   csExamResult                            CsExamResult?             @relation(fields: [csExamResultId], references: [csExamResultId], onDelete: Cascade, onUpdate: NoAction, map: "FK_OtherExaminer_CSExamResult")
3298 |   userOtherExaminerUserIdToUser           User                      @relation("OtherExaminer_UserIDToUser", fields: [userId], references: [userId], onUpdate: NoAction, map: "FK_OtherExaminer_User")
3299 |   userOtherExaminerActualExamUserIdToUser User?                     @relation("OtherExaminer_ActualExamUserIDToUser", fields: [actualExamUserId], references: [userId], onDelete: NoAction, onUpdate: NoAction, map: "FK_OtherExaminer_User1")
3300 |   otherExaminerAttachments                OtherExaminerAttachment[]
3301 |   otherExaminerConfigs                    OtherExaminerConfig[]
3302 | 
3303 |   @@index([actualExamUserId], map: "IX_OtherExaminer_ActualExamUserID")
3304 |   @@index([alertPeriod], map: "IX_OtherExaminer_AlertPeriod")
3305 |   @@index([assignDate], map: "IX_OtherExaminer_AssignDate")
3306 |   @@index([csExamResultId], map: "IX_OtherExaminer_CSExamResultID")
3307 |   @@index([deadline], map: "IX_OtherExaminer_Deadline")
3308 |   @@index([examDate], map: "IX_OtherExaminer_ExamDate")
3309 |   @@index([examinerSn], map: "IX_OtherExaminer_ExaminerSn")
3310 |   @@index([examStatusId], map: "IX_OtherExaminer_ExamStatusID")
3311 |   @@index([groupId], map: "IX_OtherExaminer_GroupID")
3312 |   @@index([originalUserId], map: "IX_OtherExaminer_OriginalUserID")
3313 |   @@index([replied], map: "IX_OtherExaminer_Replied")
3314 |   @@index([userId], map: "IX_OtherExaminer_UserID")
3315 |   @@schema("data")
3316 | }
3317 | 
3318 | model OtherExaminerAttachment {
3319 |   sn              Int            @id(map: "PK_OtherExaminerAttachment") @default(autoincrement()) @map("SN")
3320 |   attachmentId    Int?           @map("AttachmentID")
3321 |   otherExaminerSn Int?           @map("OtherExaminerSN")
3322 |   attachment      Attachment?    @relation(fields: [attachmentId], references: [attachmentId], onDelete: NoAction, onUpdate: NoAction, map: "FK_OtherExaminerAttachment_Attachment")
3323 |   otherExaminer   OtherExaminer? @relation(fields: [otherExaminerSn], references: [sn], onDelete: Cascade, map: "FK_OtherExaminerAttachment_OtherExaminer")
3324 | 
3325 |   @@unique([sn, attachmentId, otherExaminerSn], map: "Unique_OtherExaminerAttachment")
3326 |   @@schema("join")
3327 | }
3328 | 
3329 | model OtherExaminerConfig {
3330 |   sn                             Int                             @id(map: "PK_OtherExaminerConfig") @default(autoincrement()) @map("Sn")
3331 |   examinerSn                     Int                             @map("ExaminerSn")
3332 |   userId                         Int                             @map("UserID")
3333 |   requireMemo                    String?                         @map("RequireMemo") @db.NVarChar(Max)
3334 |   halt                           Boolean?                        @default(false, map: "DF_OtherExaminerConfig_Halt") @map("Halt")
3335 |   carbonNotify                   String?                         @map("CarbonNotify") @db.NVarChar(Max)
3336 |   sendReminderMail               Boolean?                        @default(false, map: "DF_OtherExaminerConfig_SendReminderMail") @map("SendReminderMail")
3337 |   deadline                       Int?                            @map("Deadline")
3338 |   alertPeriod                    Int?                            @map("AlertPeriod")
3339 |   examStatusId                   Int?                            @map("ExamStatusID")
3340 |   originalUserId                 Int?                            @map("OriginalUserID")
3341 |   examinerGroupSn                Int                             @map("ExaminerGroupSn")
3342 |   enable                         Boolean                         @map("Enable")
3343 |   createDate                     DateTime                        @map("CreateDate") @db.DateTime
3344 |   seq                            Int                             @map("Seq")
3345 |   otherExaminerSn                Int?                            @map("OtherExaminerSn")
3346 |   contractExaminer               ContractExaminer                @relation(fields: [examinerSn], references: [sn], onDelete: Cascade, onUpdate: NoAction, map: "FK_OtherExaminerConfig_ContractExaminer")
3347 |   examinerGroup                  ExaminerGroup                   @relation(fields: [examinerGroupSn], references: [sn], onUpdate: NoAction, map: "FK_OtherExaminerConfig_ExaminerGroup")
3348 |   examStatus                     ExamStatus?                     @relation(fields: [examStatusId], references: [examStatusId], onDelete: NoAction, onUpdate: NoAction, map: "FK_OtherExaminerConfig_ExamStatus")
3349 |   otherExaminer                  OtherExaminer?                  @relation(fields: [otherExaminerSn], references: [sn], onDelete: NoAction, onUpdate: NoAction, map: "FK_OtherExaminerConfig_OtherExaminer")
3350 |   user                           User                            @relation(fields: [userId], references: [userId], onUpdate: NoAction, map: "FK_OtherExaminerConfig_User")
3351 |   otherExaminerConfigAttachments OtherExaminerConfigAttachment[]
3352 | 
3353 |   @@index([alertPeriod], map: "IX_OtherExaminerConfig_AlertPeriod")
3354 |   @@index([createDate], map: "IX_OtherExaminerConfig_CreateDate")
3355 |   @@index([deadline], map: "IX_OtherExaminerConfig_Deadline")
3356 |   @@index([enable], map: "IX_OtherExaminerConfig_Enable")
3357 |   @@index([examinerSn], map: "IX_OtherExaminerConfig_ExaminerSn")
3358 |   @@index([examStatusId], map: "IX_OtherExaminerConfig_ExamStatusID")
3359 |   @@index([examinerGroupSn], map: "IX_OtherExaminerConfig_FlowTypeId")
3360 |   @@index([halt], map: "IX_OtherExaminerConfig_Halt")
3361 |   @@index([originalUserId], map: "IX_OtherExaminerConfig_OriginalUserID")
3362 |   @@index([otherExaminerSn], map: "IX_OtherExaminerConfig_OtherExaminerSn")
3363 |   @@index([seq], map: "IX_OtherExaminerConfig_Seq")
3364 |   @@index([userId], map: "IX_OtherExaminerConfig_UserID")
3365 |   @@schema("data")
3366 | }
3367 | 
3368 | model OtherExaminerConfigAttachment {
3369 |   sn                    Int                 @id(map: "PK_OtherExaminerConfigAttachment") @default(autoincrement()) @map("SN")
3370 |   attachmentId          Int                 @map("AttachmentID")
3371 |   otherExaminerConfigSn Int                 @map("OtherExaminerConfigSN")
3372 |   attachment            Attachment          @relation(fields: [attachmentId], references: [attachmentId], onUpdate: NoAction, map: "FK_OtherExaminerConfigAttachment_Attachment")
3373 |   otherExaminerConfig   OtherExaminerConfig @relation(fields: [otherExaminerConfigSn], references: [sn], onUpdate: NoAction, map: "FK_OtherExaminerConfigAttachment_OtherExaminerConfig")
3374 | 
3375 |   @@index([attachmentId], map: "IX_OtherExaminerConfigAttachment_AttachmentID")
3376 |   @@index([otherExaminerConfigSn], map: "IX_OtherExaminerConfigAttachment_OtherExaminerConfigSN")
3377 |   @@schema("join")
3378 | }
3379 | 
3380 | model OtpToken {
3381 |   sn          Int       @id(map: "PK_OTPToken") @default(autoincrement()) @map("SN")
3382 |   token       String    @map("Token") @db.NVarChar(250)
3383 |   createDate  DateTime  @default(now(), map: "DF_OTPToken_CreateDate") @map("CreateDate") @db.DateTime
3384 |   expiresDate DateTime? @map("ExpiresDate") @db.DateTime
3385 |   used        Boolean   @default(false, map: "DF_OTPToken_Used") @map("Used")
3386 |   type        Int       @map("Type")
3387 |   message     String?   @map("Message") @db.NVarChar(Max)
3388 | 
3389 |   @@map("OTPToken")
3390 |   @@schema("dbo")
3391 | }
3392 | 
3393 | model Partner {
3394 |   partnerId        Int               @id(map: "PK_Partner") @default(autoincrement()) @map("PartnerID")
3395 |   companyName      String            @map("CompanyName") @db.NVarChar(1024)
3396 |   address          String?           @map("Address") @db.NVarChar(Max)
3397 |   head             String?           @map("Head") @db.NVarChar(125)
3398 |   unifiedSn        String?           @map("UnifiedSN") @db.NVarChar(50)
3399 |   fax              String?           @map("Fax") @db.NVarChar(125)
3400 |   tel              String?           @map("Tel") @db.NVarChar(125)
3401 |   disable          Boolean           @default(false, map: "DF_Partner_Disable") @map("Disable")
3402 |   defaultContactId Int?              @map("DefaultContactID")
3403 |   code             String?           @map("Code") @db.NVarChar(255)
3404 |   txt01            String?           @map("Txt01") @db.NVarChar(255)
3405 |   txt02            String?           @map("Txt02") @db.NVarChar(255)
3406 |   txt03            String?           @map("Txt03") @db.NVarChar(255)
3407 |   txt04            String?           @map("Txt04") @db.NVarChar(1024)
3408 |   contractPartners ContractPartner[]
3409 |   partnerContacts  PartnerContact[]
3410 |   partnerSignLogs  PartnerSignLog[]
3411 | 
3412 |   @@index([code], map: "IX_Partner_Code")
3413 |   @@index([defaultContactId], map: "IX_Partner_DefaultContactID")
3414 |   @@index([disable], map: "IX_Partner_Disable")
3415 |   @@index([fax], map: "IX_Partner_Fax")
3416 |   @@index([head], map: "IX_Partner_Head")
3417 |   @@index([partnerId], map: "IX_Partner_PartnerID")
3418 |   @@index([tel], map: "IX_Partner_Tel")
3419 |   @@index([txt01], map: "IX_Partner_Txt01")
3420 |   @@index([txt02], map: "IX_Partner_Txt02")
3421 |   @@index([txt03], map: "IX_Partner_Txt03")
3422 |   @@index([unifiedSn], map: "IX_Partner_UnifiedSN")
3423 |   @@schema("data")
3424 | }
3425 | 
3426 | model PartnerContact {
3427 |   partnerContactId Int               @id(map: "PK_PartnerContact") @default(autoincrement()) @map("PartnerContactID")
3428 |   contactName      String?           @map("ContactName") @db.NVarChar(125)
3429 |   contactPhone     String?           @map("ContactPhone") @db.NVarChar(125)
3430 |   mobilePhone      String?           @map("MobilePhone") @db.NVarChar(125)
3431 |   email            String?           @map("Email") @db.NVarChar(255)
3432 |   disable          Boolean?          @default(false, map: "DF_PartnerContact_Disable") @map("Disable")
3433 |   partnerId        Int               @map("PartnerID")
3434 |   default          Boolean?          @default(false, map: "DF_PartnerContact_Default") @map("Default")
3435 |   contractPartners ContractPartner[]
3436 |   partner          Partner           @relation(fields: [partnerId], references: [partnerId], onDelete: Cascade, map: "FK_PartnerContact_Partner")
3437 | 
3438 |   @@index([contactName], map: "IX_PartnerContact_ContactName")
3439 |   @@index([contactPhone], map: "IX_PartnerContact_ContactPhone")
3440 |   @@index([email], map: "IX_PartnerContact_Email")
3441 |   @@index([mobilePhone], map: "IX_PartnerContact_MobilePhone")
3442 |   @@index([partnerId], map: "IX_PartnerContact_PartnerID")
3443 |   @@schema("data")
3444 | }
3445 | 
3446 | model PartnerSignLog {
3447 |   sn         Int       @id(map: "PK_PartnerSignLog") @default(autoincrement()) @map("Sn")
3448 |   partnerId  Int?      @map("PartnerID")
3449 |   notifyDate DateTime? @map("NotifyDate") @db.DateTime
3450 |   signDate   DateTime? @map("SignDate") @db.DateTime
3451 |   processDay Int?      @map("ProcessDay")
3452 |   contractId Int?      @map("ContractID")
3453 |   contract   Contract? @relation(fields: [contractId], references: [contractId], onDelete: Cascade, onUpdate: NoAction, map: "FK_PartnerSignLog_Contract")
3454 |   partner    Partner?  @relation(fields: [partnerId], references: [partnerId], onDelete: NoAction, onUpdate: NoAction, map: "FK_PartnerSignLog_Partner")
3455 | 
3456 |   @@index([contractId], map: "IX_PartnerSignLog_ContractID")
3457 |   @@index([notifyDate], map: "IX_PartnerSignLog_NotifyDate")
3458 |   @@index([partnerId], map: "IX_PartnerSignLog_PartnerID")
3459 |   @@index([processDay], map: "IX_PartnerSignLog_ProcessDay")
3460 |   @@index([signDate], map: "IX_PartnerSignLog_SignDate")
3461 |   @@schema("data")
3462 | }
3463 | 
3464 | model Project {
3465 |   projectId         Int                @id(map: "PK_Project") @default(autoincrement()) @map("ProjectID")
3466 |   projectName       String?            @map("ProjectName") @db.NVarChar(Max)
3467 |   createDate        DateTime?          @default(now(), map: "DF_Project_CreateDate") @map("CreateDate") @db.DateTime
3468 |   projectTypeId     Int?               @map("ProjectTypeID")
3469 |   contactPerson     String?            @map("ContactPerson") @db.NVarChar(Max)
3470 |   projectManagerId  Int?               @map("ProjectManagerID")
3471 |   purpose           String?            @map("Purpose") @db.NVarChar(Max)
3472 |   memo              String?            @map("Memo") @db.NVarChar(Max)
3473 |   projectNo         String?            @map("ProjectNo") @db.NVarChar(Max)
3474 |   projectType       ProjectType?       @relation(fields: [projectTypeId], references: [sn], onDelete: Cascade, map: "FK_Project_ProjectType")
3475 |   user              User?              @relation(fields: [projectManagerId], references: [userId], onDelete: NoAction, onUpdate: NoAction, map: "FK_Project_User")
3476 |   projectApplicants ProjectApplicant[]
3477 |   projectContracts  ProjectContract[]
3478 |   projectEvents     ProjectEvent[]
3479 | 
3480 |   @@index([createDate], map: "IX_Project_CreateDate")
3481 |   @@index([projectManagerId], map: "IX_Project_ProjectManagerID")
3482 |   @@index([projectTypeId], map: "IX_Project_ProjectTypeID")
3483 |   @@schema("data")
3484 | }
3485 | 
3486 | model ProjectApplicant {
3487 |   sn        Int     @id(map: "PK_ProjectApplicant") @default(autoincrement()) @map("Sn")
3488 |   projectId Int     @map("ProjectID")
3489 |   userId    Int     @map("UserID")
3490 |   project   Project @relation(fields: [projectId], references: [projectId], onDelete: Cascade, map: "FK_ProjectApplicant_Project")
3491 |   user      User    @relation(fields: [userId], references: [userId], onDelete: Cascade, map: "FK_ProjectApplicant_User")
3492 | 
3493 |   @@index([projectId], map: "IX_ProjectApplicant_ProjectID")
3494 |   @@index([userId], map: "IX_ProjectApplicant_UserID")
3495 |   @@schema("join")
3496 | }
3497 | 
3498 | model ProjectContract {
3499 |   sn         Int       @id(map: "PK_ProjectContract") @default(autoincrement()) @map("Sn")
3500 |   projectId  Int?      @map("ProjectID")
3501 |   contractId Int?      @map("ContractID")
3502 |   contract   Contract? @relation(fields: [contractId], references: [contractId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ProjectContract_Contract")
3503 |   project    Project?  @relation(fields: [projectId], references: [projectId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ProjectContract_Project")
3504 | 
3505 |   @@index([contractId], map: "IX_ProjectContract_ContractID")
3506 |   @@index([projectId], map: "IX_ProjectContract_ProjectID")
3507 |   @@schema("join")
3508 | }
3509 | 
3510 | model ProjectEvent {
3511 |   sn        Int      @id(map: "PK_ProjectEvent") @default(autoincrement()) @map("Sn")
3512 |   eventId   Int?     @map("EventID")
3513 |   projectId Int?     @map("ProjectID")
3514 |   event     Event?   @relation(fields: [eventId], references: [eventId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ProjectEvent_Event")
3515 |   project   Project? @relation(fields: [projectId], references: [projectId], onDelete: Cascade, onUpdate: NoAction, map: "FK_ProjectEvent_Project")
3516 | 
3517 |   @@index([eventId], map: "IX_ProjectEvent_EventID")
3518 |   @@index([projectId], map: "IX_ProjectEvent_ProjectID")
3519 |   @@schema("join")
3520 | }
3521 | 
3522 | model ProjectType {
3523 |   sn           Int       @id(map: "PK_ProjectType") @default(autoincrement()) @map("Sn")
3524 |   name         String?   @map("Name") @db.NVarChar(Max)
3525 |   disable      Boolean?  @default(false, map: "DF_ProjectType_Disable") @map("Disable")
3526 |   systemDefine Boolean?  @default(false, map: "DF_ProjectType_SystemDefine") @map("SystemDefine")
3527 |   projects     Project[]
3528 | 
3529 |   @@index([disable], map: "IX_ProjectType_Disable")
3530 |   @@index([sn], map: "IX_ProjectType_Sn")
3531 |   @@index([systemDefine], map: "IX_ProjectType_SystemDefine")
3532 |   @@schema("code")
3533 | }
3534 | 
3535 | model RelatedContract {
3536 |   sn                                                 Int                       @id(map: "PK_RelatedContract") @default(autoincrement()) @map("Sn")
3537 |   contractId                                         Int?                      @map("ContractID")
3538 |   relatedContractId                                  Int?                      @map("RelatedContractID")
3539 |   memo                                               String?                   @map("Memo") @db.NVarChar(Max)
3540 |   contractRequireAttributeSn                         Int?                      @map("ContractRequireAttributeSn")
3541 |   contractRelatedContractContractIdToContract        Contract?                 @relation("RelatedContract_ContractIDToContract", fields: [contractId], references: [contractId], onDelete: Cascade, onUpdate: NoAction, map: "FK_RelatedContract_Contract")
3542 |   contractRelatedContractRelatedContractIdToContract Contract?                 @relation("RelatedContract_RelatedContractIDToContract", fields: [relatedContractId], references: [contractId], onDelete: NoAction, onUpdate: NoAction, map: "FK_RelatedContract_Contract1")
3543 |   contractRequireAttribute                           ContractRequireAttribute? @relation(fields: [contractRequireAttributeSn], references: [sn], onDelete: Cascade, onUpdate: NoAction, map: "FK_RelatedContract_ContractRequireAttribute")
3544 | 
3545 |   @@index([contractId], map: "IX_RelatedContract_ContractID")
3546 |   @@index([contractRequireAttributeSn], map: "IX_RelatedContract_ContractRequireAttributeSn")
3547 |   @@index([relatedContractId], map: "IX_RelatedContract_RelatedContractID")
3548 |   @@schema("join")
3549 | }
3550 | 
3551 | model SerialNumber {
3552 |   serialTypeId  Int     @id(map: "PK_SerialNumber") @default(autoincrement()) @map("SerialTypeID")
3553 |   serialName    String? @map("SerialName") @db.NVarChar(50)
3554 |   serialRuleXml String? @map("SerialRuleXml") @db.Xml
3555 | 
3556 |   @@index([serialName], map: "IX_SerialNumber_SerialName")
3557 |   @@schema("data")
3558 | }
3559 | 
3560 | model SignAttachment {
3561 |   sn              Int              @id(map: "PK_SignAttachment") @default(autoincrement()) @map("Sn")
3562 |   attachmentId    Int?             @map("AttachmentID")
3563 |   signTypeId      Int?             @map("SignTypeID")
3564 |   attachment      Attachment?      @relation(fields: [attachmentId], references: [attachmentId], onDelete: Cascade, map: "FK_SignAttachment_Attachment")
3565 |   signRequirement SignRequirement? @relation(fields: [signTypeId], references: [signTypeId], onDelete: Cascade, map: "FK_SignAttachment_Sign")
3566 | 
3567 |   @@index([attachmentId], map: "IX_SignAttachment_AttachmentID")
3568 |   @@index([signTypeId], map: "IX_SignAttachment_SignTypeID")
3569 |   @@schema("join")
3570 | }
3571 | 
3572 | model SignAttachmentInfo {
3573 |   sn                   Int                   @id(map: "PK_SignAttachmentInfo") @default(autoincrement()) @map("SN")
3574 |   contractId           Int                   @map("ContractID")
3575 |   attachmentId         Int                   @map("AttachmentID")
3576 |   userId               Int?                  @map("UserID")
3577 |   watermarkSn          Int                   @map("WatermarkSn")
3578 |   signDate             DateTime              @map("SignDate") @db.DateTime
3579 |   version              Int?                  @map("Version")
3580 |   needPageNum          Boolean               @default(false, map: "DF__SignAttac__NeedP__6166761E") @map("NeedPageNum")
3581 |   attachmentCertifieds AttachmentCertified[]
3582 |   attachmentWatermark  AttachmentWatermark   @relation(fields: [watermarkSn], references: [sn], onUpdate: NoAction, map: "FK_SignAttachmentInfo_AttachmentWatermark")
3583 | 
3584 |   @@index([attachmentId], map: "IX_SignAttachmentInfo_AttachmentID")
3585 |   @@index([contractId], map: "IX_SignAttachmentInfo_ContractID")
3586 |   @@index([signDate], map: "IX_SignAttachmentInfo_SignDate")
3587 |   @@index([userId], map: "IX_SignAttachmentInfo_UserID")
3588 |   @@index([version], map: "IX_SignAttachmentInfo_Version")
3589 |   @@index([watermarkSn], map: "IX_SignAttachmentInfo_WatermarkSn")
3590 |   @@schema("join")
3591 | }
3592 | 
3593 | model SignRequirement {
3594 |   signTypeId           Int                   @id(map: "PK_SignRequirement") @default(autoincrement()) @map("SignTypeID")
3595 |   name                 String?               @map("Name") @db.NVarChar(125)
3596 |   disable              Boolean?              @default(false, map: "DF_SignRequirement_Disable") @map("Disable")
3597 |   systemDefine         Boolean?              @default(false, map: "DF_SignRequirement_SystemDefine") @map("SystemDefine")
3598 |   signType             String?               @map("SignType") @db.NVarChar(50)
3599 |   custodianUserId      Int?                  @map("Custodian_UserID")
3600 |   sealCode             String?               @map("SealCode") @db.NVarChar(450)
3601 |   belongOwner          String?               @map("BelongOwner") @db.NVarChar(450)
3602 |   purpose              String?               @map("Purpose") @db.NVarChar(450)
3603 |   enabled              Boolean               @default(true, map: "DF__SignRequi__Enabl__65370702") @map("Enabled")
3604 |   contractRequireSigns ContractRequireSign[]
3605 |   signAttachments      SignAttachment[]
3606 |   user                 User?                 @relation(fields: [custodianUserId], references: [userId], onDelete: NoAction, onUpdate: NoAction, map: "FK_SignRequirement_User_Custodian_UserID")
3607 | 
3608 |   @@index([belongOwner], map: "IX_SignRequirement_BelongOwner")
3609 |   @@index([custodianUserId], map: "IX_SignRequirement_Custodian_UserID")
3610 |   @@index([disable], map: "IX_SignRequirement_Disable")
3611 |   @@index([enabled], map: "IX_SignRequirement_Enabled")
3612 |   @@index([name], map: "IX_SignRequirement_Name")
3613 |   @@index([purpose], map: "IX_SignRequirement_Purpose")
3614 |   @@index([sealCode], map: "IX_SignRequirement_SealCode")
3615 |   @@index([signType], map: "IX_SignRequirement_SignType")
3616 |   @@index([signTypeId], map: "IX_SignRequirement_SignTypeID")
3617 |   @@index([systemDefine], map: "IX_SignRequirement_SystemDefine")
3618 |   @@schema("code")
3619 | }
3620 | 
3621 | model SiteCode {
3622 |   sn              Int              @id(map: "PK_SiteCode") @default(autoincrement()) @map("Sn")
3623 |   siteName        String           @map("SiteName") @db.NVarChar(250)
3624 |   code            String?          @map("Code") @db.NVarChar(100)
3625 |   contractCustoms ContractCustom[]
3626 | 
3627 |   @@index([code], map: "IX_SiteCode_Code")
3628 |   @@index([siteName], map: "IX_SiteCode_SiteName")
3629 |   @@schema("code")
3630 | }
3631 | 
3632 | model SnStore {
3633 |   prefix String @id(map: "PK_SNStore") @map("Prefix") @db.NVarChar(50)
3634 |   sn     Int?   @map("SN")
3635 |   snType Int?   @map("SNType")
3636 | 
3637 |   @@index([sn], map: "IX_SNStore_SN")
3638 |   @@index([snType], map: "IX_SNStore_SNType")
3639 |   @@map("SNStore")
3640 |   @@schema("code")
3641 | }
3642 | 
3643 | model SqlUpdateList {
3644 |   sn         Int      @id(map: "PK_Table_SN") @default(autoincrement()) @map("SN")
3645 |   commitId   String   @map("CommitID") @db.NVarChar(10)
3646 |   filePath   String   @map("FilePath") @db.NVarChar(Max)
3647 |   createDate DateTime @map("CreateDate") @db.DateTime
3648 | 
3649 |   @@index([createDate], map: "IX_SQL_UpdateList_CreateDate")
3650 |   @@index([commitId], map: "IX_Table_CommitID")
3651 |   @@map("SQL_UpdateList")
3652 |   @@schema("dbo")
3653 | }
3654 | 
3655 | model StampDuty {
3656 |   stampDutyType       Int                 @id(map: "PK_StampDuty") @map("StampDutyType")
3657 |   stampDutyName       String              @map("StampDutyName") @db.NVarChar(50)
3658 |   seq                 Int                 @map("Seq")
3659 |   haveDescription     Boolean
3660 |   contractStampDuties ContractStampDuty[]
3661 | 
3662 |   @@index([seq], map: "IX_StampDuty_Seq")
3663 |   @@index([stampDutyName], map: "IX_StampDuty_StampDutyName")
3664 |   @@schema("dbo")
3665 | }
3666 | 
3667 | model SyncStage {
3668 |   sn                                           Int                            @id(map: "PK__SyncStag__32151C44A40B8B72") @default(autoincrement()) @map("Sn")
3669 |   examStageId                                  Int?                           @map("ExamStageID")
3670 |   syncName                                     String?                        @map("SyncName") @db.NVarChar(155)
3671 |   syncExamStageId                              Int?                           @map("SyncExamStageID")
3672 |   urgentLevelId                                Int?                           @map("UrgentLevelID")
3673 |   seq                                          Int?                           @map("Seq")
3674 |   disable                                      Boolean?                       @default(false, map: "DF__SyncStage__Disab__184C96B4") @map("Disable")
3675 |   contractFlowDefaultSyncStages                ContractFlowDefaultSyncStage[]
3676 |   examStageSyncStageExamStageIdToExamStage     ExamStage?                     @relation("SyncStage_ExamStageIDToExamStage", fields: [examStageId], references: [examStageId], onDelete: NoAction, onUpdate: NoAction, map: "FK_SyncStage_ExamStageID")
3677 |   examStageSyncStageSyncExamStageIdToExamStage ExamStage?                     @relation("SyncStage_SyncExamStageIDToExamStage", fields: [syncExamStageId], references: [examStageId], onDelete: NoAction, onUpdate: NoAction, map: "FK_SyncStage_SyncExamStageID")
3678 | 
3679 |   @@index([examStageId], map: "IX_SyncStage_ExamStageID")
3680 |   @@index([seq], map: "IX_SyncStage_Seq")
3681 |   @@index([syncExamStageId], map: "IX_SyncStage_SyncExamStageID")
3682 |   @@index([syncName], map: "IX_SyncStage_SyncName")
3683 |   @@index([urgentLevelId], map: "IX_SyncStage_UrgentLevelID")
3684 |   @@schema("code")
3685 | }
3686 | 
3687 | model SystemLanguage {
3688 |   sn           Int     @id(map: "PK_SystemLanguage") @default(autoincrement()) @map("SN")
3689 |   language     String  @map("Language") @db.NVarChar(50)
3690 |   languageCode String  @map("LanguageCode") @db.NVarChar(20)
3691 |   enabled      Boolean @map("Enabled")
3692 |   seq          Int?    @map("Seq")
3693 | 
3694 |   @@index([language], map: "IX_SystemLanguage_Language")
3695 |   @@index([languageCode], map: "IX_SystemLanguage_LanguageCode")
3696 |   @@index([seq], map: "IX_SystemLanguage_Seq")
3697 |   @@schema("code")
3698 | }
3699 | 
3700 | model TempAllCaseList {
3701 |   contractId      Int       @id(map: "PK_TempAllCaseList") @map("ContractId")
3702 |   effectiveDate   DateTime? @map("EffectiveDate") @db.DateTime
3703 |   monitoringEvent String?   @map("MonitoringEvent") @db.NVarChar(450)
3704 |   contractStatus  String?   @map("ContractStatus") @db.NVarChar(450)
3705 | 
3706 |   @@index([contractStatus], map: "IX_TempAllCaseList_ContractStatus")
3707 |   @@index([effectiveDate], map: "IX_TempAllCaseList_EffectiveDate")
3708 |   @@index([monitoringEvent], map: "IX_TempAllCaseList_MonitoringEvent")
3709 |   @@schema("data")
3710 | }
3711 | 
3712 | model TempPartner {
3713 |   sn          Int      @id(map: "PK_TempPartner") @default(autoincrement()) @map("Sn")
3714 |   contractId  Int      @map("ContractId")
3715 |   companyName String   @map("CompanyName") @db.NVarChar(1024)
3716 |   address     String?  @map("Address") @db.NVarChar(4000)
3717 |   head        String?  @map("Head") @db.NVarChar(125)
3718 |   unifiedSn   String?  @map("UnifiedSN") @db.NVarChar(50)
3719 |   fax         String?  @map("Fax") @db.NVarChar(125)
3720 |   tel         String?  @map("Tel") @db.NVarChar(125)
3721 |   code        String?  @map("Code") @db.NVarChar(255)
3722 |   txt01       String?  @map("Txt01") @db.NVarChar(255)
3723 |   txt02       String?  @map("Txt02") @db.NVarChar(255)
3724 |   txt03       String?  @map("Txt03") @db.NVarChar(255)
3725 |   contract    Contract @relation(fields: [contractId], references: [contractId], onDelete: Cascade, map: "FK_TempPartner_Contract")
3726 | 
3727 |   @@index([code], map: "IX_TempPartner_Code")
3728 |   @@index([contractId], map: "IX_TempPartner_ContractId")
3729 |   @@index([fax], map: "IX_TempPartner_Fax")
3730 |   @@index([head], map: "IX_TempPartner_Head")
3731 |   @@index([tel], map: "IX_TempPartner_Tel")
3732 |   @@index([txt01], map: "IX_TempPartner_Txt01")
3733 |   @@index([txt02], map: "IX_TempPartner_Txt02")
3734 |   @@index([txt03], map: "IX_TempPartner_Txt03")
3735 |   @@index([unifiedSn], map: "IX_TempPartner_UnifiedSN")
3736 |   @@schema("data")
3737 | }
3738 | 
3739 | model TempUpdateLog {
3740 |   sn         Int      @id(map: "PK_TempUpdateLog") @default(autoincrement()) @map("Sn")
3741 |   tableName  String   @map("TableName") @db.NVarChar(450)
3742 |   updateTime DateTime @map("UpdateTime") @db.DateTime
3743 | 
3744 |   @@index([tableName], map: "IX_TempUpdateLog_TableName")
3745 |   @@schema("data")
3746 | }
3747 | 
3748 | model TransferCaseLog {
3749 |   transferId  Int       @id(map: "PK_TransferCaseLog") @default(autoincrement()) @map("TransferID")
3750 |   fromUserId  Int?      @map("FromUserID")
3751 |   toUserId    Int?      @map("ToUserID")
3752 |   contractId  Int?      @map("ContractID")
3753 |   examStageId Int?      @map("ExamStageID")
3754 |   createDate  DateTime? @map("CreateDate") @db.DateTime
3755 | 
3756 |   @@index([contractId], map: "IX_TransferCaseLog_ContractID")
3757 |   @@index([createDate], map: "IX_TransferCaseLog_CreateDate")
3758 |   @@index([examStageId], map: "IX_TransferCaseLog_ExamStageID")
3759 |   @@index([fromUserId], map: "IX_TransferCaseLog_FromUserID")
3760 |   @@index([toUserId], map: "IX_TransferCaseLog_ToUserID")
3761 |   @@schema("dbo")
3762 | }
3763 | 
3764 | /// The underlying table does not contain a valid unique identifier and can therefore currently not be handled by Prisma Client.
3765 | model UpdateRevision {
3766 |   sn         Int       @default(autoincrement()) @map("SN")
3767 |   revision   String?   @map("Revision") @db.NVarChar(50)
3768 |   updateDate DateTime? @default(now(), map: "DF_UpdateRevision_UpdateDate") @map("UpdateDate") @db.DateTime
3769 | 
3770 |   @@index([revision], map: "IX_UpdateRevision_Revision")
3771 |   @@index([sn], map: "IX_UpdateRevision_SN")
3772 |   @@index([updateDate], map: "IX_UpdateRevision_UpdateDate")
3773 |   @@ignore
3774 |   @@schema("dbo")
3775 | }
3776 | 
3777 | model UrgentLevel {
3778 |   urgentLevelId                             Int            @id(map: "PK_UrgentLevel") @default(autoincrement()) @map("UrgentLevelID")
3779 |   urgentName                                String         @map("UrgentName") @db.NVarChar(125)
3780 |   disable                                   Boolean        @default(false, map: "DF_UrgentLevel_Disable") @map("Disable")
3781 |   systemDefine                              Boolean        @default(false, map: "DF_UrgentLevel_SystemDefine") @map("SystemDefine")
3782 |   contractContractUrgentLevelToUrgentLevels Contract[]     @relation("Contract_UrgentLevelToUrgentLevel")
3783 |   contractFlows                             ContractFlow[]
3784 | 
3785 |   @@index([disable], map: "IX_UrgentLevel_Disable")
3786 |   @@index([urgentName], map: "IX_UrgentLevel_Name")
3787 |   @@index([urgentLevelId], map: "IX_UrgentLevel_Sn")
3788 |   @@index([systemDefine], map: "IX_UrgentLevel_SystemDefine")
3789 |   @@schema("code")
3790 | }
3791 | 
3792 | model User {
3793 |   userId                                            Int                                  @id(map: "PK_User") @default(autoincrement()) @map("UserID")
3794 |   name                                              String?                              @map("Name") @db.NVarChar(450)
3795 |   loginId                                           String?                              @map("LoginID") @db.NVarChar(50)
3796 |   role                                              Boolean?                             @default(false, map: "DF_User_Role") @map("Role")
3797 |   disable                                           Boolean?                             @default(false, map: "DF_User_Disable") @map("Disable")
3798 |   description                                       String?                              @map("Description") @db.NVarChar(Max)
3799 |   systemDefine                                      Boolean?                             @default(false, map: "DF_User_SystemDefine") @map("SystemDefine")
3800 |   lastLogin                                         DateTime?                            @default(now(), map: "DF_User_LastLogin") @map("LastLogin") @db.DateTime
3801 |   departmentId                                      Int?                                 @map("DepartmentID")
3802 |   ext                                               String?                              @map("Ext") @db.NVarChar(50)
3803 |   email                                             String?                              @map("Email") @db.NVarChar(450)
3804 |   branchId                                          Int?                                 @map("BranchID")
3805 |   stop                                              Boolean?                             @default(false, map: "DF_User_Stop") @map("Stop")
3806 |   englishName                                       String?                              @map("EnglishName") @db.NVarChar(450)
3807 |   address                                           String?                              @map("Address") @db.NVarChar(Max)
3808 |   password                                          String?                              @map("Password") @db.NVarChar(Max)
3809 |   userNo                                            String?                              @map("UserNo") @db.NVarChar(450)
3810 |   memo                                              String?                              @map("Memo") @db.NVarChar(Max)
3811 |   tel                                               String?                              @map("Tel") @db.NVarChar(255)
3812 |   uid                                               String?                              @map("UID") @db.NVarChar(255)
3813 |   employeeId                                        String?                              @map("EmployeeID") @db.NVarChar(255)
3814 |   title                                             String?                              @map("Title") @db.NVarChar(255)
3815 |   positionLevel                                     String?                              @map("PositionLevel") @db.NVarChar(255)
3816 |   lineManager                                       String?                              @map("LineManager") @db.NVarChar(255)
3817 |   head                                              String?                              @map("Head") @db.NVarChar(255)
3818 |   siteName                                          String?                              @map("Site_Name") @db.NVarChar(255)
3819 |   ecsNetMobileEnable                                Boolean                              @default(false, map: "DF_User_ECSNetMobileEnable") @map("ECSNetMobileEnable")
3820 |   txt01                                             String?                              @map("Txt01") @db.NVarChar(255)
3821 |   isAddedManually                                   Boolean                              @default(false, map: "DF_User_IsAddedManually") @map("IsAddedManually")
3822 |   loginFail                                         Int                                  @default(0, map: "DF__User__LoginFail__4A8310C6") @map("LoginFail")
3823 |   actingAgents                                      ActingAgent[]
3824 |   actingEntries                                     ActingEntry[]
3825 |   apiLogs                                           ApiLog[]
3826 |   attachments                                       Attachment[]
3827 |   attachmentCertifieds                              AttachmentCertified[]
3828 |   contracts                                         Contract[]
3829 |   contractExaminers                                 ContractExaminer[]
3830 |   contractFileTemplates                             ContractFileTemplate[]
3831 |   contractFileTemplateUserAuthorities               ContractFileTemplateUserAuthority[]
3832 |   contractFlowCsDefaultExaminers                    ContractFlowCsDefaultExaminer[]
3833 |   contractFlowDefaultExaminers                      ContractFlowDefaultExaminer[]
3834 |   contractHistoryContractHistoryAssignUserIdToUsers ContractHistory[]                    @relation("ContractHistory_AssignUserIDToUser")
3835 |   contractHistoryContractHistoryExamUserIdToUsers   ContractHistory[]                    @relation("ContractHistory_ExamUserIDToUser")
3836 |   contractMessageBoards                             ContractMessageBoard[]
3837 |   contractRequireSigns                              ContractRequireSign[]
3838 |   contractTypeDepartments                           ContractTypeDepartment[]
3839 |   events                                            Event[]
3840 |   eventSendMailLists                                EventSendMailList[]
3841 |   examStages                                        ExamStage[]
3842 |   loginLogs                                         LoginLog[]
3843 |   otherExaminerOtherExaminerUserIdToUsers           OtherExaminer[]                      @relation("OtherExaminer_UserIDToUser")
3844 |   otherExaminerOtherExaminerActualExamUserIdToUsers OtherExaminer[]                      @relation("OtherExaminer_ActualExamUserIDToUser")
3845 |   otherExaminerConfigs                              OtherExaminerConfig[]
3846 |   projects                                          Project[]
3847 |   projectApplicants                                 ProjectApplicant[]
3848 |   signRequirements                                  SignRequirement[]
3849 |   department                                        Department?                          @relation(fields: [departmentId], references: [departmentId], onDelete: NoAction, onUpdate: NoAction, map: "FK_User_Department")
3850 |   userAuthorities                                   UserAuthority[]
3851 |   userComments                                      UserComment[]
3852 |   userContractAuthorities                           UserContractAuthority[]
3853 |   userContractAuthorityForDepartments               UserContractAuthorityForDepartment[]
3854 |   userDepartments                                   UserDepartment[]
3855 |   userRoleUserRoleRoleUserIdToUsers                 UserRole[]                           @relation("UserRole_RoleUserIDToUser")
3856 |   userRoleUserRoleUserIdToUsers                     UserRole[]                           @relation("UserRole_UserIDToUser")
3857 | 
3858 |   @@index([branchId], map: "IX_User_BranchID")
3859 |   @@index([departmentId], map: "IX_User_DepartmentID")
3860 |   @@index([disable], map: "IX_User_Disable")
3861 |   @@index([email], map: "IX_User_Email")
3862 |   @@index([employeeId], map: "IX_User_EmployeeID")
3863 |   @@index([englishName], map: "IX_User_EnglishName")
3864 |   @@index([ext], map: "IX_User_Ext")
3865 |   @@index([head], map: "IX_User_Head")
3866 |   @@index([lastLogin], map: "IX_User_LastLogin")
3867 |   @@index([lineManager], map: "IX_User_LineManager")
3868 |   @@index([loginFail], map: "IX_User_LoginFail")
3869 |   @@index([loginId], map: "IX_User_LoginID")
3870 |   @@index([name], map: "IX_User_Name")
3871 |   @@index([positionLevel], map: "IX_User_PositionLevel")
3872 |   @@index([role], map: "IX_User_Role")
3873 |   @@index([siteName], map: "IX_User_Site_Name")
3874 |   @@index([stop], map: "IX_User_Stop")
3875 |   @@index([systemDefine], map: "IX_User_SystemDefine")
3876 |   @@index([tel], map: "IX_User_Tel")
3877 |   @@index([title], map: "IX_User_Title")
3878 |   @@index([txt01], map: "IX_User_Txt01")
3879 |   @@index([uid], map: "IX_User_UID")
3880 |   @@index([userId], map: "IX_User_UserID")
3881 |   @@index([userNo], map: "IX_User_UserNo")
3882 |   @@schema("data")
3883 | }
3884 | 
3885 | model UserAuthority {
3886 |   sn           Int        @id(map: "PK_UserAuthority") @default(autoincrement()) @map("Sn")
3887 |   userId       Int?       @map("UserID")
3888 |   authorityId  Int?       @map("AuthorityID")
3889 |   systemDefine Boolean?   @default(false, map: "DF_UserAuthority_SystemDefine") @map("SystemDefine")
3890 |   authority    Authority? @relation(fields: [authorityId], references: [authorityId], onDelete: Cascade, map: "FK_UserAuthority_Authority")
3891 |   user         User?      @relation(fields: [userId], references: [userId], onDelete: Cascade, map: "FK_UserAuthority_User")
3892 | 
3893 |   @@unique([userId, authorityId], map: "IX_UserAuthority_UserID_AuthorityID")
3894 |   @@index([authorityId], map: "IX_UserAuthority_AuthorityID")
3895 |   @@index([userId], map: "IX_UserAuthority_UserID")
3896 |   @@schema("join")
3897 | }
3898 | 
3899 | model UserComment {
3900 |   sn      Int     @id(map: "PK_UserComment") @default(autoincrement()) @map("Sn")
3901 |   userId  Int?    @map("UserID")
3902 |   comment String? @map("Comment") @db.NVarChar(Max)
3903 |   user    User?   @relation(fields: [userId], references: [userId], onDelete: Cascade, map: "FK_UserComment_User")
3904 | 
3905 |   @@index([userId], map: "IX_UserComment_UserID")
3906 |   @@schema("join")
3907 | }
3908 | 
3909 | model UserContractAuthority {
3910 |   sn          Int        @id(map: "PK_UserContractAuthority") @default(autoincrement()) @map("Sn")
3911 |   userId      Int?       @map("UserID")
3912 |   contractId  Int?       @map("ContractID")
3913 |   authorityId Int?       @map("AuthorityID")
3914 |   authority   Authority? @relation(fields: [authorityId], references: [authorityId], onDelete: NoAction, onUpdate: NoAction, map: "FK_UserContractAuthority_Authority")
3915 |   contract    Contract?  @relation(fields: [contractId], references: [contractId], onDelete: NoAction, onUpdate: NoAction, map: "FK_UserContractAuthority_Contract")
3916 |   user        User?      @relation(fields: [userId], references: [userId], onDelete: NoAction, onUpdate: NoAction, map: "FK_UserContractAuthority_User")
3917 | 
3918 |   @@index([authorityId], map: "IX_UserContractAuthority_AuthorityID")
3919 |   @@index([contractId], map: "IX_UserContractAuthority_ContractID")
3920 |   @@index([userId], map: "IX_UserContractAuthority_UserID")
3921 |   @@schema("join")
3922 | }
3923 | 
3924 | model UserContractAuthorityForDepartment {
3925 |   sn           Int         @id(map: "PK_UserContractAuthorityForDepartment") @default(autoincrement()) @map("Sn")
3926 |   userId       Int?        @map("UserID")
3927 |   departmentId Int?        @map("DepartmentID")
3928 |   authorityId  Int?        @map("AuthorityID")
3929 |   authority    Authority?  @relation(fields: [authorityId], references: [authorityId], onDelete: NoAction, onUpdate: NoAction, map: "FK_UserContractAuthorityForDepartment_Authority")
3930 |   department   Department? @relation(fields: [departmentId], references: [departmentId], onDelete: NoAction, onUpdate: NoAction, map: "FK_UserContractAuthorityForDepartment_Department")
3931 |   user         User?       @relation(fields: [userId], references: [userId], onDelete: NoAction, onUpdate: NoAction, map: "FK_UserContractAuthorityForDepartment_User")
3932 | 
3933 |   @@index([authorityId], map: "IX_UserContractAuthorityForDepartment_AuthorityID")
3934 |   @@index([departmentId], map: "IX_UserContractAuthorityForDepartment_DepartmentID")
3935 |   @@index([userId], map: "IX_UserContractAuthorityForDepartment_UserID")
3936 |   @@schema("join")
3937 | }
3938 | 
3939 | model UserDepartment {
3940 |   sn                                               Int         @id(map: "PK_UserDepartment") @default(autoincrement()) @map("SN")
3941 |   userId                                           Int?        @map("UserID")
3942 |   departmentId                                     Int?        @map("DepartmentID")
3943 |   present                                          Boolean?    @map("Present")
3944 |   createOn                                         DateTime?   @map("CreateOn") @db.DateTime
3945 |   createBy                                         String?     @map("CreateBy") @db.NVarChar(255)
3946 |   modifyOn                                         DateTime?   @map("ModifyOn") @db.DateTime
3947 |   modifyBy                                         String?     @map("ModifyBy") @db.NVarChar(255)
3948 |   branchId                                         Int?        @map("BranchID")
3949 |   departmentUserDepartmentDepartmentIdToDepartment Department? @relation("UserDepartment_DepartmentIDToDepartment", fields: [departmentId], references: [departmentId], onDelete: NoAction, onUpdate: NoAction, map: "FK_UserDepartment_Department")
3950 |   departmentUserDepartmentBranchIdToDepartment     Department? @relation("UserDepartment_BranchIDToDepartment", fields: [branchId], references: [departmentId], onDelete: NoAction, onUpdate: NoAction, map: "FK_UserDepartment_Department_BranchID")
3951 |   user                                             User?       @relation(fields: [userId], references: [userId], onDelete: Cascade, map: "FK_UserDepartment_User")
3952 | 
3953 |   @@unique([userId, departmentId], map: "IX_UserDepartment_UserID_DepartmentID")
3954 |   @@index([branchId], map: "IX_UserDepartment_BranchID")
3955 |   @@index([createBy], map: "IX_UserDepartment_CreateBy")
3956 |   @@index([createOn], map: "IX_UserDepartment_CreateOn")
3957 |   @@index([modifyBy], map: "IX_UserDepartment_ModifyBy")
3958 |   @@index([modifyOn], map: "IX_UserDepartment_ModifyOn")
3959 |   @@index([userId, present], map: "IX_UserDepartment_UserID_Present")
3960 |   @@schema("join")
3961 | }
3962 | 
3963 | model UserRole {
3964 |   sn                           Int     @id(map: "PK_UserRole") @default(autoincrement()) @map("Sn")
3965 |   userId                       Int     @map("UserID")
3966 |   roleUserId                   Int     @map("RoleUserID")
3967 |   systemDefine                 Boolean @default(false, map: "DF_UserRole_SystemDefine") @map("SystemDefine")
3968 |   userUserRoleRoleUserIdToUser User    @relation("UserRole_RoleUserIDToUser", fields: [roleUserId], references: [userId], onUpdate: NoAction, map: "FK_UserRole_RoleUser")
3969 |   userUserRoleUserIdToUser     User    @relation("UserRole_UserIDToUser", fields: [userId], references: [userId], onDelete: Cascade, map: "FK_UserRole_User")
3970 | 
3971 |   @@unique([userId, roleUserId], map: "IX_UserRole_UserID_RoleUserID")
3972 |   @@index([roleUserId], map: "IX_UserRole_RoleUserID")
3973 |   @@index([userId], map: "IX_UserRole_UserID")
3974 |   @@schema("join")
3975 | }
3976 | 
3977 | model UsingLog {
3978 |   sn          Int       @id(map: "PK_UsingLog") @default(autoincrement()) @map("Sn")
3979 |   loginSn     Int?      @map("LoginSn")
3980 |   usingStatus String?   @map("UsingStatus") @db.NVarChar(Max)
3981 |   usingDate   DateTime? @default(now(), map: "DF_UsingLog_UsingDate") @map("UsingDate") @db.DateTime
3982 |   examStage   String?   @map("ExamStage") @db.NVarChar(250)
3983 |   loginLog    LoginLog? @relation(fields: [loginSn], references: [sn], onDelete: Cascade, map: "FK_UsingLog_LoginLog")
3984 | 
3985 |   @@index([examStage], map: "IX_UsingLog_ExamStage")
3986 |   @@index([loginSn], map: "IX_UsingLog_LoginSn")
3987 |   @@index([usingDate], map: "IX_UsingLog_UsingDate")
3988 |   @@schema("data")
3989 | }
3990 | 
3991 | model Webconfig {
3992 |   sn       Int     @default(autoincrement()) @map("SN")
3993 |   category String  @map("Category") @db.NVarChar(50)
3994 |   key      String  @map("Key") @db.NVarChar(255)
3995 |   value    String? @map("Value") @db.NVarChar(Max)
3996 |   desc     String? @map("Desc") @db.NVarChar(255)
3997 | 
3998 |   @@id([category, key], map: "PK_Webconfig")
3999 |   @@index([desc], map: "IX_Webconfig_Desc")
4000 |   @@index([sn], map: "IX_Webconfig_SN")
4001 |   @@schema("dbo")
4002 | }
</content>
</file>
<environment_details>
# VSCode Visible Files
src/services/contract-access-service.ts

# VSCode Open Tabs
src/routes/contract-access-route.ts,src/services/contract-access-service.ts

# Current Time
4/24/2025, 4:55:26 PM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
27,217 (3%)

# Current Cost
$0.21

# Current Mode
<slug>prisma-repositories-typescript-prompts</slug>
<name>prisma-repositories-typescript.prompts</name>
<model>openai/gpt-4.1</model>
</environment_details>

---

**Assistant:**

<thinking>
1. schema.prisma 並未有明確的 ContractAccess 申請主表，僅有 Contract、ContractAccessRelated、ContractExtendInfo 等。
2. 依據 route/service 的需求，repository 需能儲存一筆合約調閱申請，並產生 applyNo、contractGuid。
3. 目前以 Contract 表的 applyNo 與 contractGuid 欄位為主，暫以 Contract 作為儲存點（未來如有專屬表再調整）。
4. contractAccessRepository 需實作 createContractAccess，並回傳 { applyNo, contractGuid }。
5. 嚴格型別、依賴注入、JSDoc、單例導出。
</thinking>

<write_to_file>
<path>src/repositories/contract-access-repository.ts</path>
<content>
/**
 * 合約調閱申請存儲庫
 * 封裝所有合約調閱申請的資料存取操作
 */
import type { PrismaClient, Contract } from "../../generated/prisma/client";
import { prisma } from "../prisma-client";
import type { CreateContractAccessInput, CreateContractAccessResult } from "../services/contract-access-service";

/**
 * 合約調閱申請存儲庫
 */
export class ContractAccessRepository {
  constructor(private prisma: PrismaClient) {}

  /**
   * 創建合約調閱申請
   * @param input 申請資料
   * @returns 申請結果（申請編號與合約GUID）
   */
  async createContractAccess(input: CreateContractAccessInput): Promise<CreateContractAccessResult> {
    // 實際應用應根據資料表設計儲存，這裡以 Contract 表為例
    // 產生 applyNo 與 contractGuid（實務應有更嚴謹產生規則）
    const now = new Date();
    const applyNo = `CA${now.getFullYear()}${(now.getMonth() + 1)
      .toString()
      .padStart(2, "0")}${now.getDate().toString().padStart(2, "0")}${now.getTime().toString().slice(-4)}`;
    const contractGuid = crypto.randomUUID();

    // 實際應用應根據 input 寫入更多欄位
    const contract = await this.prisma.contract.create({
      data: {
        applyNo,
        contractGuid: {
          create: {
            guid: contractGuid,
          },
        },
        // 其他欄位可依 input 實際對應
        // ...
      },
      include: {
        contractGuid: true,
      },
    });

    return {
      applyNo: contract.applyNo ?? undefined,
      contractGuid: contract.contractGuid?.guid ?? contractGuid,
    };
  }
}

// 導出單例實例
export const contractAccessRepository = new ContractAccessRepository(prisma);
</content>
<line_count>48</line_count>
</write_to_file>

---

**User:**

[write_to_file for 'src/repositories/contract-access-repository.ts'] Result:
The content was successfully saved to src/repositories/contract-access-repository.ts.
<environment_details>
# VSCode Visible Files
src/repositories/contract-access-repository.ts

# VSCode Open Tabs
src/routes/contract-access-route.ts,src/services/contract-access-service.ts,src/repositories/contract-access-repository.ts

# Current Time
4/24/2025, 4:55:53 PM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
108,053 (10%)

# Current Cost
$0.43

# Current Mode
<slug>prisma-repositories-typescript-prompts</slug>
<name>prisma-repositories-typescript.prompts</name>
<model>openai/gpt-4.1</model>
</environment_details>
[TASK RESUMPTION] This task was interrupted 1 minute ago. It may or may not be complete, so please reassess the task context. Be aware that the project state may have changed since then. If the task has not been completed, retry the last step before interruption and proceed with completing the task.

Note: If you previously attempted a tool use that the user did not provide a result for, you should assume the tool use was not successful and assess whether you should retry. If the last tool was a browser_action, the browser has been closed and you must launch a new browser if needed.
<environment_details>
# VSCode Visible Files
src/repositories/contract-access-repository.ts

# VSCode Open Tabs
src/routes/contract-access-route.ts,src/services/contract-access-service.ts,src/repositories/contract-access-repository.ts

# Current Time
4/24/2025, 4:57:15 PM (Asia/Taipei, UTC+8:00)

# Current Context Size (Tokens)
108,053 (10%)

# Current Cost
$0.43

# Current Mode
<slug>prisma-repositories-typescript-prompts</slug>
<name>prisma-repositories-typescript.prompts</name>
<model>openai/gpt-4.1</model>


# Current Workspace Directory (/home/bevis/repo/ecs-ten/ecs-ten-server) Files
.env
.env.example
.windsurfrules
bun.lock
justfile
package-lock.json
package.json
README-task-master.md
README.md
swagger.json
taskmaster-plan.md
tsconfig.json
generated/
generated/prisma/
generated/prisma/client.d.ts
generated/prisma/client.js
generated/prisma/default.d.ts
generated/prisma/default.js
generated/prisma/edge.d.ts
generated/prisma/edge.js
generated/prisma/index-browser.js
generated/prisma/index.d.ts
generated/prisma/index.js
generated/prisma/libquery_engine-debian-openssl-3.0.x.so.node
generated/prisma/package.json
generated/prisma/schema.prisma
generated/prisma/wasm.d.ts
generated/prisma/wasm.js
generated/prisma/runtime/
generated/prisma/runtime/edge-esm.js
generated/prisma/runtime/edge.js
generated/prisma/runtime/index-browser.d.ts
generated/prisma/runtime/index-browser.js
generated/prisma/runtime/library.d.ts
generated/prisma/runtime/library.js
generated/prisma/runtime/react-native.js
generated/prisma/runtime/wasm.js
http/
http/contracts.http
keys/
keys/private/
keys/private/cluster.pkcs8.pem
keys/public/
keys/public/cluster.spki.pem
prisma/
prisma/schema.prisma
scripts/
scripts/example_prd.txt
scripts/prd.txt
src/
src/env-manager.ts
src/generate-jwt.ts
src/index.ts
src/prisma-client.ts
src/middleware/
src/middleware/auth.ts
src/middleware/error.ts
src/middleware/index.ts
src/middleware/jwt.ts
src/middleware/logger.ts
src/repositories/
src/repositories/contract-access-repository.ts
src/repositories/contract-repository.ts
src/repositories/user-repository.ts
src/routes/
src/routes/auth-route.ts
src/routes/contract-access-route.ts
src/routes/contract-route.ts
src/routes/contracts-route.ts
src/routes/index.ts
src/routes/user-route.ts
src/routes/users-route.ts
src/services/
src/services/auth-service.ts
src/services/contract-access-service.ts
src/services/contract-service-define.ts
src/services/contract-service.ts
src/services/user-service-define.ts
src/services/user-service.ts
src/types/
src/types/contract-types.ts
src/types/general-types.ts
src/types/user-types.ts
src/utils/
src/utils/file-utility.ts
src/utils/password-util.ts
tasks/
tasks/task_001.txt
tasks/task_002.txt
tasks/task_003.txt
tasks/task_004.txt
tasks/task_005.txt
tasks/task_006.txt
tasks/task_007.txt
tasks/task_008.txt
tasks/task_009.txt
tasks/task_010.txt
tasks/task_011.txt
tasks/task_012.txt
tasks/task_013.txt
tasks/task_014.txt
tasks/task_015.txt
tasks/task_016.txt
tasks/task_017.txt
tasks/task_018.txt
tasks/task_019.txt
tasks/task_020.txt
tasks/tasks.json
</environment_details>

