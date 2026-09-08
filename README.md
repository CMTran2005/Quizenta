<div align="center">

<img src="./public/logo.png" alt="Exam Bank Logo" width="120" />

# Exam Bank — Hệ Thống Quản Lý Đề Thi Thông Minh

[![Vercel Deployment](https://img.shields.io/badge/Live_Demo-Vercel-black?style=for-the-badge&logo=vercel)](https://exam-bank-system.vercel.app/)

![Version](https://img.shields.io/badge/version-1.9.1-gray)
![Language](https://img.shields.io/badge/JavaScript-96.5%25-fff2b2)
![TypeScript](https://img.shields.io/badge/TypeScript-3.1%25-bbf7d0)
![CSS](https://img.shields.io/badge/CSS-0.4%25-e9d5ff)

[Tiếng Việt](#tieng-viet) | [English](#english)

</div>

---

<a id="tieng-viet"></a>

## Tiếng Việt

### Giới Thiệu

Exam Bank System là một giải pháp quản lý ngân hàng đề thi và tổ chức thi trực tuyến toàn diện, được thiết kế dành cho các cơ sở giáo dục hiện đại. Nền tảng hỗ trợ soạn thảo đề thi, quản lý ngân hàng câu hỏi, tổ chức thi trực tuyến và phân tích kết quả học tập.

Hệ thống kết hợp các công nghệ tiên tiến bao gồm trí tuệ nhân tạo (Gemini 2.5 Flash) để tự động hóa quá trình nhập liệu đề thi từ ảnh (AI OCR), MathLive để nhập công thức toán học và KaTeX để hiển thị công thức.

### Tính Năng Nổi Bật

#### 1. Cổng Giáo Viên & Trình Soạn Thảo Đề Thi
* Soạn Thảo Thời Gian Thực: Hỗ trợ nhiều giáo viên cùng cộng tác biên soạn trực tiếp trên một đề thi, đồng bộ trạng thái và hiện thị sự có mặt của các cộng tác viên.
* Quản Lý Loại Câu Hỏi Đa Dạng: Hỗ trợ đầy đủ các dạng câu hỏi bao gồm Trắc nghiệm, Đúng/Sai, Điền khuyết, Tự luận, Ghép đôi và Sắp xếp.
* Trợ Lý Số Hóa AI OCR: Tận dụng mô hình Gemini 2.5 Flash để bóc tách nội dung từ ảnh chụp đề thi viết tay hoặc bản in, tự động phân tích cấu trúc câu hỏi và phân loại các phần liên quan.
* Công Cụ Nhập Liệu Toán Học: Tích hợp MathLive cung cấp bàn phím ảo giúp nhập công thức nhanh và trực quan, kết hợp KaTeX để hiển thị công thức đẹp mắt.
* Đấu Trường Live Quiz: Tổ chức thi trực tiếp theo thời gian thực với sảnh chờ, bảng xếp hạng realtime, hiệu ứng âm thanh và vinh danh người chiến thắng.
* Quản Lý Thư Mục & Thùng Rác: Tổ chức đề thi khoa học theo thư mục phân cấp và môn học. Hỗ trợ xóa mềm (soft delete) để phục hồi dữ liệu khi cần.

#### 2. Cổng Học Sinh & Thi Trực Tuyến
* Giao Diện Làm Bài Chuyên Nghiệp: Tách biệt bộ đếm thời gian, danh sách điều hướng câu hỏi và khung làm bài để tối ưu trải nghiệm thi.
* Hệ Thống Chống Gian Lận Đa Tầng:
  * Phát hiện chuyển tab hoặc rời khỏi màn hình thi thông qua Page Visibility API.
  * Khóa các tổ hợp phím hệ thống như F12, Ctrl+C (Sao chép), Ctrl+V (Dán), Ctrl+P (In ấn), Ctrl+U (Xem mã nguồn) trong khi làm bài.
  * Ứng dụng MutationObserver nhằm phát hiện và vô hiệu hóa các tiện ích mở rộng can thiệp vào DOM (ví dụ Sider, Grammarly).
* Sổ Tay Lỗi Sai & Ôn Luyện: Tự động tổng hợp các câu trả lời sai để học sinh có thể luyện tập lại.
* Gamification & Đấu Giải: Áp dụng điểm kinh nghiệm (XP), hệ thống hạng (Leagues) và huy hiệu để khuyến khích học sinh.

#### 3. Học Tập Flashcards (Spaced Repetition)
* Hệ thống tự động chuyển đổi các câu hỏi làm sai từ Sổ Tay Lỗi Sai thành Flashcards.
* Tích hợp thuật toán SM-2 (SuperMemo-2) để quản lý khoảng cách ôn tập dựa trên phản hồi người dùng.

#### 4. Cổng Phụ Huynh
* Kết Nối Học Sinh: Phụ huynh có thể liên kết tài khoản của con em thông qua Mã học sinh hoặc Email.
* Báo Cáo Học Tập Trực Quan: Cung cấp biểu đồ Radar và biểu đồ Area Chart để phân tích hiệu suất và tần suất luyện tập.

#### 5. Cổng Quản Trị & Bảng Thống Kê
* Quản lý tài khoản người dùng và phân quyền truy cập hệ thống.
* Biểu đồ trực quan hóa dữ liệu tăng trưởng đề thi và số lượng câu hỏi theo tháng.
* Thống kê hiệu suất AI OCR bao gồm tỷ lệ chính xác (confidence rate) và thời gian phản hồi (latency).

### Kiến Trúc Tổng Quan

Dự án sử dụng Next.js App Router kết hợp với Firebase. Logic nghiệp vụ được tách biệt thông qua kiến trúc Modular ở cả client và server.

```mermaid
graph TD
    subgraph Giao dien Nguoi dung (Trinh duyet Client)
        TeacherPortal[Cong Giao vien: Soan de, Live Quiz, Thong ke]
        StudentPortal[Cong Hoc sinh: Lam bai, Chong gian lan, Flashcards]
        ParentPortal[Cong Phu huynh: Theo doi tien do, Bieu do]
        AdminPortal[Cong Admin: Quan tri tai khoan]
        ClientStore[Zustand Store & SWR Cache]
    end

    subgraph Tang Xu ly Trung gian (Next.js App Router)
        RouteHandlers[API Routes & Server Actions]
        GradingEngine[Bo cham diem: /api/exams/submit]
        AIEngine[Xu ly AI OCR: Gemini 2.5 Flash]
    end

    subgraph Dich vu Cloud & Persistence
        FirebaseAuth[Firebase Authentication]
        Firestore[(Firebase Firestore - Rules Enforced)]
        Cloudinary[Luu tru anh Cloudinary]
        GCloudVision[Google Cloud Vision API]
    end

    TeacherPortal --> ClientStore
    StudentPortal --> ClientStore
    ParentPortal --> ClientStore
    ClientStore --> RouteHandlers
    RouteHandlers --> GradingEngine
    RouteHandlers --> AIEngine
    GradingEngine --> FirebaseAdmin[Firebase Admin SDK]
    FirebaseAdmin --> Firestore
    FirebaseAdmin --> FirebaseAuth
    AIEngine --> GCloudVision
```

#### Trụ Cột An Toàn Thông Tin
* Server-Side Grading: Toàn bộ quá trình chấm điểm và đối chiếu kết quả được xử lý ở server (ví dụ endpoint `/api/exams/submit`) để tránh gian lận trên client.
* Firestore Security Rules: Áp dụng quy tắc bảo mật (`firestore.rules`) nhằm giới hạn quyền truy cập dữ liệu; người dùng chỉ có quyền đọc/ghi dữ liệu hợp lệ.

#### Kiến Trúc Ngoại Tuyến (Offline-First Capability)
* Sử dụng `@ducanh2912/next-pwa` để cấu hình Service Worker, cache tài nguyên tĩnh và hình ảnh từ Firebase Storage.
* Tích hợp LocalForage để lưu tiến trình làm bài trong IndexedDB, giúp khôi phục khi mất kết nối.

### Cấu Hình Môi Trường

Tạo tệp `.env.local` ở thư mục gốc và điền các biến môi trường sau:

```env
# Google Gemini AI Key
GEMINI_API_KEY=your_gemini_api_key_here

# Cloudinary Storage Settings (Dành cho upload hình ảnh câu hỏi)
NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
NEXT_PUBLIC_CLOUDINARY_UPLOAD_PRESET=your_cloudinary_upload_preset

# Firebase Client SDK Configuration (Kết nối Auth và Firestore ở Client)
NEXT_PUBLIC_FIREBASE_API_KEY=your_firebase_api_key
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
NEXT_PUBLIC_FIREBASE_PROJECT_ID=your_project_id
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=your_project.web.app
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
NEXT_PUBLIC_FIREBASE_APP_ID=your_app_id

# Firebase Admin SDK Configuration (Chạy Server-side Actions bảo mật)
FIREBASE_CLIENT_EMAIL=your_firebase_client_email
FIREBASE_PRIVATE_KEY="your_firebase_private_key"

# Google Cloud Vision API Key (Cho quy trình OCR dự phòng nâng cao)
GOOGLE_CLOUD_API_KEY=your_gcp_api_key
```

### Cài Đặt

Thực hiện theo các bước sau để thiết lập môi trường phát triển cục bộ:

1. Clone mã nguồn dự án từ kho lưu trữ:
```bash
git clone https://github.com/CMTran2005/Exam-Bank-System.git
cd Exam-Bank-System
```

2. Cài đặt các gói phụ thuộc (Dependencies):
```bash
npm install
```

3. Xác thực cấu hình môi trường: Đảm bảo đã tạo và điền đầy đủ các biến vào `.env.local` theo phần cấu hình ở trên.

### Chạy Dự Án

* Khởi chạy môi trường phát triển (Local Development Server):
```bash
npm run dev
```
Sau khi khởi chạy thành công, truy cập ứng dụng qua trình duyệt tại: `http://localhost:3000`

* Biên dịch dự án cho môi trường Production:
```bash
npm run build
```

* Vận hành ứng dụng Production (nếu package.json định nghĩa script `start`):
```bash
npm start
```

* Kiểm tra chất lượng mã nguồn (Linter):
```bash
npm run lint
```

### Cấu Trúc Thư Mục

```text
exam-bank-system/
├── app/                          # Dẫn hướng Next.js App Router và Server API
│   ├── api/                      # Các API Routes xử lý Server-side (Chấm thi, AI OCR)
│   ├── (teacher)/                # Giao diện Cổng Giáo viên (Soạn đề, quản lý lớp)
│   ├── student/                  # Giao diện Cổng Học sinh (Làm bài, Flashcards, Leagues)
│   ├── parent/                   # Giao diện Cổng Phụ huynh (Xem báo cáo năng lực con em)
│   ├── login/                    # Phân hệ Xác thực & Đăng nhập
│   └── layout.jsx                # Layout gốc của toàn bộ hệ thống
├── components/                   # Kho lưu trữ các React Components dùng chung
│   ├── layout/                   # Bố cục giao diện (Header, Sidebar theo từng vai trò)
│   ├── question/                 # Trình soạn thảo và hiển thị câu hỏi nâng cao
│   ├── teacher/                  # Các thành phần dành riêng cho phân hệ giáo viên
│   ├── student/                  # Các thành phần phục vụ quá trình làm bài của học sinh
│   ├── shared/                   # Các UI Components tùy chỉnh và Context Providers
│   └── ui/                       # Hệ thống UI nguyên bản từ shadcn/ui
├── hooks/                        # Các React Custom Hooks quản lý Business Logic tách biệt
│   ├── teacher/                  # Hook quản lý đề thi, lớp học và phân tích số liệu
│   ├── student/                  # Hook xử lý ca thi, lấy danh sách lớp, gamification
│   ├── parent/                   # Hook liên kết con em và tổng hợp báo cáo năng lực
│   └── shared/                   # Hook tiện ích chung (địa giới, cấu hình hệ thống)
├── services/                     # Lớp Giao tiếp Dữ liệu (Data Access Layer) chuẩn JSDoc
│   ├── classService.js           # Nghiệp vụ quản lý lớp học và thành viên lớp
│   ├── examService.js            # Nghiệp vụ quản lý và phân loại đề thi
│   ├── examAttemptService.js     # Ghi nhận kết quả thi và lịch sử chống gian lận
│   ├── flashcardService.js       # Thuật toán lặp lại ngắt quãng SM-2 cho Flashcards
│   └── badgeService.js           # Nghiệp vụ tính điểm gamification và phân phối huy hiệu
├── store/                        # Quản lý trạng thái toàn cục bằng Zustand Stores
├── lib/                          # Các hàm tiện ích, cấu hình và hằng số dùng chung
├── public/                       # Thư mục chứa tài nguyên tĩnh (Hình ảnh, manifest, v.v.)
└── config/                       # Các tệp cấu hình cho hệ thống
```

### Lộ Trình Phát Triển

Bảng tiến độ phát triển (ví dụ các giai đoạn chính):

| Giai Đoạn | Mô Tả Công Việc | Trạng Thái |
|---|---|---|
| Giai Đoạn 1 | Thiết lập nền tảng Next.js, cấu hình TailwindCSS, shadcn/ui và Dark Mode. | Hoàn thành |
| Giai Đoạn 2 | Phát triển lõi soạn thảo câu hỏi, tích hợp Gemini OCR và MathLive. | Hoàn thành |
| Giai Đoạn 3 | Tái cấu trúc mã nguồn theo mô hình Modular. | Hoàn thành |
| Giai Đoạn 4 | Hoàn thiện Module xác thực Firebase và Dashboard. | Hoàn thành |
| Giai Đoạn 5 | Cổng cộng tác thời gian thực, chế độ tập trung và tự động lưu. | Hoàn thành |
| Giai Đoạn 6 | Hệ thống Gamification và Flashcards. | Hoàn thành |
| Giai Đoạn 7 | Server-Side Grading và chống gian lận nâng cao. | Hoàn thành |
| Giai Đoạn 8 | Chuẩn hóa tài liệu, tối ưu hiệu suất và UI. | Hoàn thành |
| Giai Đoạn 9 | Tối ưu hóa chế độ ngoại tuyến và đồng bộ ngầm. | Đang phát triển |

### Hướng Dẫn Đóng Góp

Chào mừng mọi đóng góp từ cộng đồng. Vui lòng tuân thủ quy trình sau:

1. Phân Nhánh (Branching Strategy):
   * Các tính năng mới: `feature/ten-tinh-nang`
   * Sửa lỗi: `bugfix/ten-loi`
   * Refactor: `refactor/ten-phong-ban`

2. Tiêu Chuẩn Viết Mã:
   * Mọi hàm, hook và service mới cần có JSDoc.
   * Viết mã rõ ràng, dễ hiểu và có kiểm thử nếu có thể.

3. Quy Trình Gửi Pull Request:
   * Đảm bảo lint pass: `npm run lint`.
   * Gửi PR kèm mô tả chi tiết các thay đổi và lý do.

### Giấy Phép

Dự án được phát hành theo giấy phép MIT. Xem chi tiết trong tệp `LICENSE`.

---

<a id="english"></a>

## English

### Introduction

Exam Bank System is a comprehensive online question bank management and examination platform designed for modern educational institutions. The platform supports exam editing, question bank management, online exam delivery and performance analytics.

The system integrates advanced technologies including Large Language Models (Gemini 2.5 Flash) for automated question digitization (AI OCR), MathLive for formula input and KaTeX for rendering mathematics.

### Key Features

#### 1. Teacher Portal & Exam Editor
* Real-time Collaboration: Multiple educators can collaborate on the same exam with live presence and synchronized state.
* Diverse Question Types: Support for Multiple Choice, True/False, Fill-in-the-blank, Essay, Matching and Sorting.
* AI OCR Digitization: Uses Gemini 2.5 Flash to parse handwriting or scanned pages and populate editable fields automatically.
* Mathematical Formula Editor: MathLive integration for intuitive formula entry and KaTeX for rendering.
* Live Quiz Arena: Host synchronous quizzes with lobbies, live leaderboards and winner podiums.
* Directory Management & Recycle Bin: Hierarchical folders and soft-delete functionality to recover deleted content.

#### 2. Student Portal & Exam Experience
* Professional Testing Interface: Clear separation of timer, question navigation and exam viewport for optimal UX.
* Multi-layered Anti-Cheat System:
  * Detects tab switches or window blur using the Page Visibility API.
  * Disables developer shortcuts and system keys during exams (F12, Ctrl+C, Ctrl+V, Ctrl+P, Ctrl+U).
  * Uses MutationObserver to detect browser extensions that modify the DOM and take mitigation actions.
* Practice Hub & Error Notebook: Collects incorrect responses for focused practice.
* Gamification & Leagues: XP, ranks and badges to encourage student engagement.

#### 3. Flashcards (Spaced Repetition)
* Converts incorrect questions into Flashcards automatically.
* Implements the SM-2 (SuperMemo-2) spaced repetition algorithm to schedule reviews.

#### 4. Parent Dashboard
* Link student accounts via Student ID or registered email.
* Visual performance reports using Radar and Area charts.

#### 5. Admin Panel & Analytics
* User account and role management.
* Charts for monthly growth of exams and question counts.
* AI OCR telemetry including confidence rate and latency metrics.

### Overall Architecture

The platform is built with Next.js App Router and Firebase. Business logic is separated across modular client-side and secure server-side routes.

```mermaid
graph TD
    subgraph User Interface (Client Browser)
        TeacherPortal[Teacher Portal: Exam Editor, Live Quiz Host, Analytics]
        StudentPortal[Student Portal: Exam Session, Anti-Cheat, Flashcards]
        ParentPortal[Parent Portal: Progress Tracker, Visual Charts]
        AdminPortal[Admin Portal: Account & Role Management]
        ClientStore[Zustand Store & SWR Cache]
    end

    subgraph Server Middleware (Next.js App Router)
        RouteHandlers[API Routes & Server Actions]
        GradingEngine[Grading Engine: /api/exams/submit]
        AIEngine[AI OCR Processor: Gemini 2.5 Flash]
    end

    subgraph Cloud Infrastructure & Persistence
        FirebaseAuth[Firebase Authentication]
        Firestore[(Firebase Firestore - Rules Enforced)]
        Cloudinary[Cloudinary Image Cloud]
        GCloudVision[Google Cloud Vision API]
    end

    TeacherPortal --> ClientStore
    StudentPortal --> ClientStore
    ParentPortal --> ClientStore
    ClientStore --> RouteHandlers
    RouteHandlers --> GradingEngine
    RouteHandlers --> AIEngine
    GradingEngine --> FirebaseAdmin[Firebase Admin SDK]
    FirebaseAdmin --> Firestore
    FirebaseAdmin --> FirebaseAuth
    AIEngine --> GCloudVision
```

### Env Configuration

Create a `.env.local` file and define the variables (see Vietnamese section above for details).

### Installation & Running

Same instructions as in the Vietnamese section (clone, npm install, npm run dev, npm run build, npm start, npm run lint).

### Contribution & License

Follow the branching strategy and PR protocol described above. The project is licensed under the MIT License.

---

<div align="center">

**Made with love by CMTran2005**

[GitHub](https://github.com/CMTran2005) | [Email](mailto:cmtran2005@gmail.com) | [Repository](https://github.com/CMTran2005/Exam-Bank-System)

</div>
