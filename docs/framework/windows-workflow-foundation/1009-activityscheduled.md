---
description: 'Hakkında daha fazla bilgi edinin: 1009-Activityzamanlandı'
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 80ee250955a03927fb9db2b1242d420be77a6df8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755557"
---
# <a name="1009---activityscheduled"></a>1009 - ActivityScheduled

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1009|  
|Anahtar sözcükler|WFRuntime|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir etkinliğin yürütme için zamanlanmakta olduğunu gösterir.  
  
## <a name="message"></a>İleti  

 DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %4 ', DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %1 ' üst etkinliği  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs: String|Üst etkinliğin tür adı.|  
|ParentDisplayName|xs: String|Ana etkinliğin görünen adı.|  
|Parentınstanceıd|xs: String|Ana etkinliğin örnek kimliği.|  
|ChildActivity|xs: String|Zamanlanan alt etkinliğin tür adı.|  
|ChildDisplayName|xs: String|Zamanlanan alt etkinliğin görünen adı.|  
|Childınstanceıd|xs: String|Zamanlanan alt etkinliğin örnek kimliği.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
