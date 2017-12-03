---
title: "WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60c7e2ddd4d4d57b675f2c12f8c5f567e8d23020
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme
Otomatik olarak başlatılmasını yeteneğini denetleyebilirsiniz [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Hizmet Konağı (WcfSvcHost.exe) için bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aynı başka bir projenin hata ayıklamasını yaparken hizmet kitaplığı proje [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] içeren birden çok proje çözümü.  
  
 Bunu yapmak için sağ tıklatın [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet projesinde **Çözüm Gezgini**, seçin **özellikleri**, tıklatıp **WCF seçenekleri** sekmesi. **Başlat WCF hizmeti aynı çözüm başka bir projede hata ayıklama sırasında konak** onay kutusu varsayılan olarak etkindir. Kutusunu temizleyebilirsiniz böylece [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet konağı belirli bu proje için başka bir projeye aynı çözüm içinde hata ayıklaması sırasında değil başlattı.  
  
 Bu davranış F5 hata ayıklama veya bu proje için hizmet Başvurusu Ekle işlevler etkilemez.  
  
 Bu seçenek şu projeler için kullanılabilir:  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Hizmet kitaplığı projesi.  
  
-   Sıralı iş akışı hizmeti kitaplığı projesi.  
  
-   Durum makinesi iş akışı hizmeti kitaplığı projesi.  
  
-   Dağıtım Hizmeti kitaplığı projesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
