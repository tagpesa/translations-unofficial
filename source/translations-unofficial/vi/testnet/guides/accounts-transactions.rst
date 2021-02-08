.. _Discord: https://discord.gg/xWmQ5tp

.. _guide-account-transactions:

=========================================================
Concordium ID: Tìm hiểu về tài khoản và giao dịch
=========================================================

.. contents::
   :local:
   :backlinks: none

Trước khi làm theo hướng dẫn này, hãy chắc chắn rằng bạn đã tạo initial account và identity như bài hướng dẫn :ref:`the previous chapter<testnet-get-started>`.

Tạo tài khoản mới
====================

Trước khi tìm hiểu cách hoạt động của tài khoản, số dư và giao dịch, hãy tạo tài khoản thứ hai. Bắt đầu bằng cách vào *Accounts*. Ở góc trên bên phải, bạn sẽ thấy một **dấu cộng**. Ấn vào đó để tiếp tục. Ở màn hình tiếp theo, bạn sẽ được yêu cầu nhập tên cho tài khoản mới. Ở ví dụ này, chúng tôi đặt là *Example Account 2*, nhưng bạn có thể đặt theo ý mình.

.. image:: images/concordium-id/acc1.png
      :width: 32%
.. image:: images/concordium-id/acc2.png
      :width: 32%

Khi ấn **Next**, bước tiếp theo bạn cần lựa chọn Identity cho tài khoản mới. Có thể bạn đã có một hoặc nhiều Identity, bạn có thể chọn bất kỳ cái nào bạn muốn trong danh sách. Click vào một Identity, bạn sẽ được chuyển sang bước tiếp theo. Khi tạo một tài khoản thường, ví dụ tài khoản không được tạo ra cùng lúc tạo Identity, bạn có thể chọn công khai một số :ref:`glossary-attribute`. Điều này không cần thiết, và nếu bạn phân vân không biết có nên không, chúng tôi khuyên bạn không nên công khai thuộc tính nào, vì chúng sẽ được lưu trên chuỗi và không thể xóa.

.. image:: images/concordium-id/acc3.png
      :width: 32%
.. image:: images/concordium-id/acc4.png
      :width: 32%

Nếu nhấn vào **Reveal account attributes button**, bạn sẽ được chuyển sang trang tiếp theo. Bạn có thể bỏ chọn những thuộc tính muốn công khai, sau đó nhấn **Submit account**. Click **Submit account** ở đây hoặc ở trang trước đều đưa bạn đến bước cuối cùng, đây là nơi tóm tắt lại tài khoản của bạn và cho biết tài khoản đang được gửi.

.. image:: images/concordium-id/acc5.png
      :width: 32%
.. image:: images/concordium-id/acc6.png
      :width: 32%

