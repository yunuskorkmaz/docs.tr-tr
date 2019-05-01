---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924663"
---
# <a name="1009---activityscheduled"></a>1009 - ActivityScheduled
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1009|  
|anahtar sözcükler|WFRuntime|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Yürütme için zamanlanan bir etkinlik gösterir.  
  
## <a name="message"></a>İleti  
 Üst etkinlik '%1', DisplayName: '%2', InstanceId: '%3' zamanlanmış alt etkinliği '%4', DisplayName: '%5', InstanceId: '%6'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs:string|Üst etkinliğin tür adı.|  
|ParentDisplayName|xs:string|Üst etkinliğin görünen adı.|  
|ParentInstanceId|xs:string|Üst etkinliği örneği kimliği.|  
|ChildActivity|xs:string|Zamanlanmış bir alt etkinlik türü adı.|  
|ChildDisplayName|xs:string|Zamanlanmış bir alt etkinlik görünen adı.|  
|ChildInstanceId|xs:string|Zamanlanmış bir alt etkinlik örneği kimliği.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
