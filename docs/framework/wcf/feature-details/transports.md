---
title: Windows Communication Foundation'da Taşımalar
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 077d63d8038b245a68083611897c1e6c68971071
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598677"
---
# <a name="transports-in-windows-communication-foundation"></a>Windows Communication Foundation'da Taşımalar
Aktarım katmanı, kanal yığınının en düşük düzeyindedir. Windows Communication Foundation (WCF) ' de kullanılan ana aktarımlar HTTP, HTTPS, TCP ve adlandırılmış kanallardır. Bu bölümdeki konular, bu aktarımlar arasında seçim yapma, taşımayı yapılandırma ve ayarlama özelliklerini ayarlama hakkında tartışın.  
  
 WCF ek aktarımlar içerir. Message Queuing (MSMQ olarak da bilinir) taşıma hakkında daha fazla bilgi için bkz. [Kuyruklar ve güvenilir oturumlar](queues-and-reliable-sessions.md). Eşler arası aktarım hakkında daha fazla bilgi için bkz. eşler [arası ağ iletişimi](peer-to-peer-networking.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Taşıma Seçme](choosing-a-transport.md)  
 Üç ana aktarım ve seçim ile ilgili dikkat edilmesi gerekenler açıklanmaktadır.  
  
 [İleti Kodlayıcı Seçme](choosing-a-message-encoder.md)  
 İleti kodlama bağlama öğesi seçerken göz önünde bulundurmanız gereken faktörleri açıklar.  
  
 [İleti Aktarma Akışı](streaming-message-transfer.md)  
 Akış yapmak için aktarım katmanının nasıl yapılandırılacağını açıklar.  
  
 [HTTP ve HTTPS Yapılandırma](configuring-http-and-https.md)  
 HTTP ve HTTPS aktarım bağlama öğelerinin nasıl yapılandırılacağını açıklar.  
  
 [Nasıl yapılır: WCF URL Ayırmayı Kısıtlı Ayırma ile Değiştirme](how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 WCFURL kısıtlı ayırmaları kullanmayı açıklar.  
  
 [Taşıma Kotaları](transport-quotas.md)  
 Aktarım katmanında kullanılabilir kotaları ayarlamayla ilgili önemli noktaları açıklar.  
  
 [NAT ve Güvenlik Duvarlarıyla Çalışma](working-with-nats-and-firewalls.md)  
 Bir güvenlik duvarının arkasında veya ağ adresi çevirisi (NAT) olduğunda iletiler gönderildiğinde veya alındığında aktarım katmanının nasıl yapılandırılacağını açıklar.  
  
 [Net.TCP Bağlantı Noktası Paylaşımı](net-tcp-port-sharing.md)  
 WCF 'nin net. TCP bağlantı noktası paylaşma bileşeninin nasıl kullanılacağını açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Bağlamalar](bindings.md)  
  
 [Bağlamaları Genişletme](../extending/extending-bindings.md)
