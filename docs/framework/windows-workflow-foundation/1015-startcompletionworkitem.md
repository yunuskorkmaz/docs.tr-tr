---
title: 1015 - StartCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 44ef71e254a2407b416a0efc4b560bf2f6013a74
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1015---startcompletionworkitem"></a>1015 - StartCompletionWorkItem
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1015|  
|Anahtar Sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir CompletionWorkItem yürütme başlanacağını gösterir.  
  
## <a name="message"></a>İleti  
 Üst etkinlik '%1', DisplayName için CompletionWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'. '%4', DisplayName etkinliği tamamlandı: '%5', örnek kimliği: '%6'.  
  
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
