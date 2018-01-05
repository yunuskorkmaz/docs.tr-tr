---
title: "BindingElement Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0184d07210322e6ed04441f7190857cf07205b15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-bindingelement"></a>BindingElement Oluşturma
Bağlamalar ve bağlama öğeleri (genişletmek nesneleri <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>sırasıyla) yerlerdir nerede [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uygulama modeli, kanal fabrikaları ve kanal dinleyicileri ile ilişkilendirilmiş. Bağlamaları, özel kanalları kullanılarak programlama kanal düzeyinde açıklandığı gibi gerektirir [hizmet kanal düzeyi programlama](../../../../docs/framework/wcf/extending/service-channel-level-programming.md) ve [istemci kanal düzeyi programlama](../../../../docs/framework/wcf/extending/client-channel-level-programming.md). Bu konuda, kanalda kullanarak etkinleştirmek için en düşük gereksinim ele alınmıştır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], geliştirilmesi bir <xref:System.ServiceModel.Channels.BindingElement> kanal ve 4. adımda açıklandığı gibi uygulama etkinleştir kullanımdan [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="overview"></a>Genel Bakış  
 Oluşturma bir <xref:System.ServiceModel.Channels.BindingElement> kanalınızı kullanmayı geliştiricilerinin için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama. <xref:System.ServiceModel.Channels.BindingElement>nesneleri, gelen kullanılabilir <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> bağlanmak için sınıf bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanalınızı kesin türü bilgilerinin kalmadan kanalınızı uygulamaya.  
  
 Bir kez bir <xref:System.ServiceModel.Channels.BindingElement> bırakıldı oluşturulan, kalan kanal geliştirme adımları açıklanan izleyerek, gereksinimlerinize bağlı olarak daha fazla işlevsellik etkinleştirebilirsiniz [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="adding-a-binding-element"></a>Bir bağlama öğesi ekleme  
 Özel bir uygulamak için <xref:System.ServiceModel.Channels.BindingElement>, öğesinden devralınan bir sınıf yazma <xref:System.ServiceModel.Channels.BindingElement>. Geliştirdiyseniz, örneğin, bir `ChunkingChannel` , büyük iletileri parçalara bölmeniz ve bunları diğer tarafta yeniden birleştirmek, uygulayarak bu kanal herhangi bağlamada kullanabileceğiniz bir <xref:System.ServiceModel.Channels.BindingElement> ve bağlama kullanmak için yapılandırma. Bu konunun geri kalanında kullanan `ChunkingChannel` bağlama öğesi uygulama gereksinimleri göstermek için bir örnek olarak.  
  
 A `ChunkingBindingElement` oluşturmaktan sorumlu `ChunkingChannelFactory` ve `ChunkingChannelListener`. Bu geçersiz kılar <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> ve <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> uygulamaları ve tür parametresi olup olmadığını denetler <xref:System.ServiceModel.Channels.IDuplexSessionChannel> (örneğimizde tarafından desteklenen tek kanal şekli budur `ChunkingChannel`) ve bağlamayı diğer bağlama öğeleri bu destek Kanal şekli.  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A>ilk denetler istenen kanal şekli oluşturulabilir ve öbekli için ileti eylemlerin bir listesini alır. Ardından yeni bir oluşturur `ChunkingChannelFactory`, iç kanal fabrikası geçirme. (Bir aktarım bağlama öğesi oluşturuyorsanız, o öğeye bağlama yığınında son sunucudur ve bu nedenle kanal dinleyicisi veya kanal fabrikası oluşturmanız gerekir.)  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A>oluşturma için benzer bir uygulamaya sahip `ChunkingChannelListener` ve iç kanal dinleyicisi geçirme.  
  
 Bir taşıma kanalı kullanılarak başka bir örnek olarak [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneği aşağıdaki geçersiz kılma sağlar.  
  
 Örnekte, bağlama öğedir `UdpTransportBindingElement`, den türetilen <xref:System.ServiceModel.Channels.TransportBindingElement>. Bu kanal ile ilişkilendirilen oluşturucuları oluşturmak için aşağıdaki yöntemleri geçersiz kılar.  
  
```  
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
            return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
            return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 Kopyalama için de üyeleri içeren `BindingElement` ve bizim düzenini (soap.udp) döndürüyor.  
  
#### <a name="protocol-binding-elements"></a>Protokol bağlama öğeleri  
 Yeni bağlama öğeleri değiştirin veya herhangi bir yeni aktarımlar, kodlamaları veya üst düzey iletişim kuralları ekleme içerdiği bağlama öğelerinin kullanmasıdır. Genişleterek bağlama yeni bir protokol öğesi oluşturmak için başlangıç <xref:System.ServiceModel.Channels.BindingElement> sınıfı. En azından, ardından uygulamalıdır <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType> ve uygulamanıza `ChannelProtectionRequirements` kullanarak <xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType>. Bu döndürür <xref:System.ServiceModel.Security.ChannelProtectionRequirements> Bu bağlama öğesi için.  Daha fazla bilgi için bkz. <xref:System.ServiceModel.Security.ChannelProtectionRequirements>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>Bu bağlama öğesi yeni bir kopyasını döndürmelidir. En iyi uygulama, bu bağlama öğesi yazarlarına uygulama olan öneririz <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> temel kopya Oluşturucu çağıran kopya Oluşturucu kullanarak, daha sonra bu sınıftaki ek alanlar klonlar.  
  
#### <a name="transport-binding-elements"></a>Bağlama öğeleri taşıma  
 Yeni bir aktarım bağlama öğesi oluşturmak için genişletme <xref:System.ServiceModel.Channels.TransportBindingElement> arabirimi. En azından, ardından uygulamalıdır <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> yöntemi ve <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType> özelliği.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>– Bu bağlama öğesinin yeni bir kopya döndürmelidir.  En iyi uygulama, bağlama öğesi yazarların temel kopya oluşturucu çağırır ve ardından bu sınıftaki ek alanlar klonlar kopya Oluşturucu yapmamanız kopya uygulamak öneririz.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A>– <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> Bağlama öğesi tarafından temsil edilen aktarım protokolü için URI şeması özelliği döndürür alın. Örneğin, <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType> döndürmek "http" ve "net.tcp" kendi ilgili <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> özellikleri.  
  
#### <a name="encoding-binding-elements"></a>Kodlama bağlama öğeleri  
 Genişleterek yeni kodlama bağlama öğeleri oluşturmak için başlangıç <xref:System.ServiceModel.Channels.BindingElement> sınıfı ve uygulama <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType> sınıfı. En azından, ardından uygulamalıdır <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> yöntemleri ve <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType> özelliği.  
  
-   <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>. Bu bağlama öğesi yeni bir kopyasını döndürür. En iyi uygulama, bu bağlama öğesi yazarlarına uygulama olan öneririz <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> temel kopya Oluşturucu çağıran kopya Oluşturucu kullanarak, daha sonra bu sınıftaki ek alanlar klonlar.  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>. Döndürür bir <xref:System.ServiceModel.Channels.MessageEncoderFactory>, hangi gerçek sınıf için bir tanıtıcı sağlayan yeni kodlayıcıyı ve hangi genişletmelidir uygulayan <xref:System.ServiceModel.Channels.MessageEncoder>. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Channels.MessageEncoderFactory> ve <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>. Döndürür <xref:System.ServiceModel.Channels.MessageVersion> bu kodlama kullanıldığında, temsil eden sürümlerinde SOAP ve WS adresleme kullanın.  
  
 İsteğe bağlı yöntemleri ve özellikleri kullanıcı tanımlı kodlama bağlama öğeleri için tam bir listesi için bkz: <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 Yeni bir bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz: [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
 Bir bağlama öğesi için kanalınızı oluşturduktan sonra geri dönüp [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md) olup, bağlama öğesi için yapılandırma dosyası desteği eklemek, istediğiniz ve meta veri yayın desteği ekleme görmek için konu ve olup olmadığını ve bağlama öğesi kullanan bir kullanıcı tarafından tanımlanan bağlama oluşturmak için nasıl.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [Geliştirme Kanalları](../../../../docs/framework/wcf/extending/developing-channels.md)  
 [Taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
