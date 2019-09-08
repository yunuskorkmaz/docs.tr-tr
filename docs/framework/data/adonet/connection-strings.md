---
title: ADO.NET içinde bağlantı dizeleri
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 8f726ca71ba955ef542d15e0e8318c2b310e607e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784907"
---
# <a name="connection-strings-in-adonet"></a>ADO.NET içinde bağlantı dizeleri

Bir bağlantı dizesi, veri sağlayıcısından bir veri kaynağına parametre olarak geçirilen başlatma bilgilerini içerir. Veri sağlayıcısı, bağlantı dizesini <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> özelliğin değeri olarak alır. Sağlayıcı bağlantı dizesini ayrıştırır ve sözdiziminin doğru olduğundan ve anahtar sözcüklerin desteklendiğinden emin olmanızı sağlar. Daha sonra <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> yöntemi, ayrıştırılmış bağlantı parametrelerini veri kaynağına geçirir. Veri kaynağı daha fazla doğrulama gerçekleştirir ve bir bağlantı oluşturur.

## <a name="connection-string-syntax"></a>Bağlantı dizesi sözdizimi

Bağlantı dizesi, anahtar/değer parametre çiftlerinin noktalı virgülle ayrılmış listesidir:

```
keyword1=value; keyword2=value;
```

Anahtar sözcükler büyük/küçük harfe duyarlı değildir. Ancak değerler, veri kaynağına bağlı olarak büyük/küçük harfe duyarlı olabilir. Anahtar sözcüklerin ve değerlerin her ikisi de [boşluk karakterleri](https://en.wikipedia.org/wiki/Whitespace_character#Unicode)içerebilir. Baştaki ve sondaki boşluk, anahtar sözcüklerde ve tırnak işaretsiz değerlerde yok sayılır.

Bir değer noktalı virgül, [Unicode denetim karakterleri](https://en.wikipedia.org/wiki/Unicode_control_characters)veya baştaki veya sondaki boşluk içeriyorsa, tek veya çift tırnak işareti içine alınmalıdır. Örneğin:

```
Keyword=" whitespace  ";
Keyword='special;character';
```

Kapsayan karakter, içerdiği değer içinde gerçekleşmeyebilir. Bu nedenle, tek tırnak işareti içeren bir değer yalnızca çift tırnak işaretleri içine alınabilir ve tam tersi de geçerlidir:

```
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

Ayrıca, kapsayan karakterden ikisini birlikte kullanarak da kaçış yapabilirsiniz:

```
Keyword="double""quotation";
Keyword='single''quotation';
```

Tırnak işareti ve eşittir işareti, kaçış gerektirmez, bu nedenle aşağıdaki bağlantı dizeleri geçerlidir:

```
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

Her değer bir sonraki noktalı virgül veya dize sonuna kadar okunduğundan, ikinci örnekteki `a=b=c`değer ve son noktalı virgül isteğe bağlıdır.

Tüm bağlantı dizeleri yukarıda açıklanan temel sözdizimini paylaşır. Tanınan anahtar sözcükler kümesi, sağlayıcıya bağlıdır ve *ODBC*gibi önceki API 'lerden yıllarca yaşmıştır. *SQL Server* (`SqlClient`) için *.NET Framework* veri sağlayıcısı, eski API 'lerden birçok anahtar sözcüğü destekler, ancak genellikle daha esnektir ve ortak bağlantı dizesi anahtar sözcüklerinin birçoğu için eş anlamlıları kabul eder.

Yazım hataları hatalara neden olabilir. Örneğin, `Integrated Security=true` geçerlidir, ancak `IntegratedSecurity=true` hataya neden olur.

Kimliği doğrulanmamış Kullanıcı girişinden, çalışma zamanında el ile oluşturulan bağlantı dizeleri, dize ekleme saldırılarına karşı savunmasız kalır ve veri kaynağındaki güvenliği tehlikeye at. Bu sorunları gidermek için, *ADO.NET* 2,0 her bir *.NET Framework* veri sağlayıcısı için [bağlantı dizesi oluşturucuları](connection-string-builders.md) sunmuştur. Bu bağlantı dizesi oluşturucuları, parametreleri kesin türü belirtilmiş özellikler olarak kullanıma sunar ve veri kaynağına gönderilmeden önce bağlantı dizesinin doğrulanmasını mümkün hale getirir.

## <a name="in-this-section"></a>Bu Bölümde

[Bağlantı dizesi oluşturucuları](connection-string-builders.md)\
Çalışma zamanında geçerli bağlantı dizeleri `ConnectionStringBuilder` oluşturmak için sınıfların nasıl kullanılacağını gösterir.

[Bağlantı dizeleri ve yapılandırma dosyaları](connection-strings-and-configuration-files.md)\
Yapılandırma dosyalarındaki bağlantı dizelerinin nasıl depolanacağını ve alınacağını gösterir.

[Bağlantı dizesi sözdizimi](connection-string-syntax.md)\
, `SqlClient`, Ve `OracleClient` `OleDb`için sağlayıcıyaözelbağlantıdizelerininnasılyapılandırılacağınıaçıklar.`Odbc`

[Bağlantı bilgilerini koruma](protecting-connection-information.md)\
Bir veri kaynağına bağlanmak için kullanılan bilgileri koruma tekniklerini gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Kaynağına Bağlanma](/cpp/data/odbc/connecting-to-a-data-source)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
