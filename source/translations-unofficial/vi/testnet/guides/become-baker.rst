
.. _networkDashboardLink: https://dashboard.testnet.concordium.com/
.. _node-dashboard: http://localhost:8099
.. _Discord: https://discord.com/invite/xWmQ5tp

.. _become-a-baker:

==================================
Trở thành Baker (Tạo khối)
==================================

.. contents::
   :local:
   :backlinks: none

Phần này giải thích Baker là gì, vài trò của nó trong hệ thống và cách trở thành Baker.

Đọc bài này bạn sẽ biết được:

-  Baker là gì và các khái niệm liên quan.
-  Cách nâng cấp node của bạn thành Baker.

Quy trình trở thành Baker có thể tóm tắt thành các bước sau:

#. Tạo tài khoản và kiếm GTU.
#. Tạo Baker key.
#. Đăng ký Baker key với các tài khoản.
#. Chạy node với Baker key.

Sau khi hoàn thành các bước, node của bạn có thể nướng khối. Nếu các khối sau khi nướng được thêm vào chuỗi, bạn sẽ nhận được phần thưởng.

.. note::

   Ở phần này, chúng ta sẽ sử dụng tên ``bakerAccount`` là tên của tài khoản sẽ được sử dụng để trở thành Baker

Định nghĩa
===========

Baker
-----

Node là một baker khi tham gia hệ thống bằng cách tạo khối mới và được thêm vào chuỗi. Baker thu thập, đặt hàng và xác nhận các giao dịch trong một khối để duy trì tính toàn vẹn của hệ thống. Baker ký tên lên từng khối họ xác nhận để phần còn lại của hệ thống có thể kiểm tra và truy cập.

Baker keys
----------

Mỗi baker có một khóa điện tử được gọi là *baker keys*. Node sử dụng những khóa này để ký tên lên các khối. Để xác nhận một khối được ký bởi một baker cụ thể, node phải chạy với một bộ baker key.

Tài khoản Baker
-------------

Mỗi tài khoản có thể sử dụng một bộ baker key để đăng ký làm baker.


Bất cứ khi nào Baker đưa một khối hợp lệ vào chuỗi, sau một thời gian phần thưởng sẽ được trả vào tài khoản liên kết.

Stake và lottery
-----------------

.. todo::

   - Liên kết đến lịch phân phối.

Tài khoản có thể stake một phần GTU và sau đó có thể phân phối tất cả hoặc một phần của số lượng stake này. GTU được stake không thể di chuyển hoặc giao dịch cho đến khi được phân hành bởi Baker.

.. note::

   Nếu một tài khoản nhận được GTU từ giao dịch phân phối, có thể dùng nó để stake ngay cả khi chưa được phát hành.

Để được chọn xác nhận khối, baker phải tham gia *stake* với xác xuất chiến thắng xấp xỉ số GTU stake.

Số tiền stake tương tự được sử dụng để tính toàn liệu Baker có được tham gia uy ban quyết toán hay không. Xem Finalization_.

.. _epochs-and-slots:

Kỷ nguyên và thời điểm
----------------

Trong Concordium blockchain, thời gian được chia thành *các thời điểm*. Thời điểm có thời gian cố định tại khối khởi điểm. Trên bất kỳ nhánh, mỗi thời điểm có thể có một khối, nhưng nhiều khối trên các nhánh khác nhau có thể được tạo ra cùng một thời điểm.

.. todo::

   Hãy thêm một ảnh.

Khi xem xét phần thưởng và các khái niệm liên quan đến bake, chúng tôi sử dụng khái niệm *kỷ nguyên* là khoảng thời gian xác định mà ở đó một tập hợp baker và stake được cố định. Kỷ nguyên có khoảng thời gian cố định ở khối khởi điểm. Ở testnet, epoch = 1 giờ.

Bắt đầu
============

Quản lý tài khoản
-----------------

Phần này sẽ tóm tắt ngắn gọn các bước liên quan đến nhập một tài khoản. Để đọc hướng dẫn chi tiết, xem tại :ref:`managing_accounts`.

Tài khoản được tạo bằng ứng dụng :ref:`concordium_id`. Khi tài khoản được tạo thành công, chuyển đến trang **More** và chọn **Export**, bạn sẽ nhận được file JSON bao gồm thông tin tài khoản.

Để nhập một tài khoản, chạy lệnh

.. code-block:: console

   $concordium-client config account import <path/to/exported/file> --name bakerAccount

