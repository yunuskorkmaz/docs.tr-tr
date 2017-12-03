---
title: 213 - ServiceHostStarted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc12626263e21f5fd7310157dcdafe327e6d17a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="213---servicehoststarted"></a>213 - ServiceHostStarted
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|213|  
|Anahtar Sözcükler|Sorun giderme, ServiceHost EndToEndMonitoring, ögesi,|  
|Düzey|LogAlways|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir Web barındırılan hizmeti ana bilgisayar başlatıldığında bu olay yayınlanır. Bu, genelde hizmet tarafından bir ileti etkinleştirildiğinde gerçekleşir. Hizmet otomatik olarak başlatılacak şekilde yapılandırılmış olsa da oluşabilir.  
  
## <a name="message"></a>İleti  
 ServiceHost başlatıldı: '%1'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Hizmet türü adı|`xs:string`|Hizmet uygulama türü CLR tam adı.|  
|HostReference|`xs:string`|Bu alan, barındırılan Web Hizmetleri için Web hiyerarşi hizmetinde benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'. Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
