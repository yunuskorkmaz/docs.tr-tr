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
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="bbd01-103">Prototipsiz skaler veri türleri</span><span class="sxs-lookup"><span data-stu-id="bbd01-103">Protobuf scalar data types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="bbd01-104">Prototip, yerel skaler değer türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="bbd01-104">Protobuf supports a range of native scalar value types.</span></span> <span data-ttu-id="bbd01-105">Aşağıdaki tabloda bunların hepsi eşdeğer C# tür ile listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="bbd01-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="bbd01-106">Prototip türü</span><span class="sxs-lookup"><span data-stu-id="bbd01-106">Protobuf type</span></span> | <span data-ttu-id="bbd01-107">C#türüyle</span><span class="sxs-lookup"><span data-stu-id="bbd01-107">C# type</span></span>      | <span data-ttu-id="bbd01-108">Notlar</span><span class="sxs-lookup"><span data-stu-id="bbd01-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="bbd01-109">1\.</span><span class="sxs-lookup"><span data-stu-id="bbd01-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="bbd01-110">1\.</span><span class="sxs-lookup"><span data-stu-id="bbd01-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="bbd01-111">1\.</span><span class="sxs-lookup"><span data-stu-id="bbd01-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="bbd01-112">1\.</span><span class="sxs-lookup"><span data-stu-id="bbd01-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="bbd01-113">2</span><span class="sxs-lookup"><span data-stu-id="bbd01-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="bbd01-114">2</span><span class="sxs-lookup"><span data-stu-id="bbd01-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="bbd01-115">2</span><span class="sxs-lookup"><span data-stu-id="bbd01-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="bbd01-116">2</span><span class="sxs-lookup"><span data-stu-id="bbd01-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="bbd01-117">3</span><span class="sxs-lookup"><span data-stu-id="bbd01-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="bbd01-118">4</span><span class="sxs-lookup"><span data-stu-id="bbd01-118">4</span></span>     |

## <a name="notes"></a><span data-ttu-id="bbd01-119">Notlar</span><span class="sxs-lookup"><span data-stu-id="bbd01-119">Notes</span></span>

1. <span data-ttu-id="bbd01-120">`int32` Ve`int64` için standart kodlama, imzalanmış değerlerle çalışırken verimsiz bir değer.</span><span class="sxs-lookup"><span data-stu-id="bbd01-120">The standard encoding for `int32` and `int64` is inefficient when working with signed values.</span></span> <span data-ttu-id="bbd01-121">Alanınız büyük olasılıkla negatif sayı içeriyorsa, bunun yerine veya `sint32` `sint64` kullanın.</span><span class="sxs-lookup"><span data-stu-id="bbd01-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="bbd01-122">Her iki tür de sırasıyla C# `int` ve `long` türleriyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="bbd01-122">Both types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="bbd01-123">`fixed` Alanlar, her zaman değerin ne kadar olduğunu bağımsız olarak aynı sayıda bayt kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbd01-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="bbd01-124">Bu davranış, daha büyük değerler için serileştirme ve seri durumdan çıkarma sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbd01-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="bbd01-125">Prototip dizeler UTF-8 (veya 7 bit ASCII) kodlardır ve kodlanan uzunluk 2<sup>32</sup>' den büyük olamaz.</span><span class="sxs-lookup"><span data-stu-id="bbd01-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded, and the encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="bbd01-126">Prototip çalışma zamanı, dizilere ve `ByteString` dizilerden C# `byte[]` kolayca eşleyen bir tür sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbd01-126">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="bbd01-127">Diğer .NET ilkel türleri</span><span class="sxs-lookup"><span data-stu-id="bbd01-127">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="bbd01-128">Tarihler ve saatler</span><span class="sxs-lookup"><span data-stu-id="bbd01-128">Dates and times</span></span>

<span data-ttu-id="bbd01-129">Yerel skaler türler tarih ve saat değerleri için, C#, ve ile <xref:System.DateTimeOffset> <xref:System.TimeSpan>eşdeğerdir <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="bbd01-129">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="bbd01-130">Bu türler, desteklenen platformlar genelinde daha karmaşık alan türleri için kod oluşturma ve çalışma zamanı desteği sağlayan bazı Google "tanınmış türler" uzantıları kullanılarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="bbd01-130">These types can be specified using some of Google's "Well Known Types" extensions, which provide code generation and runtime support for more complex field types across the supported platforms.</span></span> <span data-ttu-id="bbd01-131">Aşağıdaki tabloda tarih ve saat türleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bbd01-131">The following table shows the date and time types:</span></span>

