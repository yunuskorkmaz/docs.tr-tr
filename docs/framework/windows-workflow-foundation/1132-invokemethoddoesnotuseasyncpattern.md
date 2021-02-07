---
description: 'Hakkında daha fazla bilgi edinin: 1132-ınvokemethodlınotumevsimsyncmodel'
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 05bbd1f6047ab4c6451d71a4f6007f3112f9630f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667284"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a>1132 - InvokeMethodDoesNotUseAsyncPattern

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1132|  
|Anahtar sözcükler|WFRuntime|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 CacheMetadata adımı sırasında InvokeMethod etkinliği, yöntemi çağrılırken zaman uyumsuz deseninin kullanılmadığını gösterir.  
  
## <a name="message"></a>İleti  

 InvokeMethod ' %1 '-yöntem zaman uyumsuz model kullanmıyor.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs: String|InvokeMethod etkinliğinin görünen adı.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