``concordium-client`` sẽ yêu cầu bạn nhập mật khẩu để giải mã file và nhập tất cả tài khoản. Mật khẩu đó cũng sẽ được sử dụng để mã hóa khóa giao dịch.

Tạo Baker key và đăng ký
--------------------------------------------

.. note::

   Bước này yêu cầu tài khoản phải có GTU, hãy nhận 100 GTU từ Concordium ID.

Mỗi tài khoản có baker ID duy nhất được sử dụng khi đăng ký Baker. ID này được cung cấp bởi hệ thống và không thể đoán trước. ID này phải được cung cấp thông qua Baker key để node có thể tạo khối. ``concordium-client`` sẽ tự động điền thông tin này khi thực hiện các thao tác sau.

Để tạo key mới, chạy lệnh:

.. code-block:: console

   $concordium-client baker generate-keys <keys-file>.json

Bạn có thể tự đặt tên file. Để đăng ký khóa với mạng, bạn cần chạy node :ref:`running a node <running-a-node>` và gửi giao dịch ``baker add`` đến mạng:

.. code-block:: console

   $concordium-client baker add <keys-file>.json --sender bakerAccount --stake <amountToStake> --out <concordium-data-dir>/baker-credentials.json

thay các thông tin

- ``<amountToStake>`` số GTU bạn muốn stake
- ``<concordium-data-dir>`` theo đường dẫn bên dưới

  * Linux và MacOS: ``~/.local/share/concordium``
  * Windows: ``%LOCALAPPDATA%\\concordium``.

(Tên file được tạo ra nên giữ nguyên ``baker-credentials.json``).

Dùng tùy chọn ``--no-restake`` để bỏ qua tính năng tự động nhập lãi vào gốc. Thao tác này được mô tả trong phần `Restaking the earnings`_.

Để chạy node với baker key và bắt đầu tạo khối, trước tiên bạn cần tắt node đang chạy (có thể nhấn ``Ctrl + C`` ở cửa sổ dòng lệnh hoặc sử dụng ``concordium-node-stop``).

Sau khi lưu file ở thư mục phù hợp (đã hoàn thành ở phần trước khi chọn nơi xuất file), chạy lại node bằng lệnh ``concordium-node``. Node sẽ tự động nướng khi baker được đưa vào danh sách các baker ở kỷ nguyên hiện tại.

This change will be executed
immediately and will take effect when finishing the epoch after the one in which
the transaction for adding the baker was included in a block.

Thay đổi này sẽ được thực hiện ngay lập tức và có hiệu lực sau khi kết thúc kỷ nguyên sau của kỷ nguyên có giao dịch đăng ký Baker được đưa vào khối.

.. table:: Mốc thời gian: đăng ký baker

   +-------------------------------------------+-----------------------------------------+-----------------+
   |                                           | Khi giao dịch được thêm vào khối        | Sau 2 kỷ nguyên |
   +===========================================+=========================================+=================+
   | Thay đổi có thể truy vấn bằng node        |  ✓                                      |                 |
   +-------------------------------------------+-----------------------------------------+-----------------+
   | Baker chính thức được công nhận           |                                         | ✓               |
   +-------------------------------------------+-----------------------------------------+-----------------+

.. note::

   Nếu giao dịch đăng ký Baker được thêm vào khối ở kỷ nguyên `E`, Baker sẽ được công nhận tại kỷ nguyên `E+2`.

Quản lý Baker
==================

Kiểm tra trạng thái của Baker và quyền lực của nó
------------------------------------------------------

Để kiểm tra xem node có đang nướng không, bạn có thể xem từ nhiều nguồn khác nhau.

- Tại bảng điều khiển `network dashboard <http://dashboard.testnet.concordium.com>`_, node của bạn sẽ hiện thị baker ID tại cột ``Baker``.
- Bạn có thể sử dụng ``concordium-client`` để kiểm tra danh sách Baker hiện tại và số GTU được stake, quyền lực. Quyền lực sẽ cho biết khả năng chiến thắng quyền tạo khối của một Baker.

  .. code-block:: console

     $concordium-client consensus show-parameters --include-bakers
     Election nonce:      07fe0e6c73d1fff4ec8ea910ffd42eb58d5a8ecd58d9f871d8f7c71e60faf0b0
     Election difficulty: 4.0e-2
     Bakers:
                                  Account                       Lottery power
             ----------------------------------------------------------------
         ...
         34: 4p2n8QQn5akq3XqAAJt2a5CsnGhDvUon6HExd2szrfkZCTD4FX   <0.0001
         ...

