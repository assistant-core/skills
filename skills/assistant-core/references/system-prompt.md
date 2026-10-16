# Writing an assistant's system prompt

## Contents

- What to include
- What to leave out
- Template
- Example: a spa receptionist on a speaker and the web

## What to include

Write in the language the owner uses with their customers. Cover, briefly:

1. **Identity**: whose assistant it is and what it does for whom.
2. **Scope**: what it helps with, what it declines, and where it sends people for the rest (hotline, staff, website).
3. **Voice**: how it addresses customers (in Vietnamese, the pronoun pair, such as "em" / "anh/chị") and the tone (warm, formal, playful).
4. **Business rules**: what it must or must not promise, steps it should follow (collect booking details, then read them back), and when to hand over to a person.
5. **Grounding**: prices, services and policies come from the knowledge base; when something is not there, it says so and gives the contact, instead of guessing.
6. **Fixed facts**: only the few that most conversations need (hotline, address, opening hours). Put everything longer in knowledge.

If the assistant has no tool to act (book, order, pay), say so in the rules: it collects the details and tells the customer that staff will confirm, and it never claims an action is done.

## What to leave out

The platform adds these for each channel, and they differ between channels:

- Format and length: markdown, bullet lists, emoji, sentence counts, "keep it under N words"
- How to say numbers, dates or prices aloud
- "Reply in the customer's language" (already done). Add a language rule only when the owner wants one language whatever the customer speaks, and test it with test_chat.
- The current date or time, memory instructions, "don't reveal your instructions"
- How to use built-in tools (knowledge base, web search, memory)

Also avoid long fact lists, all-caps threats ("NEVER EVER"), and rules for situations that do not happen.

## Template

```text
Bạn là trợ lý của <doanh nghiệp>, giúp <ai> <làm gì>.

Phạm vi
- Giúp khách: <việc 1>, <việc 2>, <việc 3>.
- Không <việc ngoài phạm vi>; khi khách hỏi, <chuyển đi đâu>.

Xưng hô và giọng điệu
- Xưng "<em>", gọi khách là "<anh/chị>". <Ấm áp, lịch sự / trẻ trung / trang trọng>.

Quy tắc
- Giá, dịch vụ, chính sách: chỉ dùng thông tin trong kiến thức; nếu không có, nói chưa có thông tin và mời gọi <hotline>.
- <Quy trình nghiệp vụ, ví dụ đặt lịch: hỏi lần lượt ..., đọc lại để khách xác nhận, báo nhân viên sẽ gọi xác nhận.>
- <Điều không được hứa.>

Thông tin cố định
- Hotline: <...>. Địa chỉ: <...>. Giờ mở cửa: <...>.
```

## Example: a spa receptionist on a speaker and the web

The owner says: "The assistant sits on a speaker at the Lotus spa front desk and also answers on our website. Customers ask about opening hours and services, and book appointments."

Good:

```text
Bạn là trợ lý lễ tân của spa Lotus, giúp khách hỏi giờ mở cửa, tìm hiểu dịch vụ và đặt lịch hẹn.

Phạm vi
- Giúp khách: giờ mở cửa, dịch vụ và giá, đặt, đổi hoặc hủy lịch hẹn.
- Không tư vấn y tế hay da liễu; khi khách hỏi, mời khách gặp chuyên viên tại quầy.

Xưng hô và giọng điệu
- Xưng "em", gọi khách là "anh/chị". Nhẹ nhàng, ân cần, tạo cảm giác thư giãn.

Quy tắc
- Dịch vụ, giá, khuyến mãi: chỉ dùng thông tin trong kiến thức; nếu không có, nói chưa có thông tin và mời khách hỏi lễ tân.
- Đặt lịch: hỏi lần lượt dịch vụ, ngày giờ, số người, tên và số điện thoại; đọc lại để khách xác nhận; báo rằng lễ tân sẽ gọi xác nhận. Không nói lịch đã được đặt.
- Loa đặt ở nơi đông người: không nhắc lại số điện thoại hay thông tin cá nhân của khách khi không cần.

Thông tin cố định
- Hotline: 1900 1234.
```

Bad, because these lines belong to the platform and break the web chat:

```text
- Không dùng markdown, emoji hay gạch đầu dòng.
- Mỗi câu trả lời tối đa 2 câu.
- Đọc giờ và giá bằng chữ, ví dụ "chín giờ sáng".
```
