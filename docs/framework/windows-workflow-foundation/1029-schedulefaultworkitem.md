---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924364"
---
# <a name="1029---schedulefaultworkitem"></a>1029 - ScheduleFaultWorkItem
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1029|  
|anahtar sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir FaultWorkItem zamanlandı gösterir.  
  
## <a name="message"></a>İleti  
 '%1', DisplayName etkinliği için bir FaultWorkItem zamanlandı: '%2', InstanceId: '%3'.  Özel durum '%4', DisplayName etkinliğinden yayıldığı: '%5', InstanceId: '%6'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:string|Hata etkinlik türü adı.|  
|FaultActivityDisplayName|xs:string|Hata etkinliğin görünen adı.|  
|FaultActivityInstanceId|xs:string|Hata etkinliği örneği kimliği.|  
|ExceptionActivity|xs:string|Özel durum oluşturdu etkinlik türü adı.|  
|ExceptionActivityDisplayName|xs:string|Özel durum oluşturan etkinliğin görünen adı.|  
|ExceptionActivityInstanceId|xs:string|Örnek kimliği etkinliğin özel durum oluşturdu.|  
|Özel Durum|xs:string|Özel durum için özel durum ayrıntıları|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
