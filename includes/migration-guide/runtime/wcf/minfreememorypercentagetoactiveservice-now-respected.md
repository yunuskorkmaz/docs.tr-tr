---
ms.openlocfilehash: fa472b3a142f55f0cbdd83eabbbb00bddd9786d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235885"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>MinFreeMemoryPercentageToActiveService artık uyulduğundan

|   |   |
|---|---|
|Ayrıntılar|Bu ayar, bir WCF hizmet aktif edilmeden önce sunucuda bellek alt sınırı belirler. Önlemek üzere tasarlanmış <xref:System.OutOfMemoryException?displayProperty=name> özel durumlar. .NET Framework 4.5, bu ayarın hiçbir etkisi vardı. .NET Framework 4.5.1, ayar dikkate alınır.|
|Öneri|Web sunucusunda kullanılabilir boş bellek yapılandırma ayarları tarafından tanımlandığı yüzdenin ise bir özel durum oluşur. Başarıyla başlatıldı ve kısıtlı bellek ortamında çalışan bazı WCF hizmetlerinde başarısız olabilir.|
|Kapsam|İkincil|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|
