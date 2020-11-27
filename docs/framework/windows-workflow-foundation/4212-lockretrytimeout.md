---
title: 4212 - LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: 43ec434064f768fc976232c6d3013f17c80fe053
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267175"
---
# <a name="4212---lockretrytimeout"></a>4212 - LockRetryTimeout

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|4212|  
|Anahtar sözcükler|Wfınstancestore|  
|Düzey|Uyarı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 SQL sağlayıcısı örnek kilidini edinmeye çalışırken bir zaman aşımıyla karşılaştı.  
  
## <a name="message"></a>İleti  

 Örnek kilidi alınmaya çalışılırken zaman aşımı oluştu.  İşlem ayrılan %1 zaman aşımı süresi içinde tamamlanmadı. Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Gecikme|xs: String|Yeniden denemeler arasındaki gecikme.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
