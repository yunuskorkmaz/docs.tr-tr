---
title: 1010 - ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: d0ebf32ec1d5fe5b34ffe650d5547891be0eb665
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239919"
---
# <a name="1010---activitycompleted"></a>1010 - ActivityCompleted

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1010|  
|Anahtar sözcükler|WFRuntime|  
|Düzey|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Bir etkinliğin yürütmenin tamamlandığını gösterir.  
  
## <a name="message"></a>İleti  

 DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si ' %4 ' durumunda tamamlandı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Etkinlik|xs: String|Etkinliğin tür adı.|  
|DisplayName|xs: String|Etkinliğin görünen adı.|  
|InstanceId|xs: String|Etkinliğin örnek kimliği.|  
|Durum|xs: String|Etkinliğin durumu.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
