---
title: 217 - ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: 5979cd8ffe0e05b61af01d2aa98c4a2c63fd432c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461071"
---
# <a name="217---clientoperationprepared"></a>217 - ClientOperationPrepared
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|217|  
|Anahtar Sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay yalnızca bir işlem hizmetine gönderilmeden önce istemcileri tarafından yayınlanır.  
  
## <a name="message"></a>İleti  
 İstemci, '%2' sözleşmeyle ilişkilendirilmiş ' %1' eylemi yürütüyor. '%3' ileti gönderilir.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Eylem|`xs:string`|Giden iletinin SOAP eylemi üstbilgisi.|  
|Sözleşme adı|`xs:string`|Anlaşma adı. Örnek: ICalculator.|  
|Hedef|`xs:string`|İleti gönderilir hizmet uç noktası adresi.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'. Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
