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
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="1f83e-103">Protobuf skaler veri türleri</span><span class="sxs-lookup"><span data-stu-id="1f83e-103">Protobuf scalar data types</span></span>

<span data-ttu-id="1f83e-104">Protokol arabelleği (Protobuffer), yerel skaler değer türlerinin bir aralığını destekler.</span><span class="sxs-lookup"><span data-stu-id="1f83e-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="1f83e-105">Aşağıdaki tabloda bunların hepsi eşdeğer C# türü ile listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="1f83e-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="1f83e-106">Prototip türü</span><span class="sxs-lookup"><span data-stu-id="1f83e-106">Protobuf type</span></span> | <span data-ttu-id="1f83e-107">C# türü</span><span class="sxs-lookup"><span data-stu-id="1f83e-107">C# type</span></span>      | <span data-ttu-id="1f83e-108">Notlar</span><span class="sxs-lookup"><span data-stu-id="1f83e-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="1f83e-109">1</span><span class="sxs-lookup"><span data-stu-id="1f83e-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="1f83e-110">1</span><span class="sxs-lookup"><span data-stu-id="1f83e-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="1f83e-111">1</span><span class="sxs-lookup"><span data-stu-id="1f83e-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="1f83e-112">1</span><span class="sxs-lookup"><span data-stu-id="1f83e-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="1f83e-113">2</span><span class="sxs-lookup"><span data-stu-id="1f83e-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="1f83e-114">2</span><span class="sxs-lookup"><span data-stu-id="1f83e-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="1f83e-115">2</span><span class="sxs-lookup"><span data-stu-id="1f83e-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="1f83e-116">2</span><span class="sxs-lookup"><span data-stu-id="1f83e-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="1f83e-117">3</span><span class="sxs-lookup"><span data-stu-id="1f83e-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="1f83e-118">4</span><span class="sxs-lookup"><span data-stu-id="1f83e-118">4</span></span>     |

<span data-ttu-id="1f83e-119">Notlar:</span><span class="sxs-lookup"><span data-stu-id="1f83e-119">Notes:</span></span>

1. <span data-ttu-id="1f83e-120">Ve için standart kodlama `int32` , `int64` imzalanmış değerlerle çalışırken verimsiz bir değer.</span><span class="sxs-lookup"><span data-stu-id="1f83e-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="1f83e-121">Alanınız büyük olasılıkla negatif sayı içeriyorsa, `sint32` `sint64` bunun yerine veya kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f83e-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="1f83e-122">Bu türler `int` sırasıyla C# ve türleriyle eşlenir `long` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="1f83e-123">`fixed`Alanlar, her zaman değerin ne kadar olduğunu bağımsız olarak aynı sayıda bayt kullanır.</span><span class="sxs-lookup"><span data-stu-id="1f83e-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="1f83e-124">Bu davranış, daha büyük değerler için serileştirme ve seri durumdan çıkarma sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f83e-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="1f83e-125">Prototip dizeler UTF-8 (veya 7 bit ASCII) kodlardır.</span><span class="sxs-lookup"><span data-stu-id="1f83e-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="1f83e-126">Kodlanan uzunluk 2<sup>32</sup>' den büyük olamaz.</span><span class="sxs-lookup"><span data-stu-id="1f83e-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="1f83e-127">Prototip çalışma zamanı, `ByteString` C# dizileriyle ve bu dizilere kolayca eşleyen bir tür sağlar `byte[]` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="1f83e-128">Diğer .NET ilkel türleri</span><span class="sxs-lookup"><span data-stu-id="1f83e-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="1f83e-129">Tarihler ve saatler</span><span class="sxs-lookup"><span data-stu-id="1f83e-129">Dates and times</span></span>

<span data-ttu-id="1f83e-130">Yerel skaler türler tarih ve saat değerleri için, C# ' nin, <xref:System.DateTimeOffset> <xref:System.DateTime> ve ile eşdeğerdir <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="1f83e-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="1f83e-131">Bu türleri, bazı Google "tanınmış türler" uzantılarını kullanarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f83e-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="1f83e-132">Bu uzantılar desteklenen platformlar genelinde karmaşık alan türleri için kod oluşturma ve çalışma zamanı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f83e-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span>

