---
title: 222 - OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: c49aad0f93ce47b66306d75741267530dc6d3fe5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781647"
---
# <a name="222---operationfailed"></a>222 - OperationFailed
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|222|  
|anahtar sözcükler|Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,|  
|Düzey|Uyarı|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay yayılan olduğunda hizmet modelinin varsayılan `OperationInvoker` kendi metodu çağrılırken bir özel durumla karşılaştı. Not öğesinden türetilen, özel durumlar `FaultException` değil derleyicisindeki bu olayın neden.  
  
## <a name="message"></a>İleti  
 '%1' yöntemi tarafından OperationInvoker çağrıldığında işlenmeyen bir özel durum oluşturdu. Yöntem çağrısı süresi '%2' ms idi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Yöntem adı|`xs:string`|CLR adı tarafından çağrılan yöntemin `OperationInvoker`.|  
|Süresi|`xs:long`|Geçen milisaniye cinsinden zaman `OperationInvoker` yöntemini çağırmak için.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
