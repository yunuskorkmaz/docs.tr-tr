---
title: Prototipsiz skaler veri türleri-WCF geliştiricileri için gRPC
description: .NET Core 'da Protoarabellek ve gRPC tarafından desteklenen temel ve iyi bilinen veri türleri hakkında bilgi edinin.
ms.date: 09/09/2019
ms.openlocfilehash: ae7f5f48099000dff0eefb36e23cb9b9f2ac517c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971549"
---
# <a name="protobuf-scalar-data-types"></a>Protobuf skaler veri türleri

Prototip, yerel skaler değer türlerini destekler. Aşağıdaki tabloda bunların hepsi eşdeğer C# tür ile listelenmektedir:

| Prototip türü | C#türüyle      | Notlar |
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

## <a name="notes"></a>Notlar

1. `int32` ve `int64` için standart kodlama, imzalanmış değerlerle çalışırken verimsiz bir değer. Alanınız büyük olasılıkla negatif sayı içeriyorsa, bunun yerine `sint32` veya `sint64` kullanın. Her iki tür de sırasıyla C# `int` ve `long` türleriyle eşlenir.
2. `fixed` alanlar, her zaman değerin ne kadar olduğunu bağımsız olarak aynı sayıda bayt kullanır. Bu davranış, daha büyük değerler için serileştirme ve seri durumdan çıkarma sağlar.
3. Prototip dizeler UTF-8 (veya 7 bit ASCII) kodlardır ve kodlanan uzunluk 2<sup>32</sup>' den büyük olamaz.
4. Prototip çalışma zamanı, `byte[]` dizilerden ve bu kaynaklardan C# kolayca eşleyen bir `ByteString` türü sağlar.

## <a name="other-net-primitive-types"></a>Diğer .NET ilkel türleri

### <a name="dates-and-times"></a>Tarihler ve saatler

Yerel skaler türler, <xref:System.DateTimeOffset>, <xref:System.DateTime>ve <xref:System.TimeSpan>eşdeğer C#tarih ve saat değerleri için sağlamaz. Bu türler, desteklenen platformlar genelinde daha karmaşık alan türleri için kod oluşturma ve çalışma zamanı desteği sağlayan bazı Google "tanınmış türler" uzantıları kullanılarak belirtilebilir. Aşağıdaki tabloda tarih ve saat türleri gösterilmektedir:

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

C# Sınıfındaki oluşturulan Özellikler .net tarih ve saat türleri değildir. Özellikler, `DateTimeOffset`, `DateTime`ve `TimeSpan`dönüştürmek için yöntemler sağlayan `Google.Protobuf.WellKnownTypes` ad alanındaki `Timestamp` ve `Duration` sınıflarını kullanır.

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
> `Timestamp` türü UTC zamanları ile birlikte çalışarak `DateTimeOffset` değerler her zaman sıfır bir uzaklığa sahiptir ve `DateTime.Kind` özelliği her zaman `DateTimeKind.Utc`olur.

### <a name="systemguid"></a>System. Guid

Diğer platformlarda `UUID` olarak bilinen <xref:System.Guid> türü, prototipte doğrudan desteklenmez ve bunun için iyi bilinen bir tür yoktur. En iyi yaklaşım, tüm diller ve platformlar tarafından ayrıştırılabilen standart `8-4-4-4-12` onaltılık biçimi (örneğin, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`) kullanılarak `string` alanı olarak `Guid` değerlerini idare kullanmaktır. `Guid` değerleri için `bytes` alanı kullanmayın, çünkü bitime ile ilgili sorunlar, Java gibi diğer platformlarla etkileşerek Erratic davranışa neden olabilir.

### <a name="nullable-types"></a>Boş değer atanabilir tipler

İçin C# prototip kod oluşturma, `int32`için `int` gibi yerel türleri kullanır. Bu, değerlerin her zaman dahil olduğu ve null olamayacağı anlamına gelir. C# Kodunuzda `int?` kullanma gibi açık null gerektiren değerler Için, prototipli "Iyi bilinen türler", null yapılabilir C# türlere derlenen sarmalayıcıları içerir. Bunları kullanmak için, `wrappers.proto` `.proto` dosyanıza aşağıdaki gibi içeri aktarın:

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Prototip, oluşturulan ileti özelliği için basit `T?` (örneğin, `int?`) kullanır.

Aşağıdaki tabloda, sarmalama türlerinin, eşdeğer C# türlerine sahip tüm listesi gösterilmektedir:

| C#türüyle   | İyi bilinen tür sarmalayıcısı       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

`Timestamp` ve `Duration` bilinen türler, .NET içinde sınıflar olarak temsil edilir. bu nedenle, null yapılabilir bir sürüme gerek yoktur, ancak `DateTimeOffset` veya `TimeSpan`dönüştürülürken bu türlerin özelliklerinde null denetimi yapmanız önemlidir.

## <a name="decimals"></a>In

Prototip, yalnızca `double` ve `float`.NET `decimal` türünü yerel olarak desteklemez. Prototip projesinde, iyi bilinen türlere standart bir `Decimal` türü ekleme olasılığa, bunu destekleyen diller ve çerçeveler için platform desteğiyle, ancak henüz hiçbir şey uygulanmadığı için, prototipli projede devam eden bir tartışma vardır.

.NET istemcileri ve sunucuları arasında güvenli seri hale getirme için çalışacak `decimal` türünü temsil eden bir ileti tanımı oluşturmak mümkündür, ancak diğer platformlardaki geliştiricilerin kullanılmakta olan biçimi anlaması ve onun için kendi işlemesini uygulaması gerekir.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Protoarabellek için özel bir ondalık tür oluşturma

Çok basit bir uygulama, `currency` alanı olmadan bazı Google API 'Leri tarafından kullanılan standart olmayan `Money` türüne benzer.

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

`nanos` alanı `-0.999_999_999``0.999_999_999` değerleri temsil eder. Örneğin, `1.5m` `decimal` değer `{ units = 1, nanos = 500_000_000 }` olarak temsil edilir (Bu nedenle bu örnekteki `nanos` alanı, daha büyük değerler için `sfixed32` daha verimli bir şekilde kodlayan `int32` türünü kullanır). `units` alanı negatifse, `nanos` alanı da negatif olmalıdır.

> [!NOTE]
> `decimal` değerlerini bayt dizeleri olarak kodlamak için birden çok başka algoritma mevcuttur, ancak bu iletinin bunlardan herhangi birinin anlaşılması çok daha kolay olur ve değerler farklı platformlarda *[bitikten](https://en.wikipedia.org/wiki/Endianness)* etkilenmez.

Bu tür ile BCL `decimal` türü arasında dönüştürme bunun gibi bir şekilde C# uygulanabilir.

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
> Bunun gibi özel yardımcı program ileti türlerini kullandığınızda, diğer geliştiricilerin kendi dillerinde veya çerçevesindeki eşdeğer türe ve bu türden dönüştürme uygulayabilmesi için, onları `.proto` yorumlarla belgeetmeniz **gerekir** .

>[!div class="step-by-step"]
>[Önceki](protobuf-messages.md)
>[İleri](protobuf-nested-types.md)