| <span data-ttu-id="bbd01-132">C#türüyle</span><span class="sxs-lookup"><span data-stu-id="bbd01-132">C# type</span></span> | <span data-ttu-id="bbd01-133">Prototip iyi bilinen tür</span><span class="sxs-lookup"><span data-stu-id="bbd01-133">Protobuf well-known type</span></span> |
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

<span data-ttu-id="bbd01-134">C# Sınıfındaki oluşturulan Özellikler .net tarih ve saat türleri değildir.</span><span class="sxs-lookup"><span data-stu-id="bbd01-134">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="bbd01-135">Özellikleri, ve, `Timestamp` , `Duration` ve `DateTimeOffset` `DateTime` `Google.Protobuf.WellKnownTypes` '`TimeSpan`a dönüştürmek için yöntemler sağlayan ad alanındaki ve sınıflarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbd01-135">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace, which provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="bbd01-136">`Timestamp` Tür UTC zamanları ile birlikte çalışarak. değerler her zaman sıfır bir uzaklığa sahiptir `DateTime.Kind` ve özellik her zaman `DateTimeKind.Utc`olur. `DateTimeOffset`</span><span class="sxs-lookup"><span data-stu-id="bbd01-136">The `Timestamp` type works with UTC times; `DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property will always be `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="bbd01-137">System. Guid</span><span class="sxs-lookup"><span data-stu-id="bbd01-137">System.Guid</span></span>

