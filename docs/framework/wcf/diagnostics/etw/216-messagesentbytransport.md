---
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: fa21568e4c8c38eefe359c417d47ec0a9d30a7c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458689"
---
# <a name="216---messagesentbytransport"></a>216 - MessageSentByTransport
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|216|  
|Anahtar Sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay, bir TCP tabanlı taşıma ileti gönderdiğinde oluşur. Aktarım düzeyinde birden çok ileti istemciler ve hizmetler için tek bir işlem arasında değiştirilebilir unutmayın. Bu iyi bir örneği olan güvenlik altyapı davranışı nedeniyle olabilir. Bu nedenle, sayısı **MessageSentByTransport** gösterilen olayları hizmetinizin bağlama ve yapılandırmasına göre değişir.  
  
## <a name="message"></a>İleti  
 Taşıma '%1' için bir ileti gönderdi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|DestinationAddress|`xs:string`|İstek iletisi gönderildiği adresi.|  
|HostReference|xs: String|Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'. Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
