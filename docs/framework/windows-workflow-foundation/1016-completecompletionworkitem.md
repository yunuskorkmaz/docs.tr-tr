---
description: 'Hakkında daha fazla bilgi edinin: 1016-Completecompletionworkıtem'
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 849e192d63b5db19e5beea31befcdc38d4340c6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792914"
---
# <a name="1016---completecompletionworkitem"></a>1016 - CompleteCompletionWorkItem

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1016|  
|Anahtar sözcükler|WFRuntime|  
|Level|Ayrıntılı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir CompletionWorkItem 'ın tamamlandığını gösterir.  
  
## <a name="message"></a>İleti  

 DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' üst etkinliği için bir CompletionWorkItem tamamlandı. DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' Activity 'si tamamlandı.  
  
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
