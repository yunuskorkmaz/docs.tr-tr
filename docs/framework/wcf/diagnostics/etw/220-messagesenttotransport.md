---
title: 220 - MessageSentToTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d391d7bb8276f4b20d831acd59aa8a78db38995c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="220---messagesenttotransport"></a>220 - MessageSentToTransport
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimliği|220|  
|Anahtar Sözcükler|Sorun giderme, ServiceModel EndToEndMonitoring|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay, hizmet modeli aktarıma ileti gönderdiğinde yayınlanır.  
  
> [!NOTE]
>  Bu olay için tek yönlü aktarmaları yayılan değil.  
  
## <a name="message"></a>İleti  
 Dağıtıcı taşıma için bir ileti gönderdi. Bağıntı Kimliği '%1' ==.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Bağıntı Kimliği|`xs:GUID`|Etkinlik ilişkilendirmek için kullanılan bir `MessageSentToTransport` ilgili olayı bir hizmeti veya istemci `MessageReceivedFromTransport` diğer uçtaki.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'. Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
