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
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="4b4d7-103">Protobuf skaler veri türleri</span><span class="sxs-lookup"><span data-stu-id="4b4d7-103">Protobuf scalar data types</span></span>

<span data-ttu-id="4b4d7-104">Protokol Arabelleği (Protobuf) yerel skaler değer türleri bir dizi destekler.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="4b4d7-105">Aşağıdaki tabloda bunların hepsi eşdeğer C# türüne sahip olarak listelenebvardır:</span><span class="sxs-lookup"><span data-stu-id="4b4d7-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="4b4d7-106">Protobuf tipi</span><span class="sxs-lookup"><span data-stu-id="4b4d7-106">Protobuf type</span></span> | <span data-ttu-id="4b4d7-107">C# tipi</span><span class="sxs-lookup"><span data-stu-id="4b4d7-107">C# type</span></span>      | <span data-ttu-id="4b4d7-108">Notlar</span><span class="sxs-lookup"><span data-stu-id="4b4d7-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="4b4d7-109">1</span><span class="sxs-lookup"><span data-stu-id="4b4d7-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="4b4d7-110">1</span><span class="sxs-lookup"><span data-stu-id="4b4d7-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="4b4d7-111">1</span><span class="sxs-lookup"><span data-stu-id="4b4d7-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="4b4d7-112">1</span><span class="sxs-lookup"><span data-stu-id="4b4d7-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="4b4d7-113">2</span><span class="sxs-lookup"><span data-stu-id="4b4d7-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="4b4d7-114">2</span><span class="sxs-lookup"><span data-stu-id="4b4d7-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="4b4d7-115">2</span><span class="sxs-lookup"><span data-stu-id="4b4d7-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="4b4d7-116">2</span><span class="sxs-lookup"><span data-stu-id="4b4d7-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="4b4d7-117">3</span><span class="sxs-lookup"><span data-stu-id="4b4d7-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="4b4d7-118">4</span><span class="sxs-lookup"><span data-stu-id="4b4d7-118">4</span></span>     |

<span data-ttu-id="4b4d7-119">Notlar:</span><span class="sxs-lookup"><span data-stu-id="4b4d7-119">Notes:</span></span>

1. <span data-ttu-id="4b4d7-120">İmzalanan değerlerle `int32` `int64` çalışırken standart kodlama ve verimsizdir.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="4b4d7-121">Alanınız negatif sayılar içeriyorsa, `sint32` `sint64` kullanın veya bunun yerine.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="4b4d7-122">Bu türler sırasıyla `int` `long` C# ve türleri ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="4b4d7-123">Alanlar, `fixed` değeri ne olursa olsun her zaman aynı sayıda bayt kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="4b4d7-124">Bu davranış, serileştirme ve deserialization daha büyük değerler için daha hızlı yapar.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="4b4d7-125">Protobuf dizeleri UTF-8 (veya 7-bit ASCII) kodlanır.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="4b4d7-126">Kodlanmış uzunluk 2<sup>32'den</sup>büyük olamaz.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="4b4d7-127">Protobuf çalışma süresi, `ByteString` C# `byte[]` dizilerine kolayca eşlenebilen bir tür sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="4b4d7-128">Diğer .NET ilkel türleri</span><span class="sxs-lookup"><span data-stu-id="4b4d7-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="4b4d7-129">Tarihler ve saatler</span><span class="sxs-lookup"><span data-stu-id="4b4d7-129">Dates and times</span></span>

<span data-ttu-id="4b4d7-130">Yerel skaler türleri, C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>ve <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="4b4d7-131">Bu türleri, Google'ın "Bilinen Türleri" uzantılarından bazılarını kullanarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="4b4d7-132">Bu uzantılar, desteklenen platformlardaki karmaşık alan türleri için kod oluşturma ve çalışma zamanı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span>

<span data-ttu-id="4b4d7-133">Aşağıdaki tablo tarih ve saat türlerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="4b4d7-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="4b4d7-134">C# tipi</span><span class="sxs-lookup"><span data-stu-id="4b4d7-134">C# type</span></span> | <span data-ttu-id="4b4d7-135">Protobuf iyi bilinen tip</span><span class="sxs-lookup"><span data-stu-id="4b4d7-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="4b4d7-136">C# sınıfında oluşturulan özellikler .NET tarih ve saat türleri değildir.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="4b4d7-137">Özellikler `Google.Protobuf.WellKnownTypes` ad `Timestamp` alanında `Duration` ve sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="4b4d7-138">Bu sınıflar ve dönüştürme için `DateTimeOffset`yöntemler `DateTime`sağlar `TimeSpan`, , ve .</span><span class="sxs-lookup"><span data-stu-id="4b4d7-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="4b4d7-139">Tür `Timestamp` UTC kez çalışır.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="4b4d7-140">`DateTimeOffset`değerleri her zaman sıfır bir `DateTime.Kind` ofset `DateTimeKind.Utc`var ve özelliği her zaman .</span><span class="sxs-lookup"><span data-stu-id="4b4d7-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="4b4d7-141">System.Guid</span><span class="sxs-lookup"><span data-stu-id="4b4d7-141">System.Guid</span></span>

<span data-ttu-id="4b4d7-142">Protobuf, diğer platformlarda <xref:System.Guid> olduğu gibi `UUID` bilinen türü doğrudan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="4b4d7-143">Bunun için iyi bilinen bir türü yok.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-143">There's no well-known type for it.</span></span>