<span data-ttu-id="1f83e-133">Aşağıdaki tabloda tarih ve saat türleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1f83e-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="1f83e-134">C# türü</span><span class="sxs-lookup"><span data-stu-id="1f83e-134">C# type</span></span> | <span data-ttu-id="1f83e-135">Prototip iyi bilinen tür</span><span class="sxs-lookup"><span data-stu-id="1f83e-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="1f83e-136">C# sınıfındaki oluşturulan Özellikler .NET tarih ve saat türleri değildir.</span><span class="sxs-lookup"><span data-stu-id="1f83e-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="1f83e-137">Özellikler, `Timestamp` `Duration` ad alanındaki ve sınıflarını kullanır `Google.Protobuf.WellKnownTypes` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="1f83e-138">Bu sınıflar,, ve ' a dönüştürmek için yöntemler sağlar `DateTimeOffset` `DateTime` `TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="1f83e-139">`Timestamp`Tür UTC saatleriyle birlikte çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1f83e-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="1f83e-140">`DateTimeOffset` değerler her zaman sıfır bir uzaklığa sahiptir ve `DateTime.Kind` özellik her zaman olur `DateTimeKind.Utc` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="1f83e-141">System. Guid</span><span class="sxs-lookup"><span data-stu-id="1f83e-141">System.Guid</span></span>

<span data-ttu-id="1f83e-142">Protoarabellek, <xref:System.Guid> diğer platformlarda olduğu bilinen türü doğrudan desteklemez `UUID` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="1f83e-143">Bunun için iyi bilinen bir tür yoktur.</span><span class="sxs-lookup"><span data-stu-id="1f83e-143">There's no well-known type for it.</span></span>

<span data-ttu-id="1f83e-144">En iyi yaklaşım, `Guid` `string` Standart `8-4-4-4-12` onaltılı biçimi (örneğin,) kullanarak değerleri bir alan olarak idare kullanmaktır `45a9fda3-bd01-47a9-8460-c1cd7484b0b3` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="1f83e-145">Tüm diller ve platformlar bu biçimi ayrıştırabilirler.</span><span class="sxs-lookup"><span data-stu-id="1f83e-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="1f83e-146">`bytes`Değerler için bir alan kullanmayın `Guid` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="1f83e-147">([Vikipedi Definition](https://en.wikipedia.org/wiki/Endianness)) *ile Ilgili sorunlar* , prototip, Java gibi diğer platformlarla etkileşime girildiğinde Erratic davranışa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f83e-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="1f83e-148">Null atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="1f83e-148">Nullable types</span></span>

<span data-ttu-id="1f83e-149">C# için prototip kod oluşturma, gibi yerel türleri kullanır `int` `int32` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="1f83e-150">Bu nedenle değerler her zaman dahil edilir ve null olamaz.</span><span class="sxs-lookup"><span data-stu-id="1f83e-150">So the values are always included and can't be null.</span></span>

