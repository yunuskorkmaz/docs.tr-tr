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
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Değişken türleri için bir veya daha fazla alanın prototipini oluşturma

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

WCF 'de dinamik özellik türlerini (türündeki `object`Özellikler) işlemek karmaşıktır. Serileştiriciler belirtilmelidir, [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) öznitelikleri sağlanmalı ve bu şekilde devam etmelidir.

Prototip, birden fazla türden olabilecek değerlerle ilgilenmede iki basit seçenek sağlar. Tür bilinen prototipsiz ileti türlerini temsil edebilir, `oneof` ancak anahtar sözcüğü belirli bir ileti içinde bir alan aralığının yalnızca bir tane ayarlanabilir olmasını belirtmenize izin verir. `Any`

## <a name="any"></a>Any

`Any`, prototipteki "iyi bilinen türlerden" biridir: desteklenen tüm dillerdeki uygulamalarla birlikte yararlı ve yeniden kullanılabilir ileti türleri koleksiyonu. `Any` Türü kullanmak için `google/protobuf/any.proto` tanımı içeri aktarmanız gerekir.

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

C# Kodunda, `Any` sınıfı alanı ayarlamaya, iletiyi ayıklamanıza ve türü denetlemeye yönelik yöntemler sağlar.

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

Oluşturulan her türdeki `Any` statikalan,alantürleriniçözmekiçinprotoarabelleğiiçyansıma`Descriptor` kodu tarafından kullanılır. Aynı zamanda bir `TryUnpack<T>` yöntemi de vardır, ancak bu, başarısız olduğunda `T` bile başlatılmamış bir örneğini oluşturur, bu sayede `Is` yöntemi yukarıda gösterildiği gibi kullanmak daha iyidir.

## <a name="oneof"></a>Oneof

Oneof alanları bir dil özelliğidir: `oneof` anahtar sözcüğü, ileti sınıfını oluşturduğunda derleyici tarafından işlenir. İletiyi belirtmek için kullanmak `oneof` şöyle görünebilir: `ChangeNotification`

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

`oneof` Küme içindeki alanlar, genel ileti bildiriminde benzersiz alan numaralarına sahip olmalıdır.

Kullandığınızda `oneof`, oluşturulan C# kod, alanların hangisinin ayarlandığını belirten bir sabit listesi içerir. Hangi alanın ayarlandığını bulmak için sabit listesini test edebilirsiniz. Ayarlı olmayan alanlar, özel `null` durum oluşturmak yerine varsayılan değer döndürür.

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

Bir `oneof` kümesinin parçası olan herhangi bir alanın ayarlanması, belirlenen diğer alanları otomatik olarak temizler. `repeated` İle`oneof`kullanamazsınız. Bunun yerine, bu sınırlamaya geçici bir çözüm için yinelenen alan veya `oneof` küme ile iç içe geçmiş bir ileti oluşturabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](protobuf-reserved.md)
>[İleri](protobuf-enums.md)
