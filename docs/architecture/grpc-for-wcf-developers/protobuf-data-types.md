---
title: Protobuf skaler veri türleri - WCF geliştiricileri için gRPC
description: .NET Core'da Protobuf ve gRPC'nin desteklediği temel ve iyi bilinen veri türleri hakkında bilgi edinin.
ms.date: 09/09/2019
ms.openlocfilehash: ea3b53426ecf6f50f3bae22a537e227b07248508
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249441"
---
# <a name="protobuf-scalar-data-types"></a>Protobuf skaler veri türleri

Protokol Arabelleği (Protobuf) yerel skaler değer türleri bir dizi destekler. Aşağıdaki tabloda bunların hepsi eşdeğer C# türüne sahip olarak listelenebvardır:

| Protobuf tipi | C# tipi      | Notlar |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | 1     |
| `int64`       | `long`       | 1     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | 1     |
| `sint64`      | `long`       | 1     |
| `fixed32`     | `uint`       | 2     |
| `fixed64`     | `ulong`      | 2     |
| `sfixed32`    | `int`        | 2     |
| `sfixed64`    | `long`       | 2     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | 3     |
| `bytes`       | `ByteString` | 4     |

Notlar:

1. İmzalanan değerlerle `int32` `int64` çalışırken standart kodlama ve verimsizdir. Alanınız negatif sayılar içeriyorsa, `sint32` `sint64` kullanın veya bunun yerine. Bu türler sırasıyla `int` `long` C# ve türleri ile eşlenir.
2. Alanlar, `fixed` değeri ne olursa olsun her zaman aynı sayıda bayt kullanır. Bu davranış, serileştirme ve deserialization daha büyük değerler için daha hızlı yapar.
3. Protobuf dizeleri UTF-8 (veya 7-bit ASCII) kodlanır. Kodlanmış uzunluk 2<sup>32'den</sup>büyük olamaz.
4. Protobuf çalışma süresi, `ByteString` C# `byte[]` dizilerine kolayca eşlenebilen bir tür sağlar.

## <a name="other-net-primitive-types"></a>Diğer .NET ilkel türleri

### <a name="dates-and-times"></a>Tarihler ve saatler

Yerel skaler türleri, C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>ve <xref:System.TimeSpan>. Bu türleri, Google'ın "Bilinen Türleri" uzantılarından bazılarını kullanarak belirtebilirsiniz. Bu uzantılar, desteklenen platformlardaki karmaşık alan türleri için kod oluşturma ve çalışma zamanı desteği sağlar.

Aşağıdaki tablo tarih ve saat türlerini gösterir:

| C# tipi | Protobuf iyi bilinen tip |
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

C# sınıfında oluşturulan özellikler .NET tarih ve saat türleri değildir. Özellikler `Google.Protobuf.WellKnownTypes` ad `Timestamp` alanında `Duration` ve sınıfları kullanır. Bu sınıflar ve dönüştürme için `DateTimeOffset`yöntemler `DateTime`sağlar `TimeSpan`, , ve .

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
> Tür `Timestamp` UTC kez çalışır. `DateTimeOffset`değerleri her zaman sıfır bir `DateTime.Kind` ofset `DateTimeKind.Utc`var ve özelliği her zaman .

### <a name="systemguid"></a>System.Guid

Protobuf, diğer platformlarda <xref:System.Guid> olduğu gibi `UUID` bilinen türü doğrudan desteklemez. Bunun için iyi bilinen bir türü yok.

En iyi yaklaşım, `Guid` standart `string` `8-4-4-4-12` hexadecimal biçimini kullanarak (örneğin,) `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`değerleri alan olarak işlemektir. Tüm diller ve platformlar bu biçimi ayrıştırabilir.

Değerler için `Guid` alan `bytes` kullanmayın. Protobuf Java gibi diğer platformlarla etkileşimhalindeyken, *endoyanness* [(Vikipedi tanımı)](https://en.wikipedia.org/wiki/Endianness)ile ilgili sorunlar düzensiz davranışlara neden olabilir.

### <a name="nullable-types"></a>Boş değer atanabilir tipler

C# için Protobuf kod oluşturma gibi `int` yerel `int32`türleri kullanır. Yani değerler her zaman dahildir ve null olamaz.

C# kodunuzda kullanmak `int?` gibi açık null gerektiren değerler için, Protobuf'un "İyi Bilinen Türleri" geçersiz C# türlerine derlenmiş ambalajları içerir. Bunları kullanmak için `wrappers.proto` dosyanıza şu şekilde aktarın: `.proto`

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf oluşturulan ileti `T?` özelliği için `int?`basit (örneğin, ) kullanır.

Aşağıdaki tabloda, eşdeğer C# türüne sahip sarıcı türlerinin tam listesi gösterilmektedir:

| C# tipi   | İyi Bilinen Tip Sarıcı       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

İyi bilinen türleri `Timestamp` `Duration` ve sınıflar olarak .NET temsil edilir. C# 8 ve ötesinde, nullable başvuru türlerini kullanabilirsiniz. Ancak, dönüşüm yaparken bu tür özellikleri geçersiz olup olmadığını kontrol `DateTimeOffset` etmek `TimeSpan`önemlidir.

## <a name="decimals"></a>Ondalıklar

Protobuf yerel olarak .NET `decimal` türünü desteklemiyor, sadece `double` ve `float`. Protobuf projesinde, onu destekleyen diller ve çerçeveler `Decimal` için platform desteği yle, tanınmış türlere standart bir tür ekleme olasılığı hakkında devam eden bir tartışma vardır. Henüz hiçbir şey uygulanmadı.

.NET istemcileri ve sunucuları arasında `decimal` güvenli serileştirme için çalışacak türü temsil edecek bir ileti tanımı oluşturmak mümkündür. Ancak diğer platformlardaki geliştiricilerin kullanılan formatı anlamaları ve bunun için kendi kullanımlarını uygulamaları gerekir.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Protobuf için özel bir ondalık yazı oluşturma

Basit bir uygulama, bazı Google `Money` API'lerin alanı olmadan `currency` kullandığı standart dışı türe benzer olabilir.

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

Alan, `nanos` `-0.999_999_999`değerlerinden `0.999_999_999` gelen değerleri temsil eder. Örneğin, `decimal` değer `1.5m` . `{ units = 1, nanos = 500_000_000 }` Bu nedenle, `nanos` bu örnekteki `sfixed32` alan, daha büyük değerlere `int32` göre daha verimli kodlayan türü kullanır. `units` Alan negatifse, `nanos` alan da negatif olmalıdır.

> [!NOTE]
> Değerleri bayt dizeleri olarak `decimal` kodlamak için birden çok algoritma vardır, ancak bu iletiyi anlamak bunlardan daha kolaydır. Değerler farklı platformlarda ensizlikten etkilenmez.

Bu tür ve BCL `decimal` türü arasında dönüştürme C# aşağıdaki gibi uygulanabilir:

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
> Bu gibi özel ileti türlerini her kullandığınızda, `.proto`bunları 'deki açıklamalarla *belgelemeniz gerekir.* Diğer geliştiriciler daha sonra kendi dil lerinde veya çerçevelerinde eşdeğer türe dönüştürme uygulayabilir.

>[!div class="step-by-step"]
>[Önceki](protobuf-messages.md)
>[Sonraki](protobuf-nested-types.md)
