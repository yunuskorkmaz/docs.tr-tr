---
title: 213 - ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 819efa2e13c94e2c7a16c24f6ba9c7ef2b87ef8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781829"
---
# <a name="213---servicehoststarted"></a>213 - ServiceHostStarted
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|213|  
|anahtar sözcükler|Sorun giderme, ServiceHost EndToEndMonitoring, ögesi,|  
|Düzey|LogAlways|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bir Web servisinin ana bilgisayar başlatıldığında bu olay yayılır. Bu durum, genellikle bir ileti hizmeti etkin olduğunda gerçekleşir. Hizmet otomatik olarak başlatılacak şekilde yapılandırılmışsa da oluşabilir.  
  
## <a name="message"></a>İleti  
 ServiceHost başlatıldı: '%1'.  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Hizmet türü adı|`xs:string`|Hizmet uygulaması türü CLR tam adı.|  
|HostReference|`xs:string`|Bu alan, barındırılan Web Hizmetleri için Hizmet Web hiyerarşideki benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.|
