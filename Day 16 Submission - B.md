# Day 16 Submission

**Họ và tên:** Phan Thị Mai Phương  
**Mã học viên:** 2A202600281  

---
## 0. Improvement
Bản B cải thiện so với bản A chủ yếu ở việc chuyển từ mô tả mơ hồ sang mô tả có ngữ cảnh và có thể kiểm chứng hơn. Phần Idea reframed và Customer đã được làm rõ bằng các chi tiết định lượng (ví dụ: 15–30 paper), giúp hình dung rõ workflow thực tế thay vì chỉ hiểu ở mức khái niệm.

Ở phần Need Map, em đã viết lại theo hướng JTBD rõ ràng hơn, với situation cụ thể (đang làm literature review, đọc nhiều paper), và outcome gắn với hệ quả thực tế (hoàn thành synthesis, giảm việc đọc lại). Đồng thời, các phần pain signal và current workaround cũng được diễn đạt chi tiết hơn nhằm thấy rõ hành vi lặp lại và chi phí thời gian của người dùng, thay vì chỉ dừng ở cảm giác “tốn thời gian”.

Phần Strategy được cải thiện ở chỗ giảm tính generic, chuyển từ mô tả kỹ thuật (“multi-agent pipeline”) sang nhấn mạnh giá trị cốt lõi là “giữ mối liên hệ giữa nhiều nguồn” và “hỗ trợ kiểm chứng”, giúp phân biệt rõ hơn với chatbot thông thường.

Ngoài ra, bản B thể hiện sự tiến bộ ở tư duy sản phẩm khi chỉnh lại Market sizing theo hướng có logic hơn (user × pricing) và đồng thời thay đổi Judgment từ “Worth pursuing now” sang “Worth pursuing but not now”, vì các giả định chưa được validate, đặc biệt là về trust và willingness to pay. Phần Moat và Open questions trong bản B được chuyển từ suy đoán chung sang nêu cụ thể loại dữ liệu cần tích lũy và các yếu tố cần kiểm chứng, giúp có thể định hướng tốt hơn cho bước tiếp theo (Day 17).

## 1. Idea reframed

**Original idea:**  
> Xây dựng một hệ thống multi-agent RAG để tìm kiếm, đọc và tóm tắt tài liệu học thuật hoặc văn bản chuyên ngành, hỗ trợ tạo survey toàn diện cho các paper  

**Reframed as a product opportunity:**  
> Một nhóm sinh viên/nghiên cứu sinh đang phải xử lý lượng lớn tài liệu dài và phân tán để làm survey, nhưng quá trình này tốn rất nhiều thời gian do phải đọc, chọn lọc và tự tổng hợp thông tin từ nhiều nguồn khác nhau. Trong thực tế, để viết được một survey có chất lượng, họ thường phải đọc khoảng 15–30 paper, và mỗi paper lại tốn thêm thời gian để hiểu và trích xuất ý chính.  
>
> Nhiều các công cụ hiện tại (search engine, PDF reader, chatbot) chỉ hỗ trợ từng bước riêng lẻ trong workflow, nhưng chưa kết nối tốt giữa các bước như tìm kiếm – đọc – tổng hợp – kiểm chứng. Điều này khiến quá trình làm việc bị đứt đoạn, khó duy trì ngữ cảnh giữa nhiều tài liệu và phụ thuộc nhiều vào thao tác thủ công.  
>
> Founding belief: nếu có thể tự động hóa việc kết nối các bước này trong một pipeline thống nhất, người dùng có thể giảm đáng kể thời gian làm survey, đồng thời vẫn giữ được khả năng theo dõi và kiểm chứng thông tin từ các nguồn gốc ban đầu.  

---

## 2. Customer / Segment Card

- **Segment name:** Sinh viên năm cuối đang viết khóa luận hoặc survey paper đầu tiên  
- **Operational context:** Cần đọc ít nhất 15–30 paper chất lượng thật để tổng hợp thành một phần literature review có hệ thống và logic rõ ràng  
- **Recurring workflow:** Search paper → đọc từng bài → ghi chú → so sánh → viết lại  
- **Pain moment:** Không biết bắt đầu từ đâu, hoặc dù đã đọc nhiều nhưng vẫn không thể tổng hợp thành một hệ thống ý rõ ràng và mạch lạc  
- **Why now:** LLM ngày càng phổ biến và dễ tiếp cận hơn, nhưng vẫn chưa đủ đáng tin trong các task học thuật yêu cầu độ chính xác và kiểm chứng cao  
- **Access path:** Sinh viên trong lab, trường đại học, hoặc các cộng đồng học thuật online  

**One-sentence description:**  
> Một người đang tập làm research nhưng bị quá tải khi phải đọc nhiều tài liệu và gặp khó khăn trong việc tổng hợp chúng thành một hệ thống ý rõ ràng  

---

## 3. Need Map (2–3 needs)

### Need #1 (priority)
- **Statement (JTBD):** When I have to read and take notes on multiple papers (15–30 bài) for a literature review, I want to quickly understand the key ideas and relationships between them, so I can complete the synthesis section on time without having to read every paper in full.  
- **Current workaround:** Đọc từng paper rồi ghi chú thủ công, sau đó tự tổng hợp lại  
- **Pain signal:** Tốn rất nhiều thời gian nhưng vẫn thấy “chưa hiểu hết”, và dễ bị bỏ sót các ý quan trọng nếu chỉ đọc một lần  
- **Evidence / proxy evidence:** Người dùng bắt buộc phải đọc nhiều paper và tự ghi chú thủ công.
- **Why underserved:** Ít có tool nào có thể tổng hợp nhiều nguồn cùng lúc mà vẫn giữ được mối liên hệ giữa các tài liệu và ngữ cảnh tổng thể  

---