<span data-ttu-id="1f83e-151">C# kodunuzda kullanılması gibi açık null gerektiren değerler için `int?` , prototipli "Iyi bilinen türler", Nullable C# türlerine derlenen sarmalayıcıları içerir.</span><span class="sxs-lookup"><span data-stu-id="1f83e-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="1f83e-152">Bunları kullanmak için, dosyanıza aşağıdaki gibi içeri aktarın `wrappers.proto` `.proto` :</span><span class="sxs-lookup"><span data-stu-id="1f83e-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="1f83e-153">Prototip, `T?` oluşturulan ileti özelliği için basit (örneğin, `int?` ) kullanır.</span><span class="sxs-lookup"><span data-stu-id="1f83e-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="1f83e-154">Aşağıdaki tabloda, eşdeğer C# türüyle sarmalayıcı türlerinin tüm listesi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1f83e-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="1f83e-155">C# türü</span><span class="sxs-lookup"><span data-stu-id="1f83e-155">C# type</span></span>   | <span data-ttu-id="1f83e-156">İyi bilinen tür sarmalayıcısı</span><span class="sxs-lookup"><span data-stu-id="1f83e-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="1f83e-157">İyi bilinen türler, `Timestamp` `Duration` .net olarak sınıflar olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="1f83e-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes.</span></span> <span data-ttu-id="1f83e-158">C# 8 ve ötesinde, null yapılabilir başvuru türlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f83e-158">In C# 8 and beyond, you can use nullable reference types.</span></span> <span data-ttu-id="1f83e-159">Ancak, veya ' ye dönüştürürken bu türlerin özelliklerinde null olup olmadığını denetlemek önemlidir `DateTimeOffset` `TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-159">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="1f83e-160">Ondalıklar</span><span class="sxs-lookup"><span data-stu-id="1f83e-160">Decimals</span></span>

<span data-ttu-id="1f83e-161">Prototip `decimal` , yalnızca ve .NET türünü yerel olarak desteklemez `double` `float` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-161">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="1f83e-162">Prototip projesinde `Decimal` , iyi bilinen türlere standart bir tür ekleme olasılığa ve bunu destekleyen diller ve çerçeveler için platform desteğiyle bir standart tür ekleme olasılığa ilişkin devam eden bir tartışma vardır.</span><span class="sxs-lookup"><span data-stu-id="1f83e-162">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="1f83e-163">Henüz hiçbir şey uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="1f83e-163">Nothing has been implemented yet.</span></span>

<span data-ttu-id="1f83e-164">`decimal`.NET istemcileri ve sunucuları arasında güvenli serileştirme için çalışacak olan türü temsil eden bir ileti tanımı oluşturmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="1f83e-164">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="1f83e-165">Ancak diğer platformlardaki geliştiricilerin, kullanılmakta olan biçimi anlaması ve onun için kendi işlemesini uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f83e-165">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="1f83e-166">Protoarabellek için özel bir ondalık tür oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f83e-166">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="1f83e-167">Basit bir uygulama, `Money` bazı Google API 'lerinin kullandığı standart olmayan türe benzer olabilir `currency` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-167">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

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

<span data-ttu-id="1f83e-168">`nanos`Alan, öğesinden değerlerini temsil `0.999_999_999` eder `-0.999_999_999` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-168">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="1f83e-169">Örneğin, `decimal` değer `1.5m` olarak temsil edilir `{ units = 1, nanos = 500_000_000 }` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-169">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="1f83e-170">Bu, `nanos` Bu örnekteki alanın, `sfixed32` daha büyük değerler için daha verimli bir şekilde kodlama türünü kullanmadığına neden olur `int32` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-170">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="1f83e-171">`units`Alan negatifse `nanos` alanın de negatif olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f83e-171">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="1f83e-172">Değerleri bayt dizeleri olarak kodlamak için birden çok farklı algoritma mevcuttur `decimal` , ancak bu iletinin bunlardan herhangi birinin anlaşılması kolaylaşır.</span><span class="sxs-lookup"><span data-stu-id="1f83e-172">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="1f83e-173">Değerler farklı platformlarda bitime tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="1f83e-173">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="1f83e-174">Bu tür ile BCL türü arasında dönüştürme `decimal` C# ' de şöyle uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="1f83e-174">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

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
> <span data-ttu-id="1f83e-175">Bu gibi özel ileti türlerini kullandığınızda, bunları içindeki yorumlarla belgeetmeniz *gerekir* `.proto` .</span><span class="sxs-lookup"><span data-stu-id="1f83e-175">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="1f83e-176">Diğer geliştiriciler daha sonra kendi dillerinde veya çerçevesinde eşdeğer türe ve dönüşümünü uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="1f83e-176">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1f83e-177">[Önceki](protobuf-messages.md) 
> [Sonraki](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="1f83e-177">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
