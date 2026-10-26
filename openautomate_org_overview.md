# OpenAutomate (`OpenAutomateOrg`) — Organization & Repository Overview

**OpenAutomate** (Business Process Automation Management & Orchestration Platform — **BPAMP**) là nền tảng mã nguồn mở quản lý và điều phối tự động hóa quy trình doanh nghiệp (RPA) theo kiến trúc Cloud-Native và Multi-Tenant, được phát triển bởi nhóm đồ án tốt nghiệp **SE_02** tại Đại học FPT Đà Nẵng. Nền tảng giúp doanh nghiệp triển khai, lập lịch, giám sát và vận hành các bot tự động hóa Python trên các Windows Bot Agent phân tán mà không bị phụ thuộc vào bản quyền thương mại đắt đỏ.

* **GitHub Organization:** [github.com/OpenAutomateOrg](https://github.com/OpenAutomateOrg)
* **Trang chủ dự án:** [openautomate.io/en](https://www.openautomate.io/en)
* **Tài liệu kỹ thuật (Mintlify):** [openautomate.mintlify.app](https://openautomate.mintlify.app/)
* **Video Demo hệ thống:** [OneDrive Video Demo](https://1drv.ms/v/c/e3908a1e20eb3b1a/ESVxLz6Wm-ZEgGdfV2jcg6oBE71-kzJhIQQzzGuqeBlIRA?e=fr6iZB)
* **Tài liệu tóm tắt & Kiến trúc:** [OpenAutomate Project Summary (Google Doc)](https://docs.google.com/document/d/1pQ2Ej8qps5iUN4o0fsiL3uMhvtsmwt6Q6hIyLKEBJjw/edit?usp=drivesdk&ouid=114827782292727089322) · [System Architecture Diagram](https://drive.google.com/file/d/1tAs6q-MDREt_HrrSb7fK5Ial8BeT-CKR/view?usp=drivesdk) · [Database Schema (`OpenAutomateDb.png`)](https://drive.google.com/file/d/1jskb-MdFYx97shzOn9iao1gmpYBjTk24/view?usp=drivesdk)

## 1. Cấu trúc Repositories & Thành phần trong `OpenAutomateOrg`

| Repository / Thành phần | Vai trò chính | Công nghệ cốt lõi | Tính năng nổi bật |
| :--- | :--- | :--- | :--- |
| **[OpenAutomate.Frontend](https://www.google.com/url?sa=E&source=gmail&q=https://github.com/OpenAutomateOrg/OpenAutomate.Frontend)** | Giao diện điều phối trung tâm (Cloud Orchestrator Web UI) | Next.js, TypeScript, Shadcn UI, Tailwind CSS, SWR | Quản lý Multi-Tenant (`/[tenant]/...`), phân quyền RBAC (`OWNER`, `DEVELOPER`, `USER`, System Admin), truy vấn dữ liệu & thống kê qua OData, quản lý Bot Agents, Automation Packages, Schedules, Assets (nhập/xuất CSV, xóa hàng loạt) và theo dõi trạng thái thực thi thời gian thực. |
| **[OpenAutomate.PublicSite](https://www.google.com/url?sa=E&source=gmail&q=https://github.com/OpenAutomateOrg/OpenAutomate.PublicSite)** | Cổng thông tin & Landing Page giới thiệu nền tảng | Next.js, TypeScript, Tailwind CSS, Three.js, GSAP | Hiệu ứng đồ họa 3D và chuyển động mượt mà với Three.js & GSAP, hỗ trợ đa ngôn ngữ (`en` / `vi`), trình diễn Video Demo, bảng gói dịch vụ (Pricing Plans) và điều hướng sang hệ thống Orchestrator & Documentation. |
| **[openautomate-bot-template](https://github.com/OpenAutomateOrg/openautomate-bot-template)** | Bộ khung mẫu (Cookiecutter) phát triển Python RPA Bot | Python 3.11+, Cookiecutter, `openautomateagent` SDK, Selenium | Cung cấp 5 mẫu bot tiêu chuẩn (Hello World, File Processing, Database Operations, Web Automation, API Integration) tích hợp sẵn SDK để gửi log, cập nhật trạng thái và truy xuất biến cấu hình/tài sản (Assets). |
| **Backend Orchestrator Service** | Hệ thống API điều phối trung tâm & lập lịch ngầm | ASP.NET Core, C#, .NET Worker Services, SignalR, Quartz.NET, SQL Server, Redis | Cung cấp REST/OData API theo từng Tenant, kết nối hai chiều thời gian thực qua SignalR (`hub.openautomate.io`), lập lịch công việc nâng cao với Quartz.NET, lưu trữ gói bot trên AWS S3 và tích hợp trợ lý AI qua FastMCP, n8n & Claude AI. |
| **Windows Bot Agent & Python SDK** | Tác nhân thực thi phân tán trên máy trạm/server | Windows Service & Agent UI, Python 3.11/3.12 (`x64`), `openautomateagent` | Đăng ký kết nối với Cloud Orchestrator bằng Machine Key và Organization Slug, tải về gói ZIP tự động hóa, cô lập tiến trình thực thi (tối đa 5 luồng đồng thời trên mỗi Agent) và đồng bộ log trực tiếp về Dashboard. |

## 2. Điểm nhấn Kiến trúc & Tính năng Cốt lõi

* **Kiến trúc Multi-Tenant & Bảo mật RBAC:** Cô lập dữ liệu hoàn toàn giữa các đơn vị tổ chức (Organization Units) thông qua định tuyến theo định danh tổ chức (Organization Slug) và cơ chế phân quyền chi tiết cho từng vai trò quản trị viên hệ thống, chủ sở hữu, lập trình viên và người vận hành.
* **Điều phối & Giám sát Thời gian thực (Real-Time Orchestration):** Kết hợp [OpenAutomate Dashboard](https://openautomate.mintlify.app/orchestrator/dashboard) với SignalR giúp theo dõi trực tiếp tiến trình tải gói bot, trạng thái khởi chạy, nhật ký thực thi (logs) và thông báo hoàn tất hoặc lỗi ngay trên giao diện web.
* **Lập lịch Tự động hóa Linh hoạt (Advanced Scheduling):** Vận hành các tác vụ theo yêu cầu (On-demand) hoặc theo lịch định kỳ phức tạp thông qua hệ thống xử lý nền Quartz.NET.
* **Hệ sinh thái Phát triển Bot bằng Python:** Khởi tạo nhanh dự án bot qua [Python Bot Templates](https://openautomate.mintlify.app/developer/python-templates) (`cookiecutter https://github.com/OpenAutomateOrg/openautomate-bot-template`), đóng gói thành tệp `.zip` kèm `requirements.txt` và triển khai trực tiếp lên Orchestrator.
* **Hạ tầng Đám mây & CI/CD Hiện đại:** Triển khai Frontend trên Vercel, Backend đóng gói Docker chạy trên AWS (Fargate, Application Load Balancer, App Runner, S3, ECR, VPC), kết hợp kiểm soát chất lượng mã nguồn và tự động hóa quy trình qua GitHub Actions, SonarQube Cloud, Mintlify, GitHub Copilot và Claude Code.
* **Trợ lý AI Tích hợp (AI-Powered Assistance):** Hỗ trợ quản lý và tương tác tác vụ tự động hóa bằng ngôn ngữ tự nhiên thông qua tích hợp FastMCP, n8n và Claude AI.

## 3. Đóng góp Cá nhân (Front-End & RPA Developer — Phan Hoàng Nhật)

* **Xây dựng hệ thống Front-End ([OpenAutomate.Frontend](https://www.google.com/url?sa=E&source=gmail&q=https://github.com/OpenAutomateOrg/OpenAutomate.Frontend) & [OpenAutomate.PublicSite](https://www.google.com/url?sa=E&source=gmail&q=https://github.com/OpenAutomateOrg/OpenAutomate.PublicSite)):** Phát triển 2 ứng dụng Next.js (TypeScript) sử dụng Shadcn UI và Tailwind CSS cho giao diện điều phối đa tổ chức bảo mật, kết hợp Three.js và GSAP cho hiệu ứng tương tác trên trang chủ.
* **Thiết kế tầng Dữ liệu & Tích hợp API:** Xây dựng kiến trúc truy vấn dữ liệu phía client với SWR (caching, revalidation) kết nối với ASP.NET Core API & OData endpoints để xử lý đầy đủ các luồng CRUD, thống kê tổng hợp trên Dashboard, nhập/xuất tài sản qua CSV và thao tác xóa hàng loạt (bulk delete) cho Packages, Schedules, Assets, Users và Agents.
* **Phát triển Bot RPA Thực tế:** Xây dựng các kịch bản bot tự động hóa nghiệp vụ tài chính bằng Python (thu thập dữ liệu web, tính toán danh mục và tự động hóa thao tác báo cáo văn phòng/email).

## 4. Phiên bản Tiếng Anh (English Summary — Dùng cho GitHub Profile / Portfolio)

```markdown
### OpenAutomate (`OpenAutomateOrg`) — Cloud-Native Python RPA Orchestration Platform

**OpenAutomate** is an open-source, multi-tenant Business Process Automation Management & Orchestration Platform designed as a cost-effective alternative to proprietary RPA suites. It enables organizations to develop, deploy, schedule, and monitor distributed Python automation bots from a centralized cloud control plane without vendor lock-in.

- **Organization:** [github.com/OpenAutomateOrg](https://github.com/OpenAutomateOrg)
- **Website:** [openautomate.io/en](https://www.openautomate.io/en) | **Docs:** [openautomate.mintlify.app](https://openautomate.mintlify.app/)
- **Demo Video:** [Watch on OneDrive](https://1drv.ms/v/c/e3908a1e20eb3b1a/ESVxLz6Wm-ZEgGdfV2jcg6oBE71-kzJhIQQzzGuqeBlIRA?e=fr6iZB)

#### Core Repositories & Ecosystem
- **[`OpenAutomate.Frontend`](https://github.com/OpenAutomateOrg/OpenAutomate.Frontend):** Multi-tenant Cloud Orchestrator web application built with Next.js, TypeScript, Shadcn UI, Tailwind CSS, and SWR. Features tenant-isolated workspaces, granular RBAC, OData-powered analytics and filtering, CSV asset import/export, Quartz schedule management, and real-time execution monitoring.
- **[`OpenAutomate.PublicSite`](https://github.com/OpenAutomateOrg/OpenAutomate.PublicSite):** Bilingual (`en`/`vi`) marketing and landing site built with Next.js, TypeScript, Tailwind CSS, Three.js, and GSAP animations.
- **[`openautomate-bot-template`](https://github.com/OpenAutomateOrg/openautomate-bot-template):** Official Cookiecutter templates and Python SDK (`openautomateagent`) for building standardized automation bots (Web Automation, File Processing, Database Operations, and API Integration).
- **Backend & Distributed Bot Agent:** ASP.NET Core (C#) backend with SignalR real-time hubs, Quartz.NET job scheduling, SQL Server, Redis, and AWS Fargate/S3 infrastructure, paired with a Windows Bot Agent runtime executing isolated Python 3.11+ processes.
```