### Need #2
- **Statement (JTBD):** When I receive an AI-generated summary while working on a topic, I want to know the exact sources of each piece of information, so I can use the content in my work without having to re-check every source manually.  
- **Current workaround:** Tự kiểm tra lại từng đoạn bằng cách quay lại nguồn gốc hoặc search lại.  
- **Pain signal:** Không dám sử dụng trực tiếp output từ AI vì lo ngại sai lệch hoặc thiếu chính xác.
- **Evidence / proxy evidence:** Người dùng phải lặp lại việc search và đọc nhiều lần khi chưa chắc chắn về độ đúng của thông tin.  
- **Why underserved:** LLM hiện tại thường không cung cấp đầy đủ citation hoặc giải thích rõ ràng nguồn gốc thông tin, dẫn đến khó kiểm chứng.  

---

### Need #3
- **Statement (JTBD):** When I search for papers multiple times using different keywords on the same topic, I want to know what relevant directions or papers I might be missing, so I can ensure my literature review is not incomplete.  
- **Current workaround:** Lặp lại việc search với nhiều keyword khác nhau và tự kiểm tra lại kết quả.  
- **Pain signal:** Lo lắng rằng mình có thể bỏ sót các hướng nghiên cứu quan trọng hoặc paper liên quan.  
- **Evidence / proxy evidence:** Workflow search lặp lại nhiều lần với các từ khóa khác nhau.  
- **Why underserved:** Search hiện tại phụ thuộc nhiều vào keyword và chưa hỗ trợ tốt việc khám phá các hướng liên quan một cách hệ thống.  

---

## 4. Strategy Statement

For sinh viên và nghiên cứu sinh mới bắt đầu  
who struggle with việc đọc và tổng hợp nhiều tài liệu học thuật,  
our product helps them tạo ra các tổng hợp thông tin có cấu trúc kèm theo nguồn dẫn rõ ràng,  
through việc xử lý và liên kết nhiều tài liệu cùng lúc trong một workflow thống nhất,  
unlike chatbot chỉ trả lời từng câu hỏi rời rạc,  
because chúng tôi tập trung vào việc giữ mối liên hệ giữa nhiều nguồn và hỗ trợ kiểm chứng thông tin trong quá trình tổng hợp.  

---

## 5. Moat Hypothesis

**Moat mechanism:** Learning from usage data  

If we deploy nhiều lần trong context học thuật, the following improve:  
1. Khả năng tìm đúng paper liên quan trong từng domain cụ thể  
2. Cách hệ thống tóm tắt và liên kết thông tin giữa nhiều tài liệu phù hợp hơn với task survey  
3. Một phần khả năng đánh giá chất lượng output dựa trên cách người dùng tương tác và phản hồi  

**Why competitors cannot easily replicate this:**  
> Hệ thống cần tích lũy dữ liệu về cách người dùng chọn, đọc và tổng hợp nhiều tài liệu cùng lúc trong một workflow thực tế — loại dữ liệu này không dễ thu thập chỉ từ các tương tác hỏi–đáp đơn lẻ như chatbot thông thường.  

---

## 6. Initial TAM / SAM / SOM view

| Layer | Estimate | Key assumptions | Confidence |
|---|---|---|---|
| TAM | $200M–$2.5B | ~20–50M người dùng có nhu cầu research (10–20% sinh viên toàn cầu) × $10–$50/user/năm | low |
| SAM | $2.5M–$150M | ~0.5–5M sinh viên năm cuối làm khóa luận/survey (10–30% TAM, có thể tiếp cận) × $5–$30/user/năm | low |
| SOM | $2.5K–$225K | Capture 1–3% SAM × ~5% trả phí × $10–$30/user/năm trong 12–24 tháng | low |

**Top 3 unknowns requiring further research:**
1. Người dùng có thực sự sử dụng tool này thường xuyên trong suốt quá trình làm khóa luận, hay chỉ sử dụng ở một số giai đoạn nhất định?  
2. Mức độ trust cần đạt (ví dụ: citation đầy đủ, khả năng giải thích reasoning) để người dùng chấp nhận sử dụng output trong research là bao nhiêu?  
3. Sinh viên có sẵn sàng trả tiền cho một tool hỗ trợ như vậy, hay sẽ tiếp tục sử dụng các công cụ miễn phí hiện tại?  

**Judgment:**
- [ ] Worth pursuing now  
- [x] Worth pursuing but not now (need to validate key assumptions first)  
- [ ] Not worth pursuing as currently framed  

---

## 7. Positioning Note (2 sentences)

**What we are:**  
> A system that helps users synthesize multiple academic sources into structured outputs with traceable evidence.  

**What we are not / not yet:**  
> Not a general-purpose chatbot, and not a replacement for deep reading or critical analysis in research.  

---

## 8. Self-assessment before Day 17

Trong 6 mắt xích (Idea → Customer → Need → Strategy → Moat → Market Size), mắt xích nào là yếu nhất?  

> Market Size — cần thêm dữ liệu thực tế để ước lượng chính xác hơn về quy mô thị trường, cũng như hiểu rõ hơn về mức độ sẵn sàng chi trả của khách hàng trong phân khúc này.  

Open questions chúng tôi muốn khám phá thêm ở Day 17:
1. Làm thế nào để cải thiện tính minh bạch (transparency) và độ tin cậy (trustworthiness) của AI-generated summaries trong bối cảnh học thuật?  
2. Quy trình pipeline hiện tại có thể được điều chỉnh hoặc mở rộng để áp dụng cho các domain khác ngoài học thuật hay không, và nếu có thì cần thay đổi gì?  
3. Những yếu tố nào (ví dụ: độ chính xác, tốc độ, UX, hoặc citation quality) thực sự ảnh hưởng đến quyết định trả phí của người dùng?  