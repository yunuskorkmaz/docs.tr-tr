---
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 94c7ce231df241778f7c6ec5fe5998eae364750d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755577"
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|3508|  
|anahtar sözcükler|WFServices|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Yapılandırma dosyasında bir TrackingProfile bulunamadı veya ActivityDefinitionId profili eşleşmiyor gösterir.  
  
## <a name="message"></a>İleti  
 TrackingProfile ActivityDefinitionId bulunamadı ' %2' için '%1'. TrackingProfile yapılandırma dosyasında bulunamadı ya da ActivityDefinitionId eşleşmiyor.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|trackingProfile|xs:string|İzleme profilinin adı.|  
|activityDefinitionId|xs:string|Etkinlik tanımı kimliği.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
