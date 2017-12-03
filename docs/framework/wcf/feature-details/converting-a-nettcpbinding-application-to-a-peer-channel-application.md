---
title: "Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d52b005013e9728cfcdb43ad289984018b90d27c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme
Kullanan istemciler arasında bağlantılar oluşturabilirsiniz [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] bağlantı parametreleri açıklayan bağlamaları kullanarak. Dönüştürme bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] eşler arası bağlantılar kullanmak için uygulama, istemci bağlantıları yaparken bu teknolojiyi destekliyorsa bir bağlama gerektirir. Eş kanal sağlar adlı bir bağlama <xref:System.ServiceModel.NetPeerTcpBinding>, benzer bir şekilde kullanabileceğiniz <xref:System.ServiceModel.NetTcpBinding>. Temel farklılıklar bir çözümleyicisini belirtme ve güvenlik ayarları tanımlama içerir.  
  
 Bir uygulama varsayılan çözümleyici ve güvenlik ayarlarını kullanıyorsa, eş kanalı kullanmak için normal bir istemci/sunucu tabanlı uygulamaya dönüştürme "NetTcpBinding" bağlamayı adının değiştirilmesi "NetPeerTcpBinding" uygulamanın içinde kapsar yapılandırma dosyası — uygulama kod tabanını değiştirmek zorunda değilsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eş kanal uygulaması oluşturma](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)  
 [Sistem tarafından sağlanan bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md)
