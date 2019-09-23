---
title: Prototipsiz numaralandırmalar-WCF geliştiricileri için gRPC
description: Prototipte numaralandırmalar bildirme ve kullanma hakkında bilgi edinin.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: d93319b713588129a19246976a82bb03a90ce680
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184241"
---
# <a name="protobuf-enumerations"></a>Prototip listeleme

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Prototip, bir `oneof` alanın türünü belirlemekte bir sabit listesinin kullanıldığı önceki bölümde görüldüğü gibi numaralandırma türlerini destekler. Kendi numaralandırma türlerinizi tanımlayabilir ve Protoda bunları sabit listesi türleri için C# derler. Prototip farklı dillerde kullanılabilir olduğundan, numaralandırmalar için adlandırma kuralları C# kurallardan farklıdır. Ancak, kod üreticisi zekice ' dir ve adları geleneksel C# harfe dönüştürür. Alan adının Pascal-case eşdeğerini, numaralandırma adıyla başlıyorsa, kaldırılır.

Örneğin, bu prototiplik numaralandırmasında alanlar `ACCOUNT_STATUS`, Pascal case numaralandırma adına eşdeğer olan ön ekine sahiptir:. `AccountStatus`

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

Prototip numaralandırma tanımlarının ilk alanları olarak sıfır sabiti **olmalıdır** . ' De C#olduğu gibi, aynı değere sahip birden fazla alan bildirebilirsiniz, ancak bu seçeneği, Numaralandırmadaki `allow_alias` seçeneğini kullanarak açıkça etkinleştirmelisiniz:

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

Numaralandırmalar bir `.proto` dosyanın en üst düzeyinde veya bir ileti tanımı içinde iç içe bildirebilirsiniz. İç içe geçmiş (iç içe geçmiş iletiler gibi) numaralandırmalar `.Types` oluşturulan ileti sınıfındaki statik sınıf içinde bildirilecektir.

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
  Region availableIn = 1;
}
```

' A ayarlarsanız `product.AvailableIn` , tamsayı değeri `3`olarak serileştirilir. `Region.NorthAmerica | Region.SouthAmerica` Bir istemci veya sunucu değeri seri durumdan çıkarmaya çalıştığında, için `3` enum tanımında bir eşleşme bulamaz ve sonuç `Region.None`olur.

Prototipte birden çok Enum değeri ile çalışmanın en iyi yolu, sabit listesi türünün `repeated` bir alanını kullanmaktır.

>[!div class="step-by-step"]
>[Önceki](protobuf-any-oneof.md)
>[İleri](protobuf-maps.md)
