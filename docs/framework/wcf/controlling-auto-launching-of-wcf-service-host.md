---
title: WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 7f21cd7ea600277461146387b962a89ea0a8472b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320622"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme
Birden çok proje içeren aynı Visual Studio çözümünde başka bir projede hata ayıkladığınızda, bir WCF hizmet kitaplığı projesi için Windows Communication Foundation (WCF) hizmet ana bilgisayarının otomatik başlatma özelliğini denetleyebilirsiniz.  
  
 Bunu yapmak için, **Çözüm Gezgini**' de WCF hizmeti projesine sağ tıklayın, **Özellikler**' i seçin ve **WCF seçenekleri** sekmesi ' ne tıklayın. **Aynı çözümdeki başka bir projenin hatalarını AYıKLARKEN WCF hizmet ana bilgisayarı Başlat** onay kutusu varsayılan olarak etkindir. Aynı çözümde başka bir proje hata ayıklaması yapıldığında, bu belirli proje için WCF hizmeti ana bilgisayarının başlatılmaması için kutuyu temizleyebilirsiniz.  
  
 Bu davranış, bu proje için F5 hata ayıklamayı veya Hizmet Başvurusu Ekle işlevlerini etkilemez.  
  
 Bu seçenek şu projeler için kullanılabilir:  
  
- WCF hizmet kitaplığı projesi.  
  
- Sıralı Iş akışı hizmet kitaplığı projesi.  
  
- Durum makinesi Iş akışı hizmet kitaplığı projesi.  
  
- Dağıtım hizmeti kitaplık projesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Hizmet Konağı (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