- Bạn có thể sử dụng ``concordium-client`` để kiểm tra tài khoản đã đăng ký Baker và số GTU stake hiện tại.

  .. code-block:: console

     $./concordium-client account show bakerAccount
     ...

     Baker: #22
      - Staked amount: 10.000000 GTU
      - Restake earnings: yes
     ...

- Nếu số lượng stake đủ lớn và node đang chạy với baker key, baker đó sẽ tạo khối và bạn có thể thấy trong ví phần thưởng được nhận như trong hình:

  .. image:: images/bab-reward.png
     :align: center
     :width: 250px

Cập nhật số dư Stake
--------------------------

Nếu muốn stake thêm, bạn có thể chạy câu lệnh bên dưới

.. code-block:: console

   $concordium-client baker update-stake --stake <newAmount> --sender bakerAccount

Thay đổi số dư stake sẽ thay đổi khả năng chiến thắng của baker.

Khi baker **stake lần đầu hoặc tăng số stake**, thay đổi đó sẽ thực hiện trên chuỗi và mọi người đều có thể thấy khi giao dịch được thêm bào khối (xem bằng cách ``concordium-client account show
bakerAccount``) và có hiệu lực sau 2 kỷ nguyên.

.. table:: Mốc thời gian: tăng lượng stake

   +----------------------------------------+-----------------------------------------+----------------+
   |                                        | Khi giao dịch được thêm vào khối        | Sau 2 kỷ nguyên|
   +========================================+=========================================+================+
   | Thay đổi có thể truy vấn bằng node     | ✓                                       |                |
   +----------------------------------------+-----------------------------------------+----------------+
   | Baker sử dụng số dư stake mới          |                                         | ✓              |
   +----------------------------------------+-----------------------------------------+----------------+

Khi Baker **giảm lượng stake**, thay đổi này cần *2 + bakerCooldownEpochs* kỷ nguyên để có hiệu lực. Mọi người có thể thấy trên chuỗi khi giao dịch được thêm vào chuỗi, có thể xem bằng ``concordium-client account show bakerAccount``:

.. code-block:: console

   $concordium-client account show bakerAccount
   ...

   Baker: #22
    - Staked amount: 50.000000 GTU to be updated to 20.000000 GTU at epoch 261  (2020-12-24 12:56:26 UTC)
    - Restake earnings: yes

   ...

.. table:: Mốc thời gian: giảm lượng stake

   +----------------------------------------+-----------------------------------------+----------------------------------------+
   |                                        | Khi giao dịch được thêm vào khối        | Sau *2 + bakerCooldownEpochs* kỷ nguyên|
   +========================================+=========================================+========================================+
   | Thay đổi có thể truy vấn bằng node     | ✓                                       |                                        |
   +----------------------------------------+-----------------------------------------+----------------------------------------+
   | Baker sử dụng số dư stake mới          |                                         | ✓                                      |
   +----------------------------------------+-----------------------------------------+----------------------------------------+
   | Giảm lượng stake lần tiếp theo hoặc    | ✗                                       | ✓                                      |
   | xóa baker                              |                                         |                                        |
   +----------------------------------------+-----------------------------------------+----------------------------------------+

.. note::

   Ở testnet, ``bakerCooldownEpochs`` được đặt ban đầu là 168 kỷ nguyên. Giá trị này có thể xem bằng cách:

   .. code-block:: console

      $concordium-client raw GetBlockSummary
      ...
              "bakerCooldownEpochs": 168
      ...

.. warning::

   Như đã lưu ý trong phần `Definitions`_, số GTU stake bị khóa, không thể di chuyển hoặc sử dụng để thanh toán. Bạn cần tính toán, cân đối stake số GTU không dùng đến trong ngắn hạn. Để xóa baker hoặc thay đổi số dư stake, bạn cần có một chút GTU để làm phí giao dịch.

Lãi nhập gốc
----------------------

Khi Baker tham gia mạng và tạo khối mới, tài khoản sẽ nhận được phần thưởng sau mỗi khối tạo được. Mặc định, phần thưởng sẽ tự động được stake.

Bạn có thể chọn nhận phần thưởng vào tài khoản thay vì tự động stake hết. Bạn có thể làm điều này bằng cạch:

.. code-block:: console

   $concordium-client baker update-restake False --sender bakerAccount
   $concordium-client baker update-restake True --sender bakerAccount

