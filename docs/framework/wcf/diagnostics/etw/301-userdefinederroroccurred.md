---
title: 301 - UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 6eb80d6f0b20af9aae6e7de5248323088e352b26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596485"
---
# <a name="301---userdefinederroroccurred"></a>301 - UserDefinedErrorOccurred
## <a name="properties"></a>Özellikler  
  
|||  
|-|-|  
|Kimlik|301|  
|anahtar sözcükler|Sorun giderme, ögesi, UserEvents, ServiceModel, EndToEndMonitoring|  
|Düzey|Hata|  
|Kanal|Microsoft Windows uygulama sunucusu-uygulamalar/analitik|  
  
## <a name="description"></a>Açıklama  
 Bu olay kullanıcı kodundan yayılır. Geliştiriciler kendi hizmetinde özel tanımlı bir hata oluştuğunda bu olay gönderebilir. Bu yapılabilir kullanarak <xref:System.Diagnostics.Eventing> API'leri. Ayrıca, bu API sarmalar ve bu olay düzgün bir şekilde yayma yapmayı gösteren bir WCF örnek yok.  
  
## <a name="message"></a>İleti  
 Ad: '%1', başvuru: '%2', yükü: % 3  
  
## <a name="details"></a>Ayrıntılar  
  
|Veri öğesi adı|Veri öğesi türü|Açıklama|  
|--------------------|--------------------|-----------------|  
|Ad|`xs:string`|Kullanıcı tanımlı olayın adı.|  
|HostReference|`xs:string`|Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar. Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '. Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|Yükü|`xs:string`|Kullanıcı tanımlı yükü olay.|
