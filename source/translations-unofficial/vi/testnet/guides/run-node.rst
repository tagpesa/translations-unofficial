.. _`Network Dashboard`: https://dashboard.testnet.concordium.com/
.. _Discord: https://discord.gg/xWmQ5tp

.. _run-a-node:

==========
Chạy Node
==========

.. contents::
   :local:
   :backlinks: none

Ở hướng dẫn này, bạn sẽ hiểu được cách chạy node trên máy tính của bạn để tham gia mạng Concordium. Nghĩa là bạn nhận khối và giao dịch từ các node khác, cũng như gửi thông tin các khối và giao dịch tới các node trong mạng Concordium. Hướng dẫn này sẽ cho bạn biết cách:

-  Chạy một Concordium node
-  theo dõi ít trên bảng điều khiển và
-  truy vấn trạng thái của Concordium blockchain ngay trên máy của bạn.

Không cần thiết phải có một tài khoản để chạy node.

Trước khi bắt đầu
================

Trước khi bắt đầu, bạn cần:

1. Cài đặt và chạy Docker.

   -  Trên *Linux*, chỉ cho phép Docker chạy với tài khoản non-root.

2. Tải và giải nén ứng dụng :ref:`concordium-node-and-client-download`.

Nâng cấp từ phiên bản Open Testnet trước đó 
===============================================

Để nâng cấp lên phần mềm Concordium hiện tại cho Open Testnet 4: 

-  Làm theo các bước như trên để :ref:`download<downloads>` phiên bản Concordium mới nhất

-  Chạy lệnh ``concordium-node-reset-data`` từ phần mềm

   -  Với *Mac*: lần đầu tiên chạy ứng dụng, bạn cần chuột phải vào file ``concordium-node-reset-data`` và chọn **Open**. Một thông báo xuất hiện cho biết nguồn gốc ứng dụng không xác định. Chọn **Open**
   -  Với *Windows*: lần đầu tiên chạy ứng dụng, mở file ``concordium-node-reset-data``. Một thông báo xuất hiện cho biết nguồn gốc ứng dụng không xác định. Chọn **More info** → **Run anyway**

-  Bạn sẽ được hỏi:

      *Do you also want to remove saved keys?*

   Tài khoản được tạo ở các phiên bản trước sẽ không còn hiệu lực với Open Testnet 3. Vì vậy, nếu bạn có tài khoản từ những phiên bản trước, nên chọn **y**, nó sẽ xóa toàn bộ tài khoản cũ.

.. _running-a-node:

Chạy node
==============

Để chạy ứng dụng tham gia Open Testnet, hãy làm theo các bước:

1. Chạy lệnh ``concordium-node`` từ thư mục ứng dụng.

-  Với *Mac*: Lần đầu tiên chạy, chuột phải vào ``concordium-node`` và chọn **Open**. Một thông báo xuất hiện cho biết nguồn gốc ứng dụng không xác định. Chọn **Open**
-  Với *Windows*: lần đầu tiên chạy ứng dụng, mở file ``concordium-node``. Một thông báo xuất hiện cho biết nguồn gốc ứng dụng không xác định. Chọn **More info** → **Run anyway**
-  Khi *restarting* node, hãy sử dụng tùy chọn ``--no-block-state-import``. Nó sẽ chỉ tải cập nhật mới của Concordium blockchain xảy ra khi node dừng hoạt động.

2. Nhập tên cho node của bạn. Tên sẽ hiển thị công khai trên bảng điều khiển.

3. Nếu ứng dụng đã được chạy trước đó, bạn sẽ được hỏi có muốn xóa dữ liệu trước đó không. Nhấn **y** sẽ xóa và tải lại toàn bộ Concordium blockchain về máy bạn. **Lưu ý rằng xóa hết dữ liệu node nghĩa là máy bạn sẽ mấy nhiều thời gian hơn để tham gia mạng Concordium**

Bây giờ ứng dụng sẽ bắt đầu tải Concordium Client và tải vào Docker. Nó sẽ chạy và bắt đầu xuất thông tin về hoạt động của node.

Xem node của bạn trên bảng điều khiển
=================================

Sau khi chạy ``concordium-node`` bạn có thể

-  Nhìn thấy node ở bạn ở bảng điều khiển `Network Dashboard`_
-  :ref:`query<testnet-query-node>` thông tin về khối, giao dịch, tài khoản

Bảng điều khiển mạng
-----------------

Sẽ mất một lúc để node của bạn bắt kịp hệ thống Concordium. Đó là bởi node cần tải thông tin của tất cả khối trên chuỗi.

Ở `Network Dashboard`_ bạn sẽ biết được mất bao lâu để node bắt kịp với mạng. Bạn có thể so sánh số lượng khối node đã nhận được với số khối hiện tại của chuỗi ở góc trên của bảng điều khiển.


Bật kết nối đến
============================

Nếu máy của bạn có tường lửa hoặc sử dụng router cá nhân, bạn chỉ có thể kết nối đến các node khác, nhưng họ sẽ không kết nối được đến node của bạn. Không sao cả, node của bạn vẫn có thể tham gia đầy đủ vào mạng Concordium. Nó có thể gửi giao dịch, :ref:`if so configured<become-a-baker>` để xử lý và hoàn thiện giao dịch.


Tuy nhiên, bạn có thể tham gia mạng tốt hơn bằng kích cho phép node nhận kết nối đến. Mặc định, ``concordium-node`` lắng nghe tại cổng ``8888`` trên router của bạn, thêm nó vào tường lửa. Chi tiết cách làm tùy thuộc vào cấu hình của bạn.

Cấu hình cổng kết nối
-----------------

Node lắng nghe trên bốn cổng, có thể được cài đặt bằng cách tùy chọn khi khởi động node. Các cổng được sử dụng:

-  8888, cổng kết nối peer-to-peer, được cài đặt bằng tùy chọn ``--listen-node-port``
-  8082, cổng được sử dụng cho middleware, được cài đặt bằng tùy chọn ``--listen-middleware-port``
-  10000, cổng gRPC, được cài đặt bằng tùy chọn ``--listen-grpc-port``

Khi thiết lập các thay đổi trên, phải dừng ứng dụng (:ref:`stop-a-node`), khởi động và bắt đầu lại. Để chạy lại, sử dụng ``concordium-node-reset-data`` hoặc chạy ``docker rm concordium-client``


Chúng tôi *đề nghị* bạn nên cài đặt tường lửa chỉ cho phép kết nối tới cổng 8888. Ai đó có quyền truy cập vào cổng khác có thể kiểm soát node của bạn hoặc các tài khoản lưu trữ trên đó.
.. _stop-a-node:

Dừng node
=================

Để dừng node, nhấn **CTRL+c** và đợi đến khi hoàn thành.

Nếu bạn lỡ tay tắt cửa sổ chạy ứng dụng mà không dừng, nó sẽ vẫn chạy ngầm trên hệ thống. Trong trường hợp đó, chạy file ``concordium-node-stop``.

Hỗ trợ & phản hồi
==================

Bạn có thể trích xuất log bằng cách sử dụng công cụ ``concordium-node-retrieve-logs``. Nó sẽ lưu log thành một file. Thêm nữa, nếu được cho phép, nó sẽ thu thập thông tin về chương trình đang chạy trên hệ thống.

Bạn có thể gửi log, thông tin hệ thống, câu hỏi và yêu cầu tới testnet@concordium.com. Bạn cũng có thể kết nối với chúng tôi tại `Discord`_, hoặc tìm hiểu tại trang xử lý sự cố :ref:`troubleshooting page<troubleshooting-and-known-issues>`

