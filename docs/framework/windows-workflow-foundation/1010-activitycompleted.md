---
title: 1010 - ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: 355281e6aa8f621bd2f9c0862e641fafec872750
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008377"
---
# <a name="1010---activitycompleted"></a>1010 - ActivityCompleted
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1010|  
|anahtar sözcükler|WFRuntime|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir etkinlik yürütmeyi tamamladığını gösterir.  
  
## <a name="message"></a>İleti  
 Etkinliği '%1', DisplayName: '%2', InstanceId: '%3' '%4' durumunda tamamlandı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Etkinlik|xs:string|Etkinlik türü adı.|  
|displayName|xs:string|Etkinliğin görünen adı.|  
|InstanceId|xs:string|Etkinlik örneği kimliği.|  
|Durum|xs:string|Etkinliğin durumu.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