<span data-ttu-id="4b4d7-144">En iyi yaklaşım, `Guid` standart `string` `8-4-4-4-12` hexadecimal biçimini kullanarak (örneğin,) `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`değerleri alan olarak işlemektir.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="4b4d7-145">Tüm diller ve platformlar bu biçimi ayrıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="4b4d7-146">Değerler için `Guid` alan `bytes` kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="4b4d7-147">Protobuf Java gibi diğer platformlarla etkileşimhalindeyken, *endoyanness* [(Vikipedi tanımı)](https://en.wikipedia.org/wiki/Endianness)ile ilgili sorunlar düzensiz davranışlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="4b4d7-148">Boş değer atanabilir tipler</span><span class="sxs-lookup"><span data-stu-id="4b4d7-148">Nullable types</span></span>

<span data-ttu-id="4b4d7-149">C# için Protobuf kod oluşturma gibi `int` yerel `int32`türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="4b4d7-150">Yani değerler her zaman dahildir ve null olamaz.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-150">So the values are always included and can't be null.</span></span>

<span data-ttu-id="4b4d7-151">C# kodunuzda kullanmak `int?` gibi açık null gerektiren değerler için, Protobuf'un "İyi Bilinen Türleri" geçersiz C# türlerine derlenmiş ambalajları içerir.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="4b4d7-152">Bunları kullanmak için `wrappers.proto` dosyanıza şu şekilde aktarın: `.proto`</span><span class="sxs-lookup"><span data-stu-id="4b4d7-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="4b4d7-153">Protobuf oluşturulan ileti `T?` özelliği için `int?`basit (örneğin, ) kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="4b4d7-154">Aşağıdaki tabloda, eşdeğer C# türüne sahip sarıcı türlerinin tam listesi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="4b4d7-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="4b4d7-155">C# tipi</span><span class="sxs-lookup"><span data-stu-id="4b4d7-155">C# type</span></span>   | <span data-ttu-id="4b4d7-156">İyi Bilinen Tip Sarıcı</span><span class="sxs-lookup"><span data-stu-id="4b4d7-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="4b4d7-157">İyi bilinen türleri `Timestamp` `Duration` ve sınıflar olarak .NET temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes.</span></span> <span data-ttu-id="4b4d7-158">C# 8 ve ötesinde, nullable başvuru türlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-158">In C# 8 and beyond, you can use nullable reference types.</span></span> <span data-ttu-id="4b4d7-159">Ancak, dönüşüm yaparken bu tür özellikleri geçersiz olup olmadığını kontrol `DateTimeOffset` etmek `TimeSpan`önemlidir.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-159">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="4b4d7-160">Ondalıklar</span><span class="sxs-lookup"><span data-stu-id="4b4d7-160">Decimals</span></span>

<span data-ttu-id="4b4d7-161">Protobuf yerel olarak .NET `decimal` türünü desteklemiyor, sadece `double` ve `float`.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-161">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="4b4d7-162">Protobuf projesinde, onu destekleyen diller ve çerçeveler `Decimal` için platform desteği yle, tanınmış türlere standart bir tür ekleme olasılığı hakkında devam eden bir tartışma vardır.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-162">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="4b4d7-163">Henüz hiçbir şey uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-163">Nothing has been implemented yet.</span></span>

<span data-ttu-id="4b4d7-164">.NET istemcileri ve sunucuları arasında `decimal` güvenli serileştirme için çalışacak türü temsil edecek bir ileti tanımı oluşturmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-164">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="4b4d7-165">Ancak diğer platformlardaki geliştiricilerin kullanılan formatı anlamaları ve bunun için kendi kullanımlarını uygulamaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-165">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="4b4d7-166">Protobuf için özel bir ondalık yazı oluşturma</span><span class="sxs-lookup"><span data-stu-id="4b4d7-166">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="4b4d7-167">Basit bir uygulama, bazı Google `Money` API'lerin alanı olmadan `currency` kullandığı standart dışı türe benzer olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-167">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

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

<span data-ttu-id="4b4d7-168">Alan, `nanos` `-0.999_999_999`değerlerinden `0.999_999_999` gelen değerleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-168">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="4b4d7-169">Örneğin, `decimal` değer `1.5m` . `{ units = 1, nanos = 500_000_000 }`</span><span class="sxs-lookup"><span data-stu-id="4b4d7-169">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="4b4d7-170">Bu nedenle, `nanos` bu örnekteki `sfixed32` alan, daha büyük değerlere `int32` göre daha verimli kodlayan türü kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-170">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="4b4d7-171">`units` Alan negatifse, `nanos` alan da negatif olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-171">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="4b4d7-172">Değerleri bayt dizeleri olarak `decimal` kodlamak için birden çok algoritma vardır, ancak bu iletiyi anlamak bunlardan daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-172">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="4b4d7-173">Değerler farklı platformlarda ensizlikten etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-173">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="4b4d7-174">Bu tür ve BCL `decimal` türü arasında dönüştürme C# aşağıdaki gibi uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="4b4d7-174">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

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
> <span data-ttu-id="4b4d7-175">Bu gibi özel ileti türlerini her kullandığınızda, `.proto`bunları 'deki açıklamalarla *belgelemeniz gerekir.*</span><span class="sxs-lookup"><span data-stu-id="4b4d7-175">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="4b4d7-176">Diğer geliştiriciler daha sonra kendi dil lerinde veya çerçevelerinde eşdeğer türe dönüştürme uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="4b4d7-176">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4b4d7-177">[Önceki](protobuf-messages.md)
>[Sonraki](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="4b4d7-177">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
