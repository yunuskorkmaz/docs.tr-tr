---
title: 1124 - InvokeMethodIsStatic
ms.date: 03/30/2017
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
ms.openlocfilehash: d7ad99131f9813c2102f52784fc33605bed37557
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242129"
---
# <a name="1124---invokemethodisstatic"></a>1124 - InvokeMethodIsStatic

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1124|  
|Anahtar sözcükler|WFRuntime|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 CacheMetadata adımı sırasında InvokeMethod etkinliği çağrılacak yöntemin statik olduğunu gösterir.  
  
## <a name="message"></a>İleti  

 InvokeMethod ' %1 '-Yöntem Static.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs: String|InvokeMethod etkinliğinin görünen adı.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
