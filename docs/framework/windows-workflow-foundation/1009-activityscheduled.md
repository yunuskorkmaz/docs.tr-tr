---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 812531d4206dfee20f183b9461330e71263b0bf8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239776"
---
# <a name="1009---activityscheduled"></a>1009 - ActivityScheduled

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1009|  
|Anahtar sözcükler|WFRuntime|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Bir etkinliğin yürütme için zamanlanmakta olduğunu gösterir.  
  
## <a name="message"></a>İleti  

 DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %4 ', DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %1 ' üst etkinliği  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs: String|Üst etkinliğin tür adı.|  
|ParentDisplayName|xs: String|Ana etkinliğin görünen adı.|  
|Parentınstanceıd|xs: String|Ana etkinliğin örnek kimliği.|  
|ChildActivity|xs: String|Zamanlanan alt etkinliğin tür adı.|  
|ChildDisplayName|xs: String|Zamanlanan alt etkinliğin görünen adı.|  
|Childınstanceıd|xs: String|Zamanlanan alt etkinliğin örnek kimliği.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
