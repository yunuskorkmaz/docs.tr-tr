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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34812b6ddefb69c053cfefa91d7227a7bf15f42e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
