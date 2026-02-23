# Lab_01
Данная лабораторная работа посвещена изучению утилит для разработки проектов.

## Tutorial

Задаём переменные для работы с нашим аккаунтом на GitHub, а также создаём псевдоним для команды edit (Я выбрал редактор nano):
```bash
$ export GITHUB_USERNAME=<имя_пользователя>
$ export GIST_TOKEN=<сохраненный_токен>
$ alias edit=<nano|vi|vim|subl>
```

Создаем рабочую папку внутри каталога текущего пользователя и переходим туда, затем проверяем рабочий каталог командой pwd. Далее возвращаемся назад на уровень вверх с помощью команды cd .. и также проверяем рабочий каталог командой pwd:
```sh
$ mkdir -p ${GITHUB_USERNAME}/workspace
$ cd ${GITHUB_USERNAME}/workspace
$ pwd
$ cd ..
$ pwd
```

Создаем структуру подпапок для разделения задач, проектов и отчетов. Затем переходим обратно в рабочую директорию с помощью команды cd:
```sh
$ mkdir -p workspace/tasks/
$ mkdir -p workspace/projects/
$ mkdir -p workspace/reports/
$ cd workspace
```

Происходит установка Node.js, во время которой файл загружается, распаковывается, удаляется архив, и содержимое перемещается в удобную директорию:
```sh
# Debian
$ wget https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
$ tar -xf node-v6.11.5-linux-x64.tar.xz
$ rm -rf node-v6.11.5-linux-x64.tar.xz
$ mv node-v6.11.5-linux-x64 node
```

Посмотрим список файлов в установленной директории Node.js, чтобы убедиться, что всё скачалось верно:
```sh
$ ls node/bin
$ echo ${PATH}
```
Изменяем пути для доступности Node.js, так что теперь файлы будут доступны глобально:
```sh
$ export PATH=${PATH}:`pwd`/node/bin
$ echo ${PATH}
```
Созданиём скрипт активации, который активирует путь для Node.js всякий раз, когда он запускается:
```sh
$ mkdir scripts
$ cat > scripts/activate<<EOF
export PATH=\${PATH}:`pwd`/node/bin
EOF
$ source scripts/activate
```

Скачиваем пакет gist:
```sh
$ gem install gist
```

Назначаем специальные права доступа и помещаем токен в защищённый файл, потому что без него невозможно отправить данные на сервер:
```sh
$ (umask 0077 && echo ${GIST_TOKEN} > ~/.gist)
```

## Report

Сначала создаётся отдельная папка, в которую копируются материалы лабораторной работы. Далее, используя текстовый редактор, мы редактируем и дополняем содержание нужного файла, формируя полноценный отчёт. Завершающим этапом становится публикация полученного документа на площадке GitHub:
```sh
$ export LAB_NUMBER=01
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gist REPORT.md
```

