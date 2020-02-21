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
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Değişken türleri için bir veya daha fazla alanın prototipini oluşturma

Dinamik özellik türlerini (diğer bir deyişle, `object`türündeki Özellikler) Windows Communication Foundation (WCF) içinde işlemek karmaşıktır. Örneğin, serileştiriciler belirtmeniz ve [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) öznitelikleri sağlamanız gerekir.

Protokol arabelleği (Protobuffer), birden fazla türden olabilecek değerlerle ilgilenmede iki basit seçenek sağlar. `Any` türü bilinen Prototipsiz ileti türlerini temsil edebilir. Ve `oneof` anahtar sözcüğünü kullanarak herhangi bir ileti için yalnızca bir alan aralığının ayarlayabelirtebilirsiniz.

## <a name="any"></a>Tümü

`Any`, prototipteki "iyi bilinen türlerden" biridir: desteklenen tüm dillerdeki uygulamalarla birlikte yararlı ve yeniden kullanılabilir ileti türleri koleksiyonu. `Any` türünü kullanmak için `google/protobuf/any.proto` tanımını içeri aktarmanız gerekir.

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

C# Kodda, `Any` sınıfı alanı ayarlamaya, iletiyi ayıklamanıza ve türü denetlemeye yönelik yöntemler sağlar.

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

Prototipte iç yansıma kodu, `Any` alanı türlerini çözümlemek için her oluşturulan türdeki `Descriptor` statik alanını kullanır. Ayrıca bir `TryUnpack<T>` yöntemi vardır ancak bu, başarısız olsa bile başlatılmamış bir `T` örneği oluşturur. Daha önce gösterildiği gibi `Is` yönteminin kullanılması daha iyidir.

## <a name="oneof"></a>Oneof

Oneof alanları bir dil özelliğidir: derleyici, ileti sınıfını oluşturduğunda `oneof` anahtar sözcüğünü işler. `ChangeNotification` iletisini belirtmek için `oneof` kullanmak şöyle görünebilir:

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

`oneof` kümesi içindeki alanlar, genel ileti bildiriminde benzersiz alan numaralarına sahip olmalıdır.

`oneof`kullandığınızda, oluşturulan C# kod, alanların hangisinin ayarlandığını belirten bir sabit listesi içerir. Hangi alanın ayarlandığını bulmak için sabit listesini test edebilirsiniz. Ayarlı olmayan alanlar, bir özel durum oluşturmak yerine `null` veya varsayılan değer döndürür.

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

Bir `oneof` kümesinin parçası olan herhangi bir alanın ayarlanması, belirlenen diğer alanları otomatik olarak temizler. `oneof``repeated` kullanamazsınız. Bunun yerine, bu sınırlamaya geçici bir çözüm olarak, yinelenen alanla veya `oneof` ayarlanmış olarak iç içe geçmiş bir ileti oluşturabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](protobuf-reserved.md)
>[İleri](protobuf-enums.md)
