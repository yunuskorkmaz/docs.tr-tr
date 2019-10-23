---
title: Prototipsiz numaralandırmalar-WCF geliştiricileri için gRPC
description: Prototipte numaralandırmalar bildirme ve kullanma hakkında bilgi edinin.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 37fd55e4cbc3c1e1e96e32875ddb3dcae0ca8355
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771643"
---
# <a name="protobuf-enumerations"></a>Protobuf sabit listeleri

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Prototip, bir `oneof` alanının türünü belirlemekte bir numaralandırma kullanılan önceki bölümde görüldüğü gibi numaralandırma türlerini destekler. Kendi numaralandırma türlerinizi tanımlayabilir ve Protoda bunları sabit listesi türleri için C# derler. Prototip farklı dillerde kullanılabilir olduğundan, numaralandırmalar için adlandırma kuralları C# kurallardan farklıdır. Ancak, kod üreticisi zekice ' dir ve adları geleneksel C# harfe dönüştürür. Alan adının Pascal-case eşdeğerini, numaralandırma adıyla başlıyorsa, kaldırılır.

Örneğin, bu Prototiplik numaralandırmada alanlara ön ek olarak `ACCOUNT_STATUS`, bu, Pascal büyük/küçük harf adı: `AccountStatus` ile eşdeğerdir.

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

Bu nedenle, Oluşturucu aşağıdaki koda C# denk bir sabit listesi oluşturur:

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

Prototip numaralandırma tanımlarının ilk alanları olarak sıfır sabiti **olmalıdır** . ' De C#olduğu gibi, aynı değere sahip birden fazla alan bildirebilirsiniz, ancak enum içindeki `allow_alias` seçeneğini kullanarak bu seçeneği açıkça etkinleştirmeniz gerekir:

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

[[Flags]](xref:System.FlagsAttribute) özniteliğini prototipsel olarak üretilen bir numaralandırmaya uygulamanın bir yolu yoktur ve protoarabellek, bit düzeyinde sabit listesi birleşimlerini anlamaz. Aşağıdaki örneğe göz atın:

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

@No__t_0 `Region.NorthAmerica | Region.SouthAmerica` olarak ayarlarsanız, `3` tamsayı değer olarak serileştirilir. Bir istemci veya sunucu değeri seri durumdan çıkarmaya çalıştığında, `3` için enum tanımında bir eşleşme bulamaz ve sonuç `Region.None` olur.

Prototipte birden çok Enum değeri ile çalışmanın en iyi yolu, sabit listesi türünde bir `repeated` alanı kullanmaktır.

>[!div class="step-by-step"]
>[Önceki](protobuf-any-oneof.md)
>[İleri](protobuf-maps.md)
