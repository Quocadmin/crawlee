Crawlee là gì?
Crawlee là một thư viện mã nguồn mở dùng để thu thập dữ liệu web (web scraping) và tự động hóa trình duyệt. Nói đơn giản, Crawlee giúp bạn tạo ra các chương trình tự động vào website, lấy dữ liệu bạn cần và lưu trữ lại – hoàn toàn tự động và có thể vượt qua được nhiều lớp bảo vệ chống bot của các website hiện nay.

Crawlee phù hợp cho ai?
Người mới học về web scraping, muốn có một công cụ mạnh, dễ dùng, tài liệu tốt.

Lập trình viên cần xây dựng tool thu thập dữ liệu web nhanh chóng.

Những ai muốn tự động hóa trình duyệt để lấy dữ liệu, tự động test giao diện web, hoặc thu thập dữ liệu phức tạp (cần tải trang bằng JavaScript).

Những điểm mạnh của Crawlee
Hỗ trợ cả crawling truyền thống (gửi request HTTP) và dùng trình duyệt thật (headless browser) như Chrome, Firefox, Webkit.

Tự động phát hiện và vượt qua các hệ thống chống bot (giả lập hành vi người dùng, đổi proxy, quản lý session...).

Lưu trữ kết quả, quản lý hàng đợi URL, mở rộng dễ dàng.

Tích hợp sẵn với Playwright, Puppeteer để điều khiển trình duyệt.

Có CLI (giao diện dòng lệnh) giúp khởi tạo nhanh project mẫu.

Có thể chạy trên máy tính cá nhân, server hoặc deploy lên nền tảng đám mây của Apify nếu muốn.

Cài đặt và khởi động nhanh
Yêu cầu: Cần cài Node.js từ phiên bản 16 trở lên.

Cách cài đặt nhanh nhất
Mở Terminal và gõ:

bash
Sao chép
Chỉnh sửa
npx crawlee create my-crawler
cd my-crawler
npm start
Lệnh này sẽ tạo một project mẫu và chạy thử cho bạn xem cách hoạt động của Crawlee.

Tự thêm vào dự án sẵn có
Cài Crawlee và Playwright:

bash
Sao chép
Chỉnh sửa
npm install crawlee playwright
Tạo file JavaScript, ví dụ main.js, với nội dung:

js
Sao chép
Chỉnh sửa
import { PlaywrightCrawler, Dataset } from 'crawlee';

const crawler = new PlaywrightCrawler({
    async requestHandler({ request, page, enqueueLinks, log }) {
        const title = await page.title();
        log.info(`Title of ${request.loadedUrl} is '${title}'`);
        await Dataset.pushData({ title, url: request.loadedUrl });
        await enqueueLinks();
    },
});

await crawler.run(['https://crawlee.dev']);
Chạy file bằng lệnh:

bash
Sao chép
Chỉnh sửa
node main.js
Dữ liệu sẽ được lưu mặc định vào thư mục ./storage.

Các tính năng nổi bật
Quản lý hàng đợi (queue) URL: Cho phép bạn crawl nhiều trang, dễ dàng mở rộng theo chiều sâu hoặc rộng.

Tự động lưu dữ liệu: Kết quả có thể lưu dạng JSON, CSV, v.v.

Hỗ trợ proxy, tự động đổi IP, quản lý phiên đăng nhập.

Tích hợp Playwright/Puppeteer: Có thể thao tác các website phức tạp (cần login, nhấn nút, scroll...).

Có thể cấu hình chi tiết, mở rộng qua hooks, plugin.

Dễ dàng deploy lên nền tảng đám mây (Apify Cloud) hoặc chạy local.

Tài liệu & Hỗ trợ
Tài liệu chính thức

Ví dụ code mẫu, hướng dẫn chi tiết

Thảo luận, hỏi đáp trên Discord hoặc StackOverflow với tag apify.

Tóm tắt lại
Nếu bạn muốn thu thập dữ liệu tự động từ web (scrape website), hoặc cần điều khiển trình duyệt tự động để lấy dữ liệu như một con người, Crawlee là một công cụ cực kỳ mạnh, dễ dùng và có cộng đồng hỗ trợ lớn.

Chỉ cần biết một chút về JavaScript/Node.js, bạn có thể bắt đầu xây dựng công cụ thu thập dữ liệu của riêng mình!
