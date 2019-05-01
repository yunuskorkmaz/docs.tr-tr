---
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 3f0904a561a242cd3be528c9707a409b6f98e0fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925092"
---
# <a name="1016---completecompletionworkitem"></a>1016 - CompleteCompletionWorkItem
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1016|  
|anahtar sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir CompletionWorkItem tamamlandığını gösterir.  
  
## <a name="message"></a>İleti  
 Bir CompletionWorkItem üst etkinliği '%1', DisplayName tamamlandı: '%2', InstanceId: '%3'. '%4', DisplayName etkinliği tamamlandı: '%5', InstanceId: '%6'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs:string|Üst etkinliğin tür adı.|  
|ParentDisplayName|xs:string|Üst etkinliğin görünen adı.|  
|ParentInstanceId|xs:string|Üst etkinliği örneği kimliği.|  
|CompletedActivity|xs:string|Tamamlanan etkinliğin tür adı.|  
|CompletedActivityDisplayName|xs:string|Tamamlanan etkinliğin görünen adı.|  
|CompletedActivityInstanceId|xs:string|Tamamlanan etkinliğin örnek kimliği.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