Nhấn vào **Ok, thanks**, bạn sẽ được chuyển về trang tài khoản. Bạn có thể thấy tài khoản mới vẫn đang chờ xử lý, sẽ mấy vài phút để hoàn thiện trên chuỗi. Hãy thử nhấn vào mũi tên hướng xuống bên cạnh các tài khoản. Chức năng này sẽ cho bạn thấy hai thông tin, *at disposal* và *staked*. Dòng at disposal sẽ cho bạn biết số dư tài khoản có thể sử dụng, còn staked bạn có thể tìm hiểu thêm tại :ref:`managing accounts<managing_accounts>

.. image:: images/concordium-id/acc7.png
      :width: 32%
.. image:: images/concordium-id/acc8.png
      :width: 32%

Tạo giao dịch
====================

Tiếp theo, thử nhấn vào **Balance** ở tài khoản mới. Tại đây, bạn sẽ thấy số dư, tại thời điểm này bạn có thể nhận được 100 GTU để sử dụng trên Testnet. Yêu cầu nhận 100 GTU là chức năng Testnet, nhưng thực tế ở Testnet 4 bạn sẽ nhận được 2000 GTU. Mỗi tài khoản chỉ có thể nhận GTU một lần. Nhấn vào đây, bạn sẽ thấy một giao dịch xuất hiện. Mất một chút thời gian xử lý, sau đó bạn sẽ nhận được 2000 GTU vào tài khoản.

.. image:: images/concordium-id/acc9.png
      :width: 32%
.. image:: images/concordium-id/acc10.png
      :width: 32%

Bây giờ chúng ta đã có GTU trong tài khoản, hãy thử tại một giao dịch. Để làm điều này, hãy nhấn nút **SEND**. Ở màn hình tiếp theo, nhập số lượng muốn chuyển, chọn người nhận. Ở ví dụ này chúng ta sẽ chuyển 10 GTU.

.. image:: images/concordium-id/acc11.png
      :width: 32%
.. image:: images/concordium-id/acc12.png
      :width: 32%

Nhập số lượng xong, chúng ta sẽ chọn người nhận. Hãy nhấn nút **Recipient or shield amount**. Ở đây, bạn có thể tìm người nhận trong danh bạ hoặc thêm người nhận bằng cách quét mã QR. Như bạn thấy trong hình, chúng tôi chỉ có một người nhận, *Example Account 1*. Ở trên, có lựa chọn *Shield an amount*, chúng ta sẽ tìm hiểu về cái này sau. Hãy chọn người nhận là *Example Account 1* ở ví dụ này.

.. image:: images/concordium-id/acc13.png
      :width: 32%
.. image:: images/concordium-id/acc14.png
      :width: 32%

Nhập xong số lượng và người nhận, nhấn **Send Funds** để tiếp tục. Bạn sẽ được chuyển sang bước xác nhận, hãy kiểm tra lại số lượng, người nhận và tài khoản gửi. Nhấn **Yes, send funds**, bạn sẽ xác thực bằng cách sử dụng mật khẩu hoặc sinh trắc học, sau đó giao dịch sẽ được gửi lên chuỗi. Sẽ mất một lúc để giao dịch được hoàn tất. 

.. image:: images/concordium-id/acc15.png
      :width: 32%
.. image:: images/concordium-id/acc16.png
      :width: 32%

Bây giờ, ở tài khoản *Example Account 2*, nhìn vào *Transfers* sẽ thấy số lượng GTU đã được khấu trừ, cộng thêm phí giao dịch. Tất cả giao dịch đều tốn một khoản phí, tùy vào loại giao dịch mà phí sẽ khác nhau. Nhấn vào giao dịch sẽ cho bạn thấy thông tin chi tiết.

.. image:: images/concordium-id/acc17.png
      :width: 32%
.. image:: images/concordium-id/acc18.png
      :width: 32%

.. _move-an-amount-to-the-shielded-balance:

Chuyển GTU vào Shielded balance
========================================

Nếu bạn quay trở lại trang *Accounts*, bạn sẽ thấy 10 GTU đã được chuyển vào số dư của tài khoản *Example Account 1*. Có thể bạn sẽ nhận ra, các tài khoản có thêm loại số dư khác là Shielded balance. Hiểu đơn giản, đây giống như két sắt để bạn cất GTU an toàn hơn (GTU trong tài khoản này được gọi là shielded GTU). Hãy thử chuyển shielded GTU tới tài khoản *Example Account 2*. Bắt đầu bằng cách nhấn vào **Shielded Balance** ở tài khoản.

.. image:: images/concordium-id/acc19.png
      :width: 32%
.. image:: images/concordium-id/acc20.png
      :width: 32%

Tiếp theo, nhấn nút **SEND** và nhập số lượng GTU muốn *bảo vệ*, đây là bước để chuyển GTU vào *Shielded Balance*. Sau đó, hãy nhấn **Select Recipient or shield amount*, thay vì chọn người nhận, lần này bạn hãy chọn **Shield amount**.

.. image:: images/concordium-id/acc21.png
      :width: 32%
.. image:: images/concordium-id/acc22.png
      :width: 32%

Bạn có thể tiếp tục và xác nhận giao dịch giống như đã làm với giao dịch bình thường ở phần trên. Giao dịch sẽ cần một lúc để hoàn thành trên chuỗi.

.. image:: images/concordium-id/acc23.png
      :width: 32%
.. image:: images/concordium-id/acc24.png
      :width: 32%

Quay lại trang *Accounts*, có thể thấy 10 GTU trong *Shielded Balance* của *Example Account 2*. Nếu nhấn vào *Shielded Balance*, bạn sẽ thấy một giao dịch trong phần Transfers. Loại giao dịch này cũng tốn phí, nhưng phí sẽ được khấu trừ ở số dư thường của tài khoản. Bạn có thể quay lại và xem chi tiết giao dịch trong tài khoản *Balance*.

.. image:: images/concordium-id/acc25.png
      :width: 32%
.. image:: images/concordium-id/acc26.png
      :width: 32%

Tạo Shielded transfer
========================

Khi đã có shielded GTU, bạn có thể thử tạo giao dịch *Shielded transfer*, nghĩa là bạn có thể tạo một giao dịch với shielded GTU. Bước đầu tiên là vào *shielded balance* của tài khoản có shielded GTU. Nhấn nút **SEND**. Hãy nhập số lượng và chọn người nhận. Ở ví dụ này, chúng tôi sẽ chuyển 2 GTU. Khi nhấn **Select Recipient or unshield amount**, bạn có thể chọn người nhận. Chúng tôi chọn *Example Account 2* trong ví dụ này.

.. image:: images/concordium-id/acc27.png
      :width: 32%
.. image:: images/concordium-id/acc28.png
      :width: 32%

Sau khi đã xong số lượng và người nhận, bạn có thể tiếp tục. Giống như những giao dịch khác, bạn sẽ thấy màn hình xác nhận và tiếp tục bằng cách nhập mật khẩu hoặc sinh trắc học, sau đó gửi giao dịch lên chuỗi. Chờ một lúc để giao dịch hoàn thiện trên chuỗi. 

.. image:: images/concordium-id/acc29.png
      :width: 32%
.. image:: images/concordium-id/acc30.png
      :width: 32%

Bây giờ, nếu quay lại trang *Accounts*, bạn sẽ thấy một cái khóa nhỏ xuất hiện bên cạnh số dư của *Shielded Balance*. Nó cho thấy có giao dịch mới đến tài khoản shielded balance. Thử nhấn vào shielded balance, bạn sẽ phải nhập mật khẩu hoặc sinh trắc học để truy cập. Có bước này vì bạn cần phải mở khóa để có thể xem số dư trong tài khoản này.

.. image:: images/concordium-id/acc31.png
      :width: 32%
.. image:: images/concordium-id/acc32.png
      :width: 32%

Mở khóa GTU
==================

Sau khi mở khóa, bạn đã có thể xem được số dư trong tài khoản *shielded balance* và ở trang *Accounts*. Bây giờ, nếu muốn chuyển GTU ở shielded balance tới số dư thường thì làm thế nào? Hãy thử chuyển 2 GTU tới số dư thường, hành động này được gọi là *Unshielding*. Để làm điều này, hãy nhấn nút **SEND** ở tài khoản shielded balance. Nhập số lượng 2, và chọn  **Select Recipient
or unshield amount**. **Choose Unshield amount**

.. image:: images/concordium-id/acc33.png
      :width: 32%
.. image:: images/concordium-id/acc34.png
      :width: 32%
Hoàn thành giao dịch như đã làm với các giao dịch khác, và thử chuyển sang số dư thường. Nếu giao dịch đã xử lý xong trên chuỗi. Bạn có thể thấy số GTU được mở khóa được thêm vào số dư thương. Để ý nó không phải là 2 GTU, dù bạn vừa mở khóa 2 GTU. Đó là vì phí giao dichj sẽ được khấu trừ từ số dư thường của tài khoản thực hiện giao dịch.

.. image:: images/concordium-id/acc35.png
      :width: 32%
.. image:: images/concordium-id/acc36.png
      :width: 32%

Chia sẻ địa chỉ ví
==========================

Nếu bạn muốn chia sẻ địa chỉ tài khoản, rất đơn giản bằng cách nhấn vào nút **Address**. Bạn sẽ được chuyển đến trang có nhiều lựa chọn để chia sẻ địa chỉ tài khoản. Thử nhấn vào nút **Share** và chia sẻ với ai đó.

.. image:: images/concordium-id/acc37.png
      :width: 32%
.. image:: images/concordium-id/acc38.png
      :width: 32%

Kiểm tra lịch trình phân phối
==========================

Với Concordium Blockchain, bạn có thể tạo giao dịch phân phối một số lượng theo thời gian. Đây là chức năng *transfer with a schedule*. Chúng ta sẽ không đi sâu vào cách tạo loại giao dịch này, nó không thể thực hiện ở Concordium ID, nhưng bạn có thể kiểm tra lịch phân phối. Nếu nhận được giao dịch loại này, bạn có thể nhấn vào menu ở góc trên bên phải. Sau đó nhấn **Release schedule**, bạn sẽ được chuyển đến trang có thông tin chi tiết về số lượng và thời gian GTU được phân phối. Nếu bạn muốn tìm hiểu thêm về cách tạo giao dịch này, hãy xem thêm tại trang :ref:`concordium_client` và  :ref:`transactions`

.. image:: images/concordium-id/rel1.png
      :width: 32%
.. image:: images/concordium-id/rel2.png
      :width: 32%
.. image:: images/concordium-id/rel3.png
      :width: 32%

Hỗ trợ & phản hồi
=======================================

Nếu bạn gặp vấn đề nào hoặc có đề xuất, hãy đăng lên `Discord`_ hoặc gửi mail đến testnet@concordium.com