---
description: 'Hakkında daha fazla bilgi edinin: 3508-TrackingProfileNotFound'
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 3e97af1689a868fb103b06413a0c4f28b0c1f652
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778015"
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|3508|  
|Anahtar sözcükler|WFServices|  
|Level|Ayrıntılı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Description  

 Yapılandırma dosyasında bir TrackingProfile bulunamadığını ya da ActivityDefinitionId 'nin profille eşleşip eşleşmediği gösterir.  
  
## <a name="message"></a>İleti  

 ' %2 ' ActivityDefinitionId için TrackingProfile ' %1 ' bulunamadı. TrackingProfile yapılandırma dosyasında bulunamadı ya da ActivityDefinitionId eşleşmiyor.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Description|  
|--------------------|--------------------|-----------------|  
|TrackingProfile|xs: String|İzleme profilinin adı.|  
|ActivityDefinitionId|xs: String|Etkinlik tanımı kimliği.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