## 1. Скачайте библиотеку boost с помощью утилиты wget. Адрес для скачивания https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz.
### Для выполнения этого адания, я использовал следующую команду: 
```sh
wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
```
### Вывод в консоль:
```sh
--2026-02-23 12:16:26--  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
Resolving sourceforge.net (sourceforge.net)... 104.18.13.149, 104.18.12.149, 2606:4700::6812:d95, ...
Connecting to sourceforge.net (sourceforge.net)|104.18.13.149|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/ [following]
--2026-02-23 12:16:26--  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/
Reusing existing connection to sourceforge.net:443.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/download [following]
--2026-02-23 12:16:27--  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/download
Reusing existing connection to sourceforge.net:443.
HTTP request sent, awaiting response... 302 Found
Location: https://downloads.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?ts=gAAAAABpnEUbTrKBYuSmSP-48iUaBWtz9-v5Ulra0D9f-Cb-7ROyjIMaQe_HtFl3J4o1UtOM14w_AhnZKOb8CUKQRfItayZd1g%3D%3D&use_mirror=altushost-swe&r= [following]
--2026-02-23 12:16:27--  https://downloads.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?ts=gAAAAABpnEUbTrKBYuSmSP-48iUaBWtz9-v5Ulra0D9f-Cb-7ROyjIMaQe_HtFl3J4o1UtOM14w_AhnZKOb8CUKQRfItayZd1g%3D%3D&use_mirror=altushost-swe&r=
Resolving downloads.sourceforge.net (downloads.sourceforge.net)... 104.18.12.149, 104.18.13.149, 2606:4700::6812:c95, ...
Connecting to downloads.sourceforge.net (downloads.sourceforge.net)|104.18.12.149|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://altushost-swe.dl.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?viasf=1 [following]
--2026-02-23 12:16:28--  https://altushost-swe.dl.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?viasf=1
Resolving altushost-swe.dl.sourceforge.net (altushost-swe.dl.sourceforge.net)... 79.142.76.130
Connecting to altushost-swe.dl.sourceforge.net (altushost-swe.dl.sourceforge.net)|79.142.76.130|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 111710205 (107M) [application/x-gzip]
Saving to: ‘boost_1_69_0.tar.gz.1’

boost_1_69_0.tar.gz 100%[===================>] 106.53M  4.32MB/s    in 49s     

2026-02-23 12:17:19 (2.19 MB/s) - ‘boost_1_69_0.tar.gz.1’ saved [111710205/111710205]
```
## 2. Разархивируйте скаченный файл в директорию ~/boost_1_69_0
### Для выполнения этого задания я использовал команду:
```sh
tar -xf boost_1_69_0.tar.gz
```
## 3. Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.
### Для выполнения этого задания, я использовал команду:
```sh
find ~/boost_1_69_0 -maxdepth 1 -type f | wc -l 
```
-maxdepth 1 - позволяет не учитывать поддиректории
_type f - ищем файлы
wc -l - команда для подсчета
### Вывод в консоль:
```sh
12
```
## 4. Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.
### Для выполнения этого задания, я использовал следующую команду:
```sh
find ~/boost_1_69_0 -type f | wc -l
```
### Вывод в консоль:
```sh
61191
```
## 5. Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).
### Для выполнения этого задания, я использовал следующие команды:
```sh
1) find boost_1_69_0 -type f \( -name "*.h" -o -name "*.hpp" -o -name "*.hh" -o -name "*.hxx" \) | wc -l
2) find boost_1_69_0 -type f -name "*.cpp" | wc -l
3) find boost_1_69_0 -type f ! \( -name "*.h" -o -name "*.hpp" -o -name "*.hh" -o -name "*.hxx" -o -name "*.cpp" \) | wc -l
```
### Вывод в консоль:
```sh
1) 15208
2) 13774
3) 32209
```
## 6. Найдите полный пусть до файла any.hpp внутри библиотеки boost.
### Для выполнения этого задания, я использовал следующую команду:
```sh
find boost_1_69_0/boost -name "any.hpp" -type f
```
### Вывод в консоль:
```sh
boost_1_69_0/boost/fusion/include/any.hpp
boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
boost_1_69_0/boost/fusion/algorithm/query/any.hpp
boost_1_69_0/boost/xpressive/detail/utility/any.hpp
boost_1_69_0/boost/proto/detail/any.hpp
boost_1_69_0/boost/any.hpp
boost_1_69_0/boost/hana/any.hpp
boost_1_69_0/boost/hana/fwd/any.hpp
boost_1_69_0/boost/spirit/home/support/algorithm/any.hpp
boost_1_69_0/boost/type_erasure/any.hpp
```
## 7. Выведите в консоль все файлы, где упоминается последовательность boost::asio.
### Для выполнения этого задания, я использовал следующие команды:
```sh
1)cd boost_1_69_0
2)grep -rl "boost::asio" boost_1_69_0
```
grep - ищет текст в файлах
### Вывод в консоль:
```sh
boost_1_69_0/libs/coroutine2/doc/coro.qbk
boost_1_69_0/libs/coroutine2/doc/motivation.qbk
boost_1_69_0/libs/process/doc/autodoc.xml
boost_1_69_0/libs/process/doc/tutorial.qbk
boost_1_69_0/libs/process/doc/extend.qbk
boost_1_69_0/libs/process/example/wait.cpp
boost_1_69_0/libs/process/example/io.cpp
boost_1_69_0/libs/process/example/async_io.cpp
boost_1_69_0/libs/process/test/bind_stdout_stderr.cpp
boost_1_69_0/libs/process/test/system_test1.cpp
boost_1_69_0/libs/process/test/async_system_stackful.cpp
boost_1_69_0/libs/process/test/bind_stdin.cpp
boost_1_69_0/libs/process/test/spawn.cpp
boost_1_69_0/libs/process/test/on_exit2.cpp
boost_1_69_0/libs/process/test/exit_code.cpp
boost_1_69_0/libs/process/test/async_fut.cpp
boost_1_69_0/libs/process/test/bind_stdout.cpp
boost_1_69_0/libs/process/test/async_system_stackless.cpp
boost_1_69_0/libs/process/test/async_system_fail.cpp
boost_1_69_0/libs/process/test/async_system_stackful_except.cpp
boost_1_69_0/libs/process/test/async_system_future.cpp
boost_1_69_0/libs/process/test/wait.cpp
boost_1_69_0/libs/process/test/async_pipe.cpp
boost_1_69_0/libs/process/test/on_exit3.cpp
boost_1_69_0/libs/process/test/system_test2.cpp
boost_1_69_0/libs/process/test/async_system_stackful_error.cpp
boost_1_69_0/libs/process/test/bind_stderr.cpp
boost_1_69_0/libs/process/test/async.cpp
boost_1_69_0/libs/process/test/on_exit.cpp
boost_1_69_0/libs/process/test/spawn_fail.cpp
boost_1_69_0/libs/asio/doc/reference.qbk
boost_1_69_0/libs/asio/doc/requirements/ResolveHandler.qbk
boost_1_69_0/libs/asio/doc/requirements/ConstBufferSequence.qbk
boost_1_69_0/libs/asio/doc/requirements/SignalHandler.qbk
boost_1_69_0/libs/asio/doc/requirements/ReadHandler.qbk
boost_1_69_0/libs/asio/doc/requirements/WriteHandler.qbk
boost_1_69_0/libs/asio/doc/requirements/MoveAcceptHandler.qbk
boost_1_69_0/libs/asio/doc/requirements/RangeConnectHandler.qbk
boost_1_69_0/libs/asio/doc/requirements/ShutdownHandler.qbk
boost_1_69_0/libs/asio/doc/requirements/BufferedHandshakeHandler.qbk
boost_1_69_0/libs/asio/doc/requirements/Handler.qbk
boost_1_69_0/libs/asio/doc/requirements/HandshakeHandler.qbk
boost_1_69_0/libs/asio/doc/requirements/AcceptHandler.qbk
boost_1_69_0/libs/asio/doc/requirements/IteratorConnectHandler.qbk
boost_1_69_0/libs/asio/doc/requirements/ConnectHandler.qbk
boost_1_69_0/libs/asio/doc/requirements/WaitHandler.qbk
boost_1_69_0/libs/asio/doc/requirements/MutableBufferSequence.qbk
boost_1_69_0/libs/asio/doc/tutorial.qbk
boost_1_69_0/libs/asio/doc/overview/spawn.qbk
boost_1_69_0/libs/asio/doc/overview/coroutines_ts.qbk
boost_1_69_0/libs/asio/doc/overview/allocation.qbk
boost_1_69_0/libs/asio/doc/overview/strands.qbk
boost_1_69_0/libs/asio/doc/overview/buffers.qbk
boost_1_69_0/libs/asio/doc/overview/other_protocols.qbk
boost_1_69_0/libs/asio/doc/overview/protocols.qbk
boost_1_69_0/libs/asio/doc/overview/signals.qbk
boost_1_69_0/libs/asio/doc/overview/ssl.qbk
boost_1_69_0/libs/asio/doc/overview/basics.qbk
boost_1_69_0/libs/asio/doc/overview/cpp2011.qbk
boost_1_69_0/libs/asio/doc/overview/posix.qbk
boost_1_69_0/libs/asio/doc/overview/coroutine.qbk
boost_1_69_0/libs/asio/doc/overview/line_based.qbk
boost_1_69_0/libs/asio/doc/examples.qbk
boost_1_69_0/libs/asio/doc/using.qbk
boost_1_69_0/libs/asio/doc/reference.xsl
boost_1_69_0/libs/asio/example/cpp17/coroutines_ts/double_buffered_echo_server.cpp
boost_1_69_0/libs/asio/example/cpp17/coroutines_ts/chat_server.cpp
boost_1_69_0/libs/asio/example/cpp17/coroutines_ts/echo_server.cpp
boost_1_69_0/libs/asio/example/cpp17/coroutines_ts/range_based_for.cpp
boost_1_69_0/libs/asio/example/cpp17/coroutines_ts/refactored_echo_server.cpp
boost_1_69_0/libs/asio/example/cpp11/chat/chat_server.cpp
boost_1_69_0/libs/asio/example/cpp11/chat/chat_client.cpp
boost_1_69_0/libs/asio/example/cpp11/futures/daytime_client.cpp
boost_1_69_0/libs/asio/example/cpp11/local/stream_server.cpp
boost_1_69_0/libs/asio/example/cpp11/local/stream_client.cpp
boost_1_69_0/libs/asio/example/cpp11/local/connect_pair.cpp
boost_1_69_0/libs/asio/example/cpp11/local/iostream_client.cpp
boost_1_69_0/libs/asio/example/cpp11/operations/composed_2.cpp
boost_1_69_0/libs/asio/example/cpp11/operations/composed_1.cpp
boost_1_69_0/libs/asio/example/cpp11/operations/composed_5.cpp
boost_1_69_0/libs/asio/example/cpp11/operations/composed_3.cpp
boost_1_69_0/libs/asio/example/cpp11/operations/composed_4.cpp
boost_1_69_0/libs/asio/example/cpp11/echo/blocking_tcp_echo_client.cpp
boost_1_69_0/libs/asio/example/cpp11/echo/async_udp_echo_server.cpp
boost_1_69_0/libs/asio/example/cpp11/echo/async_tcp_echo_server.cpp
boost_1_69_0/libs/asio/example/cpp11/echo/blocking_tcp_echo_server.cpp
boost_1_69_0/libs/asio/example/cpp11/echo/blocking_udp_echo_client.cpp
boost_1_69_0/libs/asio/example/cpp11/echo/blocking_udp_echo_server.cpp
boost_1_69_0/libs/asio/example/cpp11/http/server/server.cpp
boost_1_69_0/libs/asio/example/cpp11/http/server/reply.cpp
boost_1_69_0/libs/asio/example/cpp11/http/server/server.hpp
boost_1_69_0/libs/asio/example/cpp11/http/server/reply.hpp
boost_1_69_0/libs/asio/example/cpp11/http/server/connection.cpp
boost_1_69_0/libs/asio/example/cpp11/http/server/connection.hpp
boost_1_69_0/libs/asio/example/cpp11/spawn/echo_server.cpp
boost_1_69_0/libs/asio/example/cpp11/spawn/parallel_grep.cpp
boost_1_69_0/libs/asio/example/cpp11/multicast/sender.cpp
boost_1_69_0/libs/asio/example/cpp11/multicast/receiver.cpp
boost_1_69_0/libs/asio/example/cpp11/executors/priority_scheduler.cpp
boost_1_69_0/libs/asio/example/cpp11/executors/bank_account_2.cpp
boost_1_69_0/libs/asio/example/cpp11/executors/bank_account_1.cpp
boost_1_69_0/libs/asio/example/cpp11/executors/actor.cpp
boost_1_69_0/libs/asio/example/cpp11/executors/pipeline.cpp
boost_1_69_0/libs/asio/example/cpp11/executors/fork_join.cpp
boost_1_69_0/libs/asio/example/cpp11/iostreams/http_client.cpp
boost_1_69_0/libs/asio/example/cpp11/timers/time_t_timer.cpp
boost_1_69_0/libs/asio/example/cpp11/handler_tracking/async_tcp_echo_server.cpp
boost_1_69_0/libs/asio/example/cpp11/handler_tracking/custom_tracking.hpp
boost_1_69_0/libs/asio/example/cpp11/allocation/server.cpp
boost_1_69_0/libs/asio/example/cpp11/invocation/prioritised_handlers.cpp
boost_1_69_0/libs/asio/example/cpp11/buffers/reference_counted.cpp
boost_1_69_0/libs/asio/example/cpp11/fork/daemon.cpp
boost_1_69_0/libs/asio/example/cpp11/fork/process_per_connection.cpp
boost_1_69_0/libs/asio/example/cpp11/timeouts/server.cpp
boost_1_69_0/libs/asio/example/cpp11/timeouts/blocking_token_tcp_client.cpp
boost_1_69_0/libs/asio/example/cpp11/timeouts/blocking_udp_client.cpp
boost_1_69_0/libs/asio/example/cpp11/timeouts/async_tcp_client.cpp
boost_1_69_0/libs/asio/example/cpp11/timeouts/blocking_tcp_client.cpp
boost_1_69_0/libs/asio/example/cpp11/ssl/server.cpp
boost_1_69_0/libs/asio/example/cpp11/ssl/client.cpp
boost_1_69_0/libs/asio/example/cpp11/socks4/socks4.hpp
boost_1_69_0/libs/asio/example/cpp11/socks4/sync_client.cpp
boost_1_69_0/libs/asio/example/cpp11/nonblocking/third_party_lib.cpp
boost_1_69_0/libs/asio/example/cpp03/chat/posix_chat_client.cpp
boost_1_69_0/libs/asio/example/cpp03/chat/chat_server.cpp
boost_1_69_0/libs/asio/example/cpp03/chat/chat_client.cpp
boost_1_69_0/libs/asio/example/cpp03/local/stream_server.cpp
boost_1_69_0/libs/asio/example/cpp03/local/stream_client.cpp
boost_1_69_0/libs/asio/example/cpp03/local/connect_pair.cpp
boost_1_69_0/libs/asio/example/cpp03/local/iostream_client.cpp
boost_1_69_0/libs/asio/example/cpp03/echo/blocking_tcp_echo_client.cpp
boost_1_69_0/libs/asio/example/cpp03/echo/async_udp_echo_server.cpp
boost_1_69_0/libs/asio/example/cpp03/echo/async_tcp_echo_server.cpp
boost_1_69_0/libs/asio/example/cpp03/echo/blocking_tcp_echo_server.cpp
boost_1_69_0/libs/asio/example/cpp03/echo/blocking_udp_echo_client.cpp
boost_1_69_0/libs/asio/example/cpp03/echo/blocking_udp_echo_server.cpp
boost_1_69_0/libs/asio/example/cpp03/serialization/server.cpp
boost_1_69_0/libs/asio/example/cpp03/serialization/client.cpp
boost_1_69_0/libs/asio/example/cpp03/serialization/connection.hpp
boost_1_69_0/libs/asio/example/cpp03/windows/transmit_file.cpp
boost_1_69_0/libs/asio/example/cpp03/http/server4/server.cpp
boost_1_69_0/libs/asio/example/cpp03/http/server4/reply.cpp
boost_1_69_0/libs/asio/example/cpp03/http/server4/server.hpp
boost_1_69_0/libs/asio/example/cpp03/http/server4/main.cpp
boost_1_69_0/libs/asio/example/cpp03/http/server4/reply.hpp
boost_1_69_0/libs/asio/example/cpp03/http/server4/request_parser.hpp
boost_1_69_0/libs/asio/example/cpp03/http/server3/server.cpp
boost_1_69_0/libs/asio/example/cpp03/http/server3/reply.cpp
boost_1_69_0/libs/asio/example/cpp03/http/server3/server.hpp
boost_1_69_0/libs/asio/example/cpp03/http/server3/reply.hpp
boost_1_69_0/libs/asio/example/cpp03/http/server3/connection.cpp
boost_1_69_0/libs/asio/example/cpp03/http/server3/connection.hpp
boost_1_69_0/libs/asio/example/cpp03/http/client/async_client.cpp
boost_1_69_0/libs/asio/example/cpp03/http/client/sync_client.cpp
boost_1_69_0/libs/asio/example/cpp03/http/server2/server.cpp
boost_1_69_0/libs/asio/example/cpp03/http/server2/reply.cpp
boost_1_69_0/libs/asio/example/cpp03/http/server2/io_context_pool.hpp
boost_1_69_0/libs/asio/example/cpp03/http/server2/server.hpp
boost_1_69_0/libs/asio/example/cpp03/http/server2/io_context_pool.cpp
boost_1_69_0/libs/asio/example/cpp03/http/server2/reply.hpp
boost_1_69_0/libs/asio/example/cpp03/http/server2/connection.cpp
boost_1_69_0/libs/asio/example/cpp03/http/server2/connection.hpp
boost_1_69_0/libs/asio/example/cpp03/http/server/server.cpp
boost_1_69_0/libs/asio/example/cpp03/http/server/reply.cpp
boost_1_69_0/libs/asio/example/cpp03/http/server/server.hpp
boost_1_69_0/libs/asio/example/cpp03/http/server/reply.hpp
boost_1_69_0/libs/asio/example/cpp03/http/server/connection.cpp
boost_1_69_0/libs/asio/example/cpp03/http/server/connection.hpp
boost_1_69_0/libs/asio/example/cpp03/spawn/echo_server.cpp
boost_1_69_0/libs/asio/example/cpp03/spawn/parallel_grep.cpp
boost_1_69_0/libs/asio/example/cpp03/multicast/sender.cpp
boost_1_69_0/libs/asio/example/cpp03/multicast/receiver.cpp
boost_1_69_0/libs/asio/example/cpp03/icmp/ipv4_header.hpp
boost_1_69_0/libs/asio/example/cpp03/icmp/ping.cpp
boost_1_69_0/libs/asio/example/cpp03/services/basic_logger.hpp
boost_1_69_0/libs/asio/example/cpp03/services/daytime_client.cpp
boost_1_69_0/libs/asio/example/cpp03/services/logger_service.hpp
boost_1_69_0/libs/asio/example/cpp03/services/logger_service.cpp
boost_1_69_0/libs/asio/example/cpp03/iostreams/daytime_client.cpp
boost_1_69_0/libs/asio/example/cpp03/iostreams/daytime_server.cpp
boost_1_69_0/libs/asio/example/cpp03/iostreams/http_client.cpp
boost_1_69_0/libs/asio/example/cpp03/timers/time_t_timer.cpp
boost_1_69_0/libs/asio/example/cpp03/allocation/server.cpp
boost_1_69_0/libs/asio/example/cpp03/invocation/prioritised_handlers.cpp
boost_1_69_0/libs/asio/example/cpp03/buffers/reference_counted.cpp
boost_1_69_0/libs/asio/example/cpp03/fork/daemon.cpp
boost_1_69_0/libs/asio/example/cpp03/fork/process_per_connection.cpp
boost_1_69_0/libs/asio/example/cpp03/timeouts/server.cpp
boost_1_69_0/libs/asio/example/cpp03/timeouts/blocking_token_tcp_client.cpp
boost_1_69_0/libs/asio/example/cpp03/timeouts/blocking_udp_client.cpp
boost_1_69_0/libs/asio/example/cpp03/timeouts/async_tcp_client.cpp
boost_1_69_0/libs/asio/example/cpp03/timeouts/blocking_tcp_client.cpp
boost_1_69_0/libs/asio/example/cpp03/ssl/server.cpp
boost_1_69_0/libs/asio/example/cpp03/ssl/client.cpp
boost_1_69_0/libs/asio/example/cpp03/socks4/socks4.hpp
boost_1_69_0/libs/asio/example/cpp03/socks4/sync_client.cpp
boost_1_69_0/libs/asio/example/cpp03/porthopper/server.cpp
boost_1_69_0/libs/asio/example/cpp03/porthopper/protocol.hpp
boost_1_69_0/libs/asio/example/cpp03/porthopper/client.cpp
boost_1_69_0/libs/asio/example/cpp03/nonblocking/third_party_lib.cpp
boost_1_69_0/libs/asio/example/cpp03/tutorial/timer2/timer.cpp
boost_1_69_0/libs/asio/example/cpp03/tutorial/daytime7/server.cpp
boost_1_69_0/libs/asio/example/cpp03/tutorial/timer5/timer.cpp
boost_1_69_0/libs/asio/example/cpp03/tutorial/daytime_dox.txt
boost_1_69_0/libs/asio/example/cpp03/tutorial/daytime4/client.cpp
boost_1_69_0/libs/asio/example/cpp03/tutorial/timer4/timer.cpp
boost_1_69_0/libs/asio/example/cpp03/tutorial/daytime6
```
</details>

