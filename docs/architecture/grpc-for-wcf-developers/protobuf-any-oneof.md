---
title: Değişken türleri için bir veya daha fazla alan için alanların prototip geliştiriciler için gRPC
description: İletilerle Ilgili değişken nesne türlerini temsil etmek için any türlerini ve oneof anahtar sözcüğünü nasıl kullanacağınızı öğrenin.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 9e730e96bfdb25ef6e07ee10967921408c6f2e84
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184283"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="e7aec-103">Değişken türleri için bir veya daha fazla alanın prototipini oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7aec-103">Protobuf Any and Oneof fields for variant types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="e7aec-104">WCF 'de dinamik özellik türlerini (türündeki `object`Özellikler) işlemek karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="e7aec-104">Handling dynamic property types (that is, properties of type `object`) in WCF is complicated.</span></span> <span data-ttu-id="e7aec-105">Serileştiriciler belirtilmelidir, [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) öznitelikleri sağlanmalı ve bu şekilde devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="e7aec-105">Serializers must be specified, [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes must be provided, and so on.</span></span>

<span data-ttu-id="e7aec-106">Prototip, birden fazla türden olabilecek değerlerle ilgilenmede iki basit seçenek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7aec-106">Protobuf provides two simpler options for dealing with values that may be of more than one type.</span></span> <span data-ttu-id="e7aec-107">Tür bilinen prototipsiz ileti türlerini temsil edebilir, `oneof` ancak anahtar sözcüğü belirli bir ileti içinde bir alan aralığının yalnızca bir tane ayarlanabilir olmasını belirtmenize izin verir. `Any`</span><span class="sxs-lookup"><span data-stu-id="e7aec-107">The `Any` type can represent any known Protobuf message type, while the `oneof` keyword allows you to specify that only one of a range of fields can be set in any given message.</span></span>

## <a name="any"></a><span data-ttu-id="e7aec-108">Any</span><span class="sxs-lookup"><span data-stu-id="e7aec-108">Any</span></span>

<span data-ttu-id="e7aec-109">`Any`, prototipteki "iyi bilinen türlerden" biridir: desteklenen tüm dillerdeki uygulamalarla birlikte yararlı ve yeniden kullanılabilir ileti türleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="e7aec-109">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="e7aec-110">`Any` Türü kullanmak için `google/protobuf/any.proto` tanımı içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7aec-110">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

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

<span data-ttu-id="e7aec-111">C# Kodunda, `Any` sınıfı alanı ayarlamaya, iletiyi ayıklamanıza ve türü denetlemeye yönelik yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7aec-111">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

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

<span data-ttu-id="e7aec-112">Oluşturulan her türdeki `Any` statikalan,alantürleriniçözmekiçinprotoarabelleğiiçyansıma`Descriptor` kodu tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e7aec-112">The `Descriptor` static field on each generated type is used by Protobuf's internal reflection code to resolve `Any` field types.</span></span> <span data-ttu-id="e7aec-113">Aynı zamanda bir `TryUnpack<T>` yöntemi de vardır, ancak bu, başarısız olduğunda `T` bile başlatılmamış bir örneğini oluşturur, bu sayede `Is` yöntemi yukarıda gösterildiği gibi kullanmak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="e7aec-113">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails, so it's better to use the `Is` method as shown above.</span></span>

## <a name="oneof"></a><span data-ttu-id="e7aec-114">Oneof</span><span class="sxs-lookup"><span data-stu-id="e7aec-114">Oneof</span></span>

<span data-ttu-id="e7aec-115">Oneof alanları bir dil özelliğidir: `oneof` anahtar sözcüğü, ileti sınıfını oluşturduğunda derleyici tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="e7aec-115">Oneof fields are a language feature: the `oneof` keyword is handled by the compiler when it generates the message class.</span></span> <span data-ttu-id="e7aec-116">İletiyi belirtmek için kullanmak `oneof` şöyle görünebilir: `ChangeNotification`</span><span class="sxs-lookup"><span data-stu-id="e7aec-116">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

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

<span data-ttu-id="e7aec-117">`oneof` Küme içindeki alanlar, genel ileti bildiriminde benzersiz alan numaralarına sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7aec-117">Fields within the `oneof` set must have unique field numbers within the overall message declaration.</span></span>

<span data-ttu-id="e7aec-118">Kullandığınızda `oneof`, oluşturulan C# kod, alanların hangisinin ayarlandığını belirten bir sabit listesi içerir.</span><span class="sxs-lookup"><span data-stu-id="e7aec-118">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="e7aec-119">Hangi alanın ayarlandığını bulmak için sabit listesini test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7aec-119">You can test the enum to find which field is set.</span></span> <span data-ttu-id="e7aec-120">Ayarlı olmayan alanlar, özel `null` durum oluşturmak yerine varsayılan değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="e7aec-120">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

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

<span data-ttu-id="e7aec-121">Bir `oneof` kümesinin parçası olan herhangi bir alanın ayarlanması, belirlenen diğer alanları otomatik olarak temizler.</span><span class="sxs-lookup"><span data-stu-id="e7aec-121">Setting any field that is part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="e7aec-122">`repeated` İle`oneof`kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e7aec-122">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="e7aec-123">Bunun yerine, bu sınırlamaya geçici bir çözüm için yinelenen alan veya `oneof` küme ile iç içe geçmiş bir ileti oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7aec-123">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e7aec-124">[Önceki](protobuf-reserved.md)
>[İleri](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="e7aec-124">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
