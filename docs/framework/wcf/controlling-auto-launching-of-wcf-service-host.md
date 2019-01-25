---
title: WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: f7f58a684449819fe945ad1ba5bff12f425c8294
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712398"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme
Aynı Visual Studio çözümde birden çok proje içeren başka bir projede hata ayıklaması yaparken, bir WCF hizmet kitaplığı projesi için Windows Communication Foundation (WCF) hizmet ana bilgisayarı (WcfSvcHost.exe) otomatik olarak başlatılmasını yeteneğini denetleyebilirsiniz.  
  
 Bunu yapmak için WCF Hizmeti projeye sağ tıklayın **Çözüm Gezgini**, seçin **özellikleri**, tıklatıp **WCF seçenekleri** sekmesi. **Başlat WCF hizmet aynı çözümdeki başka bir proje hata ayıklama konağı** onay kutusu varsayılan olarak etkindir. Böylece bu belirli proje için WCF hizmet konağı aynı çözümdeki başka bir projenin hataları ayıklandığında başlatılmaz kutusunun işaretini kaldırabilirsiniz.  
  
 F5 hata ayıklaması veya hizmet Başvurusu Ekle işlevleri bu proje için bu davranışı etkilemez.  
  
 Bu seçenek, aşağıdaki projeler için kullanılabilir:  
  
-   WCF hizmet kitaplığı projesi.  
  
-   Sıralı iş akışı hizmet kitaplığı projesi.  
  
-   Durum makinesi iş akışı hizmet kitaplığı projesi.  
  
-   Dağıtım hizmet kitaplığı projesi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WCF Hizmet Konağı (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
