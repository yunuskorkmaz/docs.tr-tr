---
title: 1013 - CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: 654f961088c371ab53e4a81f40e3c63335efb1a8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239594"
---
# <a name="1013---completeexecuteactivityworkitem"></a>1013 - CompleteExecuteActivityWorkItem

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1013|  
|Anahtar sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Bir ExecuteActivityWorkItem 'ın tamamlandığını belirtir  
  
## <a name="message"></a>İleti  

 DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir ExecuteActivityWorkItem tamamlandı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Etkinlik|xs: String|Etkinliğin tür adı.|  
|DisplayName|xs: String|Etkinliğin görünen adı.|  
|InstanceId|xs: String|Etkinliğin örnek kimliği.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
