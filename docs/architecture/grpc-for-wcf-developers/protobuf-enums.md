---
title: Protobuf hesaplamaları - WCF geliştiricileri için gRPC
description: Protobuf'ta sayısallaştırmaları nasıl beyan edin ve kullanacağınızı öğrenin.
ms.date: 09/09/2019
ms.openlocfilehash: 2177f568a671fa0e651625c6e025ac70c243feb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148081"
---
# <a name="protobuf-enumerations"></a>Protobuf sabit listeleri

Protobuf numaralandırma türlerini destekler. Bu desteği, bir `Oneof` alanın türünü belirlemek için bir enumun kullanıldığı önceki bölümde gördünuz. Kendi numaralandırma türlerinizi tanımlayabilirsiniz ve Protobuf bunları C# enum türlerine derler.

Protobuf'u çeşitli dillerde kullanabileceğinizden, numaralandırmaiçin adlandırma kuralları C# kurallarından farklıdır. Ancak, kod üreteci adları geleneksel C# örneğine dönüştürür. Alan adının Pascal-case eşdeğeri numaralandırma adı ile başlarsa, o zaman kaldırılır.

Örneğin, aşağıdaki Protobuf numaralandırmasında, alanlar `ACCOUNT_STATUS`. Bu önek Pascal-case enum adı, `AccountStatus`eşdeğerdir.

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

Jeneratör aşağıdaki koda eşdeğer bir C# enum oluşturur:

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

Protobuf numaralandırma tanımları ilk alanları olarak sıfır *sabitolmalıdır.* C#'da olduğu gibi, aynı değere sahip birden çok alanı bildirebilirsiniz. Ancak, enumdaki `allow_alias` seçeneği kullanarak bu seçeneği açıkça etkinleştirmelisiniz:

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

Bir `.proto` dosyada en üst düzeyde ki tümumerations'ı bildirebilir veya ileti tanımı içinde iç içe. İç içe geçmiş iletiler gibi iç içe geçmiş yinelemeler, oluşturulan ileti sınıfındaki `.Types` statik sınıf içinde bildirilir.

[[Bayraklar]](xref:System.FlagsAttribute) özniteliğini Protobuf tarafından oluşturulan bir enuma uygulamanın bir yolu yoktur ve Protobuf bitwise enum kombinasyonlarını anlamaz. Aşağıdaki örneğe bakın:

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

Ayarlarsanız, `product.AvailableIn` bu sayı, tümsado değeri `3`olarak serihale edilir. `Region.NorthAmerica | Region.SouthAmerica` Bir istemci veya sunucu değeri deserialize etmeye çalıştığında, enum tanımında bir `3`eşleşme bulamaz. Sonuç. `Region.None`

Protobuf'ta birden çok enum değeriyle çalışmanın `repeated` en iyi yolu, enum türünde bir alan kullanmaktır.

>[!div class="step-by-step"]
>[Önceki](protobuf-any-oneof.md)
>[Sonraki](protobuf-maps.md)
