---
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 2192b63b8a08657b69f6e3984f898bd6baddbc5f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294189"
---
# <a name="1131---invokemethoduseasyncpattern"></a>1131 - InvokeMethodUseAsyncPattern

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1131|  
|Anahtar sözcükler|WFRuntime|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 CacheMetadata adımı sırasında InvokeMethod etkinliği yöntemi çağrılırken zaman uyumsuz bir model kullandığını belirtir.  
  
## <a name="message"></a>İleti  

 InvokeMethod ' %1 '-Yöntem ' %2 ' ve ' %3 ' zaman uyumsuz modelini kullanıyor.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs: String|InvokeMethod etkinliğinin görünen adı.|  
|BeginMethod|xs: String|Begin yönteminin adı.|  
|EndMethod|xs: String|End yönteminin adı.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
