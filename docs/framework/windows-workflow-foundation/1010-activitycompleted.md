---
description: 'Hakkında daha fazla bilgi edinin: 1010-ActivityCompleted'
title: 1010 - ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: c72339449b94b0ea5d6d8fa227b606cc25c29704
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755544"
---
# <a name="1010---activitycompleted"></a>1010 - ActivityCompleted

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1010|  
|Anahtar sözcükler|WFRuntime|  
|Level|Bilgi|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Description  

 Bir etkinliğin yürütmenin tamamlandığını gösterir.  
  
## <a name="message"></a>İleti  

 DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si ' %4 ' durumunda tamamlandı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|Etkinlik|xs: String|Etkinliğin tür adı.|  
|DisplayName|xs: String|Etkinliğin görünen adı.|  
|InstanceId|xs: String|Etkinliğin örnek kimliği.|  
|Durum|xs: String|Etkinliğin durumu.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
