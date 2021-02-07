---
description: 'Hakkında daha fazla bilgi edinin: 1131-ınvokemethodumevsimsyncmodel'
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 59d8e5e1fe7c5b038df6fce3211fd01977abc4f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667323"
---
# <a name="1131---invokemethoduseasyncpattern"></a>1131 - InvokeMethodUseAsyncPattern

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1131|  
|Anahtar sözcükler|WFRuntime|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 CacheMetadata adımı sırasında InvokeMethod etkinliği yöntemi çağrılırken zaman uyumsuz bir model kullandığını belirtir.  
  
## <a name="message"></a>İleti  

 InvokeMethod ' %1 '-Yöntem ' %2 ' ve ' %3 ' zaman uyumsuz modelini kullanıyor.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs: String|InvokeMethod etkinliğinin görünen adı.|  
|BeginMethod|xs: String|Begin yönteminin adı.|  
|EndMethod|xs: String|End yönteminin adı.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
