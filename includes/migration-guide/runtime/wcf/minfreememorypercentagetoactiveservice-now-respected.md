---
ms.openlocfilehash: b23182ad1da8208a69b78fc7bc872780d386a59a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496257"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>Minfreememoryyüztagetoactiveservice artık dikkate alındı

#### <a name="details"></a>Ayrıntılar

Bu ayar, bir WCF hizmetinin etkinleştirilmeden önce sunucuda kullanılabilir olması gereken en düşük belleği belirler. Özel durumları engellemek için tasarlanmıştır <xref:System.OutOfMemoryException?displayProperty=fullName> . .NET Framework 4,5 ' de, bu ayarın etkisi yoktur. .NET Framework 4.5.1, ayar izlenir.

#### <a name="suggestion"></a>Öneri

Web sunucusunda kullanılabilir boş bellek yapılandırma ayarı tarafından tanımlanan yüzdeden küçükse bir özel durum oluşur. Başarılı bir şekilde başlatılan ve kısıtlanmış bir bellek ortamında çalıştırılan bazı WCF Hizmetleri artık başarısız olabilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4.5.1|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
