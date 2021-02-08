---
description: 'Hakkında daha fazla bilgi edinin: bir NetTcpBinding uygulamasını eş kanal uygulamasına dönüştürme'
title: Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 828ffce38fb05acff851c9fe5a6fbb38fffad6aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780420"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme

Bağlantı parametrelerini tanımlayan bağlamaları kullanarak, WinFX kullanarak istemciler arasında bağlantılar oluşturabilirsiniz. Bir .NET Framework uygulamasını eşler arası bağlantıları kullanacak şekilde dönüştürmek, istemci bağlantıları yaparken bu teknolojiyi destekleyen bir bağlama gerektirir. Eş kanal, <xref:System.ServiceModel.NetPeerTcpBinding> ile benzer bir şekilde kullanabileceğiniz, adlı bir bağlama sağlar <xref:System.ServiceModel.NetTcpBinding> . Temel farklılıklar, bir çözümleyici Hizmeti belirtmeyi ve güvenlik ayarlarını tanımlamayı içerir.  
  
 Bir uygulama varsayılan çözümleyici ve güvenlik ayarlarını kullanıyorsa, normal bir istemci/sunucu tabanlı uygulamayı eş kanalını kullanacak şekilde dönüştürmek, uygulamanın yapılandırma dosyasında "NetTcpBinding" olan bağlamanın "NetPeerTcpBinding" olarak değiştirilmesini gerektirir; uygulama kodu tabanını değiştirmeniz gerekmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanal Uygulaması Oluşturma](building-a-peer-channel-application.md)
- [Sistem Tarafından Sağlanan Bağlamalar](../system-provided-bindings.md)
