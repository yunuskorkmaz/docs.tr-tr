---
description: 'Hakkında daha fazla bilgi edinin: 1015-Startcompletionworkıtem'
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6c79a02b144aa1176eb1cb334c8430c8f0babc3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792927"
---
# <a name="1015---startcompletionworkitem"></a>1015 - StartCompletionWorkItem

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1015|  
|Anahtar sözcükler|WFRuntime|  
|Level|Ayrıntılı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir CompletionWorkItem 'ın yürütmeyi başlatdığını gösterir.  
  
## <a name="message"></a>İleti  

 DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' üst etkinliği için bir CompletionWorkItem 'ın yürütülmesi başlatılıyor. DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' Activity 'si tamamlandı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs: String|Üst etkinliğin tür adı.|  
|ParentDisplayName|xs: String|Ana etkinliğin görünen adı.|  
|Parentınstanceıd|xs: String|Ana etkinliğin örnek kimliği.|  
|CompletedActivity|xs: String|Tamamlanan etkinliğin tür adı.|  
|CompletedActivityDisplayName|xs: String|Tamamlanan etkinliğin görünen adı.|  
|Completedactivityınstanceıd|xs: String|Tamamlanan etkinliğin örnek kimliği.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
