---
title: "Geliştirme Kanalları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dd33f987ab28b42c16aa4798c59675225dcaf520
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="developing-channels"></a>Geliştirme Kanalları
İle kullanılan protokolü veya taşıma kanal geliştirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uygulama katmanı çeşitli adımlar gerektirir. Bu konu, bu adımları açıklar ve daha fazla bilgi için belirli konular işaret eder. Kanal modeli ve bu konuda açıklanan çeşitli türlerini anlamak için bkz: [kanal modeli genel bakış](../../../../docs/framework/wcf/extending/channel-model-overview.md). Tam aktarım kanal örnek için bkz [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md).  
  
## <a name="the-channel-development-task-list"></a>Kanal geliştirme görev listesi  
 Kullanıcı tanımlı bir kanal oluşturmak için adımlar aşağıdaki gibidir. Tüm kanalları gerekir:  
  
1.  İleti Exchange desenleri kanalının karar (<xref:System.ServiceModel.Channels.IOutputChannel>, <xref:System.ServiceModel.Channels.IInputChannel>, <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IRequestChannel>, veya <xref:System.ServiceModel.Channels.IReplyChannel>), <xref:System.ServiceModel.Channels.IChannelFactory> ve <xref:System.ServiceModel.Channels.IChannelListener> , sessionful destekleyip yanı sıra destekleyecek Bu arabirimleri çeşidi. Ayrıntılar için bkz [bir ileti değişim deseni seçin](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md).  
  
2.  Bir kanal fabrikası ve dinleyici oluşturun (<xref:System.ServiceModel.Channels.IChannelFactory> ve <xref:System.ServiceModel.Channels.IChannelListener>) ileti değişim deseni destekler. Oluşturucuları geliştirme hakkında daha fazla bilgi için bkz: [istemci: kanal fabrikaları ve kanallar](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md). Dinleyicileri geliştirme hakkında daha fazla bilgi için bkz: [hizmet: kanal dinleyicileri ve kanallar](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md).  
  
3.  Ağa özgü özel durumlar ya da normalleştirilmiş emin olun <xref:System.TimeoutException?displayProperty=nameWithType> veya uygun türetilmiş sınıf <xref:System.ServiceModel.CommunicationException>. Ayrıntılar için bkz [özel durum işleme ve hataları](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
4.  Uygulama katmanı kullanımdan etkinleştirmek için add bir <xref:System.ServiceModel.Channels.BindingElement> , özel kanalda bir kanal yığınına ekler. Daha fazla bilgi için bkz: [BindingElement oluşturma](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md).  
  
 Uygulama katmanı daha kapsamlı desteğini etkinleştirmek için aşağıdaki ek adımları gereklidir:  
  
1.  Yapılandırma sistemi için yeni bir bağlama öğesi kullanıma sunmak için bir bağlama öğesi uzantısı bölümü ekleyin. Daha fazla bilgi için bkz: [yapılandırma ve meta verileri desteği](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
2.  Diğer uç noktalara Özellikleri iletişim kurmak için meta verileri uzantıları ekleyin. Daha fazla bilgi için bkz: [yapılandırma ve meta verileri desteği](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
3.  Bağlama öğeleri iyi tanımlanmış bir profili göre yığınını önceden yapılandırır bir bağlaması ekleyin. Daha fazla bilgi için bkz: [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
4.  Bir bağlama bölümü ve yapılandırma sistemi bağlamayı kullanıma sunmak için bağlama yapılandırma öğesi ekleyin. Daha fazla bilgi için bkz: [yapılandırma ve meta verileri desteği](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlamaları genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md)
