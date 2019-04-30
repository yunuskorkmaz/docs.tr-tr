---
title: 217 - ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: 5979cd8ffe0e05b61af01d2aa98c4a2c63fd432c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781775"
---
# <a name="217---clientoperationprepared"></a>217 - ClientOperationPrepared
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|217|  
|anahtar sözcükler|Sorun giderme, ServiceModel|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay, yalnızca bir işlem hizmetine gönderilmeden önce istemcileri tarafından yayınlanır.  
  
## <a name="message"></a>İleti  
 İstemci, '%1' ile '%2' sözleşme ilişkili eylemi yürütüyor. '%3' ileti gönderilir.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Eylem|`xs:string`|Giden iletinin SOAP eylemi üstbilgisi.|  
|Sözleşme adı|`xs:string`|Sözleşme adı. Örnek: ICalculator.|  
|Hedef|`xs:string`|Mesajın gönderilip gönderilmediği hizmet uç noktası adresi.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
