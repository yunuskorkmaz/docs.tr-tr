---
title: Değişken türleri için bir veya daha fazla alan için alanların prototip geliştiriciler için gRPC
description: İletilerle Ilgili değişken nesne türlerini temsil etmek için any türlerini ve oneof anahtar sözcüğünü nasıl kullanacağınızı öğrenin.
ms.date: 09/09/2019
ms.openlocfilehash: af3ba22c238aa80a8c6119f62d5d8914770cad68
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971611"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="e9b1b-103">Değişken türleri için bir veya daha fazla alanın prototipini oluşturma</span><span class="sxs-lookup"><span data-stu-id="e9b1b-103">Protobuf Any and Oneof fields for variant types</span></span>

<span data-ttu-id="e9b1b-104">WCF 'de dinamik özellik türlerini (`object`türündeki Özellikler) işlemek karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-104">Handling dynamic property types (that is, properties of type `object`) in WCF is complicated.</span></span> <span data-ttu-id="e9b1b-105">Serileştiriciler belirtilmelidir, [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) öznitelikleri sağlanmalı ve bu şekilde devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-105">Serializers must be specified, [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes must be provided, and so on.</span></span>

<span data-ttu-id="e9b1b-106">Prototip, birden fazla türden olabilecek değerlerle ilgilenmede iki basit seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-106">Protobuf provides two simpler options for dealing with values that may be of more than one type.</span></span> <span data-ttu-id="e9b1b-107">`Any` türü bilinen Prototipsiz ileti türlerini temsil edebilir, ancak `oneof` anahtar sözcüğü belirli bir ileti içinde yalnızca bir alan aralığı ayarlayabilmesinin izin verdiği.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-107">The `Any` type can represent any known Protobuf message type, while the `oneof` keyword allows you to specify that only one of a range of fields can be set in any given message.</span></span>

## <a name="any"></a><span data-ttu-id="e9b1b-108">Tümü</span><span class="sxs-lookup"><span data-stu-id="e9b1b-108">Any</span></span>

<span data-ttu-id="e9b1b-109">`Any`, prototipteki "iyi bilinen türlerden" biridir: desteklenen tüm dillerdeki uygulamalarla birlikte yararlı ve yeniden kullanılabilir ileti türleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-109">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="e9b1b-110">`Any` türünü kullanmak için `google/protobuf/any.proto` tanımını içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-110">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

```protobuf
syntax "proto3"

import "google/protobuf/any.proto"

message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
    int32 id = 1;
    google.protobuf.Any instrument = 2;
}
```

<span data-ttu-id="e9b1b-111">C# Kodda, `Any` sınıfı alanı ayarlamaya, iletiyi ayıklamanıza ve türü denetlemeye yönelik yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-111">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    if (change.Instrument.Is(Stock.Descriptor))
    {
        FormatStock(change.Instrument.Unpack<Stock>());
    }
    else if (change.Instrument.Is(Currency.Descriptor))
    {
        FormatCurrency(change.Instrument.Unpack<Currency>());
    }
    else
    {
        throw new ArgumentException("Unknown instrument type");
    }
}
```

<span data-ttu-id="e9b1b-112">Oluşturulan her türdeki `Descriptor` statik alanı, `Any` alanı türlerini çözümlemek için prototipte iç yansıma kodu tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-112">The `Descriptor` static field on each generated type is used by Protobuf's internal reflection code to resolve `Any` field types.</span></span> <span data-ttu-id="e9b1b-113">Ayrıca bir `TryUnpack<T>` yöntemi vardır ancak bu, başarısız olsa bile başlatılmamış bir `T` örneğini oluşturur, bu nedenle `Is` yönteminin yukarıda gösterildiği gibi kullanılması daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-113">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails, so it's better to use the `Is` method as shown above.</span></span>

## <a name="oneof"></a><span data-ttu-id="e9b1b-114">Oneof</span><span class="sxs-lookup"><span data-stu-id="e9b1b-114">Oneof</span></span>

<span data-ttu-id="e9b1b-115">Oneof alanları bir dil özelliğidir: `oneof` anahtar sözcüğü, ileti sınıfını oluşturduğunda derleyici tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-115">Oneof fields are a language feature: the `oneof` keyword is handled by the compiler when it generates the message class.</span></span> <span data-ttu-id="e9b1b-116">`ChangeNotification` iletisini belirtmek için `oneof` kullanmak şöyle görünebilir:</span><span class="sxs-lookup"><span data-stu-id="e9b1b-116">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

```protobuf
message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
  int32 id = 1;
  oneof instrument {
    Stock stock = 2;
    Currency currency = 3;
  }
}
```

<span data-ttu-id="e9b1b-117">`oneof` kümesi içindeki alanlar, genel ileti bildiriminde benzersiz alan numaralarına sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-117">Fields within the `oneof` set must have unique field numbers within the overall message declaration.</span></span>

<span data-ttu-id="e9b1b-118">`oneof`kullandığınızda, oluşturulan C# kod, alanların hangisinin ayarlandığını belirten bir sabit listesi içerir.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-118">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="e9b1b-119">Hangi alanın ayarlandığını bulmak için sabit listesini test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-119">You can test the enum to find which field is set.</span></span> <span data-ttu-id="e9b1b-120">Ayarlı olmayan alanlar, bir özel durum oluşturmak yerine `null` veya varsayılan değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-120">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    switch (change.InstrumentCase)
    {
        case ChangeNotification.InstrumentOneofCase.None:
            return;
        case ChangeNotification.InstrumentOneofCase.Stock:
            FormatStock(change.Stock);
            break;
        case ChangeNotification.InstrumentOneofCase.Currency:
            FormatCurrency(change.Currency);
            break;
        default:
            throw new ArgumentException("Unknown instrument type");
    }
}
```

<span data-ttu-id="e9b1b-121">Bir `oneof` kümesinin parçası olan herhangi bir alanı ayarlamak, küme içindeki diğer alanları otomatik olarak temizler.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-121">Setting any field that is part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="e9b1b-122">`oneof``repeated` kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-122">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="e9b1b-123">Bunun yerine, bu sınırlamaya geçici bir çözüm olarak, yinelenen alanla veya `oneof` ayarlanmış olarak iç içe geçmiş bir ileti oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9b1b-123">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e9b1b-124">[Önceki](protobuf-reserved.md)
>[İleri](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="e9b1b-124">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
