# 🚀 Postman Data-Driven API Automation Framework


===================================================================================

An enterprise-ready API automated testing framework designed to validate the User Registration lifecycle endpoints hosted via ReqRes.in. This mini-project showcases advanced Quality Assurance patterns, including environment-switching mechanisms, dynamic variable injection, and multi-record Data-Driven Testing (DDT) loops.



🔗 Live Interactive Documentation: [View Live Postman Documentation](https://documenter.getpostman.com/view/39290336/2sBXwvL9aG)



\---



\## 🛠️ Tools Used



Postman Desktop Client: Used for request composition, environment management, and script execution.



JavaScript (Postman Sandbox): Used for writing dynamic assertions, pre-request scripts, and state mutations.



\---



\## 📋 Project Overview



This project delivers end-to-end automated testing coverage for a core User Registration API. It is architected to evaluate system resilience across isolated server scopes by dynamically injecting functional payloads and datasets through the Postman environment model.



\### Core Implementation Competencies:

Dynamic Environment Switching: Seamless context switching across functional stages (e.g., QA vs. Staging environments) without payload mutation.



Dynamic Chaining\*\*: Inter-request state preservation, isolating variables from upstream responses (such as `token` or `userId`) and mapping them downstream.





Data-Driven Testing (DDT): Mass payload script execution utilizing external flat data formats (`.csv`) to parse sequential iterations continuously.

Run Automation\*\*: Full test orchestration mapped using the native Postman Collection Runner client.



\---



\## 🌐 API Endpoints Tested (ReqRes.in)

The project structures a complete CRUD validation lifecycle around the following standard endpoints:



| Method | Endpoint | Description | Purpose in Suite |

| :--- | :--- | :--- | :--- |

| POST | `https://reqres.inapi/login` | User Login | Authenticates session and dynamically extracts the `token`. |

| POST | `https://reqres.inapi/users` | Create User | Injects names/jobs sequentially from the CSV file. Saves the generated `id`. |

| GET | `https://reqres.inapi/users/{{id}}` | Get User Details | Verifies that the created user instance is successfully queryable. |

| PUT | `https://reqres.inapi/users/{{id}}` | Update User | Performs a modification payload test on existing user instances. |

| DELETE | `https://reqres.inapi/users/{{id}}` | Delete User | Removes the user instance and asserts successful teardown state code (204). |



\---



\## 🛠️ Key Technical Features

Authentication Automation: Intercepts session headers on login actions, filtering token parameters out to handle secure resource validation.



Full CRUD Validations: Structured request loops inspecting foundational Create, Read, Update, and Delete endpoints against user instances.



Dynamic Assertion Matrix : Custom JavaScript verification scripts inspecting expected HTTP response statuses, content headers, and JSON body structural integrity.



\---



\## 📦 Repository Structure

```text

├── Collections/

│   └── User\_Registration\_Tests.postman\_collection.json   # Core Request Suite

├── Environments/

│   ├── QA\_Environment.postman\_environment.json           # Target QA Environment

│   └── Staging\_Environment.postman\_environment.json      # Target Staging Environment

├── Data/

│   └── users.csv                                         # DDT Iteration Input Dataset

└── README.md                                             # System Documentation

```



\---



\## 🚀 Getting Started



\### 1. Environment Configurations



Import the provided environment templates located in the `Environments/` path. Ensure you initialize variables representing target deployment URLs and authentication parameters:

\* `baseUrl` (Set to `https://reqres.in`)

\* `token`

\* `id`



\### 2. Collection Import

Load the testing framework into your Postman Workspace by importing the `.json` resource found in the `Collections/` directory.



\### 3. Execution via Collection Runner

1\. Open the Collection Runner dashboard inside Postman.

2\. Designate your target environment (`QA` or `Staging`) via the workspace dropdown menu.

3\. Attach the input iteration database file (`Data/users.csv`). Ensure columns explicitly align with your payload tags (e.g., `{{name}}`, `{{job}}`).

4\. Click Run User Registration to trigger the testing workflow sequence.



\---



\## 💡 Best Practices Implemented



\* Variable Isolation Syntax\*\*: Standardized usage of `{{variable\_name}}` formatting ensures clean separation between environment attributes and dynamic iteration objects.



Secret Masking \& Security: Highly sensitive properties (e.g., access tokens, keys) are designated as Sensitive types in the Postman variable register to guarantee masking in UI run displays.



Header Architecture\*\*: Modular control of mandatory HTTP context protocols (specifically `Authorization` signatures) to maintain access state stability across sequential tests.



