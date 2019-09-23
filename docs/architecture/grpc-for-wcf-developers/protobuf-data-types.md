---
title: Prototipsiz skaler veri türleri-WCF geliştiricileri için gRPC
description: .NET Core 'da Protoarabellek ve gRPC tarafından desteklenen temel ve iyi bilinen veri türleri hakkında bilgi edinin.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 8c8db795e927a44e9f75ec828336630ec9978eb6
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184269"
---
# <a name="protobuf-scalar-data-types"></a>Prototipsiz skaler veri türleri

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Prototip, yerel skaler değer türlerini destekler. Aşağıdaki tabloda bunların hepsi eşdeğer C# tür ile listelenmektedir:

| Prototip türü | C#türüyle      | Notlar |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | 1\.     |
| `int64`       | `long`       | 1\.     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | 1\.     |
| `sint64`      | `long`       | 1\.     |
| `fixed32`     | `uint`       | 2     |
| `fixed64`     | `ulong`      | 2     |
| `sfixed32`    | `int`        | 2     |
| `sfixed64`    | `long`       | 2     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | 3     |
| `bytes`       | `ByteString` | 4     |

## <a name="notes"></a>Notlar

1. `int32` Ve`int64` için standart kodlama, imzalanmış değerlerle çalışırken verimsiz bir değer. Alanınız büyük olasılıkla negatif sayı içeriyorsa, bunun yerine veya `sint32` `sint64` kullanın. Her iki tür de sırasıyla C# `int` ve `long` türleriyle eşlenir.
2. `fixed` Alanlar, her zaman değerin ne kadar olduğunu bağımsız olarak aynı sayıda bayt kullanır. Bu davranış, daha büyük değerler için serileştirme ve seri durumdan çıkarma sağlar.
3. Prototip dizeler UTF-8 (veya 7 bit ASCII) kodlardır ve kodlanan uzunluk 2<sup>32</sup>' den büyük olamaz.
4. Prototip çalışma zamanı, dizilere ve `ByteString` dizilerden C# `byte[]` kolayca eşleyen bir tür sağlar.

## <a name="other-net-primitive-types"></a>Diğer .NET ilkel türleri

### <a name="dates-and-times"></a>Tarihler ve saatler

Yerel skaler türler tarih ve saat değerleri için, C#, ve ile <xref:System.DateTimeOffset> <xref:System.TimeSpan>eşdeğerdir <xref:System.DateTime>. Bu türler, desteklenen platformlar genelinde daha karmaşık alan türleri için kod oluşturma ve çalışma zamanı desteği sağlayan bazı Google "tanınmış türler" uzantıları kullanılarak belirtilebilir. Aşağıdaki tabloda tarih ve saat türleri gösterilmektedir:

| C#türüyle | Prototip iyi bilinen tür |
| ------- | ------------------------ |
| `DateTimeOffset` | `google.protobuf.Timestamp` |
| `DateTime` | `google.protobuf.Timestamp` |
| `TimeSpan` | `google.protobuf.Duration` |

```protobuf  
syntax = "proto3"

import "google/protobuf/duration.proto";  
import "google/protobuf/timestamp.proto";

message Meeting {

    string subject = 1;
    google.protobuf.Timestamp time = 2;
    google.protobuf.Duration duration = 3;

}  
```

C# Sınıfındaki oluşturulan Özellikler .net tarih ve saat türleri değildir. Özellikleri, ve, `Timestamp` , `Duration` ve `DateTimeOffset` `DateTime` `Google.Protobuf.WellKnownTypes` '`TimeSpan`a dönüştürmek için yöntemler sağlayan ad alanındaki ve sınıflarını kullanır.

```csharp
// Create Timestamp and Duration from .NET DateTimeOffset and TimeSpan
var meeting = new Meeting
{
    Time = Timestamp.FromDateTimeOffset(meetingTime), // also FromDateTime()
    Duration = Duration.FromTimeSpan(meetingLength)
};

// Convert Timestamp and Duration to .NET DateTimeOffset and TimeSpan
DateTimeOffset time = meeting.Time.ToDateTimeOffset();
TimeSpan? duration = meeting.Duration?.ToTimeSpan();
```

> [!NOTE]
> `Timestamp` Tür UTC zamanları ile birlikte çalışarak. değerler her zaman sıfır bir uzaklığa sahiptir `DateTime.Kind` ve özellik her zaman `DateTimeKind.Utc`olur. `DateTimeOffset`

### <a name="systemguid"></a>System. Guid

