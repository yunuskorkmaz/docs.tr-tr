---
title: 218 - ClientOperationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 974fde79d8b24c17928fa4ff38bb9d35d6b5a815
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="218---clientoperationcompleted"></a>218 - ClientOperationCompleted
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|218|  
|Anahtar Sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay yalnızca bir işlem tamamlandıktan sonra istemciler tarafından yayınlanır. Yalnızca ileti başarıyla gönderildikten sonra tek yönlü işlemlerinde budur. Yanıt alındıktan sonra istek-yanıt işlemlerinde budur.  
  
## <a name="message"></a>İleti  
 İstemci, '%2' sözleşmeyle ilişkilendirilmiş ' %1' eylemi yürütülürken tamamlandı. '%3' ileti gönderildi.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Eylem|xs: String|Giden iletinin SOAP eylemi üstbilgisi.|  
|Sözleşme adı|`xs:string`|Anlaşma adı. Örnek: ICalculator.|  
|Hedef|`xs:string`|İletinin gönderildiği hizmet uç noktası adresi.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'. Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
