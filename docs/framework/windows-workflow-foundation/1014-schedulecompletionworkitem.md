---
title: 1014 - ScheduleCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b6f58cf711a91a748d3516bdd0708cc89b02c623
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1014---schedulecompletionworkitem"></a>1014 - ScheduleCompletionWorkItem
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1014|  
|Anahtar Sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir CompletionWorkItem zamanlanmış gösterir.  
  
## <a name="message"></a>İleti  
 Bir CompletionWorkItem üst etkinliği '%1', DisplayName zamanlandı: '%2', örnek kimliği: '%3'.  '%4', DisplayName etkinliği tamamlandı: '%5', örnek kimliği: '%6'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs: String|Üst etkinlik türü adı.|  
|Ana görüntü adı|xs: String|Üst etkinliğin görünen adı.|  
|ParentInstanceId|xs: String|Üst etkinlik örnek kimliği.|  
|CompletedActivity|xs: String|Tamamlanan etkinliğin türü adı.|  
|CompletedActivityDisplayName|xs: String|Tamamlanan etkinliğin görünen adı.|  
|CompletedActivityInstanceId|xs: String|Tamamlanan etkinliğin örnek kimliği.|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
