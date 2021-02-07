---
description: 'Hakkında daha fazla bilgi edinin: WCF hizmet konağının otomatik olarak başlatılmasını denetleme'
title: WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: f0e9a4e79a403920c0bc6a512b30fb038b2aa1f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677398"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>WCF Hizmet Konağının Otomatik Olarak Başlatılmasını Denetleme

Birden çok proje içeren aynı Visual Studio çözümünde başka bir projede hata ayıklarken, bir WCF hizmet kitaplığı projesi için Windows Communication Foundation (WCF) hizmet ana bilgisayarı (WcfSvcHost.exe) otomatik başlatma özelliğini kontrol edebilirsiniz.  
  
 Bunu yapmak için, **Çözüm Gezgini**' de WCF hizmeti projesine sağ tıklayın, **Özellikler**' i seçin ve **WCF seçenekleri** sekmesi ' ne tıklayın. **Aynı çözümdeki başka bir projenin hatalarını AYıKLARKEN WCF hizmet ana bilgisayarı Başlat** onay kutusu varsayılan olarak etkindir. Aynı çözümde başka bir proje hata ayıklaması yapıldığında, bu belirli proje için WCF hizmeti ana bilgisayarının başlatılmaması için kutuyu temizleyebilirsiniz.  
  
 Bu davranış, bu proje için F5 hata ayıklamayı veya Hizmet Başvurusu Ekle işlevlerini etkilemez.  
  
 Bu seçenek şu projeler için kullanılabilir:  
  
- WCF hizmet kitaplığı projesi.  
  
- Sıralı Iş akışı hizmet kitaplığı projesi.  
  
- Durum makinesi Iş akışı hizmet kitaplığı projesi.  
  
- Dağıtım hizmeti kitaplık projesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Hizmet Ana Bilgisayarı (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
