---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="1009---activityscheduled"></a>1009 - ActivityScheduled
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1009|  
|Anahtar Sözcükler|WFRuntime|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir etkinlik çalıştırılmak üzere zamanlanmış gösterir.  
  
## <a name="message"></a>İleti  
 Üst etkinlik '%1', DisplayName: '%2', örnek kimliği: '%3' zamanlanmış alt etkinliği '%4', DisplayName: '%5', örnek kimliği: '%6'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs: String|Üst etkinlik türü adı.|  
|Ana görüntü adı|xs: String|Üst etkinliğin görünen adı.|  
|ParentInstanceId|xs: String|Üst etkinlik örnek kimliği.|  
|ChildActivity|xs: String|Zamanlanmış alt etkinlik türü adı.|  
|ChildDisplayName|xs: String|Zamanlanmış alt etkinliğin görünen adı.|  
|ChildInstanceId|xs: String|Zamanlanmış alt etkinlik örnek kimliği.|  
|AppDomain|xs: String|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
