---
title: "Windows Communication Foundation'da Taşımalar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62eb27919e762004667b3d5179c35cb04d9a9422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="transports-in-windows-communication-foundation"></a>Windows Communication Foundation'da Taşımalar
Aktarım katmanı kanal yığının en düşük düzeyinde bulunur. Kullanılan ana taşımalar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] HTTP, HTTPS, TCP ve adlandırılmış kanallar geçerlidir. Bu bölümdeki konular arasında bu taşımaları seçme, taşıma yapılandırma ve ayarlama özellikleri ayarlama tartışın.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ek taşımalar içerir. Message Queuing (MSMQ olarak da bilinir) taşıma hakkında daha fazla bilgi için bkz: [kuyruklar ve güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md). Eşler arası taşıma hakkında daha fazla bilgi için bkz: [eşler arası ağ](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Taşıma Seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 Üç ana aktarımları ve seçerek de ilgili önemli noktalar açıklanır.  
  
 [İleti Kodlayıcı Seçme](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 Bir ileti kodlama bağlama öğesi seçerken göz önüne almanız gereken faktörler açıklanmaktadır.  
  
 [İleti Aktarma Akışı](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 Akış yapmak için Aktarım katmanı yapılandırılacağını açıklar.  
  
 [HTTP ve HTTPS Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 Bağlama öğeleri HTTP ve HTTPS taşıma yapılandırılacağını açıklar.  
  
 [Nasıl yapılır: WCF URL Ayırmayı Kısıtlı Ayırma ile Değiştirme](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Nasıl kullanılacağını açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]URL ayırmalarını kısıtlanmış.  
  
 [Taşıma Kotaları](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 Aktarım katmanında kullanılabilir kotaları ayarlama konuları açıklanmaktadır.  
  
 [NAT ve Güvenlik Duvarlarıyla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 İletileri gönderilen veya alınan bir güvenlik duvarının arkasında veya ağ adresi çevirisi (NAT) mevcut olduğunda, Aktarım katmanı yapılandırılacağını açıklar.  
  
 [Net.TCP Bağlantı Noktası Paylaşımı](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 Net.TCP bağlantı noktası paylaşma bileşeninin kullanmayı açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Bağlamalar](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [Bağlamaları Genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md)
