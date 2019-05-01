---
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6a2d4c866ec7d43e8ae40b5616a97c3b7adf1843
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032272"
---
# <a name="1015---startcompletionworkitem"></a>1015 - StartCompletionWorkItem
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1015|  
|anahtar sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir CompletionWorkItem yürütme başlanacağını gösterir.  
  
## <a name="message"></a>İleti  
 Üst etkinlik '%1', DisplayName için bir CompletionWorkItem yürütülmesi başlatılıyor: '%2', InstanceId: '%3'. '%4', DisplayName etkinliği tamamlandı: '%5', InstanceId: '%6'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs:string|Üst etkinliğin tür adı.|  
|ParentDisplayName|xs:string|Üst etkinliğin görünen adı.|  
|ParentInstanceId|xs:string|Üst etkinliği örneği kimliği.|  
|CompletedActivity|xs:string|Tamamlanan etkinliğin tür adı.|  
|CompletedActivityDisplayName|xs:string|Tamamlanan etkinliğin görünen adı.|  
|CompletedActivityInstanceId|xs:string|Tamamlanan etkinliğin örnek kimliği.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
