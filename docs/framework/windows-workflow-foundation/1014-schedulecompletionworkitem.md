---
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 50b00a49ea73dcbe09e8f4c4195cbce8c1cbf615
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982273"
---
# <a name="1014---schedulecompletionworkitem"></a>1014 - ScheduleCompletionWorkItem
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1014|  
|anahtar sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir CompletionWorkItem zamanlandı gösterir.  
  
## <a name="message"></a>İleti  
 Bir CompletionWorkItem üst etkinliği '%1', DisplayName zamanlandı: '%2', InstanceId: '%3'.  '%4', DisplayName etkinliği tamamlandı: '%5', InstanceId: '%6'.  
  
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
