---
title: ADO.NET bağlantı dizeleri
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 078fdab257115296f9ff00330265cb14ff8674c8
ms.sourcegitcommit: 5fd80619c760fa8c25d33a6f5661247cb65da465
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50409463"
---
# <a name="connection-strings-in-adonet"></a>ADO.NET bağlantı dizeleri

Bir bağlantı dizesi, bir veri kaynağı için veri sağlayıcısı'ndan bir parametre olarak geçen başlatma bilgileri içerir. Veri sağlayıcısı değeri olarak bağlantı dizesini alan <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> özelliği. Sağlayıcı bağlantı dizesini ayrıştırmak ve sözdiziminin doğru olduğunu ve anahtar sözcükleri desteklendiğinden emin olmanızı sağlar. Ardından <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> yöntemi, veri kaynağına ayrıştırılmış bağlantı parametrelerini geçirir. Veri kaynağını daha fazla doğrulama gerçekleştirir ve bir bağlantı kurar.

## <a name="connection-string-syntax"></a>Bağlantı dizesi söz dizimi

Bir bağlantı dizesi anahtar/değer parametresi çiftleri noktalı virgülle ayrılmış bir listesi verilmiştir:
  
    keyword1=value; keyword2=value;
  
Anahtar sözcükler, büyük küçük harfe duyarlı değildir. Değerleri, ancak veri kaynağına bağlı olarak duyarlı olabilir. Hem anahtar hem de değerleri içerebilir [boşluk karakterleri](https://en.wikipedia.org/wiki/Whitespace_character#Unicode). Baştaki ve sondaki boşluk anahtar sözcükleri yok sayıldı ve tırnak işareti olmayan değerler.

Bir değer virgül içeriyorsa [Unicode denetim karakterlerini](https://en.wikipedia.org/wiki/Unicode_control_characters), veya baştaki veya sondaki boşlukları, bunu tek veya çift tırnak içine alınmalıdır. Örneğin:

    Keyword=" whitespace  ";
    Keyword='special;character';

Kapsayan karakter kendisini kapsayan değeri içinde gerçekleşmeyebilir. Bu nedenle, tek tırnak işareti içeren bir değeri yalnızca çift tırnak işareti bulunan ve tersi içine alınabilir:

    Keyword='double"quotation;mark';
    Keyword="single'quotation;mark";

Aşağıdaki bağlantı dizelerinin geçerli olduğu şekilde eşittir işareti yanı sıra, tırnak işaretleri kaçış, gerek yoktur:

    Keyword=no "escaping" 'required';
    Keyword=a=b=c

Sonraki noktalı virgül veya dizenin sonuna kadar her değer okunur olduğundan, ikinci örnek değer `a=b=c`, ve son noktalı virgül isteğe bağlıdır.

Tüm bağlantı dizeleri, yukarıda açıklanan aynı temel sözdizimi paylaşın. Tanınan bir anahtar kümesini sağlayıcısında ancak bağlıdır ve önceki API'leri yıl boyunca gelişmiştir *ODBC*. *.NET Framework* için veri sağlayıcısı *SQL Server* (`SqlClient`) daha eski API'lar, birçok sözcüklerden destekler ancak genellikle daha esnek ve eş anlamlılar pek çok ortak bağlantı dizesini kabul eder. anahtar sözcükler.

Yazım hatalarının hatalara neden olabilir. Örneğin, `Integrated Security=true` geçerlidir, ancak `IntegratedSecurity=true` bir hataya neden olur.

Bağlantı dizeleri çalışma anında doğrulanmamış kullanıcı girişini el ile oluşturulmuş dize enjeksiyon saldırılarına karşı savunmasız ve veri kaynağındaki güvenliği tehlikeye atabilir. Bu sorunları gidermeye yönelik *ADO.NET* 2.0 kullanılmaya [bağlantı dizesi oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md) her *.NET Framework* veri sağlayıcısı. Bu bağlantı dizesi oluşturucular parametreleri kesin türü belirtilmiş bir özellik olarak kullanıma sunmak ve veri kaynağına göndermeden önce bağlantı dizesini doğrulamak mümkün kılar.

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
