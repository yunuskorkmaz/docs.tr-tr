---
title: ADO.NET bağlantı dizeleri
ms.date: 03/30/2017
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 1e6e2b6870195c99279639e1f4576a30b7126d4d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583704"
---
# <a name="connection-strings-in-adonet"></a>ADO.NET bağlantı dizeleri
.NET Framework 2.0 sunulan geçerli bağlantı dizeleri çalışma zamanında oluşturma kolaylaştırmak bağlantı dizesi Oluşturucusu sınıfları yeni anahtar sözcüklerin Tanıtımı da dahil olmak üzere, bağlantı dizeleri ile çalışmak için yeni özellikler.  
  
Bir bağlantı dizesi, bir veri kaynağı için veri sağlayıcısı'ndan bir parametre olarak geçen başlatma bilgileri içerir. Veri sağlayıcısında söz dizimi bağlıdır ve bağlantı dizesini bağlantı denemesi sırasında ayrıştırılır. Söz dizimi hataları bir çalışma zamanı özel durumu oluşturur, ancak yalnızca veri kaynağı bağlantı bilgileri aldıktan sonra diğer hataları oluşur. Doğrulanmış sonra veri kaynağının bağlantı dizesinde belirtilen seçenekleri uygular ve bağlantı açar.
  
Bir bağlantı dizesi biçimi, anahtar/değer parametresi çiftleri noktalı virgülle ayrılmış bir listesi verilmiştir:
  
    keyword1=value; keyword2=value;
  
Anahtar sözcükler, büyük küçük harfe duyarlı değildir. Değerleri, ancak veri kaynağına bağlı olarak duyarlı olabilir. Hem anahtar hem de değerleri içerebilir [boşluk karakterleri](https://en.wikipedia.org/wiki/Whitespace_character#Unicode), baştaki ve sondaki anahtar sözcükleri yok sayıldı ve tırnak işareti olmayan olsa da değerler.

Bir değer virgül içeriyorsa [Unicode denetim karakterlerini](https://en.wikipedia.org/wiki/Unicode_control_characters), baştaki veya sondaki bu alınmalıdır tek veya çift tırnak işaretleri içine, örneğin:

    Keyword=" whitespace  ";
    Keyword='special;character';

Kapsayan karakter kendisini kapsayan değeri içinde gerçekleşmeyebilir. Bu nedenle, tek tırnak işareti içeren bir değeri yalnızca çift tırnak işareti ve bunun tersi de içine alınabilir:

    Keyword='double"quotation;mark';
    Keyword="single'quotation;mark";

Aşağıdaki bağlantı dizelerinin geçerli olduğu şekilde eşittir işareti yanı sıra, tırnak işaretleri kaçış, gerek yoktur:

    Keyword=no "escaping" 'required';
    Keyword=a=b=c

Sonraki noktalı virgül veya dizenin sonuna kadar her değer okunur olduğundan, ikinci örnek değer `a=b=c`, ve son noktalı virgül isteğe bağlıdır.

Geçerli bağlantı dizesi söz dizimi sağlayıcısına bağımlıdır ve ODBC gibi önceki API'leri yıl boyunca gelişmiştir. SQL Server (SqlClient) için .NET Framework veri sağlayıcısı birçok eski sözdizimi öğeleri birleştirir ve ortak bağlantı dizesi söz dizimi ile genellikle daha esnektir. Vardır sık eşit bağlantı dizesi söz dizimi öğeleri için geçerli eş anlamlı sözcükler, ancak bazı söz dizimi ve yazım hataları sorunlara neden olabilir. Örneğin, "`Integrated Security=true`" geçerlidir, ancak "`IntegratedSecurity=true`" bir hataya neden olur. Ayrıca, bağlantı dizeleri çalışma zamanında doğrulanmamış kullanıcı girişini öğesinden oluşturulan dize ekleme saldırılarına karşı veri kaynağında güvenliği tehlikeye yol açabilir.
  
Bu sorunları gidermeye yönelik her .NET Framework veri sağlayıcısı için yeni bir bağlantı dizesi oluşturucular ADO.NET 2.0 kullanılmaya başlandı. Anahtar sözcükler, özellikleri, veri kaynağına göndermeden önce doğrulanması bağlantı dizesi söz dizimi etkinleştirme olarak sunulur.
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bağlantı Dizesi Oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 Nasıl kullanılacağını gösteren `ConnectionStringBuilder` sınıfları geçerli bağlantı dizeleri oluşturmak için çalışma zamanında.
  
 [Bağlantı Dizeleri ve Yapılandırma Dosyaları](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 Bağlantı dizelerini yapılandırma dosyalarında depolanıp gösterilmektedir.
  
 [Bağlantı Dizesi Söz Dizimi](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 Sağlayıcıya özgü bağlantı dizeleri için yapılandırmayı açıklar `SqlClient`, `OracleClient`, `OleDb`, ve `Odbc`.
  
 [Bağlantı Bilgilerini Koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 Bir veri kaynağına bağlanmak için kullanılan bilgileri korumaya yönelik teknikleri gösterir.
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Kaynağına Bağlanma](/cpp/data/odbc/connecting-to-a-data-source)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
