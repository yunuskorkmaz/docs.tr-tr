---
description: 'Hakkında daha fazla bilgi edinin: 1014-Schedulecompletionworkıtem'
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 85bbd9b749c1dd34d026d90d708ea7f880665fbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792940"
---
# <a name="1014---schedulecompletionworkitem"></a>1014 - ScheduleCompletionWorkItem

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1014|  
|Anahtar sözcükler|WFRuntime|  
|Level|Ayrıntılı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir CompletionWorkItem zamanlandığı olduğunu gösterir.  
  
## <a name="message"></a>İleti  

 DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' üst etkinliği için bir CompletionWorkItem zamanlandı.  DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' Activity 'si tamamlandı.  
  
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