<span data-ttu-id="bbd01-138">Diğer platformlarda olduğu `UUID` bilinen tür,prototiptedoğrudandesteklenmezvebununiçiniyibilinenbirtüryoktur.<xref:System.Guid></span><span class="sxs-lookup"><span data-stu-id="bbd01-138">The <xref:System.Guid> type, known as `UUID` on other platforms, isn't directly supported by Protobuf and there's no well-known type for it.</span></span> <span data-ttu-id="bbd01-139">En iyi yaklaşım, değerleri, `Guid` tüm diller `string` ve platformlar tarafından ayrıştırılabilen `8-4-4-4-12` standart onaltılı biçimi (örneğin, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`) kullanarak alan olarak idare kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="bbd01-139">The best approach is to handle `Guid` values as `string` field, using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), which can be parsed by all languages and platforms.</span></span> <span data-ttu-id="bbd01-140">Değer için `bytes` `Guid` bir alan kullanmayın. Bu, bitime ile ilgili problemler, Java gibi diğer platformlarla etkileşerek Erratic davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="bbd01-140">Don't use a `bytes` field for `Guid` values, as problems with endianness can result in erratic behavior when interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="bbd01-141">Boş değer atanabilir tipler</span><span class="sxs-lookup"><span data-stu-id="bbd01-141">Nullable types</span></span>

<span data-ttu-id="bbd01-142">İçin C# prototip kod oluşturma, gibi yerel türleri `int` `int32`kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbd01-142">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="bbd01-143">Bu, değerlerin her zaman dahil olduğu ve null olamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bbd01-143">This means that the values are always included and can't be null.</span></span> <span data-ttu-id="bbd01-144">Kodunuzda kullanılması `int?` gibi açık null gerektiren değerler için, prototipli "iyi bilinen türler", null yapılabilir C# türler için derlenen sarmalayıcıları içerir. C#</span><span class="sxs-lookup"><span data-stu-id="bbd01-144">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="bbd01-145">Bunları kullanmak için, `wrappers.proto` `.proto` dosyanıza aşağıdaki gibi içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="bbd01-145">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="bbd01-146">Prototip, oluşturulan ileti özelliği için `T?` basit (örneğin, `int?`) kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbd01-146">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="bbd01-147">Aşağıdaki tabloda, sarmalama türlerinin, eşdeğer C# türlerine sahip tüm listesi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="bbd01-147">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="bbd01-148">C#türüyle</span><span class="sxs-lookup"><span data-stu-id="bbd01-148">C# type</span></span>   | <span data-ttu-id="bbd01-149">İyi bilinen tür sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="bbd01-149">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="bbd01-150">İyi bilinen türler `Timestamp` ve `Duration` .NET içinde sınıflar olarak temsil edilir. bu nedenle, null yapılabilir bir sürüme gerek yoktur, ancak veya `TimeSpan`' ye `DateTimeOffset` dönüştürürken bu türlerin özelliklerinde null denetimi yapmanız önemlidir.</span><span class="sxs-lookup"><span data-stu-id="bbd01-150">The well-known types `Timestamp` and `Duration` are represented in .NET as classes, so there's no need for a nullable version, but it's important to check for null on properties of those types when converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="bbd01-151">In</span><span class="sxs-lookup"><span data-stu-id="bbd01-151">Decimals</span></span>

<span data-ttu-id="bbd01-152">Prototip, yalnızca `decimal` `double` ve `float`.NET türünü yerel olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bbd01-152">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="bbd01-153">Yaygın olarak bilinen türlere standart `Decimal` bir tür ekleme olasılığa ve bunu destekleyen diller ve çerçeveler için platform desteğiyle, ancak henüz hiçbir şey uygulanmadığı için, prototip projesinde devam eden bir tartışma vardır.</span><span class="sxs-lookup"><span data-stu-id="bbd01-153">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it, but nothing has been implemented yet.</span></span>

<span data-ttu-id="bbd01-154">.NET istemcileri ve sunucuları arasında güvenli seri hale getirme için çalışacak `decimal` olan türü temsil etmek üzere bir ileti tanımı oluşturmak mümkündür, ancak diğer platformlardaki geliştiricilerin, kullanılan biçimi anlaması ve kendi özelliklerini uygulaması gerekir işleme.</span><span class="sxs-lookup"><span data-stu-id="bbd01-154">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers, but developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="bbd01-155">Protoarabellek için özel bir ondalık tür oluşturma</span><span class="sxs-lookup"><span data-stu-id="bbd01-155">Creating a custom Decimal type for Protobuf</span></span>

<span data-ttu-id="bbd01-156">Çok basit bir uygulama, `Money` `currency` alan olmadan bazı Google API 'leri tarafından kullanılan standart olmayan türe benzer olabilir.</span><span class="sxs-lookup"><span data-stu-id="bbd01-156">A very simple implementation could be similar to the non-standard `Money` type used by some Google APIs, without the `currency` field.</span></span>

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

<span data-ttu-id="bbd01-157">Alan `nanos` `0.999_999_999` ,`-0.999_999_999`öğesinden değerlerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bbd01-157">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="bbd01-158">Örneğin `decimal` , `int32` değer `1.5m` `nanos` olarak `{ units = 1, nanos = 500_000_000 }` temsil edilir (Bu, bu örnekteki alanın, daha büyük değerler için daha verimli bir `sfixed32` şekilde kodlayan türü kullanması neden olur).</span><span class="sxs-lookup"><span data-stu-id="bbd01-158">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }` (this is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values).</span></span> <span data-ttu-id="bbd01-159">`units` Alan negatifse`nanos` alanın de negatif olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bbd01-159">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="bbd01-160">Değerleri bayt dizeleri olarak kodlamak `decimal` için birden çok farklı algoritma mevcuttur, ancak bu iletinin bunlardan herhangi birinin anlaşılması çok daha kolay olur ve değerler farklı platformlarda *[bitime](https://en.wikipedia.org/wiki/Endianness)* tarafından etkilenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="bbd01-160">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is much easier to understand than any of them, and the values are not affected by *[endianness](https://en.wikipedia.org/wiki/Endianness)* on different platforms.</span></span>

<span data-ttu-id="bbd01-161">Bu tür ile BCL `decimal` türü arasındaki dönüştürme bunun C# gibi uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="bbd01-161">Conversion between this type and the BCL `decimal` type could be implemented in C# like this.</span></span>

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
> <span data-ttu-id="bbd01-162">Bu gibi özel yardımcı program ileti türlerini kullandığınızda, diğer geliştiricilerin kendi dillerinde veya çerçevesindeki eşdeğer türe ve `.proto` bu türden dönüştürme uygulayabilmeleri için, bunları içindeki yorumlarla belgeetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bbd01-162">Whenever you use custom utility message types like this, you **must** document them with comments in the `.proto` so that other developers can implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bbd01-163">[Önceki](protobuf-messages.md)
>[İleri](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="bbd01-163">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
