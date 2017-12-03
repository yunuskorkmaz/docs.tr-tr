---
title: 219 - ServiceException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5750748f2885418b8992ce54bbdf6a92b8e1fe39
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="219---serviceexception"></a>219 - ServiceException
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|219|  
|Anahtar Sözcükler|Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir WCF Hizmeti işlenmeyen bir özel durum karşılaştığında bu olay yayınlanır. Bu etkinleştirme, ileti işleme sırasında ve kullanıcı kodu sırasında işlenmeyen özel durumları içerir.  
  
## <a name="message"></a>İleti  
 İleti işleme sırasında '%2' türünde işlenmeyen bir özel durum oluştu. ToString tam özel durum: %1.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|ExceptionToString|`xs:string`|Arama sonucu `ToString`CLR özel durumunda ().|  
|ExceptionTypeName|`xs:string`|Özel durumun türü CLR tam adı.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'. Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
