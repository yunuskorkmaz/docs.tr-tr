---
title: Prototipsiz skaler veri türleri-WCF geliştiricileri için gRPC
description: .NET Core 'da prototip ve gRPC desteği sunan temel ve iyi bilinen veri türleri hakkında bilgi edinin.
ms.date: 09/09/2019
ms.openlocfilehash: 5447067b953d257258950d020636e0b38245e20d
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91573650"
---
# <a name="protobuf-scalar-data-types"></a>Protobuf skaler veri türleri

Protokol arabelleği (Protobuffer), yerel skaler değer türlerinin bir aralığını destekler. Aşağıdaki tabloda bunların hepsi eşdeğer C# türü ile listelenmektedir:

| Prototip türü | C# türü      | Notlar |
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

1. Ve için standart kodlama `int32` , `int64` imzalanmış değerlerle çalışırken verimsiz bir değer. Alanınız büyük olasılıkla negatif sayı içeriyorsa, `sint32` `sint64` bunun yerine veya kullanın. Bu türler `int` sırasıyla C# ve türleriyle eşlenir `long` .
2. `fixed`Alanlar, her zaman değerin ne kadar olduğunu bağımsız olarak aynı sayıda bayt kullanır. Bu davranış, daha büyük değerler için serileştirme ve seri durumdan çıkarma sağlar.
3. Prototip dizeler UTF-8 (veya 7 bit ASCII) kodlardır. Kodlanan uzunluk 2<sup>32</sup>' den büyük olamaz.
4. Prototip çalışma zamanı, `ByteString` C# dizileriyle ve bu dizilere kolayca eşleyen bir tür sağlar `byte[]` .

## <a name="other-net-primitive-types"></a>Diğer .NET ilkel türleri

### <a name="dates-and-times"></a>Tarihler ve saatler

Yerel skaler türler tarih ve saat değerleri için, C# ' nin, <xref:System.DateTimeOffset> <xref:System.DateTime> ve ile eşdeğerdir <xref:System.TimeSpan> . Bu türleri, bazı Google "tanınmış türler" uzantılarını kullanarak belirtebilirsiniz. Bu uzantılar desteklenen platformlar genelinde karmaşık alan türleri için kod oluşturma ve çalışma zamanı desteği sağlar.

Aşağıdaki tabloda tarih ve saat türleri gösterilmektedir:

| C# türü | Prototip iyi bilinen tür |
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

C# sınıfındaki oluşturulan Özellikler .NET tarih ve saat türleri değildir. Özellikler, `Timestamp` `Duration` ad alanındaki ve sınıflarını kullanır `Google.Protobuf.WellKnownTypes` . Bu sınıflar,, ve ' a dönüştürmek için yöntemler sağlar `DateTimeOffset` `DateTime` `TimeSpan` .

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
> `Timestamp`Tür UTC saatleriyle birlikte çalışmaktadır. `DateTimeOffset` değerler her zaman sıfır bir uzaklığa sahiptir ve `DateTime.Kind` özellik her zaman olur `DateTimeKind.Utc` .

### <a name="systemguid"></a>System. Guid

Protoarabellek, <xref:System.Guid> diğer platformlarda olduğu bilinen türü doğrudan desteklemez `UUID` . Bunun için iyi bilinen bir tür yoktur.

En iyi yaklaşım, `Guid` `string` Standart `8-4-4-4-12` onaltılı biçimi (örneğin,) kullanarak değerleri bir alan olarak idare kullanmaktır `45a9fda3-bd01-47a9-8460-c1cd7484b0b3` . Tüm diller ve platformlar bu biçimi ayrıştırabilirler.

