# DevTrack AI

> Jira: [Thêm link Jira tại đây]

[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/XTdeRLoD)

## Project Information

| Item | Description |
|---|---|
| Course | SWR302 |
| Class | SE20A11 |
| Semester | SU26 |
| Group | 2 |
| Project Name | DevTrack AI |
| Topic | AI-Integrated Project Workspace for IT Student Teams |

## Team Members

| No | Student ID | Full Name | GitHub Username | Role | Main Responsibility |
|---:|---|---|---|---|---|
| 1 | DE190330 | Phạm Duy Hưng | hung2689 | Leader | Project coordination, requirement planning, report quality control |
| 2 | DE190465 | Nguyễn Thành Đạt | NguyenThanhDat3004 | Member | Feature implementation and project documentation |
| 3 | DE190364 | Nguyễn Lê Trung Tín | Tinnguyen13-7 | Member | Feature implementation and testing support |
| 4 | DE190313 | Trần Công Tú | TuTran205 | Member | Feature implementation and UI/UX support |
| 5 | DE200322 | Nguyễn Minh Hiếu | hieu2816 | Member | Feature implementation and technical research support |

## Tổng quan

DevTrack AI là hệ thống hỗ trợ sinh viên IT quản lý project nhóm theo hướng có quy trình, có traceability, có evidence và có báo cáo tiến độ rõ ràng. Dự án không chỉ tập trung vào việc quản lý task, mà còn liên kết các artifact quan trọng trong vòng đời phát triển phần mềm:

```text
Requirement -> Use Case -> Task -> Test Case -> Bug/Defect -> Evidence -> RTM -> Report
```

Mục tiêu chính của DevTrack AI là giúp nhóm chứng minh được requirement đã được triển khai, kiểm thử, ghi nhận lỗi, xác thực evidence và tổng hợp thành báo cáo có căn cứ.

## Người dùng chính

- Project Leader: tạo project, quản lý requirement, sprint, task, evidence, RTM và weekly report.
- Team Member: thực hiện task, cập nhật trạng thái, chạy test case, tạo bug và upload evidence.
- Mentor/Supervisor: theo dõi tiến độ, xem RTM, review evidence, xem báo cáo và góp ý.
- Admin: quản lý user, project, cấu hình AI provider, storage/upload limit và system usage.

## Phạm vi MVP

Các module chính của MVP gồm:

- Authentication & Invitation
- Project Workspace
- Requirement Management
- Use Case Management
- Task Management
- Sprint Management
- Test Case Management
- Lightweight Bug/Defect
- Evidence Vault
- Requirement Traceability Matrix (RTM)
- AI Assistant
- GitHub Integration
- Contribution Analytics
- Mentor Dashboard

Các chức năng như static analysis nâng cao, AI diff review sâu, export PDF/Excel nâng cao, burndown chart, velocity analytics và advanced notification rules sẽ phù hợp hơn cho các phase sau.

## Workflow chính

```text
1. Create Project
2. Define Requirements
3. Add Use Cases / Acceptance Criteria
4. Generate or Create Tasks
5. Assign Tasks to Members
6. Create Sprint
7. Work on Tasks
8. Create Test Cases
9. Run Tests / Create Bugs
10. Upload Evidence
11. Review Evidence
12. View RTM
13. Generate Weekly Report
```

Với người dùng mới, hệ thống nên có guided workflow, soft lock, smart empty state và AI coaching để hướng dẫn từng bước thay vì để user thao tác rời rạc.

## RTM - Requirement Traceability Matrix

RTM là module trung tâm dùng để theo dõi quan hệ giữa requirement, task, test case, bug và evidence. Mỗi dòng RTM đại diện cho một requirement và thể hiện requirement đó đang ở trạng thái nào.

Logic trạng thái đề xuất:

- `NOT_STARTED`: chưa có task hoặc toàn bộ task còn ở trạng thái todo.
- `IN_PROGRESS`: đã có tiến độ nhưng chưa đủ điều kiện hoàn thành.
- `AT_RISK`: có latest test fail/blocked, có open bug, thiếu accepted evidence bắt buộc hoặc requirement quan trọng chưa có test case.
- `DONE`: tất cả task đã done, latest test đều pass, không còn open bug và evidence bắt buộc đã được accepted.

RTM nên hoạt động theo nguyên tắc read-only với dữ liệu của các module khác. Module này đọc dữ liệu, tính toán trạng thái và tạo snapshot để phục vụ weekly report, sprint review, mentor review và audit tiến độ.

## Evidence Validation

