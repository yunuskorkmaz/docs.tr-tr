---
title: 223 - OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: cf4a455d80a1a0ac09e99bad967c1feba3653842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596544"
---
# <a name="223---operationfaulted"></a>223 - OperationFaulted
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|223|  
|anahtar sözcükler|Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay yayılan olduğunda hizmet modelinin varsayılan `OperationInvoker` türetilen bir özel durumla karşılaştı `FaultException` kendi metodu çağrılırken hata.  
  
## <a name="message"></a>İleti  
 '%1' yöntemi tarafından OperationInvoker çağrıldığında bir FaultException oluşturdu. Yöntem çağrısı süresi '%2' ms idi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|methodName|`xs:string`|CLR adı tarafından çağrılan yöntemin `OperationInvoker`.|  
|Süresi|`xs:long`|Geçen milisaniye cinsinden zaman `OperationInvoker` yöntemini çağırmak için.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