Diğer platformlarda olduğu `UUID` bilinen tür,prototiptedoğrudandesteklenmezvebununiçiniyibilinenbirtüryoktur.<xref:System.Guid> En iyi yaklaşım, değerleri, `Guid` tüm diller `string` ve platformlar tarafından ayrıştırılabilen `8-4-4-4-12` standart onaltılı biçimi (örneğin, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`) kullanarak alan olarak idare kullanmaktır. Değer için `bytes` `Guid` bir alan kullanmayın. Bu, bitime ile ilgili problemler, Java gibi diğer platformlarla etkileşerek Erratic davranışa neden olabilir.

### <a name="nullable-types"></a>Boş değer atanabilir tipler

İçin C# prototip kod oluşturma, gibi yerel türleri `int` `int32`kullanır. Bu, değerlerin her zaman dahil olduğu ve null olamayacağı anlamına gelir. Kodunuzda kullanılması `int?` gibi açık null gerektiren değerler için, prototipli "iyi bilinen türler", null yapılabilir C# türler için derlenen sarmalayıcıları içerir. C# Bunları kullanmak için, `wrappers.proto` `.proto` dosyanıza aşağıdaki gibi içeri aktarın:

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Prototip, oluşturulan ileti özelliği için `T?` basit (örneğin, `int?`) kullanır.

Aşağıdaki tabloda, sarmalama türlerinin, eşdeğer C# türlerine sahip tüm listesi gösterilmektedir:

| C#türüyle   | İyi bilinen tür sarmalayıcısı       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

İyi bilinen türler `Timestamp` ve `Duration` .NET içinde sınıflar olarak temsil edilir. bu nedenle, null yapılabilir bir sürüme gerek yoktur, ancak veya `TimeSpan`' ye `DateTimeOffset` dönüştürürken bu türlerin özelliklerinde null denetimi yapmanız önemlidir.

## <a name="decimals"></a>In

Prototip, yalnızca `decimal` `double` ve `float`.NET türünü yerel olarak desteklemez. Yaygın olarak bilinen türlere standart `Decimal` bir tür ekleme olasılığa ve bunu destekleyen diller ve çerçeveler için platform desteğiyle, ancak henüz hiçbir şey uygulanmadığı için, prototip projesinde devam eden bir tartışma vardır.

.NET istemcileri ve sunucuları arasında güvenli seri hale getirme için çalışacak `decimal` olan türü temsil etmek üzere bir ileti tanımı oluşturmak mümkündür, ancak diğer platformlardaki geliştiricilerin, kullanılan biçimi anlaması ve kendi özelliklerini uygulaması gerekir işleme.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Protoarabellek için özel bir ondalık tür oluşturma

Çok basit bir uygulama, `Money` `currency` alan olmadan bazı Google API 'leri tarafından kullanılan standart olmayan türe benzer olabilir.

```protobuf
package CustomTypes;

// Example: 12345.6789 -> { units = 12345, nanos = 678900000 }
message Decimal {

    // Whole units part of the amount
    int64 units = 1;

    // Nano units of the amount (10^-9)
    // Must be same sign as units
    sfixed32 nanos = 2;
}
```

Alan `nanos` `0.999_999_999` ,`-0.999_999_999`öğesinden değerlerini temsil eder. Örneğin `decimal` , `int32` değer `1.5m` `nanos` olarak `{ units = 1, nanos = 500_000_000 }` temsil edilir (Bu, bu örnekteki alanın, daha büyük değerler için daha verimli bir `sfixed32` şekilde kodlayan türü kullanması neden olur). `units` Alan negatifse`nanos` alanın de negatif olması gerekir.

> [!NOTE]
> Değerleri bayt dizeleri olarak kodlamak `decimal` için birden çok farklı algoritma mevcuttur, ancak bu iletinin bunlardan herhangi birinin anlaşılması çok daha kolay olur ve değerler farklı platformlarda *[bitime](https://en.wikipedia.org/wiki/Endianness)* tarafından etkilenmemiştir.

Bu tür ile BCL `decimal` türü arasındaki dönüştürme bunun C# gibi uygulanabilir.

```csharp
namespace CustomTypes
{
    public partial class GrpcDecimal
    {
        private const decimal NanoFactor = 1_000_000_000;
        public GrpcDecimal(long units, int nanos)
        {
            Units = units;
            Nanos = nanos;
        }

        public long Units { get; }
        public int Nanos { get; }

        public static implicit operator decimal(CustomTypes.Decimal grpcDecimal)
        {
            return grpcDecimal.Units + grpcDecimal.Nanos / NanoFactor;
        }

        public static implicit operator CustomTypes.Decimal(decimal value)
        {
            var units = decimal.ToInt64(value);
            var nanos = decimal.ToInt32((value - units) * NanoFactor);
            return new CustomTypes.Decimal(units, nanos);
        }
    }
}
```

> [!IMPORTANT]
> Bu gibi özel yardımcı program ileti türlerini kullandığınızda, diğer geliştiricilerin kendi dillerinde veya çerçevesindeki eşdeğer türe ve `.proto` bu türden dönüştürme uygulayabilmeleri için, bunları içindeki yorumlarla belgeetmeniz gerekir.

>[!div class="step-by-step"]
>[Önceki](protobuf-messages.md)
>[İleri](protobuf-nested-types.md)
