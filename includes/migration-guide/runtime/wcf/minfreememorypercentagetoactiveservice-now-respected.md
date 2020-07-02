---
ms.openlocfilehash: f8e5dee9e97956cea78b7c8ec999af1afe9ac66b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620651"
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
