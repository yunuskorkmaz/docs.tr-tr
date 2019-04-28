---
title: 303 - UserDefinedInformationEventOccured
ms.date: 03/30/2017
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
ms.openlocfilehash: 0b782b5ac0527b5acb3ebf0bf11c117563042495
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61595787"
---
# <a name="303---userdefinedinformationeventoccured"></a>303 - UserDefinedInformationEventOccured
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|303|  
|anahtar sözcükler|Sorun giderme, ögesi, UserEvents, ServiceModel, EndToEndMonitoring|  
|Düzey|Bilgiler|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay kullanıcı kodundan yayılır. Geliştiriciler kendi hizmetinde özel tanımlı bilgilendirici bir olay meydana geldiğinde bu olay gönderebilir. Bu yapılabilir kullanarak <xref:System.Diagnostics.Eventing> API'leri. Ayrıca, bu API sarmalar ve bu olay düzgün bir şekilde yayma yapmayı gösteren bir WCF örnek yok.  
  
## <a name="message"></a>İleti  
 Ad: '%1', başvuru: '%2', yükü: % 3  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Ad|`xs:string`|Olayın kullanıcı tanımlı adı|  
|HostReference|`xs:string`|Bu alan, barındırılan Web Hizmetleri için Hizmet Web hiyerarşideki benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Yükü|`xs:string`|Kullanıcı tanımlı yükü olay.|
