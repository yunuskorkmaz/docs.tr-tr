---
title: Prototipsiz skaler veri türleri-WCF geliştiricileri için gRPC
description: .NET Core 'da prototip ve gRPC desteği sunan temel ve iyi bilinen veri türleri hakkında bilgi edinin.
ms.date: 09/09/2019
ms.openlocfilehash: f5215550a6a2d54dfe2e859c574a34f641fdb68d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543163"
---
# <a name="protobuf-scalar-data-types"></a>Protobuf skaler veri türleri

Protokol arabelleği (Protobuffer), yerel skaler değer türlerinin bir aralığını destekler. Aşağıdaki tabloda bunların hepsi eşdeğer C# tür ile listelenmektedir:

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

Notlar:

1. `int32` ve `int64` için standart kodlama, imzalanmış değerlerle çalışırken verimsiz bir çalışmadır. Alanınız büyük olasılıkla negatif sayı içeriyorsa, bunun yerine `sint32` veya `sint64` kullanın. Bu türler sırasıyla C# `int` ve `long` türleriyle eşlenir.
2. `fixed` alanlar, her zaman değerin ne kadar olduğunu bağımsız olarak aynı sayıda bayt kullanır. Bu davranış, daha büyük değerler için serileştirme ve seri durumdan çıkarma sağlar.
3. Prototip dizeler UTF-8 (veya 7 bit ASCII) kodlardır. Kodlanan uzunluk 2<sup>32</sup>' den büyük olamaz.
4. Prototip çalışma zamanı, `byte[]` dizilerden ve bu kaynaklardan C# kolayca eşleyen bir `ByteString` türü sağlar.

## <a name="other-net-primitive-types"></a>Diğer .NET ilkel türleri

### <a name="dates-and-times"></a>Tarihler ve saatler

Yerel skaler türler, <xref:System.DateTimeOffset>, <xref:System.DateTime>ve <xref:System.TimeSpan>eşdeğer C#tarih ve saat değerleri için sağlamaz. Bu türleri, bazı Google "tanınmış türler" uzantılarını kullanarak belirtebilirsiniz. Bu uzantılar desteklenen platformlar genelinde karmaşık alan türleri için kod oluşturma ve çalışma zamanı desteği sağlar. 

Aşağıdaki tabloda tarih ve saat türleri gösterilmektedir:

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

C# Sınıfındaki oluşturulan Özellikler .net tarih ve saat türleri değildir. Özellikler, `Google.Protobuf.WellKnownTypes` ad alanındaki `Timestamp` ve `Duration` sınıflarını kullanır. Bu sınıflar, `DateTimeOffset`, `DateTime`ve `TimeSpan`dönüştürmek için yöntemler sağlar.

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
> `Timestamp` türü UTC saatleriyle birlikte çalışmaktadır. `DateTimeOffset` değerler her zaman sıfır bir uzaklığa sahiptir ve `DateTime.Kind` özelliği her zaman `DateTimeKind.Utc`.

### <a name="systemguid"></a>System. Guid

Protoarabellek, diğer platformlarda `UUID` olarak bilinen <xref:System.Guid> türünü doğrudan desteklemez. Bunun için iyi bilinen bir tür yoktur. 

En iyi yaklaşım, standart `8-4-4-4-12` onaltılı biçimi (örneğin, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`) kullanarak `Guid` değerlerini `string` alanı olarak idare kullanmaktır. Tüm diller ve platformlar bu biçimi ayrıştırabilirler.

`Guid` değerleri için `bytes` alanı kullanmayın. ([Vikipedi Definition](https://en.wikipedia.org/wiki/Endianness)) *ile Ilgili sorunlar* , prototip, Java gibi diğer platformlarla etkileşime girildiğinde Erratic davranışa neden olabilir.

### <a name="nullable-types"></a>Boş değer atanabilir tipler

İçin C# prototip kod oluşturma, `int32`için `int` gibi yerel türleri kullanır. Bu nedenle değerler her zaman dahil edilir ve null olamaz. 

C# Kodunuzda `int?` kullanma gibi açık null gerektiren değerler Için, prototipli "Iyi bilinen türler", null yapılabilir C# türlere derlenen sarmalayıcıları içerir. Bunları kullanmak için, `wrappers.proto` `.proto` dosyanıza aşağıdaki gibi içeri aktarın:

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

`Timestamp` ve `Duration` bilinen türler .NET içinde sınıflar olarak temsil edilir, bu nedenle null yapılabilir bir sürüme gerek yoktur. Ancak `DateTimeOffset` veya `TimeSpan`dönüştürme sırasında bu türlerin özelliklerinde null olup olmadığını denetlemek önemlidir.

## <a name="decimals"></a>In

Prototip, yalnızca `double` ve `float`.NET `decimal` türünü yerel olarak desteklemez. Prototip projesinde, iyi bilinen türlere standart bir `Decimal` türü ekleme olasılığa ilişkin, bunu destekleyen diller ve çerçeveler için platform desteği ile birlikte, yaygın olarak kullanılan bir tartışmada devam eden bir tartışma vardır. Henüz hiçbir şey uygulanmadı.

.NET istemcileri ve sunucuları arasında güvenli serileştirme için çalışacak `decimal` türünü temsil eden bir ileti tanımı oluşturmak mümkündür. Ancak diğer platformlardaki geliştiricilerin, kullanılmakta olan biçimi anlaması ve onun için kendi işlemesini uygulaması gerekir.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Protoarabellek için özel bir ondalık tür oluşturma

Basit bir uygulama, bazı Google API 'Lerinin kullandığı, `currency` alanı olmadan standart olmayan `Money` türüne benzer olabilir.

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

`nanos` alanı `-0.999_999_999``0.999_999_999` değerleri temsil eder. Örneğin, `1.5m` `decimal` değer `{ units = 1, nanos = 500_000_000 }`olarak temsil edilir. Bu nedenle, bu örnekteki `nanos` alanı, daha büyük değerler için `int32` daha verimli bir şekilde kodlayan `sfixed32` türünü kullanır. `units` alanı negatifse, `nanos` alanı da negatif olmalıdır.

> [!NOTE]
> `decimal` değerlerini bayt dizeleri olarak kodlamak için birden çok başka algoritma mevcuttur, ancak bu iletinin bunlardan herhangi birinin anlaşılması daha kolaydır. Değerler farklı platformlarda bitime tarafından etkilenmez.

Bu tür ile BCL `decimal` türü arasında dönüştürme C# şöyle uygulanabilir:

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
> Bu gibi özel ileti türlerini kullandığınızda, bunları `.proto`açıklamalarıyla belgeetmeniz *gerekir* . Diğer geliştiriciler daha sonra kendi dillerinde veya çerçevesinde eşdeğer türe ve dönüşümünü uygulayabilir.

>[!div class="step-by-step"]
>[Önceki](protobuf-messages.md)
>[İleri](protobuf-nested-types.md)
