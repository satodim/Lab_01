# Lab_01
## 1. Скачайте библиотеку boost с помощью утилиты wget. Адрес для скачивания https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz.
### Для выполнения этого адания, я использовал следующую команду: 
wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
### Вывод в консоль:
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
## 2. Разархивируйте скаченный файл в директорию ~/boost_1_69_0
### Для выполнения этого задания я использовал команду:
tar -xf boost_1_69_0.tar.gz
## 3. Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.
### Для выполнения этого задания, я использовал команду:
find ~/boost_1_69_0 -maxdepth 1 -type f | wc -l
### Вывод в консоль:
12
## 4. Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.
### Для выполнения этого задания, я использовал следующую команду:
find ~/boost_1_69_0 -type f | wc -l
### Вывод в консоль:
61191
## 5. Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).
### Для выполнения этого задания, я использовал следующие команды:
1) find boost_1_69_0 -type f \( -name "*.h" -o -name "*.hpp" -o -name "*.hh" -o -name "*.hxx" \) | wc -l
2) find boost_1_69_0 -type f -name "*.cpp" | wc -l
3) find boost_1_69_0 -type f ! \( -name "*.h" -o -name "*.hpp" -o -name "*.hh" -o -name "*.hxx" -o -name "*.cpp" \) | wc -l
### Вывод в консоль:
1) 15208
2) 13774
3) 32209
## 6. Найдите полный пусть до файла any.hpp внутри библиотеки boost.
### Для выполнения этого задания, я использовал следующую команду:
find boost_1_69_0/boost -name "any.hpp" -type f
### Вывод в консоль:
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
## 7. Выведите в консоль все файлы, где упоминается последовательность boost::asio.
### Для выполнения этого задания, я использовал следующие команды:
1)cd boost_1_69_0
2)grep -r "boost::asio"
### Вывод в консоль:



