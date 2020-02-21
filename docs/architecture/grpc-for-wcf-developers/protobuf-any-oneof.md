---
title: Değişken türleri için bir veya daha fazla alan için alanların prototip geliştiriciler için gRPC
description: İletilerle Ilgili değişken nesne türlerini temsil etmek için any türlerini ve oneof anahtar sözcüğünü nasıl kullanacağınızı öğrenin.
ms.date: 09/09/2019
ms.openlocfilehash: 6fe7acbd1ec35289f7ad6f3acee8509ab934619d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543202"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="fbf89-103">Değişken türleri için bir veya daha fazla alanın prototipini oluşturma</span><span class="sxs-lookup"><span data-stu-id="fbf89-103">Protobuf Any and Oneof fields for variant types</span></span>

<span data-ttu-id="fbf89-104">Dinamik özellik türlerini (diğer bir deyişle, `object`türündeki Özellikler) Windows Communication Foundation (WCF) içinde işlemek karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="fbf89-104">Handling dynamic property types (that is, properties of type `object`) in Windows Communication Foundation (WCF) is complicated.</span></span> <span data-ttu-id="fbf89-105">Örneğin, serileştiriciler belirtmeniz ve [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) öznitelikleri sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbf89-105">For example, you must specify serializers and provide [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes.</span></span>

<span data-ttu-id="fbf89-106">Protokol arabelleği (Protobuffer), birden fazla türden olabilecek değerlerle ilgilenmede iki basit seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbf89-106">Protocol Buffer (Protobuf) provides two simpler options for dealing with values that might be of more than one type.</span></span> <span data-ttu-id="fbf89-107">`Any` türü bilinen Prototipsiz ileti türlerini temsil edebilir.</span><span class="sxs-lookup"><span data-stu-id="fbf89-107">The `Any` type can represent any known Protobuf message type.</span></span> <span data-ttu-id="fbf89-108">Ve `oneof` anahtar sözcüğünü kullanarak herhangi bir ileti için yalnızca bir alan aralığının ayarlayabelirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbf89-108">And you can use the `oneof` keyword to specify that only one of a range of fields can be set in any message.</span></span>

## <a name="any"></a><span data-ttu-id="fbf89-109">Tümü</span><span class="sxs-lookup"><span data-stu-id="fbf89-109">Any</span></span>

<span data-ttu-id="fbf89-110">`Any`, prototipteki "iyi bilinen türlerden" biridir: desteklenen tüm dillerdeki uygulamalarla birlikte yararlı ve yeniden kullanılabilir ileti türleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="fbf89-110">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="fbf89-111">`Any` türünü kullanmak için `google/protobuf/any.proto` tanımını içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fbf89-111">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

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

<span data-ttu-id="fbf89-112">C# Kodda, `Any` sınıfı alanı ayarlamaya, iletiyi ayıklamanıza ve türü denetlemeye yönelik yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbf89-112">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

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

<span data-ttu-id="fbf89-113">Prototipte iç yansıma kodu, `Any` alanı türlerini çözümlemek için her oluşturulan türdeki `Descriptor` statik alanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="fbf89-113">Protobuf's internal reflection code uses the `Descriptor` static field on each generated type to resolve `Any` field types.</span></span> <span data-ttu-id="fbf89-114">Ayrıca bir `TryUnpack<T>` yöntemi vardır ancak bu, başarısız olsa bile başlatılmamış bir `T` örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fbf89-114">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails.</span></span> <span data-ttu-id="fbf89-115">Daha önce gösterildiği gibi `Is` yönteminin kullanılması daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="fbf89-115">It's better to use the `Is` method as shown earlier.</span></span>

## <a name="oneof"></a><span data-ttu-id="fbf89-116">Oneof</span><span class="sxs-lookup"><span data-stu-id="fbf89-116">Oneof</span></span>

<span data-ttu-id="fbf89-117">Oneof alanları bir dil özelliğidir: derleyici, ileti sınıfını oluşturduğunda `oneof` anahtar sözcüğünü işler.</span><span class="sxs-lookup"><span data-stu-id="fbf89-117">Oneof fields are a language feature: the compiler handles the `oneof` keyword when it generates the message class.</span></span> <span data-ttu-id="fbf89-118">`ChangeNotification` iletisini belirtmek için `oneof` kullanmak şöyle görünebilir:</span><span class="sxs-lookup"><span data-stu-id="fbf89-118">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

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

<span data-ttu-id="fbf89-119">`oneof` kümesi içindeki alanlar, genel ileti bildiriminde benzersiz alan numaralarına sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fbf89-119">Fields within the `oneof` set must have unique field numbers in the overall message declaration.</span></span>

<span data-ttu-id="fbf89-120">`oneof`kullandığınızda, oluşturulan C# kod, alanların hangisinin ayarlandığını belirten bir sabit listesi içerir.</span><span class="sxs-lookup"><span data-stu-id="fbf89-120">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="fbf89-121">Hangi alanın ayarlandığını bulmak için sabit listesini test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbf89-121">You can test the enum to find which field is set.</span></span> <span data-ttu-id="fbf89-122">Ayarlı olmayan alanlar, bir özel durum oluşturmak yerine `null` veya varsayılan değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="fbf89-122">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

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

<span data-ttu-id="fbf89-123">Bir `oneof` kümesinin parçası olan herhangi bir alanın ayarlanması, belirlenen diğer alanları otomatik olarak temizler.</span><span class="sxs-lookup"><span data-stu-id="fbf89-123">Setting any field that's part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="fbf89-124">`oneof``repeated` kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="fbf89-124">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="fbf89-125">Bunun yerine, bu sınırlamaya geçici bir çözüm olarak, yinelenen alanla veya `oneof` ayarlanmış olarak iç içe geçmiş bir ileti oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbf89-125">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fbf89-126">[Önceki](protobuf-reserved.md)
>[İleri](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="fbf89-126">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
