# HocMon Food AI Chatbot

Đồ án môn Chuyên đề Công nghệ Thông tin.

## Giới thiệu

HocMon Food AI Chatbot là chatbot hỗ trợ gợi ý món ăn và quán ăn tại khu vực Hóc Môn dựa trên nhu cầu của người dùng.

Người dùng có thể nhập yêu cầu bằng tiếng Việt, tiếng Anh hoặc tiếng Nhật. Chatbot sẽ phân tích các thông tin như khẩu vị, ngân sách, vị trí, số người hoặc hoàn cảnh đi ăn để đưa ra các món ăn và quán ăn phù hợp.

Ví dụ:

> "Ở Hóc Môn có quán nào khoảng 100k/người, thích cay và hợp đi nhóm bạn?"

Ngoài thông tin về quán ăn, đề tài cũng hướng đến việc sử dụng dữ liệu từ Google Maps và dữ liệu mạng xã hội để tham khảo xu hướng ẩm thực gần đây.

## Mục tiêu

Đề tài tập trung xây dựng chatbot có khả năng:

- Hiểu câu hỏi bằng tiếng Việt, tiếng Anh và tiếng Nhật.
- Phân tích nhu cầu ăn uống của người dùng.
- Gợi ý món ăn hoặc quán ăn phù hợp.
- Tìm kiếm thông tin dựa trên dữ liệu đã thu thập.
- Sử dụng review và rating để hỗ trợ việc gợi ý.
- Phân tích một số tín hiệu xu hướng từ dữ liệu mạng xã hội.
- Kiểm tra trạng thái hoạt động của quán trước khi gợi ý.
- Giải thích lý do tại sao món hoặc quán đó được đề xuất.

## Dữ liệu

Dữ liệu dự kiến sử dụng gồm:

### Google Maps / Google Places

- Tên quán
- Địa chỉ
- Vị trí
- Rating
- Review
- Giờ mở cửa
- Trạng thái hoạt động

### Dữ liệu mạng xã hội

Một số dữ liệu công khai hoặc dữ liệu được phép sử dụng có thể được dùng để phân tích xu hướng, ví dụ:

- Nội dung hoặc hashtag
- Thời gian đăng
- Lượt xem
- Lượt thích
- Bình luận
- Lượt chia sẻ

Trong trường hợp chưa có quyền truy cập API phù hợp, đề tài có thể sử dụng tập dữ liệu mẫu có cùng cấu trúc để thực nghiệm.

## Công nghệ dự kiến

- Python
- Google Gemini API
- PostgreSQL
- pgvector
- RAG
- Recommendation Engine
- Google Places API

Gemini được sử dụng để hiểu câu hỏi, nhận diện ngôn ngữ, trích xuất các yêu cầu của người dùng và tạo câu trả lời.

Việc lựa chọn quán hoặc món phù hợp không chỉ dựa vào LLM mà còn dựa trên dữ liệu và Recommendation Engine.

## Kiến trúc dự kiến

```text
Google Maps / Social Data
          |
          v
    ETL + Cleaning
          |
          v
Restaurant / Food / Review / Trend Data
          |
          v
 PostgreSQL + pgvector
          |
          v
      User Query
          |
          v
       Gemini
   Intent + Slot
          |
          v
Filter + Semantic Retrieval
          |
          v
Recommendation Engine
          |
          v
         RAG
          |
          v
       Gemini
          |
          v
   Chatbot Response
