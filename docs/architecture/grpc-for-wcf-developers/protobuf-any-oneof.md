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
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Değişken türleri için bir veya daha fazla alanın prototipini oluşturma

WCF 'de dinamik özellik türlerini (`object`türündeki Özellikler) işlemek karmaşıktır. Serileştiriciler belirtilmelidir, [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) öznitelikleri sağlanmalı ve bu şekilde devam etmelidir.

Prototip, birden fazla türden olabilecek değerlerle ilgilenmede iki basit seçenek sağlar. `Any` türü bilinen Prototipsiz ileti türlerini temsil edebilir, ancak `oneof` anahtar sözcüğü belirli bir ileti içinde yalnızca bir alan aralığı ayarlayabilmesinin izin verdiği.

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

Oluşturulan her türdeki `Descriptor` statik alanı, `Any` alanı türlerini çözümlemek için prototipte iç yansıma kodu tarafından kullanılır. Ayrıca bir `TryUnpack<T>` yöntemi vardır ancak bu, başarısız olsa bile başlatılmamış bir `T` örneğini oluşturur, bu nedenle `Is` yönteminin yukarıda gösterildiği gibi kullanılması daha iyidir.

## <a name="oneof"></a>Oneof

Oneof alanları bir dil özelliğidir: `oneof` anahtar sözcüğü, ileti sınıfını oluşturduğunda derleyici tarafından işlenir. `ChangeNotification` iletisini belirtmek için `oneof` kullanmak şöyle görünebilir:

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

Bir `oneof` kümesinin parçası olan herhangi bir alanı ayarlamak, küme içindeki diğer alanları otomatik olarak temizler. `oneof``repeated` kullanamazsınız. Bunun yerine, bu sınırlamaya geçici bir çözüm olarak, yinelenen alanla veya `oneof` ayarlanmış olarak iç içe geçmiş bir ileti oluşturabilirsiniz.

>[!div class="step-by-step"]
>[Önceki](protobuf-reserved.md)
>[İleri](protobuf-enums.md)
