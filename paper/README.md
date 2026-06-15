# DevTrack AI Scientific Paper

Thư mục này chứa bài báo khoa học **DevTrack AI: An Evidence-Based Traceability and Reporting System for Student Software Projects** dưới định dạng LaTeX (Springer LNCS).

## Cấu Trúc Thư Mục

*   `figures/`: Thư mục lưu trữ các hình ảnh minh họa (diagrams, screenshots).
*   `tables/`: Thư mục lưu trữ các bảng dữ liệu LaTeX.
*   `sections/`: Thư mục chứa các phần nội dung chính của bài báo:
    *   `abstract.tex`: Phần tóm tắt (Abstract).
    *   `01_introduction.tex`: Phần đặt vấn đề và giới thiệu (Introduction).
    *   `02_related_work.tex`: Phần nghiên cứu liên quan (Related Work).
    *   `03_method.tex`: Phần tổng quan phương pháp nghiên cứu (Method).
    *   `04_proposed.tex`: Phần thiết kế chi tiết hệ thống đề xuất (Proposed System).
*   `main.tex`: Tệp cấu hình gốc liên kết toàn bộ nội dung và hiển thị danh sách tài liệu tham khảo dưới dạng inline.
*   `references.bib`: Cơ sở dữ liệu tài liệu tham khảo BibTeX chứa 10 citation khoa học gốc.
*   `devtrack_ai_paper.tex`: Tệp nháp đơn gốc (được giữ lại làm tài liệu tham khảo cũ).

## Hướng Dẫn Biên Dịch (Compilation)

Để biên dịch tệp LaTeX chính, hãy mở tệp `main.tex` và sử dụng trình biên dịch LaTeX ưa thích của bạn (ví dụ: pdflatex trên TeXstudio, Overleaf hoặc các phần mềm khác):

```bash
pdflatex main.tex
```
