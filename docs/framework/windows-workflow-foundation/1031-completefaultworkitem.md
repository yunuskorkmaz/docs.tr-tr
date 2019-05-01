---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008804"
---
# <a name="1031---completefaultworkitem"></a>1031 - CompleteFaultWorkItem
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|1031|  
|anahtar sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama|  
  
## <a name="description"></a>Açıklama  
 Bir FaultWorkItem tamamlandığını gösterir.  
  
## <a name="message"></a>İleti  
 '%1', DisplayName etkinliği için bir FaultWorkItem tamamlandı: '%2', InstanceId: '%3'. Özel durum '%4', DisplayName etkinliğinden yayıldığı: '%5', InstanceId: '%6'.  
  
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
