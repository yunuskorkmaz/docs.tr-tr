---
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ff8a1e099934f5bf71fef0afbb7e54c0d1851fae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267188"
---
# <a name="4211---queuingsqlretry"></a>4211 - QueuingSqlRetry

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|4211|  
|Anahtar sözcükler|Wfınstancestore|  
|Düzey|Uyarı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 SQL yeniden denemeyi kuyruğa alma işlemini gösterir.  
  
## <a name="message"></a>İleti  

 SQL yeniden denemesi %1 milisaniyesi ile sıraya alınıyor.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Gecikme|xs: String|Yeniden denemeler arasındaki gecikme.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
