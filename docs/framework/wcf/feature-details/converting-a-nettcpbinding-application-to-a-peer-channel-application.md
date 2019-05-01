---
title: Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 2daeb28ee984e6df576fc3da0aacc9d5f7497c96
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857305"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme
Kullanan istemciler arasında bağlantılar oluşturabilirsiniz [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] bağlantı parametrelerini açıklayan bağlamaları kullanarak. Dönüştürme bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] eşler arası bağlantıları kullanmak için uygulama istemci bağlantıları yaparken bu teknolojiyi destekliyorsa bir bağlama gerektirir. Eş kanal adlı bir bağlama sağlar <xref:System.ServiceModel.NetPeerTcpBinding>, benzer bir şekilde kullanabileceğiniz <xref:System.ServiceModel.NetTcpBinding>. Temel farklılıklar çözümleyici hizmetini belirtme ve güvenlik ayarlarını tanımlama içerir.  
  
 Uygulamanın varsayılan çözümleyici ve güvenlik ayarlarını kullanıyorsa, eş kanaldan kullanmak için normal bir istemci/sunucu tabanlı uygulamaya dönüştürme "NetTcpBinding" bağlamayı adının değiştirilmesi "NetPeerTcpBinding için" içinde uygulamanın kapsar yapılandırma dosyası — uygulama kod tabanını değiştirmek zorunda değilsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanal Uygulaması Oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
- [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)
