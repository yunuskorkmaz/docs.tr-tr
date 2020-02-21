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
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="8ad62-103">Protobuf skaler veri türleri</span><span class="sxs-lookup"><span data-stu-id="8ad62-103">Protobuf scalar data types</span></span>

<span data-ttu-id="8ad62-104">Protokol arabelleği (Protobuffer), yerel skaler değer türlerinin bir aralığını destekler.</span><span class="sxs-lookup"><span data-stu-id="8ad62-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="8ad62-105">Aşağıdaki tabloda bunların hepsi eşdeğer C# tür ile listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="8ad62-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="8ad62-106">Prototip türü</span><span class="sxs-lookup"><span data-stu-id="8ad62-106">Protobuf type</span></span> | <span data-ttu-id="8ad62-107">C#türüyle</span><span class="sxs-lookup"><span data-stu-id="8ad62-107">C# type</span></span>      | <span data-ttu-id="8ad62-108">Notlar</span><span class="sxs-lookup"><span data-stu-id="8ad62-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="8ad62-109">1</span><span class="sxs-lookup"><span data-stu-id="8ad62-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="8ad62-110">1</span><span class="sxs-lookup"><span data-stu-id="8ad62-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="8ad62-111">1</span><span class="sxs-lookup"><span data-stu-id="8ad62-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="8ad62-112">1</span><span class="sxs-lookup"><span data-stu-id="8ad62-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="8ad62-113">2</span><span class="sxs-lookup"><span data-stu-id="8ad62-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="8ad62-114">2</span><span class="sxs-lookup"><span data-stu-id="8ad62-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="8ad62-115">2</span><span class="sxs-lookup"><span data-stu-id="8ad62-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="8ad62-116">2</span><span class="sxs-lookup"><span data-stu-id="8ad62-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="8ad62-117">3</span><span class="sxs-lookup"><span data-stu-id="8ad62-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="8ad62-118">4</span><span class="sxs-lookup"><span data-stu-id="8ad62-118">4</span></span>     |

<span data-ttu-id="8ad62-119">Notlar:</span><span class="sxs-lookup"><span data-stu-id="8ad62-119">Notes:</span></span>

1. <span data-ttu-id="8ad62-120">`int32` ve `int64` için standart kodlama, imzalanmış değerlerle çalışırken verimsiz bir çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="8ad62-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="8ad62-121">Alanınız büyük olasılıkla negatif sayı içeriyorsa, bunun yerine `sint32` veya `sint64` kullanın.</span><span class="sxs-lookup"><span data-stu-id="8ad62-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="8ad62-122">Bu türler sırasıyla C# `int` ve `long` türleriyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="8ad62-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="8ad62-123">`fixed` alanlar, her zaman değerin ne kadar olduğunu bağımsız olarak aynı sayıda bayt kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ad62-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="8ad62-124">Bu davranış, daha büyük değerler için serileştirme ve seri durumdan çıkarma sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ad62-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="8ad62-125">Prototip dizeler UTF-8 (veya 7 bit ASCII) kodlardır.</span><span class="sxs-lookup"><span data-stu-id="8ad62-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="8ad62-126">Kodlanan uzunluk 2<sup>32</sup>' den büyük olamaz.</span><span class="sxs-lookup"><span data-stu-id="8ad62-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="8ad62-127">Prototip çalışma zamanı, `byte[]` dizilerden ve bu kaynaklardan C# kolayca eşleyen bir `ByteString` türü sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ad62-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="8ad62-128">Diğer .NET ilkel türleri</span><span class="sxs-lookup"><span data-stu-id="8ad62-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="8ad62-129">Tarihler ve saatler</span><span class="sxs-lookup"><span data-stu-id="8ad62-129">Dates and times</span></span>

