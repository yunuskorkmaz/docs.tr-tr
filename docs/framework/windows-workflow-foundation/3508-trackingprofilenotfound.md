---
title: 3508 - TrackingProfileNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fb5636057193fcfb59e5062f6f3833a62b4f3027
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|3508|  
|Anahtar Sözcükler|WFServices|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir TrackingProfile yapılandırma dosyasında bulunamadı veya ActivityDefinitionId profili eşleşmiyor gösterir.  
  
## <a name="message"></a>İleti  
 '%1' TrackingProfile için ActivityDefinitionId '%2' bulunamadı. TrackingProfile yapılandırma dosyasında bulunamadı ya da ActivityDefinitionId eşleşmiyor.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|TrackingProfile|xs: String|İzleme profili adı.|  
|ActivityDefinitionId|xs: String|Etkinlik tanımı kimliği.|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
