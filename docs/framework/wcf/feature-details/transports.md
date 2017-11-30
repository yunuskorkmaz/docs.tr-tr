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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 115e2a69c7d990c7d4c59634644fb557e83ad405
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="transports-in-windows-communication-foundation"></a>Windows Communication Foundation'da Taşımalar
Aktarım katmanı kanal yığının en düşük düzeyinde bulunur. Kullanılan ana taşımalar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] HTTP, HTTPS, TCP ve adlandırılmış kanallar geçerlidir. Bu bölümdeki konular arasında bu taşımaları seçme, taşıma yapılandırma ve ayarlama özellikleri ayarlama tartışın.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ek taşımalar içerir. Message Queuing (MSMQ olarak da bilinir) taşıma hakkında daha fazla bilgi için bkz: [kuyruklar ve güvenilir oturumlar](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md). Eşler arası taşıma hakkında daha fazla bilgi için bkz: [eşler arası ağ](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Taşıma seçme](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 Üç ana aktarımları ve seçerek de ilgili önemli noktalar açıklanır.  
  
 [İleti Kodlayıcı seçme](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 Bir ileti kodlama bağlama öğesi seçerken göz önüne almanız gereken faktörler açıklanmaktadır.  
  
 [İleti aktarma akışı](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 Akış yapmak için Aktarım katmanı yapılandırılacağını açıklar.  
  
 [HTTP ve HTTPS yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 Bağlama öğeleri HTTP ve HTTPS taşıma yapılandırılacağını açıklar.  
  
 [Nasıl yapılır: WCF URL ayırmayı kısıtlı ayırma ile değiştirme](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Nasıl kullanılacağını açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]URL ayırmalarını kısıtlanmış.  
  
 [Taşıma kotaları](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 Aktarım katmanında kullanılabilir kotaları ayarlama konuları açıklanmaktadır.  
  
 [NAT ve güvenlik duvarları ile çalışma](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 İletileri gönderilen veya alınan bir güvenlik duvarının arkasında veya ağ adresi çevirisi (NAT) mevcut olduğunda, Aktarım katmanı yapılandırılacağını açıklar.  
  
 [Net.TCP bağlantı noktası paylaşımı](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 Net.TCP bağlantı noktası paylaşma bileşeninin kullanmayı açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Bağlamaları](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [Bağlamaları genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md)