<span data-ttu-id="8ad62-130">Yerel skaler türler, <xref:System.DateTimeOffset>, <xref:System.DateTime>ve <xref:System.TimeSpan>eşdeğer C#tarih ve saat değerleri için sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="8ad62-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="8ad62-131">Bu türleri, bazı Google "tanınmış türler" uzantılarını kullanarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ad62-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="8ad62-132">Bu uzantılar desteklenen platformlar genelinde karmaşık alan türleri için kod oluşturma ve çalışma zamanı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ad62-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span> 

<span data-ttu-id="8ad62-133">Aşağıdaki tabloda tarih ve saat türleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8ad62-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="8ad62-134">C#türüyle</span><span class="sxs-lookup"><span data-stu-id="8ad62-134">C# type</span></span> | <span data-ttu-id="8ad62-135">Prototip iyi bilinen tür</span><span class="sxs-lookup"><span data-stu-id="8ad62-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="8ad62-136">C# Sınıfındaki oluşturulan Özellikler .net tarih ve saat türleri değildir.</span><span class="sxs-lookup"><span data-stu-id="8ad62-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="8ad62-137">Özellikler, `Google.Protobuf.WellKnownTypes` ad alanındaki `Timestamp` ve `Duration` sınıflarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ad62-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="8ad62-138">Bu sınıflar, `DateTimeOffset`, `DateTime`ve `TimeSpan`dönüştürmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8ad62-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="8ad62-139">`Timestamp` türü UTC saatleriyle birlikte çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ad62-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="8ad62-140">`DateTimeOffset` değerler her zaman sıfır bir uzaklığa sahiptir ve `DateTime.Kind` özelliği her zaman `DateTimeKind.Utc`.</span><span class="sxs-lookup"><span data-stu-id="8ad62-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="8ad62-141">System. Guid</span><span class="sxs-lookup"><span data-stu-id="8ad62-141">System.Guid</span></span>

<span data-ttu-id="8ad62-142">Protoarabellek, diğer platformlarda `UUID` olarak bilinen <xref:System.Guid> türünü doğrudan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8ad62-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="8ad62-143">Bunun için iyi bilinen bir tür yoktur.</span><span class="sxs-lookup"><span data-stu-id="8ad62-143">There's no well-known type for it.</span></span> 

