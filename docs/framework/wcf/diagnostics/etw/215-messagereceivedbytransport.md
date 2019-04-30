---
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: a8ba90b88ef8dbe3c8651bc565da61aae16a0a4a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781842"
---
# <a name="215---messagereceivedbytransport"></a>215 - MessageReceivedByTransport
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|215|  
|anahtar sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay bir TCP tabanlı taşıma bir ileti aldığında gerçekleşir. Not taşıma düzeyinde birden çok ileti istemcileri ve Hizmetleri tek bir işlem için arasında değiştirilebilir. Bu altyapı davranışı nedeniyle olabilir, güvenlik iyi bir örnektir. Bu nedenle, sayısını `MessageReceivedByTransport` yayılan iş olayları hizmetinizin bağlama ve yapılandırmasına bağlı olarak değişir.  
  
> [!NOTE]
>  Bu olay için tek yönlü aktarmaları yayılan değil.  
  
## <a name="message"></a>İleti  
 Taşıma, '%1' den bir ileti alındı.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Dinleme adresi|`xs:string`|Alınan ileti adresi.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
