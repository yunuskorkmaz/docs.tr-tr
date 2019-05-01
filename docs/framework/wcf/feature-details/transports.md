---
title: Windows Communication Foundation'da Taşımalar
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 6bb8e8b90c26533661684bd403b9ec439f1bb37e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933737"
---
# <a name="transports-in-windows-communication-foundation"></a>Windows Communication Foundation'da Taşımalar
Kanal yığının en düşük düzey aktarım katmanıdır. Windows Communication Foundation (WCF) kullanılan ana taşımalar, HTTP, HTTPS, TCP ve adlandırılmış kanallar ' dir. Bu bölümdeki konular arasında bu taşımaları seçme, aktarım yapılandırma ve ayarlama özellikleri ayarlama açıklanmaktadır.  
  
 WCF ek taşımalar içerir. Message Queuing (MSMQ olarak da bilinir) taşıma hakkında daha fazla bilgi için bkz. [kuyruklar ve güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md). Eşler arası taşıma hakkında daha fazla bilgi için bkz. [eşler arası ağ](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Taşıma Seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 Üç ana aktarımları ve bir seçerken konularını açıklar.  
  
 [İleti Kodlayıcı Seçme](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 Bir ileti kodlama bağlama öğesi seçerken dikkate alınması gereken faktörler açıklanmaktadır.  
  
 [İleti Aktarma Akışı](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 Akış yapmak için Aktarım katmanı yapılandırılması açıklanmaktadır.  
  
 [HTTP ve HTTPS Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 HTTP ve HTTPS aktarım bağlama öğelerinin yapılandırılması açıklanmaktadır.  
  
 [Nasıl yapılır: WCF URL ayırmayı kısıtlı ayırma ile değiştirme](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Kısıtlı WCFURL ayırmaları kullanmayı açıklar.  
  
 [Taşıma Kotaları](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 Aktarım katmanında kullanılabilir kotaları ayarlama konuları açıklanmaktadır.  
  
 [NAT ve Güvenlik Duvarlarıyla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 Aktarım katmanı gönderilen ya da bir güvenlik duvarının arkasındaki veya ağ adresi çevirisi (NAT) olduğunda alınan iletileri yapılandırılması açıklanmaktadır.  
  
 [Net.TCP Bağlantı Noktası Paylaşımı](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 Net.TCP bağlantı noktası paylaşımı bileşen WCF kullanmayı açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Bağlamalar](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [Bağlamaları Genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md)