Evidence là minh chứng cho việc một requirement, task hoặc test case đã được thực hiện. Evidence có thể là screenshot, API response, GitHub commit, test result, deploy link, Figma link hoặc document.

Nguyên tắc quan trọng:

```text
Upload evidence != evidence hợp lệ
Evidence hợp lệ = status ACCEPTED
```

Chỉ evidence có trạng thái `ACCEPTED` mới nên được tính vào RTM. Evidence có thể được link tới requirement, task, test case, bug report hoặc sprint, nhưng backend cần validate để tránh evidence bị gắn sai ngữ cảnh.

## AI Integration

AI trong DevTrack AI đóng vai trò hỗ trợ, không thay thế quyết định của người dùng. Các chức năng AI gồm:

- Generate draft task từ requirement.
- Suggest test case từ acceptance criteria.
- Detect missing artifact như thiếu task, test case hoặc evidence.
- Generate weekly report draft.
- Summarize commit/diff ở mức metadata nhẹ.

Nguyên tắc sử dụng AI:

- AI output luôn là draft.
- Người dùng phải review, chỉnh sửa, accept hoặc reject.
- AI không tự mark task done.
- AI không tự accept evidence.
- AI không tự chấm điểm thành viên.

## GitHub Integration

Dự án ưu tiên hướng tích hợp nhẹ:

```text
GitHub Webhook + Conventional Commit + Regex Parsing
```

Ví dụ commit hợp lệ:

```text
feat(TASK-12): implement login API
```

Backend parse `TASK-12`, liên kết commit với task tương ứng và tạo code evidence. Commit không đúng convention sẽ được đưa vào nhóm unlinked commit để Project Leader review và link thủ công.

## RBL - Research Based Learning Focus

Dự án có sử dụng hàm lượng nghiên cứu theo hướng RBL, tập trung vào các nội dung sau:

- Thuật toán/logic nghiệp vụ: nghiên cứu cách tính RTM status, rule đánh giá requirement at risk/done, rule kiểm tra evidence hợp lệ và contribution đa chiều.
- Hệ thống và kiến trúc: nghiên cứu module boundary, data contract giữa các module và nguyên tắc RTM chỉ đọc dữ liệu từ requirement/task/test/bug/evidence.
- Công nghệ: tìm hiểu Spring Boot, PostgreSQL, Flyway, JPA/Hibernate, REST API, GitHub Webhook, file storage và AI API provider.
- AI governance: nghiên cứu cách dùng AI minh bạch trong môi trường học thuật, gồm prompt log, human review, draft/accept/reject flow và giới hạn quyền tự động hóa.
- Testing và traceability: nghiên cứu cách liên kết requirement, test case, test execution, bug, evidence và report để hỗ trợ kiểm thử hệ thống.

## Kiến trúc hệ thống

```text
Frontend Web App
-> Backend API
-> PostgreSQL Database
-> Cloud/File Storage
-> AI Service
-> GitHub Webhook/API
```

| Component | Responsibility |
|---|---|
| Frontend Web App | UI theo role, dashboard, task board, RTM, evidence và report |
| Backend API | Business logic, REST API, authentication và authorization |
| PostgreSQL | Lưu dữ liệu project, requirement, task, test, bug, evidence và report |
| File Storage | Lưu file evidence như screenshot, document, API response hoặc artifact |
| AI Service | Sinh draft task, test case, report và cảnh báo missing artifact |
| GitHub Webhook Receiver | Nhận commit metadata và liên kết commit với task |

## Công nghệ sử dụng

- Java Spring Boot
- PostgreSQL
- Flyway Migration
- JPA/Hibernate
- REST API
- GitHub Webhook
- AI API Provider
- Web frontend theo thiết kế role-based

## Project Structure

```text
backend/              Spring Boot REST API, business logic, authentication, RTM service
frontend/             Web application for role-based project workspace UI
docs/                 SRS, report materials, RBL notes, AI audit/reflection documents
.github/              GitHub configuration and workflow-related files
README.md             Project overview and setup documentation
```

## How to Run

```text
Running instructions will be updated after the team finalizes the implementation environment.
```

## Rủi ro chính

- Scope lớn so với thời gian học kỳ, cần ưu tiên MVP trước.
- Evidence nếu không có review status sẽ dễ bị upload hình thức.
- RTM phụ thuộc nhiều module nên cần thống nhất data contract sớm.
- GitHub commit convention nếu không được nhóm tuân thủ sẽ làm giảm chất lượng traceability.
- AI output cần cơ chế review để tránh hallucination hoặc quyết định tự động thiếu minh bạch.