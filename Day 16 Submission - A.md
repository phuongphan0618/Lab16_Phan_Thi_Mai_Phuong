# Day 16 Submission

**Họ và tên:** Phan Thị Mai Phương

**Mã học viên:** 2A202600281
  ---

  ## 1. Idea reframed

  Original idea:
  > Xây dựng một hệ thống multi-agent RAG để tìm kiếm, đọc và tóm tắt tài liệu học thuật hoặc văn bản chuyên ngành, hỗ trợ tạo survey toàn diện cho các paper

  Reframed as a product opportunity:
  > Một nhóm sinh viên/nghiên cứu sinh đang phải xử lý lượng lớn tài liệu dài và phân tán để làm survey, nhưng quá mất thời gian, trong khi để viết mất trung bình 20 paper chất lượng, tốn nhiều thời gian để đọc và tìm kiếm trên một paper và viết lại tổng hợp.
Các công cụ hiện tại (search engine, PDF reader, chatbot) hỗ trợ từng phần nhưng chưa kết nối tốt giữa tìm kiếm – đọc – tổng hợp – kiểm chứng. Điều này khiến workflow bị đứt đoạn và phụ thuộc nhiều vào thao tác thủ công.

Founding belief: nếu có thể tự động hóa việc kết nối các bước này trong một pipeline thống nhất, thì thời gian làm survey có thể giảm đáng kể.


  ---


  ## 2. Customer / Segment Card


  - **Segment name:** Sinh viên năm cuối / nghiên cứu sinh mới bắt đầu làm research
  - **Operational context:** Làm assignment, khóa luận hoặc bắt đầu viết survey paper
  - **Recurring workflow:** Search paper → đọc từng bài → ghi chú → so sánh → viết lại
  - **Pain moment:** Không biết bắt đầu từ đâu, hoặc đọc nhiều nhưng vẫn không tổng hợp được thành hệ thống
  - **Why now:** LLM phổ biến hơn nhưng chưa thực sự đáng tin trong task học thuật
  - **Access path:** Sinh viên trong lab, trường đại học, hoặc cộng đồng học thuật online

  One-sentence description:
  > Một người đang tập làm research nhưng bị quá tải khi phải đọc nhiều tài liệu và không biết cách tổng hợp hiệu quả
---


## 3. Need Map (2–3 needs)


### Need #1 (priority)
- **Statement (JTBD):** When I have to read many papers on a topic, I want a structured summary across documents, so I can quickly understand the landscape.
- **Current workaround:** Đọc từng paper rồi ghi chú thủ công
- **Pain signal:** Tốn rất nhiều thời gian nhưng vẫn thấy “chưa hiểu hết”
- **Evidence / proxy evidence:** Sinh viên thường chia sẻ note riêng hoặc hỏi nhau trong nhóm
- **Why underserved:** Ít có tool nào tổng hợp nhiều nguồn mà vẫn giữ được ngữ cảnh rõ ràng


### Need #2
- **Statement (JTBD):** When I get an AI-generated summary, I want to know where the information comes from, so I can trust it.
- **Current workaround:** Tự kiểm tra lại từng đoạn.
- **Pain signal:** Không dám dùng trực tiếp output từ AI.
- **Evidence / proxy evidence:** Người dùng thường cross-check với Google hoặc đọc lại paper.
- **Why underserved:**  LLM thường không minh bạch về nguồn hoặc reasoning, hoặc bị hallucination.


### Need #3 (optional)
- **Statement (JTBD):** When I explore a topic, I want to know what I might be missing, so I don’t overlook important directions.
- **Current workaround:** Search lại nhiều lần với keyword khác.
- **Pain signal:** Sợ bị thiếu ý khi viết survey.
- **Evidence / proxy evidence:** Workflow search lặp lại nhiều lần.
- **Why underserved:** Search hiện tại phụ thuộc nhiều vào keyword.

---


## 4. Strategy Statement

For sinh viên và nghiên cứu sinh mới bắt đầu
who struggle with việc đọc và tổng hợp nhiều tài liệu học thuật,
our product helps them tạo summary có cấu trúc từ nhiều nguồn
through một pipeline multi-agent kết hợp retrieval, đọc và tổng hợp,
unlike chatbot thông thường hoặc search engine,
because chúng tôi cố gắng kết nối các bước trong một workflow thống nhất.

---


## 5. Moat Hypothesis
**Moat mechanism:** Learning from usage data

If we deploy nhiều lần trong context học thuật, the following improve:
1. Khả năng tìm đúng paper liên quan
2. Cách hệ thống tóm tắt phù hợp hơn với task survey
3. Một phần khả năng đánh giá output (dù chưa chắc đủ tốt)


Why competitors cannot easily replicate this:
> Có thể cần dữ liệu về cách người dùng đọc và tổng hợp tài liệu, nhưng hiện tại chưa rõ liệu đây có phải lợi thế bền vững hay không

---


## 6. Initial TAM / SAM / SOM view

| Layer | Estimate    | Key assumptions                            | Confidence |
| ----- | ----------- | ------------------------------------------ | ---------- |
| TAM   | $1B–$5B     | Thị trường tool hỗ trợ học tập và research | low        |
| SAM   | $100M–$500M | Sinh viên và researcher                    | low        |
| SOM   | $0.5M–$2M   | Nhắm vào nhóm nhỏ ban đầu                  | low        |


**Top 3 unknowns requiring further research:**
1. Người dùng có thực sự dùng tool này thường xuyên không
2. Output có đủ tốt để thay thế workflow hiện tại không
3. Mức độ trust vào AI trong research là bao nhiêu


**Judgment:**
- [x] Worth pursuing now
- [ ] Worth pursuing but not now (need to validate [...] first)
- [ ] Not worth pursuing as currently framed


---


## 7. Positioning Note (2 sentences)

**What we are:**  
> A multi-agent system for summarizing and synthesizing academic papers efficiently.

**What we are not / not yet:**  
> A replacement for deep reading or critical analysis by researchers.



## 8. Self-assessment before Day 17


Trong 6 mắt xích (Idea → Customer → Need → Strategy → Moat → Market Size), mắt xích nào là yếu nhất?

> Market Size — cần thêm dữ liệu để ước lượng chính xác hơn về quy mô thị trường và mức độ sẵn sàng chi trả của khách hàng.

  Open questions chúng tôi muốn khám phá thêm ở Day 17:
1. Làm thế nào để cải thiện tính minh bạch và độ tin cậy của AI-generated summaries?
2. Quy trình triển khai pipeline có thể mở rộng cho các lĩnh vực khác ngoài học thuật không?
3. Đâu là các yếu tố quyết định để khách hàng sẵn sàng trả phí cho sản phẩm này?
