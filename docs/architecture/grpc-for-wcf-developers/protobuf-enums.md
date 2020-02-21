---
title: Prototipsiz numaralandırmalar-WCF geliştiricileri için gRPC
description: Prototipte numaralandırmalar bildirme ve kullanma hakkında bilgi edinin.
ms.date: 09/09/2019
ms.openlocfilehash: 01cf4a4e5e0eda1e7ddff2a6780119fcb3120dad
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543150"
---
# <a name="protobuf-enumerations"></a>Protobuf sabit listeleri

Prototip, numaralandırma türlerini destekler. Bu desteği, bir `Oneof` alanının türünü belirlemekte bir sabit listesinin kullanıldığı önceki bölümde gördünüz. Kendi numaralandırma türlerinizi tanımlayabilir ve Protoda bunları sabit listesi türleri için C# derler. 

Prototip ' i çeşitli dillerle birlikte kullanabilmeniz için, numaralandırmalar için adlandırma kuralları C# kurallardan farklıdır. Ancak, kod Oluşturucu adları geleneksel C# harfe dönüştürür. Alan adının Pascal-case eşdeğerini, numaralandırma adıyla başlıyorsa, kaldırılır.

Örneğin, aşağıdaki prototip numaralandırmasında, alanlar `ACCOUNT_STATUS`ön ekine sahiptir. Bu ön ek, `AccountStatus`Pascal-case numaralandırma adına eşdeğerdir.

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

Oluşturucu aşağıdaki koda denk C# bir sabit listesi oluşturur:

```csharp
public enum AccountStatus
{
    Unknown = 0,
    Pending = 1,
    Active = 2,
    Suspended = 3,
    Closed = 4
}
```

Prototip numaralandırma tanımlarının ilk alanları olarak sıfır sabiti *olmalıdır* . İçinde C#olduğu gibi, aynı değere sahip birden fazla alan bildirebilirsiniz. Ancak, bu seçeneği numaralandırmasında `allow_alias` seçeneğini kullanarak açıkça etkinleştirmeniz gerekir:

```protobuf
enum AccountStatus {
  option allow_alias = true;
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
  ACCOUNT_STATUS_CANCELLED = 4;
}
```

Numaralandırmalar `.proto` bir dosyanın en üst düzeyinde ya da bir ileti tanımı içinde iç içe bildirebilirsiniz. İç içe geçmiş mesajlar gibi iç içe yerleştirilmiş numaralandırmalar, oluşturulan ileti sınıfındaki `.Types` statik sınıf içinde bildirilecektir.

[[Flags]](xref:System.FlagsAttribute) özniteliğini prototipsel olarak üretilen bir numaralandırmaya uygulamanın bir yolu yoktur ve protoarabellek, bit düzeyinde sabit listesi birleşimlerini anlamaz. Aşağıdaki örneğe bakın:

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region available_in = 1;
}
```

`product.AvailableIn` `Region.NorthAmerica | Region.SouthAmerica`olarak ayarlarsanız, `3`tamsayı değer olarak serileştirilir. Bir istemci veya sunucu değeri seri durumdan çıkarmaya çalıştığında, `3`için enum tanımında bir eşleşme bulamaz. Sonuç `Region.None`olacaktır.

Prototipte birden çok Enum değeri ile çalışmanın en iyi yolu, sabit listesi türünde bir `repeated` alanı kullanmaktır.

>[!div class="step-by-step"]
>[Önceki](protobuf-any-oneof.md)
>[İleri](protobuf-maps.md)
