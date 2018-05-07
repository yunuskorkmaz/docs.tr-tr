---
title: WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: fe936ee3ff42b586c733de597de808b86f3e2575
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme
İçin Windows Communication Foundation (WCF) Hizmet Konağı (WcfSvcHost.exe) otomatik olarak başlatılmasını yeteneğini denetleyen bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] birden çok proje içeren aynı Visual Studio çözümü başka bir projesinde hata ayıklarken hizmet kitaplığı projesi .  
  
 Bunu yapmak için sağ tıklatın [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet projesinde **Çözüm Gezgini**, seçin **özellikleri**, tıklatıp **WCF seçenekleri** sekmesi. **Başlat WCF hizmeti aynı çözüm başka bir projede hata ayıklama sırasında konak** onay kutusu varsayılan olarak etkindir. Kutusunu temizleyebilirsiniz böylece [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet konağı belirli bu proje için başka bir projeye aynı çözüm içinde hata ayıklaması sırasında değil başlattı.  
  
 Bu davranış F5 hata ayıklama veya bu proje için hizmet Başvurusu Ekle işlevler etkilemez.  
  
 Bu seçenek şu projeler için kullanılabilir:  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmet kitaplığı projesi.  
  
-   Sıralı iş akışı hizmeti kitaplığı projesi.  
  
-   Durum makinesi iş akışı hizmeti kitaplığı projesi.  
  
-   Dağıtım Hizmeti kitaplığı projesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
