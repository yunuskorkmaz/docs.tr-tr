---
title: Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 42266d8c7c04e2d8f3f1e4734d9a05181c3f1ea3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595563"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme
Bağlantı parametrelerini tanımlayan bağlamaları kullanarak, WinFX kullanarak istemciler arasında bağlantılar oluşturabilirsiniz. Bir .NET Framework uygulamasını eşler arası bağlantıları kullanacak şekilde dönüştürmek, istemci bağlantıları yaparken bu teknolojiyi destekleyen bir bağlama gerektirir. Eş kanal, <xref:System.ServiceModel.NetPeerTcpBinding> ile benzer bir şekilde kullanabileceğiniz, adlı bir bağlama sağlar <xref:System.ServiceModel.NetTcpBinding> . Temel farklılıklar, bir çözümleyici Hizmeti belirtmeyi ve güvenlik ayarlarını tanımlamayı içerir.  
  
 Bir uygulama varsayılan çözümleyici ve güvenlik ayarlarını kullanıyorsa, normal bir istemci/sunucu tabanlı uygulamayı eş kanalını kullanacak şekilde dönüştürmek, uygulamanın yapılandırma dosyasında "NetTcpBinding" olan bağlamanın "NetPeerTcpBinding" olarak değiştirilmesini gerektirir; uygulama kodu tabanını değiştirmeniz gerekmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanal Uygulaması Oluşturma](building-a-peer-channel-application.md)
- [Sistem tarafından sağlanmış bağlamalar](../system-provided-bindings.md)
