---
title: WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5bb6356ba4698cad00d443fdb80b1a45d35e2175
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme
Otomatik olarak başlatılmasını yeteneğini denetleyebilirsiniz [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Hizmet Konağı (WcfSvcHost.exe) için bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] birden çok proje içeren aynı Visual Studio çözümü başka bir projesinde hata ayıklarken hizmet kitaplığı projesi.  
  
 Bunu yapmak için sağ tıklatın [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet projesinde **Çözüm Gezgini**, seçin **özellikleri**, tıklatıp **WCF seçenekleri** sekmesi. **Başlat WCF hizmeti aynı çözüm başka bir projede hata ayıklama sırasında konak** onay kutusu varsayılan olarak etkindir. Kutusunu temizleyebilirsiniz böylece [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet konağı belirli bu proje için başka bir projeye aynı çözüm içinde hata ayıklaması sırasında değil başlattı.  
  
 Bu davranış F5 hata ayıklama veya bu proje için hizmet Başvurusu Ekle işlevler etkilemez.  
  
 Bu seçenek şu projeler için kullanılabilir:  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmet kitaplığı projesi.  
  
-   Sıralı iş akışı hizmeti kitaplığı projesi.  
  
-   Durum makinesi iş akışı hizmeti kitaplığı projesi.  
  
-   Dağıtım Hizmeti kitaplığı projesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