Thay đổi này sẽ có hiệu lực ngay lập tức. Tuy nhiên, nó sẽ ảnh hưởng đến Baker ở kỷ nguyên tiếp theo. Bạn có thể xem thông tin này bằng cách sử dụng ``concordium-client``:

.. code-block:: console

   $concordium-client account show bakerAccount
   ...

   Baker: #22
    - Staked amount: 50.000000 GTU
    - Restake earnings: yes

   ...

.. table:: Mốc thời gian: thay đổi restake

   +-----------------------------------------------------+-----------------------------------+-------------------------------+
   |                                                     | Khi giao dịch được thêm vào khối  |       Sau 2 kỷ nguyên         |
   +=====================================================+===================================+===============================+
   | Thay đổi có thể truy vấn bằng node                  | ✓                                 |                               |
   +-----------------------------------------------------+-----------------------------------+-------------------------------+
   | Phần thưởng sẽ [không] tự động stake                | ✓                                 |                               |
   +-----------------------------------------------------+-----------------------------------+-------------------------------+
   | Nếu tự động stake được kích hoạt, nó sẽ ảnh hưởng   |                                   | ✓                             |
   | quyền lực của Baker                                 |                                   |                               |
   +-----------------------------------------------------+-----------------------------------+-------------------------------+

Khi Baker được đăng ký, nó sẽ tự động stake phần thưởng, nhưng như đã nói ở trên, có thể thay đổi bằng cách thêm tùy chọn ``--no-restake`` khi đăng ký baker:

.. code-block:: console

   $concordium-client baker add baker-keys.json --sender bakerAccount --stake <amountToStake> --out baker-credentials.json --no-restake

Quyết toán
------------

Quyết toán là quá trình bở phiếu được thực hiện bởi các node trong *ủy ban quyết toán* để xác nhận một khối khi phần lớn thành viên nhận và đồng ký kết quả. Khối mới phải được nối với khối cũ hợp lệ để đảm bảo tính toàn vẹn của chuỗi. Chi tiết về quá trình này có thể xem thêm tại :ref:`finalization<glossary-finalization>`.

Ủy ban này được hình thành bởi các baker. Nghĩa là để tham gia, bạn cần thay đổi số lượng stake đến ngưỡng. Ở testnet, để tham gia ủy ban cần stake **0.1% tổng GTU đang tồn tại**.

Tham gia vào ủy ban quyết toán sẽ nhận được phần thưởng tại mỗi khối được xác nhận thành công. Phần thưởng sẽ được trả vào tài khoản.

Xóa Baker
================

Nếu không muốn làm Baker nữa, bạn có thể sử dụng dòng lệnh:

.. code-block:: console

   $concordium-client baker remove --sender bakerAccount

Nó sẽ xóa node của bạn khỏi danh sách Baker và mở khóa số GTU stake để có thể chuyển, giao dịch bình thường.

Thời gian hoàn thành sẽ tương tự như khi giảm lượng stake. Thay đổi cần *2 + bakerCooldownEpochs* kỷ nguyên để có hiệu lực. Thay đổi có thể theo dõi ngay trên chuỗi khi giao dịch được đưa vào khối và bạn có thể kiểm tra thời gian hiệu lực bằng cách:

.. code-block:: console

   $concordium-client account show bakerAccount
   ...

   Baker #22 to be removed at epoch 275 (2020-12-24 13:56:26 UTC)
    - Staked amount: 20.000000 GTU
    - Restake earnings: yes

   ...

.. table:: Mốc thời gian: xóa baker

   +--------------------------------------------+-----------------------------------------+----------------------------------------+
   |                                            | Khi giao dịch được thêm vào khối        | Sau *2 + bakerCooldownEpochs* kỷ nguyên|
   +============================================+=========================================+========================================+
   | Thay đổi có thể truy vấn bằng node         | ✓                                       |                                        |
   +--------------------------------------------+-----------------------------------------+----------------------------------------+
   | Baker bị xóa khỏi danh sách                |                                         | ✓                                      |
   +--------------------------------------------+-----------------------------------------+----------------------------------------+

.. warning::

   Không thể giảm số lượng stake và xóa baker cùng lúc.

Hỗ trợ & phản hồi
=======================================
Nếu bạn gặp vấn đề nào hoặc có đề xuất, hãy đăng lên `Discord`_ hoặc gửi mail đến testnet@concordium.com
