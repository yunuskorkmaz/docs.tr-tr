---
title: 301 - UserDefinedErrorOccurred
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 56cfe60c221062e3ad7ae1b8cbdc9b135e6fa2e8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="301---userdefinederroroccurred"></a>301 - UserDefinedErrorOccurred
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|301|  
|Anahtar Sözcükler|Sorun giderme, ögesi, UserEvents, ServiceModel, EndToEndMonitoring|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay, kullanıcı kodundan yayınlanır. Geliştiriciler kendi hizmetinde özel tanımlanmış bir hata oluştuğunda bu olay yayma. Bu yapılabilir kullanarak <xref:System.Diagnostics.Eventing> API'leri. Ayrıca, bu API sarmalar ve bu olay düzgün bir şekilde yayma yapmayı gösteren bir WCF örneği yoktur.  
  
## <a name="message"></a>İleti  
 Ad: '%1', başvuru: '%2', yük: % 3  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Ad|`xs:string`|Kullanıcı tanımlı olayın adı.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'. Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.|  
|Yükü|`xs:string`|Kullanıcı tanımlı yükü olay.|
