---
title: Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 362945959a781fac360c42475148fee1e47a1183
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960126"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme
Bağlantı parametrelerini açıklayan bağlamaları kullanarak WinFX istemciler arasında bağlantılar oluşturabilirsiniz. Eşler arası bağlantıları kullanmak için bir .NET Framework uygulamasına dönüştürme istemci bağlantıları yaparken bu teknolojiyi destekliyorsa bir bağlama gerektirir. Eş kanal adlı bir bağlama sağlar <xref:System.ServiceModel.NetPeerTcpBinding>, benzer bir şekilde kullanabileceğiniz <xref:System.ServiceModel.NetTcpBinding>. Temel farklılıklar çözümleyici hizmetini belirtme ve güvenlik ayarlarını tanımlama içerir.  
  
 Uygulamanın varsayılan çözümleyici ve güvenlik ayarlarını kullanıyorsa, eş kanaldan kullanmak için normal bir istemci/sunucu tabanlı uygulamaya dönüştürme "NetTcpBinding" bağlamayı adının değiştirilmesi "NetPeerTcpBinding için" içinde uygulamanın kapsar yapılandırma dosyası — uygulama kod tabanını değiştirmek zorunda değilsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanal Uygulaması Oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
- [Sistem Tarafından Sağlanan Bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)