### 8. Скомпилирутйе boost. Можно воспользоваться инструкцией или ссылкой.
## Для выполнения, я исп. следующие команды:
```sh
1) sudo apt install g++ build-essential
2) ./bootstrap.sh --prefix=/usr/local
3) ./b2 cxxflags="-DPTHREAD_STACK_MIN=16384"
```
1) - установка компилятора
2) - настройка boost перед компиляцицей
3) - компиляция библиотек Boost

## Вывод в консоль: 
1)
```sh
eading package lists... Done
Building dependency tree... Done
Reading state information... Done
g++ is already the newest version (4:13.2.0-7ubuntu1).
The following additional packages will be installed:
  bzip2 dpkg-dev fakeroot libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libdpkg-perl libfakeroot libfile-fcntllock-perl
  lto-disabled-list make
Suggested packages:
  bzip2-doc debian-keyring git bzr make-doc
The following NEW packages will be installed:
  build-essential bzip2 dpkg-dev fakeroot libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl libfakeroot
  libfile-fcntllock-perl lto-disabled-list make
0 upgraded, 12 newly installed, 0 to remove and 34 not upgraded.
Need to get 1,769 kB of archives.
After this operation, 4,722 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://ru.archive.ubuntu.com/ubuntu noble/main amd64 make amd64 4.3-4.1build2 [180 kB]
Get:2 http://ru.archive.ubuntu.com/ubuntu noble-updates/main amd64 libdpkg-perl all 1.22.6ubuntu6.5 [269 kB]
Get:3 http://ru.archive.ubuntu.com/ubuntu noble-updates/main amd64 bzip2 amd64 1.0.8-5.1build0.1 [34.5 kB]
Get:4 http://ru.archive.ubuntu.com/ubuntu noble/main amd64 lto-disabled-list all 47 [12.4 kB]
Get:5 http://ru.archive.ubuntu.com/ubuntu noble-updates/main amd64 dpkg-dev all 1.22.6ubuntu6.5 [1,074 kB]
Get:6 http://ru.archive.ubuntu.com/ubuntu noble/main amd64 build-essential amd64 12.10ubuntu1 [4,928 B]
Get:7 http://ru.archive.ubuntu.com/ubuntu noble/main amd64 libfakeroot amd64 1.33-1 [32.4 kB]
Get:8 http://ru.archive.ubuntu.com/ubuntu noble/main amd64 fakeroot amd64 1.33-1 [67.2 kB]
Get:9 http://ru.archive.ubuntu.com/ubuntu noble/main amd64 libalgorithm-diff-perl all 1.201-1 [41.8 kB]
Get:10 http://ru.archive.ubuntu.com/ubuntu noble/main amd64 libalgorithm-diff-xs-perl amd64 0.04-8build3 [11.2 kB]
Get:11 http://ru.archive.ubuntu.com/ubuntu noble/main amd64 libalgorithm-merge-perl all 0.08-5 [11.4 kB]
Get:12 http://ru.archive.ubuntu.com/ubuntu noble/main amd64 libfile-fcntllock-perl amd64 0.22-4ubuntu5 [30.7 kB]
Fetched 1,769 kB in 0s (4,928 kB/s)           
Selecting previously unselected package make.
(Reading database ... 152962 files and directories currently installed.)
Preparing to unpack .../00-make_4.3-4.1build2_amd64.deb ...
Unpacking make (4.3-4.1build2) ...
Selecting previously unselected package libdpkg-perl.
Preparing to unpack .../01-libdpkg-perl_1.22.6ubuntu6.5_all.deb ...
Unpacking libdpkg-perl (1.22.6ubuntu6.5) ...
Selecting previously unselected package bzip2.
Preparing to unpack .../02-bzip2_1.0.8-5.1build0.1_amd64.deb ...
Unpacking bzip2 (1.0.8-5.1build0.1) ...
Selecting previously unselected package lto-disabled-list.
Preparing to unpack .../03-lto-disabled-list_47_all.deb ...
Unpacking lto-disabled-list (47) ...
Selecting previously unselected package dpkg-dev.
Preparing to unpack .../04-dpkg-dev_1.22.6ubuntu6.5_all.deb ...
Unpacking dpkg-dev (1.22.6ubuntu6.5) ...
Selecting previously unselected package build-essential.
Preparing to unpack .../05-build-essential_12.10ubuntu1_amd64.deb ...
Unpacking build-essential (12.10ubuntu1) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../06-libfakeroot_1.33-1_amd64.deb ...
Unpacking libfakeroot:amd64 (1.33-1) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../07-fakeroot_1.33-1_amd64.deb ...
Unpacking fakeroot (1.33-1) ...
Selecting previously unselected package libalgorithm-diff-perl.
Preparing to unpack .../08-libalgorithm-diff-perl_1.201-1_all.deb ...
Unpacking libalgorithm-diff-perl (1.201-1) ...
Selecting previously unselected package libalgorithm-diff-xs-perl:amd64.
Preparing to unpack .../09-libalgorithm-diff-xs-perl_0.04-8build3_amd64.deb ...
Unpacking libalgorithm-diff-xs-perl:amd64 (0.04-8build3) ...
Selecting previously unselected package libalgorithm-merge-perl.
Preparing to unpack .../10-libalgorithm-merge-perl_0.08-5_all.deb ...
Unpacking libalgorithm-merge-perl (0.08-5) ...
Selecting previously unselected package libfile-fcntllock-perl.
Preparing to unpack .../11-libfile-fcntllock-perl_0.22-4ubuntu5_amd64.deb ...
Unpacking libfile-fcntllock-perl (0.22-4ubuntu5) ...
Setting up lto-disabled-list (47) ...
Setting up libfile-fcntllock-perl (0.22-4ubuntu5) ...
Setting up libalgorithm-diff-perl (1.201-1) ...
Setting up bzip2 (1.0.8-5.1build0.1) ...
Setting up libfakeroot:amd64 (1.33-1) ...
Setting up fakeroot (1.33-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (
fakeroot) in auto mode
Setting up make (4.3-4.1build2) ...
Setting up libdpkg-perl (1.22.6ubuntu6.5) ...
Setting up libalgorithm-diff-xs-perl:amd64 (0.04-8build3) ...
Setting up libalgorithm-merge-perl (0.08-5) ...
Setting up dpkg-dev (1.22.6ubuntu6.5) ...
Setting up build-essential (12.10ubuntu1) ...
Processing triggers for man-db (2.12.0-4build2) ...
Processing triggers for libc-bin (2.39-0ubuntu8.7) ...
```
2)
```sh
Building Boost.Build engine with toolset gcc... tools/build/src/engine/bin.linuxx86_64/b2
Unicode/ICU support for Boost.Regex?... /usr
Generating Boost.Build configuration in project-config.jam...

Bootstrapping is done. To build, run:

    ./b2
    
To adjust configuration, edit 'project-config.jam'.
Further information:

   - Command line help:
     ./b2 --help
     
   - Getting started guide: 
     http://www.boost.org/more/getting_started/unix-variants.html
     
   - Boost.Build documentation:
     http://www.boost.org/build/doc/html/index.html
```
3)
```sh
Performing configuration checks

    - default address-model    : 64-bit (cached)
    - default architecture     : x86 (cached)

Building the Boost C++ Libraries.


    - C++11 mutex              : yes (cached)
    - lockfree boost::atomic_flag : yes (cached)
    - Boost.Config Feature Check: cxx11_auto_declarations : yes (cached)
    - Boost.Config Feature Check: cxx11_constexpr : yes (cached)
    - Boost.Config Feature Check: cxx11_defaulted_functions : yes (cached)
    - Boost.Config Feature Check: cxx11_final : yes (cached)
    - Boost.Config Feature Check: cxx11_hdr_mutex : yes (cached)
    - Boost.Config Feature Check: cxx11_hdr_tuple : yes (cached)
    - Boost.Config Feature Check: cxx11_lambdas : yes (cached)
    - Boost.Config Feature Check: cxx11_noexcept : yes (cached)
    - Boost.Config Feature Check: cxx11_nullptr : yes (cached)
    - Boost.Config Feature Check: cxx11_rvalue_references : yes (cached)
    - Boost.Config Feature Check: cxx11_template_aliases : yes (cached)
    - Boost.Config Feature Check: cxx11_thread_local : yes (cached)
    - Boost.Config Feature Check: cxx11_variadic_templates : yes (cached)
    - has_icu builds           : yes (cached)
warning: Graph library does not contain MPI-based parallel components.
note: to enable them, add "using mpi ;" to your user-config.jam
    - zlib                     : no  (cached)
    - bzip2                    : no  (cached)
    - lzma                     : no  (cached)
    - zstd                     : no  (cached)
    - iconv (libc)             : yes (cached)
    - icu                      : yes (cached)
warning: non-free usage requirements <runtime-link>shared ignored
warning: in main-target build_options at libs/locale/build/Jamfile.v2:414
warning: non-free usage requirements <runtime-link>shared ignored
warning: in main-target build_flags at libs/locale/build/Jamfile.v2:415
    - native-atomic-int32-supported : yes (cached)
    - native-syslog-supported  : yes (cached)
    - pthread-supports-robust-mutexes : yes (cached)
    - compiler-supports-ssse3  : yes (cached)
    - compiler-supports-avx2   : yes (cached)
    - gcc visibility           : yes (cached)
    - long double support      : yes (cached)
warning: skipping optional Message Passing Interface (MPI) library.
note: to enable MPI support, add "using mpi ;" to user-config.jam.
note: to suppress this message, pass "--without-mpi" to bjam.
note: otherwise, you can safely ignore this message.
warning: No python installation configured and autoconfiguration
note: failed.  See http://www.boost.org/libs/python/doc/building.html
note: for configuration instructions or pass --without-python to
note: suppress this message and silently skip all Boost.Python targets
    - libbacktrace builds      : yes (cached)
    - addr2line builds         : yes (cached)
    - WinDbg builds            : no  (cached)
    - WinDbgCached builds      : no  (cached)
    - BOOST_COMP_GNUC >= 4.3.0 : yes (cached)
    - zlib                     : no  (cached)
    - bzip2                    : no  (cached)
    - lzma                     : no  (cached)
    - zstd                     : no  (cached)

Component configuration:

    - atomic                   : building
    - chrono                   : building
    - container                : building
    - context                  : building
    - contract                 : building
    - coroutine                : building
    - date_time                : building
    - exception                : building
    - fiber                    : building
    - filesystem               : building
    - graph                    : building
    - graph_parallel           : building
    - iostreams                : building
    - locale                   : building
    - log                      : building
    - math                     : building
    - mpi                      : building
    - program_options          : building
    - python                   : building
    - random                   : building
    - regex                    : building
    - serialization            : building
    - stacktrace               : building
    - system                   : building
    - test                     : building
    - thread                   : building
    - timer                    : building
    - type_erasure             : building
    - wave                     : building

...patience...
...patience...
...patience...
...patience...
...patience...
...patience...
...found 13367 targets...
...updating 59 targets...
gcc.compile.c++ bin.v2/libs/thread/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/pthread/thread.o
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from libs/thread/src/pthread/thread.cpp:11:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/string:49,
                 from ./boost/thread/exceptions.hpp:20,
                 from ./boost/thread/pthread/thread_data.hpp:10,
                 from ./boost/thread/thread_only.hpp:17:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
In file included from ./boost/concept/assert.hpp:35,
                 from ./boost/concept_check.hpp:20,
                 from ./boost/range/concepts.hpp:19,
                 from ./boost/range/size_type.hpp:20,
                 from ./boost/range/size.hpp:21,
                 from ./boost/range/functions.hpp:20,
                 from ./boost/range/iterator_range_core.hpp:38,
                 from ./boost/algorithm/string/iter_find.hpp:19,
                 from ./boost/algorithm/string/split.hpp:16,
                 from libs/thread/src/pthread/thread.cpp:34:
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::constraint<Model>::failed() [with Model = boost::algorithm::FinderConcept<boost::algorithm::detail::token_finderF<boost::algorithm::detail::is_any_ofF<char> >, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/algorithm/string/iter_find.hpp:77:13:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:47:52: warning: ‘this’ pointer is null [-Wnonnull]
   47 |     static void failed() { ((Model*)0)->constraints(); }
      |                            ~~~~~~~~~~~~~~~~~~~~~~~~^~
In file included from ./boost/algorithm/string/iter_find.hpp:26:
./boost/algorithm/string/concept.hpp:40:18: note: in a call to non-static member function ‘void boost::algorithm::FinderConcept<FinderT, IteratorT>::constraints() [with FinderT = boost::algorithm::detail::token_finderF<boost::algorithm::detail::is_any_ofF<char> >; IteratorT = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   40 |             void constraints()
      |                  ^~~~~~~~~~~
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::CopyConstructible<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’:
./boost/concept_check.hpp:167:5:   required from ‘struct boost::CopyConstructible<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:125:16:   required from ‘struct boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   [ skipping 14 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
In file included from ./boost/concept_check.hpp:31:
./boost/concept/usage.hpp:16:5: note: in a call to non-static member function ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::CopyConstructible<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |     ^
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag> >]’:
./boost/concept_check.hpp:208:5:   required from ‘struct boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag> >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag> >’
./boost/concept/detail/general.hpp:51:8:   required from ‘struct boost::concepts::requirement_<void (*)(boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>)>’
./boost/iterator/iterator_concepts.hpp:114:7:   [ skipping 18 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:16:5: note: in a call to non-static member function ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>]’
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |     ^
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>]’:
./boost/iterator/iterator_concepts.hpp:114:7:   required from ‘struct boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/general.hpp:51:8:   [ skipping 13 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::Convertible<X, Y>::~Convertible() [with X = boost::iterators::random_access_traversal_tag; Y = boost::iterators::incrementable_traversal_tag]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:208:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  208 |     BOOST_CONCEPT_USAGE(Convertible) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’:
./boost/range/concepts.hpp:136:13:   required from ‘struct boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/general.hpp:51:8:   [ skipping 13 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:16:5: note: in a call to non-static member function ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |     ^
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::EqualityComparable<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’:
./boost/concept_check.hpp:233:5:   required from ‘struct boost::EqualityComparable<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/general.hpp:51:8:   [ skipping 13 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:16:5: note: in a call to non-static member function ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::EqualityComparable<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |     ^
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag> >]’:
./boost/concept_check.hpp:208:5:   required from ‘struct boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag> >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag> >’
./boost/concept/detail/general.hpp:51:8:   required from ‘struct boost::concepts::requirement_<void (*)(boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>)>’
./boost/range/concepts.hpp:152:13:   [ skipping 17 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:16:5: note: in a call to non-static member function ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>]’
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |     ^
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>]’:
./boost/range/concepts.hpp:152:13:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/general.hpp:51:8:   required from ‘struct boost::concepts::requirement_<void (*)(boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >)>’
./boost/range/concepts.hpp:278:9:   [ skipping 12 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::Convertible<X, Y>::~Convertible() [with X = boost::iterators::random_access_traversal_tag; Y = boost::iterators::single_pass_traversal_tag]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:208:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  208 |     BOOST_CONCEPT_USAGE(Convertible) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’:
./boost/range/concepts.hpp:158:13:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/general.hpp:51:8:   required from ‘struct boost::concepts::requirement_<void (*)(boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >)>’
./boost/range/concepts.hpp:278:9:   [ skipping 12 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:16:5: note: in a call to non-static member function ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |     ^
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/range/concepts.hpp:278:9:   required from ‘struct boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >’
./boost/concept/detail/general.hpp:51:8:   required from ‘struct boost::concepts::requirement_<void (*)(boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >)>’
./boost/range/algorithm/equal.hpp:174:13:   [ skipping 7 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::range_detail::SinglePassIteratorConcept<Iterator>::~SinglePassIteratorConcept() [with Iterator = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   30 |       ~model()
      |       ^
./boost/range/concepts.hpp:158:13: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  158 |             BOOST_CONCEPT_USAGE(SinglePassIteratorConcept)
      |             ^~~~~~~~~~~~~~~~~~~
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >]’:
./boost/range/concepts.hpp:284:9:   required from ‘struct boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >’
./boost/concept/detail/general.hpp:51:8:   required from ‘struct boost::concepts::requirement_<void (*)(boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >)>’
./boost/range/algorithm/equal.hpp:174:13:   [ skipping 7 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:16:5: note: in a call to non-static member function ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |     ^
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’:
./boost/range/algorithm/equal.hpp:174:13:   required from ‘bool boost::range::equal(const SinglePassRange1&, const SinglePassRange2&) [with SinglePassRange1 = boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >; SinglePassRange2 = boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/range/iterator_range_core.hpp:646:32:   required from ‘bool boost::operator==(const iterator_range<IteratorT>&, const iterator_range<Iterator2T>&) [with Iterator1T = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >; Iterator2T = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/find_iterator.hpp:333:32:   required from ‘bool boost::algorithm::split_iterator<IteratorT>::equal(const boost::algorithm::split_iterator<IteratorT>&) const [with IteratorT = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
./boost/iterator/iterator_facade.hpp:568:26:   required from ‘static bool boost::iterators::iterator_core_access::equal(const Facade1&, const Facade2&, mpl_::true_) [with Facade1 = boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >; Facade2 = boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >; mpl_::true_ = mpl_::bool_<true>]’
./boost/iterator/iterator_facade.hpp:900:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator==(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >; V1 = const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >; TC1 = forward_traversal_tag; Reference1 = const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >&; Difference1 = long int; Derived2 = boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >; V2 = const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >; TC2 = forward_traversal_tag; Reference2 = const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >&; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
./boost/iterator/iterator_adaptor.hpp:305:29:   [ skipping 2 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::SinglePassRangeConcept<T>::~SinglePassRangeConcept() [with T = const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   30 |       ~model()
      |       ^
./boost/range/concepts.hpp:284:9: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  284 |         BOOST_CONCEPT_USAGE(SinglePassRangeConcept)
      |         ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::CopyConstructible<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::CopyConstructible<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
./boost/concept_check.hpp:167:5:   required from ‘struct boost::CopyConstructible<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:125:16:   required from ‘struct boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   [ skipping 15 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::CopyConstructible<TT>::~CopyConstructible() [with TT = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:167:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  167 |     BOOST_CONCEPT_USAGE(CopyConstructible) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag> >]’
./boost/concept_check.hpp:208:5:   required from ‘struct boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag> >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag> >’
./boost/concept/detail/general.hpp:51:8:   [ skipping 19 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::Convertible<X, Y>::~Convertible() [with X = boost::iterators::random_access_traversal_tag; Y = boost::iterators::incrementable_traversal_tag]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:208:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  208 |     BOOST_CONCEPT_USAGE(Convertible) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
./boost/range/concepts.hpp:136:13:   required from ‘struct boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   [ skipping 14 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::range_detail::IncrementableIteratorConcept<Iterator>::~IncrementableIteratorConcept() [with Iterator = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   30 |       ~model()
      |       ^
./boost/range/concepts.hpp:136:13: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  136 |             BOOST_CONCEPT_USAGE(IncrementableIteratorConcept)
      |             ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::EqualityComparable<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::EqualityComparable<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
./boost/concept_check.hpp:233:5:   required from ‘struct boost::EqualityComparable<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   [ skipping 14 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::EqualityComparable<TT>::~EqualityComparable() [with TT = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:233:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  233 |     BOOST_CONCEPT_USAGE(EqualityComparable) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag> >]’
./boost/concept_check.hpp:208:5:   required from ‘struct boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag> >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag> >’
./boost/concept/detail/general.hpp:51:8:   [ skipping 18 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::Convertible<X, Y>::~Convertible() [with X = boost::iterators::random_access_traversal_tag; Y = boost::iterators::single_pass_traversal_tag]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:208:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  208 |     BOOST_CONCEPT_USAGE(Convertible) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
./boost/range/concepts.hpp:158:13:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/general.hpp:51:8:   [ skipping 13 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::range_detail::SinglePassIteratorConcept<Iterator>::~SinglePassIteratorConcept() [with Iterator = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   30 |       ~model()
      |       ^
./boost/range/concepts.hpp:158:13: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  158 |             BOOST_CONCEPT_USAGE(SinglePassIteratorConcept)
      |             ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >]’
./boost/range/concepts.hpp:284:9:   required from ‘struct boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >’
./boost/concept/detail/general.hpp:51:8:   [ skipping 8 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::SinglePassRangeConcept<T>::~SinglePassRangeConcept() [with T = const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   30 |       ~model()
      |       ^
./boost/range/concepts.hpp:284:9: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  284 |         BOOST_CONCEPT_USAGE(SinglePassRangeConcept)
      |         ^~~~~~~~~~~~~~~~~~~
gcc.link.dll bin.v2/libs/thread/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/libboost_thread.so.1.69.0
common.copy stage/lib/libboost_thread.so.1.69.0
ln-UNIX stage/lib/libboost_thread.so
gcc.compile.c++ bin.v2/libs/coroutine/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/posix/stack_traits.o
In file included from ./boost/coroutine/stack_traits.hpp:14,
                 from libs/coroutine/src/posix/stack_traits.cpp:7:
./boost/coroutine/detail/config.hpp:17:4: warning: #warning "Boost.Coroutine is now deprecated. Please switch to Boost.Coroutine2. To disable this warning message, define BOOST_COROUTINES_NO_DEPRECATION_WARNING." [-Wcpp]
   17 | #  warning                  "Boost.Coroutine is now deprecated. Please switch to Boost.Coroutine2. To disable this warning message, define BOOST_COROUTINES_NO_DEPRECATION_WARNING."
      |    ^~~~~~~
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/thread.hpp:13,
                 from libs/coroutine/src/posix/stack_traits.cpp:22:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/string:49,
                 from ./boost/thread/exceptions.hpp:20,
                 from ./boost/thread/pthread/thread_data.hpp:10,
                 from ./boost/thread/thread_only.hpp:17:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
gcc.link.dll bin.v2/libs/coroutine/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/libboost_coroutine.so.1.69.0
common.copy stage/lib/libboost_coroutine.so.1.69.0
ln-UNIX stage/lib/libboost_coroutine.so
gcc.compile.c++ bin.v2/libs/locale/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/icu/collator.o
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/thread.hpp:13,
                 from libs/locale/src/icu/collator.cpp:11:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/string:49,
                 from /usr/include/c++/13/bits/locale_classes.h:40,
                 from /usr/include/c++/13/locale:41,
                 from ./boost/locale/collator.hpp:16,
                 from libs/locale/src/icu/collator.cpp:9:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
gcc.compile.c++ bin.v2/libs/locale/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/icu/date_time.o
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/thread.hpp:13,
                 from libs/locale/src/icu/date_time.cpp:15:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/string:49,
                 from /usr/include/c++/13/bits/locale_classes.h:40,
                 from /usr/include/c++/13/locale:41,
                 from ./boost/locale/date_time_facet.hpp:18,
                 from libs/locale/src/icu/date_time.cpp:9:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
gcc.compile.c++ bin.v2/libs/locale/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/icu/formatter.o
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/thread.hpp:13,
                 from libs/locale/src/icu/predefined_formatters.hpp:14,
                 from libs/locale/src/icu/formatter.cpp:25:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/string:49,
                 from ./boost/locale/time_zone.hpp:17,
                 from ./boost/locale/formatting.hpp:17,
                 from libs/locale/src/icu/formatter.cpp:9:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
gcc.compile.c++ bin.v2/libs/locale/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/icu/numeric.o
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/thread.hpp:13,
                 from libs/locale/src/icu/predefined_formatters.hpp:14,
                 from libs/locale/src/icu/numeric.cpp:19:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/string:49,
                 from /usr/include/c++/13/bits/locale_classes.h:40,
                 from /usr/include/c++/13/locale:41,
                 from libs/locale/src/icu/numeric.cpp:9:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
gcc.link.dll bin.v2/libs/locale/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/libboost_locale.so.1.69.0
common.copy stage/lib/libboost_locale.so.1.69.0
ln-UNIX stage/lib/libboost_locale.so
gcc.compile.c++ bin.v2/libs/log/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/severity_level.o
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from libs/log/src/severity_level.cpp:23:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/functional:49,
                 from ./boost/config/no_tr1/functional.hpp:21,
                 from ./boost/smart_ptr/intrusive_ptr.hpp:24,
                 from ./boost/log/sources/severity_feature.hpp:20,
                 from libs/log/src/severity_level.cpp:18:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
gcc.compile.c++ bin.v2/libs/log/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/event.o
gcc.link.dll bin.v2/libs/log/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/libboost_log.so.1.69.0
common.copy stage/lib/libboost_log.so.1.69.0
ln-UNIX stage/lib/libboost_log.so
gcc.compile.c++ bin.v2/libs/log/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/setup/init_from_settings.o
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/log/sinks/async_frontend.hpp:39,
                 from ./boost/log/sinks.hpp:25,
                 from libs/log/src/setup/init_from_settings.cpp:54:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/string:49,
                 from /usr/include/c++/13/bits/locale_classes.h:40,
                 from /usr/include/c++/13/bits/ios_base.h:41,
                 from /usr/include/c++/13/ios:44,
                 from libs/log/src/setup/init_from_settings.cpp:28:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
gcc.link.dll bin.v2/libs/log/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/libboost_log_setup.so.1.69.0
common.copy stage/lib/libboost_log_setup.so.1.69.0
ln-UNIX stage/lib/libboost_log_setup.so
gcc.compile.c++ bin.v2/libs/type_erasure/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/dynamic_binding.o
gcc.link.dll bin.v2/libs/type_erasure/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/libboost_type_erasure.so.1.69.0
common.copy stage/lib/libboost_type_erasure.so.1.69.0
ln-UNIX stage/lib/libboost_type_erasure.so
gcc.link.dll bin.v2/libs/wave/build/gcc-13.3.0/release/threadapi-pthread/threading-multi/visibility-hidden/libboost_wave.so.1.69.0
common.copy stage/lib/libboost_wave.so.1.69.0
ln-UNIX stage/lib/libboost_wave.so
gcc.compile.c++ bin.v2/libs/thread/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/pthread/thread.o
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from libs/thread/src/pthread/thread.cpp:11:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/string:49,
                 from ./boost/thread/exceptions.hpp:20,
                 from ./boost/thread/pthread/thread_data.hpp:10,
                 from ./boost/thread/thread_only.hpp:17:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
In file included from ./boost/concept/assert.hpp:35,
                 from ./boost/concept_check.hpp:20,
                 from ./boost/range/concepts.hpp:19,
                 from ./boost/range/size_type.hpp:20,
                 from ./boost/range/size.hpp:21,
                 from ./boost/range/functions.hpp:20,
                 from ./boost/range/iterator_range_core.hpp:38,
                 from ./boost/algorithm/string/iter_find.hpp:19,
                 from ./boost/algorithm/string/split.hpp:16,
                 from libs/thread/src/pthread/thread.cpp:34:
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::constraint<Model>::failed() [with Model = boost::algorithm::FinderConcept<boost::algorithm::detail::token_finderF<boost::algorithm::detail::is_any_ofF<char> >, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/algorithm/string/iter_find.hpp:77:13:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:47:52: warning: ‘this’ pointer is null [-Wnonnull]
   47 |     static void failed() { ((Model*)0)->constraints(); }
      |                            ~~~~~~~~~~~~~~~~~~~~~~~~^~
In file included from ./boost/algorithm/string/iter_find.hpp:26:
./boost/algorithm/string/concept.hpp:40:18: note: in a call to non-static member function ‘void boost::algorithm::FinderConcept<FinderT, IteratorT>::constraints() [with FinderT = boost::algorithm::detail::token_finderF<boost::algorithm::detail::is_any_ofF<char> >; IteratorT = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   40 |             void constraints()
      |                  ^~~~~~~~~~~
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::CopyConstructible<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’:
./boost/concept_check.hpp:167:5:   required from ‘struct boost::CopyConstructible<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:125:16:   required from ‘struct boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   [ skipping 14 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
In file included from ./boost/concept_check.hpp:31:
./boost/concept/usage.hpp:16:5: note: in a call to non-static member function ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::CopyConstructible<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |     ^
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag> >]’:
./boost/concept_check.hpp:208:5:   required from ‘struct boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag> >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag> >’
./boost/concept/detail/general.hpp:51:8:   required from ‘struct boost::concepts::requirement_<void (*)(boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>)>’
./boost/iterator/iterator_concepts.hpp:114:7:   [ skipping 18 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:16:5: note: in a call to non-static member function ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>]’
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |     ^
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>]’:
./boost/iterator/iterator_concepts.hpp:114:7:   required from ‘struct boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/general.hpp:51:8:   [ skipping 13 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::Convertible<X, Y>::~Convertible() [with X = boost::iterators::random_access_traversal_tag; Y = boost::iterators::incrementable_traversal_tag]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:208:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  208 |     BOOST_CONCEPT_USAGE(Convertible) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’:
./boost/range/concepts.hpp:136:13:   required from ‘struct boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/general.hpp:51:8:   [ skipping 13 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:16:5: note: in a call to non-static member function ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |     ^
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::EqualityComparable<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’:
./boost/concept_check.hpp:233:5:   required from ‘struct boost::EqualityComparable<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/general.hpp:51:8:   [ skipping 13 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:16:5: note: in a call to non-static member function ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::EqualityComparable<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |     ^
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag> >]’:
./boost/concept_check.hpp:208:5:   required from ‘struct boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag> >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag> >’
./boost/concept/detail/general.hpp:51:8:   required from ‘struct boost::concepts::requirement_<void (*)(boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>)>’
./boost/range/concepts.hpp:152:13:   [ skipping 17 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:16:5: note: in a call to non-static member function ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>]’
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |     ^
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>]’:
./boost/range/concepts.hpp:152:13:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/general.hpp:51:8:   required from ‘struct boost::concepts::requirement_<void (*)(boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >)>’
./boost/range/concepts.hpp:278:9:   [ skipping 12 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::Convertible<X, Y>::~Convertible() [with X = boost::iterators::random_access_traversal_tag; Y = boost::iterators::single_pass_traversal_tag]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:208:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  208 |     BOOST_CONCEPT_USAGE(Convertible) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’:
./boost/range/concepts.hpp:158:13:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/general.hpp:51:8:   required from ‘struct boost::concepts::requirement_<void (*)(boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >)>’
./boost/range/concepts.hpp:278:9:   [ skipping 12 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:16:5: note: in a call to non-static member function ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |     ^
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/range/concepts.hpp:278:9:   required from ‘struct boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >’
./boost/concept/detail/general.hpp:51:8:   required from ‘struct boost::concepts::requirement_<void (*)(boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >)>’
./boost/range/algorithm/equal.hpp:174:13:   [ skipping 7 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::range_detail::SinglePassIteratorConcept<Iterator>::~SinglePassIteratorConcept() [with Iterator = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   30 |       ~model()
      |       ^
./boost/range/concepts.hpp:158:13: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  158 |             BOOST_CONCEPT_USAGE(SinglePassIteratorConcept)
      |             ^~~~~~~~~~~~~~~~~~~
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >]’:
./boost/range/concepts.hpp:284:9:   required from ‘struct boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >’
./boost/concept/detail/general.hpp:51:8:   required from ‘struct boost::concepts::requirement_<void (*)(boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >)>’
./boost/range/algorithm/equal.hpp:174:13:   [ skipping 7 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:16:5: note: in a call to non-static member function ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |     ^
./boost/concept/detail/general.hpp: In instantiation of ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’:
./boost/range/algorithm/equal.hpp:174:13:   required from ‘bool boost::range::equal(const SinglePassRange1&, const SinglePassRange2&) [with SinglePassRange1 = boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >; SinglePassRange2 = boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/range/iterator_range_core.hpp:646:32:   required from ‘bool boost::operator==(const iterator_range<IteratorT>&, const iterator_range<Iterator2T>&) [with Iterator1T = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >; Iterator2T = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/find_iterator.hpp:333:32:   required from ‘bool boost::algorithm::split_iterator<IteratorT>::equal(const boost::algorithm::split_iterator<IteratorT>&) const [with IteratorT = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
./boost/iterator/iterator_facade.hpp:568:26:   required from ‘static bool boost::iterators::iterator_core_access::equal(const Facade1&, const Facade2&, mpl_::true_) [with Facade1 = boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >; Facade2 = boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >; mpl_::true_ = mpl_::bool_<true>]’
./boost/iterator/iterator_facade.hpp:900:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator==(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >; V1 = const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >; TC1 = forward_traversal_tag; Reference1 = const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >&; Difference1 = long int; Derived2 = boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >; V2 = const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >; TC2 = forward_traversal_tag; Reference2 = const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >&; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
./boost/iterator/iterator_adaptor.hpp:305:29:   [ skipping 2 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/detail/general.hpp:39:47: warning: ‘this’ pointer is null [-Wnonnull]
   39 |     static void failed() { ((Model*)0)->~Model(); }
      |                            ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::SinglePassRangeConcept<T>::~SinglePassRangeConcept() [with T = const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   30 |       ~model()
      |       ^
./boost/range/concepts.hpp:284:9: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  284 |         BOOST_CONCEPT_USAGE(SinglePassRangeConcept)
      |         ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::CopyConstructible<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::CopyConstructible<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
./boost/concept_check.hpp:167:5:   required from ‘struct boost::CopyConstructible<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:125:16:   required from ‘struct boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   [ skipping 15 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::CopyConstructible<TT>::~CopyConstructible() [with TT = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:167:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  167 |     BOOST_CONCEPT_USAGE(CopyConstructible) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag> >]’
./boost/concept_check.hpp:208:5:   required from ‘struct boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag>]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag> >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::incrementable_traversal_tag> >’
./boost/concept/detail/general.hpp:51:8:   [ skipping 19 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::Convertible<X, Y>::~Convertible() [with X = boost::iterators::random_access_traversal_tag; Y = boost::iterators::incrementable_traversal_tag]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:208:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  208 |     BOOST_CONCEPT_USAGE(Convertible) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
./boost/range/concepts.hpp:136:13:   required from ‘struct boost::range_detail::IncrementableIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   [ skipping 14 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::range_detail::IncrementableIteratorConcept<Iterator>::~IncrementableIteratorConcept() [with Iterator = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   30 |       ~model()
      |       ^
./boost/range/concepts.hpp:136:13: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  136 |             BOOST_CONCEPT_USAGE(IncrementableIteratorConcept)
      |             ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::EqualityComparable<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::EqualityComparable<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
./boost/concept_check.hpp:233:5:   required from ‘struct boost::EqualityComparable<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/range/concepts.hpp:147:16:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   [ skipping 14 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::EqualityComparable<TT>::~EqualityComparable() [with TT = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:233:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  233 |     BOOST_CONCEPT_USAGE(EqualityComparable) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag> >]’
./boost/concept_check.hpp:208:5:   required from ‘struct boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag>]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag> >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::Convertible<boost::iterators::random_access_traversal_tag, boost::iterators::single_pass_traversal_tag> >’
./boost/concept/detail/general.hpp:51:8:   [ skipping 18 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::Convertible<X, Y>::~Convertible() [with X = boost::iterators::random_access_traversal_tag; Y = boost::iterators::single_pass_traversal_tag]’
   30 |       ~model()
      |       ^
./boost/concept_check.hpp:208:5: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  208 |     BOOST_CONCEPT_USAGE(Convertible) {
      |     ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
./boost/range/concepts.hpp:158:13:   required from ‘struct boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::range_detail::SinglePassIteratorConcept<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/general.hpp:51:8:   [ skipping 13 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::range_detail::SinglePassIteratorConcept<Iterator>::~SinglePassIteratorConcept() [with Iterator = __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> >]’
   30 |       ~model()
      |       ^
./boost/range/concepts.hpp:158:13: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  158 |             BOOST_CONCEPT_USAGE(SinglePassIteratorConcept)
      |             ^~~~~~~~~~~~~~~~~~~
./boost/concept/usage.hpp: In instantiation of ‘boost::concepts::usage_requirements<Model>::~usage_requirements() [with Model = boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’:
./boost/concept/detail/general.hpp:39:47:   required from ‘static void boost::concepts::requirement<boost::concepts::failed************ Model::************>::failed() [with Model = boost::concepts::usage_requirements<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >]’
./boost/range/concepts.hpp:284:9:   required from ‘struct boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >’
./boost/concept/detail/has_constraints.hpp:32:62:   required by substitution of ‘template<class Model> boost::concepts::detail::yes boost::concepts::detail::has_constraints_(Model*, wrap_constraints<Model, (& Model::constraints)>*) [with Model = boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > >]’
./boost/concept/detail/has_constraints.hpp:42:5:   required from ‘const bool boost::concepts::not_satisfied<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >::value’
./boost/concept/detail/has_constraints.hpp:45:51:   required from ‘struct boost::concepts::not_satisfied<boost::SinglePassRangeConcept<const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > > > >’
./boost/concept/detail/general.hpp:51:8:   [ skipping 8 instantiation contexts, use -ftemplate-backtrace-limit=0 to disable ]
./boost/iterator/iterator_facade.hpp:901:3:   required from ‘typename boost::iterators::detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<boost::iterators::detail::always_bool2, Derived1, Derived2>::type>::type boost::iterators::operator!=(const iterator_facade<Derived1, V1, TC1, Reference1, Difference1>&, const iterator_facade<Derived2, V2, TC2, Reference2, Difference2>&) [with Derived1 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V1 = std::__cxx11::basic_string<char>; TC1 = forward_traversal_tag; Reference1 = std::__cxx11::basic_string<char>; Difference1 = long int; Derived2 = transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, use_default, use_default>; V2 = std::__cxx11::basic_string<char>; TC2 = forward_traversal_tag; Reference2 = std::__cxx11::basic_string<char>; Difference2 = long int; typename detail::enable_if_interoperable<Derived1, Derived2, typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type>::type = bool; typename boost::mpl::apply2<detail::always_bool2, Derived1, Derived2>::type = bool]’
/usr/include/c++/13/bits/stl_vector.h:1671:21:   required from ‘void std::vector<_Tp, _Alloc>::_M_range_initialize(_InputIterator, _InputIterator, std::input_iterator_tag) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >]’
/usr/include/c++/13/bits/stl_vector.h:711:23:   required from ‘std::vector<_Tp, _Alloc>::vector(_InputIterator, _InputIterator, const allocator_type&) [with _InputIterator = boost::iterators::transform_iterator<boost::algorithm::detail::copy_iterator_rangeF<std::__cxx11::basic_string<char>, __gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::algorithm::split_iterator<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >, boost::iterators::use_default, boost::iterators::use_default>; <template-parameter-2-2> = void; _Tp = std::__cxx11::basic_string<char>; _Alloc = std::allocator<std::__cxx11::basic_string<char> >; allocator_type = std::allocator<std::__cxx11::basic_string<char> >]’
./boost/algorithm/string/iter_find.hpp:178:31:   required from ‘SequenceSequenceT& boost::algorithm::iter_split(SequenceSequenceT&, RangeT&, FinderT) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; FinderT = detail::token_finderF<detail::is_any_ofF<char> >]’
./boost/algorithm/string/split.hpp:146:50:   required from ‘SequenceSequenceT& boost::algorithm::split(SequenceSequenceT&, RangeT&, PredicateT, token_compress_mode_type) [with SequenceSequenceT = std::vector<std::__cxx11::basic_string<char> >; RangeT = std::__cxx11::basic_string<char>; PredicateT = detail::is_any_ofF<char>]’
libs/thread/src/pthread/thread.cpp:537:29:   required from here
./boost/concept/usage.hpp:16:48: warning: ‘this’ pointer is null [-Wnonnull]
   16 |     ~usage_requirements() { ((Model*)0)->~Model(); }
      |                             ~~~~~~~~~~~~~~~~~~~^~
./boost/concept/usage.hpp:30:7: note: in a call to non-static member function ‘boost::SinglePassRangeConcept<T>::~SinglePassRangeConcept() [with T = const boost::iterator_range<__gnu_cxx::__normal_iterator<char*, std::__cxx11::basic_string<char> > >]’
   30 |       ~model()
      |       ^
./boost/range/concepts.hpp:284:9: note: in expansion of macro ‘BOOST_CONCEPT_USAGE’
  284 |         BOOST_CONCEPT_USAGE(SinglePassRangeConcept)
      |         ^~~~~~~~~~~~~~~~~~~
gcc.archive bin.v2/libs/thread/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/libboost_thread.a
common.copy stage/lib/libboost_thread.a
gcc.compile.c++ bin.v2/libs/coroutine/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/posix/stack_traits.o
In file included from ./boost/coroutine/stack_traits.hpp:14,
                 from libs/coroutine/src/posix/stack_traits.cpp:7:
./boost/coroutine/detail/config.hpp:17:4: warning: #warning "Boost.Coroutine is now deprecated. Please switch to Boost.Coroutine2. To disable this warning message, define BOOST_COROUTINES_NO_DEPRECATION_WARNING." [-Wcpp]
   17 | #  warning                  "Boost.Coroutine is now deprecated. Please switch to Boost.Coroutine2. To disable this warning message, define BOOST_COROUTINES_NO_DEPRECATION_WARNING."
      |    ^~~~~~~
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/thread.hpp:13,
                 from libs/coroutine/src/posix/stack_traits.cpp:22:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/string:49,
                 from ./boost/thread/exceptions.hpp:20,
                 from ./boost/thread/pthread/thread_data.hpp:10,
                 from ./boost/thread/thread_only.hpp:17:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
gcc.archive bin.v2/libs/coroutine/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/libboost_coroutine.a
common.copy stage/lib/libboost_coroutine.a
gcc.compile.c++ bin.v2/libs/locale/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/collator.o
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/thread.hpp:13,
                 from libs/locale/src/icu/collator.cpp:11:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/string:49,
                 from /usr/include/c++/13/bits/locale_classes.h:40,
                 from /usr/include/c++/13/locale:41,
                 from ./boost/locale/collator.hpp:16,
                 from libs/locale/src/icu/collator.cpp:9:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
gcc.compile.c++ bin.v2/libs/locale/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/date_time.o
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/thread.hpp:13,
                 from libs/locale/src/icu/date_time.cpp:15:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/string:49,
                 from /usr/include/c++/13/bits/locale_classes.h:40,
                 from /usr/include/c++/13/locale:41,
                 from ./boost/locale/date_time_facet.hpp:18,
                 from libs/locale/src/icu/date_time.cpp:9:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
gcc.compile.c++ bin.v2/libs/locale/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/formatter.o
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/thread.hpp:13,
                 from libs/locale/src/icu/predefined_formatters.hpp:14,
                 from libs/locale/src/icu/formatter.cpp:25:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/string:49,
                 from ./boost/locale/time_zone.hpp:17,
                 from ./boost/locale/formatting.hpp:17,
                 from libs/locale/src/icu/formatter.cpp:9:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
gcc.compile.c++ bin.v2/libs/locale/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/icu/numeric.o
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/thread.hpp:13,
                 from libs/locale/src/icu/predefined_formatters.hpp:14,
                 from libs/locale/src/icu/numeric.cpp:19:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/string:49,
                 from /usr/include/c++/13/bits/locale_classes.h:40,
                 from /usr/include/c++/13/locale:41,
                 from libs/locale/src/icu/numeric.cpp:9:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
gcc.archive bin.v2/libs/locale/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/libboost_locale.a
common.copy stage/lib/libboost_locale.a
gcc.compile.c++ bin.v2/libs/log/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/severity_level.o
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from libs/log/src/severity_level.cpp:23:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/functional:49,
                 from ./boost/config/no_tr1/functional.hpp:21,
                 from ./boost/smart_ptr/intrusive_ptr.hpp:24,
                 from ./boost/log/sources/severity_feature.hpp:20,
                 from libs/log/src/severity_level.cpp:18:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
gcc.compile.c++ bin.v2/libs/log/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/event.o
gcc.archive bin.v2/libs/log/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/libboost_log.a
common.copy stage/lib/libboost_log.a
gcc.compile.c++ bin.v2/libs/log/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/setup/init_from_settings.o
In file included from ./boost/functional/hash.hpp:6,
                 from ./boost/thread/detail/thread.hpp:38,
                 from ./boost/thread/thread_only.hpp:22,
                 from ./boost/thread/thread.hpp:12,
                 from ./boost/log/sinks/async_frontend.hpp:39,
                 from ./boost/log/sinks.hpp:25,
                 from libs/log/src/setup/init_from_settings.cpp:54:
./boost/container_hash/hash.hpp:130:33: warning: ‘template<class _Arg, class _Result> struct std::unary_function’ is deprecated [-Wdeprecated-declarations]
  130 |         struct hash_base : std::unary_function<T, std::size_t> {};
      |                                 ^~~~~~~~~~~~~~
In file included from /usr/include/c++/13/string:49,
                 from /usr/include/c++/13/bits/locale_classes.h:40,
                 from /usr/include/c++/13/bits/ios_base.h:41,
                 from /usr/include/c++/13/ios:44,
                 from libs/log/src/setup/init_from_settings.cpp:28:
/usr/include/c++/13/bits/stl_function.h:117:12: note: declared here
  117 |     struct unary_function
      |            ^~~~~~~~~~~~~~
gcc.archive bin.v2/libs/log/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/libboost_log_setup.a
common.copy stage/lib/libboost_log_setup.a
gcc.compile.c++ bin.v2/libs/type_erasure/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/dynamic_binding.o
gcc.archive bin.v2/libs/type_erasure/build/gcc-13.3.0/release/link-static/threadapi-pthread/threading-multi/visibility-hidden/libboost_type_erasure.a
common.copy stage/lib/libboost_type_erasure.a
...updated 59 targets...


The Boost C++ Libraries were successfully built!

The following directory should be added to compiler include paths:

    /home/vboxuser/boost_1_69_0

The following directory should be added to linker library paths:

    /home/vboxuser/boost_1_69_0/stage/lib

```
### 9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.
## Для выполнения этого задания, я использовал следующие команды:
```sh
mkdir boost-libs
cp /usr/local/lib/libboost_*.a /home/vboxuser/boost-libs

libboost_*.a - поиск статических библиотек
```
### 10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
## Для выполнения этого задания, я использовал команду:
```sh
ls -lh boost-libs
```
## Вывод в консоль:
```sh
total 39M
-rw-r--r-- 1 root root 2.6K Feb 23 16:13 libboost_atomic.a
-rw-r--r-- 1 root root 235K Feb 23 16:13 libboost_chrono.a
-rw-r--r-- 1 root root 148K Feb 23 16:13 libboost_container.a
-rw-r--r-- 1 root root  21K Feb 23 16:13 libboost_context.a
-rw-r--r-- 1 root root 330K Feb 23 16:13 libboost_contract.a
-rw-r--r-- 1 root root 184K Feb 23 16:13 libboost_coroutine.a
-rw-r--r-- 1 root root 152K Feb 23 16:13 libboost_date_time.a
-rw-r--r-- 1 root root 1.7K Feb 23 16:13 libboost_exception.a
-rw-r--r-- 1 root root 231K Feb 23 16:13 libboost_fiber.a
-rw-r--r-- 1 root root 414K Feb 23 16:13 libboost_filesystem.a
-rw-r--r-- 1 root root 845K Feb 23 16:13 libboost_graph.a
-rw-r--r-- 1 root root 170K Feb 23 16:13 libboost_iostreams.a
-rw-r--r-- 1 root root 3.4M Feb 23 16:13 libboost_locale.a
-rw-r--r-- 1 root root 4.2M Feb 23 16:13 libboost_log.a
-rw-r--r-- 1 root root 2.6M Feb 23 16:13 libboost_log_setup.a
-rw-r--r-- 1 root root 541K Feb 23 16:13 libboost_math_c99.a
-rw-r--r-- 1 root root 448K Feb 23 16:13 libboost_math_c99f.a
-rw-r--r-- 1 root root 463K Feb 23 16:13 libboost_math_c99l.a
-rw-r--r-- 1 root root 2.7M Feb 23 16:13 libboost_math_tr1.a
-rw-r--r-- 1 root root 2.6M Feb 23 16:13 libboost_math_tr1f.a
-rw-r--r-- 1 root root 2.7M Feb 23 16:13 libboost_math_tr1l.a
-rw-r--r-- 1 root root 212K Feb 23 16:13 libboost_prg_exec_monitor.a
-rw-r--r-- 1 root root 1.6M Feb 23 16:13 libboost_program_options.a
-rw-r--r-- 1 root root  80K Feb 23 16:13 libboost_random.a
-rw-r--r-- 1 root root 3.2M Feb 23 16:13 libboost_regex.a
-rw-r--r-- 1 root root 1.2M Feb 23 16:13 libboost_serialization.a
-rw-r--r-- 1 root root  24K Feb 23 16:13 libboost_stacktrace_addr2line.a
-rw-r--r-- 1 root root  20K Feb 23 16:13 libboost_stacktrace_backtrace.a
-rw-r--r-- 1 root root  14K Feb 23 16:13 libboost_stacktrace_basic.a
-rw-r--r-- 1 root root 2.8K Feb 23 16:13 libboost_stacktrace_noop.a
-rw-r--r-- 1 root root 1.5K Feb 23 16:13 libboost_system.a
-rw-r--r-- 1 root root 2.3M Feb 23 16:13 libboost_test_exec_monitor.a
-rw-r--r-- 1 root root 449K Feb 23 16:13 libboost_thread.a
-rw-r--r-- 1 root root  53K Feb 23 16:13 libboost_timer.a
-rw-r--r-- 1 root root 175K Feb 23 16:13 libboost_type_erasure.a
-rw-r--r-- 1 root root 2.3M Feb 23 16:13 libboost_unit_test_framework.a
-rw-r--r-- 1 root root 4.5M Feb 23 16:13 libboost_wave.a
-rw-r--r-- 1 root root 793K Feb 23 16:13 libboost_wserialization.a

```
### 11. Найдите топ10 самых "тяжёлых".
## Для выполнения этого задания, я использовал команду:
```sh
ls -lhS boost-libs | head -11
```
head -11 - вывод первых 10 и заголовка
## Вывод в консоль:
```sh
total 39M
-rw-r--r-- 1 root root 4.5M Feb 23 16:13 libboost_wave.a
-rw-r--r-- 1 root root 4.2M Feb 23 16:13 libboost_log.a
-rw-r--r-- 1 root root 3.4M Feb 23 16:13 libboost_locale.a
-rw-r--r-- 1 root root 3.2M Feb 23 16:13 libboost_regex.a
-rw-r--r-- 1 root root 2.7M Feb 23 16:13 libboost_math_tr1.a
-rw-r--r-- 1 root root 2.7M Feb 23 16:13 libboost_math_tr1l.a
-rw-r--r-- 1 root root 2.6M Feb 23 16:13 libboost_math_tr1f.a
-rw-r--r-- 1 root root 2.6M Feb 23 16:13 libboost_log_setup.a
-rw-r--r-- 1 root root 2.3M Feb 23 16:13 libboost_test_exec_monitor.a
-rw-r--r-- 1 root root 2.3M Feb 23 16:13 libboost_unit_test_framework.a

```