<span data-ttu-id="8ad62-144">En iyi yaklaşım, standart `8-4-4-4-12` onaltılı biçimi (örneğin, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`) kullanarak `Guid` değerlerini `string` alanı olarak idare kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="8ad62-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="8ad62-145">Tüm diller ve platformlar bu biçimi ayrıştırabilirler.</span><span class="sxs-lookup"><span data-stu-id="8ad62-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="8ad62-146">`Guid` değerleri için `bytes` alanı kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="8ad62-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="8ad62-147">([Vikipedi Definition](https://en.wikipedia.org/wiki/Endianness)) *ile Ilgili sorunlar* , prototip, Java gibi diğer platformlarla etkileşime girildiğinde Erratic davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ad62-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="8ad62-148">Boş değer atanabilir tipler</span><span class="sxs-lookup"><span data-stu-id="8ad62-148">Nullable types</span></span>

<span data-ttu-id="8ad62-149">İçin C# prototip kod oluşturma, `int32`için `int` gibi yerel türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ad62-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="8ad62-150">Bu nedenle değerler her zaman dahil edilir ve null olamaz.</span><span class="sxs-lookup"><span data-stu-id="8ad62-150">So the values are always included and can't be null.</span></span> 

<span data-ttu-id="8ad62-151">C# Kodunuzda `int?` kullanma gibi açık null gerektiren değerler Için, prototipli "Iyi bilinen türler", null yapılabilir C# türlere derlenen sarmalayıcıları içerir.</span><span class="sxs-lookup"><span data-stu-id="8ad62-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="8ad62-152">Bunları kullanmak için, `wrappers.proto` `.proto` dosyanıza aşağıdaki gibi içeri aktarın:</span><span class="sxs-lookup"><span data-stu-id="8ad62-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="8ad62-153">Prototip, oluşturulan ileti özelliği için basit `T?` (örneğin, `int?`) kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ad62-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="8ad62-154">Aşağıdaki tabloda, sarmalama türlerinin, eşdeğer C# türlerine sahip tüm listesi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8ad62-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="8ad62-155">C#türüyle</span><span class="sxs-lookup"><span data-stu-id="8ad62-155">C# type</span></span>   | <span data-ttu-id="8ad62-156">İyi bilinen tür sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="8ad62-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="8ad62-157">`Timestamp` ve `Duration` bilinen türler .NET içinde sınıflar olarak temsil edilir, bu nedenle null yapılabilir bir sürüme gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="8ad62-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes, so there's no need for a nullable version.</span></span> <span data-ttu-id="8ad62-158">Ancak `DateTimeOffset` veya `TimeSpan`dönüştürme sırasında bu türlerin özelliklerinde null olup olmadığını denetlemek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8ad62-158">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="8ad62-159">In</span><span class="sxs-lookup"><span data-stu-id="8ad62-159">Decimals</span></span>

<span data-ttu-id="8ad62-160">Prototip, yalnızca `double` ve `float`.NET `decimal` türünü yerel olarak desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8ad62-160">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="8ad62-161">Prototip projesinde, iyi bilinen türlere standart bir `Decimal` türü ekleme olasılığa ilişkin, bunu destekleyen diller ve çerçeveler için platform desteği ile birlikte, yaygın olarak kullanılan bir tartışmada devam eden bir tartışma vardır.</span><span class="sxs-lookup"><span data-stu-id="8ad62-161">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="8ad62-162">Henüz hiçbir şey uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="8ad62-162">Nothing has been implemented yet.</span></span>

<span data-ttu-id="8ad62-163">.NET istemcileri ve sunucuları arasında güvenli serileştirme için çalışacak `decimal` türünü temsil eden bir ileti tanımı oluşturmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="8ad62-163">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="8ad62-164">Ancak diğer platformlardaki geliştiricilerin, kullanılmakta olan biçimi anlaması ve onun için kendi işlemesini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ad62-164">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="8ad62-165">Protoarabellek için özel bir ondalık tür oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ad62-165">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="8ad62-166">Basit bir uygulama, bazı Google API 'Lerinin kullandığı, `currency` alanı olmadan standart olmayan `Money` türüne benzer olabilir.</span><span class="sxs-lookup"><span data-stu-id="8ad62-166">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

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

<span data-ttu-id="8ad62-167">`nanos` alanı `-0.999_999_999``0.999_999_999` değerleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8ad62-167">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="8ad62-168">Örneğin, `1.5m` `decimal` değer `{ units = 1, nanos = 500_000_000 }`olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="8ad62-168">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="8ad62-169">Bu nedenle, bu örnekteki `nanos` alanı, daha büyük değerler için `int32` daha verimli bir şekilde kodlayan `sfixed32` türünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="8ad62-169">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="8ad62-170">`units` alanı negatifse, `nanos` alanı da negatif olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8ad62-170">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="8ad62-171">`decimal` değerlerini bayt dizeleri olarak kodlamak için birden çok başka algoritma mevcuttur, ancak bu iletinin bunlardan herhangi birinin anlaşılması daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="8ad62-171">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="8ad62-172">Değerler farklı platformlarda bitime tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="8ad62-172">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="8ad62-173">Bu tür ile BCL `decimal` türü arasında dönüştürme C# şöyle uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="8ad62-173">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

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
> <span data-ttu-id="8ad62-174">Bu gibi özel ileti türlerini kullandığınızda, bunları `.proto`açıklamalarıyla belgeetmeniz *gerekir* .</span><span class="sxs-lookup"><span data-stu-id="8ad62-174">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="8ad62-175">Diğer geliştiriciler daha sonra kendi dillerinde veya çerçevesinde eşdeğer türe ve dönüşümünü uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="8ad62-175">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8ad62-176">[Önceki](protobuf-messages.md)
>[İleri](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="8ad62-176">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
