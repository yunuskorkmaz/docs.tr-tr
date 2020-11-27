---
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 23262427c3da730eaf930a8b483c7c4d4ec3a3a4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289847"
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|3508|  
|Anahtar sözcükler|WFServices|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  

 Yapılandırma dosyasında bir TrackingProfile bulunamadığını ya da ActivityDefinitionId 'nin profille eşleşip eşleşmediği gösterir.  
  
## <a name="message"></a>İleti  

 ' %2 ' ActivityDefinitionId için TrackingProfile ' %1 ' bulunamadı. TrackingProfile yapılandırma dosyasında bulunamadı ya da ActivityDefinitionId eşleşmiyor.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|TrackingProfile|xs: String|İzleme profilinin adı.|  
|ActivityDefinitionId|xs: String|Etkinlik tanımı kimliği.|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