`bytes`Değerler için bir alan kullanmayın `Guid` . ([Vikipedi Definition](https://en.wikipedia.org/wiki/Endianness)) *ile Ilgili sorunlar* , prototip, Java gibi diğer platformlarla etkileşime girildiğinde Erratic davranışa neden olabilir.

### <a name="nullable-types"></a>Null atanabilir türler

C# için prototip kod oluşturma, gibi yerel türleri kullanır `int` `int32` . Bu nedenle değerler her zaman dahil edilir ve null olamaz.

C# kodunuzda kullanılması gibi açık null gerektiren değerler için `int?` , prototipli "Iyi bilinen türler", Nullable C# türlerine derlenen sarmalayıcıları içerir. Bunları kullanmak için, dosyanıza aşağıdaki gibi içeri aktarın `wrappers.proto` `.proto` :

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Prototip, `T?` oluşturulan ileti özelliği için basit (örneğin, `int?` ) kullanır.

Aşağıdaki tabloda, eşdeğer C# türüyle sarmalayıcı türlerinin tüm listesi gösterilmektedir:

| C# türü   | İyi bilinen tür sarmalayıcısı       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

İyi bilinen türler, `Timestamp` `Duration` .net olarak sınıflar olarak temsil edilir. C# 8 ve ötesinde, null yapılabilir başvuru türlerini kullanabilirsiniz. Ancak, veya ' ye dönüştürürken bu türlerin özelliklerinde null olup olmadığını denetlemek önemlidir `DateTimeOffset` `TimeSpan` .

## <a name="decimals"></a>Ondalıklar

Prototip `decimal` , yalnızca ve .NET türünü yerel olarak desteklemez `double` `float` . Prototip projesinde `Decimal` , iyi bilinen türlere standart bir tür ekleme olasılığa ve bunu destekleyen diller ve çerçeveler için platform desteğiyle bir standart tür ekleme olasılığa ilişkin devam eden bir tartışma vardır. Henüz hiçbir şey uygulanmadı.

`decimal`.NET istemcileri ve sunucuları arasında güvenli serileştirme için çalışacak olan türü temsil eden bir ileti tanımı oluşturmak mümkündür. Ancak diğer platformlardaki geliştiricilerin, kullanılmakta olan biçimi anlaması ve onun için kendi işlemesini uygulaması gerekir.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Protoarabellek için özel bir ondalık tür oluşturma

Basit bir uygulama, `Money` bazı Google API 'lerinin kullandığı standart olmayan türe benzer olabilir `currency` .

```protobuf
package CustomTypes;

// Example: 12345.6789 -> { units = 12345, nanos = 678900000 }
message DecimalValue {

    // Whole units part of the amount
    int64 units = 1;

    // Nano units of the amount (10^-9)
    // Must be same sign as units
    sfixed32 nanos = 2;
}
```

`nanos`Alan, öğesinden değerlerini temsil `0.999_999_999` eder `-0.999_999_999` . Örneğin, `decimal` değer `1.5m` olarak temsil edilir `{ units = 1, nanos = 500_000_000 }` . Bu, `nanos` Bu örnekteki alanın, `sfixed32` daha büyük değerler için daha verimli bir şekilde kodlama türünü kullanmadığına neden olur `int32` . `units`Alan negatifse `nanos` alanın de negatif olması gerekir.

> [!NOTE]
> Değerleri bayt dizeleri olarak kodlamak için birden çok farklı algoritma mevcuttur `decimal` , ancak bu iletinin bunlardan herhangi birinin anlaşılması kolaylaşır. Değerler farklı platformlarda bitime tarafından etkilenmez.

Bu tür ile BCL türü arasında dönüştürme `decimal` C# ' de şöyle uygulanabilir:

```csharp
namespace CustomTypes
{
    public partial class DecimalValue
    {
        private const decimal NanoFactor = 1_000_000_000;
        public DecimalValue(long units, int nanos)
        {
            Units = units;
            Nanos = nanos;
        }

        public long Units { get; }
        public int Nanos { get; }

        public static implicit operator decimal(CustomTypes.DecimalValue grpcDecimal)
        {
            return grpcDecimal.Units + grpcDecimal.Nanos / NanoFactor;
        }

        public static implicit operator CustomTypes.DecimalValue(decimal value)
        {
            var units = decimal.ToInt64(value);
            var nanos = decimal.ToInt32((value - units) * NanoFactor);
            return new CustomTypes.DecimalValue(units, nanos);
        }
    }
}
```

> [!IMPORTANT]
> Bu gibi özel ileti türlerini kullandığınızda, bunları içindeki yorumlarla belgeetmeniz *gerekir* `.proto` . Diğer geliştiriciler daha sonra kendi dillerinde veya çerçevesinde eşdeğer türe ve dönüşümünü uygulayabilir.

>[!div class="step-by-step"]
>[Önceki](protobuf-messages.md) 
> [Sonraki](protobuf-nested-types.md)
