---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: 557155fab35a37bdbaa45efb26d6bc025ad825c4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281839"
---
# <a name="1031---completefaultworkitem"></a>1031 - CompleteFaultWorkItem

## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|ID|1031|  
|Anahtar sözcükler|WFRuntime|  
|Düzey|Ayrıntılı|  
|Kanal|Microsoft-Windows-Application Server-uygulamalar/hata ayıkla|  
  
## <a name="description"></a>Açıklama  

 Bir FaultWorkItem 'ın tamamlandığını gösterir.  
  
## <a name="message"></a>İleti  

 DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir FaultWorkItem tamamlandı. Özel durum DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' etkinliğinden yayılmıştı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs: String|Hata etkinliğinin tür adı.|  
|FaultActivityDisplayName|xs: String|Hata etkinliğinin görünen adı.|  
|Faultactivityınstanceıd|xs: String|Hata etkinliğinin örnek kimliği.|  
|ExceptionActivity|xs: String|Özel durumu oluşturan etkinliğin tür adı.|  
|ExceptionActivityDisplayName|xs: String|Özel durumu oluşturan etkinliğin görünen adı.|  
|Exceptionactivityınstanceıd|xs: String|Özel durumu oluşturan etkinliğin örnek kimliği.|  
|Özel durum|xs: String|Özel durum için özel durum ayrıntıları|  
|AppDomain|xs: String|AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.|
