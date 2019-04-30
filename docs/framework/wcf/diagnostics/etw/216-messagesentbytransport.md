---
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: fa21568e4c8c38eefe359c417d47ec0a9d30a7c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781816"
---
# <a name="216---messagesentbytransport"></a>216 - MessageSentByTransport
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|216|  
|anahtar sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay bir TCP tabanlı taşıma ileti gönderdiğinde oluşur. Not taşıma düzeyinde birden çok ileti istemcileri ve Hizmetleri tek bir işlem için arasında değiştirilebilir. Bu, iyi bir örnek olan güvenlik altyapısı davranışı nedeniyle olabilir. Bu nedenle, sayısını **MessageSentByTransport** yayılan iş olayları hizmetinizin bağlama ve yapılandırmasına bağlı olarak değişir.  
  
## <a name="message"></a>İleti  
 Taşıma, '%1' için bir ileti gönderdi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|DestinationAddress|`xs:string`|İstek iletisi gönderildiği adresi.|  
|HostReference|xs:string|Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
