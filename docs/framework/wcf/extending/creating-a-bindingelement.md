---
title: BindingElement Oluşturma
ms.date: 03/30/2017
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
ms.openlocfilehash: 600bf9b394078ffc1b1bc97390bd0de406d64338
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115173"
---
# <a name="creating-a-bindingelement"></a>BindingElement Oluşturma
Bağlamalar ve bağlama öğeleri (genişletirler <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>sırasıyla) Windows Communication Foundation (WCF) uygulama modeli olduğu kanal fabrikaları ve kanal dinleyicileri ile ilişkili yerdir. Bağlamaları kullanarak özel kanallar kanal düzeyi programlama açıklandığı gerektirir [hizmet kanal düzeyi programlama](../../../../docs/framework/wcf/extending/service-channel-level-programming.md) ve [istemci kanal düzeyi programlama](../../../../docs/framework/wcf/extending/client-channel-level-programming.md). Bu konuda, WCF, geliştirme sürecini kanalınızı kullanarak etkinleştirmek için en düşük gereksinim ele alınmaktadır bir <xref:System.ServiceModel.Channels.BindingElement> kanal ve etkinleştirme kullanımdan 4 adımda açıklandığı gibi uygulama için [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="overview"></a>Genel Bakış  
 Oluşturma bir <xref:System.ServiceModel.Channels.BindingElement> kanalınızı geliştiricilerin WCF uygulamada kullanmasına olanak sağlar. <xref:System.ServiceModel.Channels.BindingElement> nesneleri, gelen kullanılabilir <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> kanalınızı kesin tür bilgilerinin zorunda kalmadan kanalınızı WCF uygulamaya bağlanmak için sınıf.  
  
 Bir kez bir <xref:System.ServiceModel.Channels.BindingElement> olmuştur oluşturulan kanal geliştirme adımlardan açıklanan izleyerek, gereksinimlerinize bağlı olarak daha fazla işlevsellik etkinleştirebilirsiniz [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="adding-a-binding-element"></a>Bir bağlama öğesi ekleniyor  
 Özel bir uygulama <xref:System.ServiceModel.Channels.BindingElement>, devralınan bir sınıf yazma <xref:System.ServiceModel.Channels.BindingElement>. Örneğin, kendi geliştirdiğiniz bir `ChunkingChannel` , büyük, iletileri parçalara bölün ve bunları diğer tarafta gerektirdiğinden verimsizliklere neden olabilir, bu kanal uygulayarak herhangi bir bağlamayı kullanabilirsiniz bir <xref:System.ServiceModel.Channels.BindingElement> ve kullanmak için bağlama yapılandırma. Bu konunun geri kalanı kullanan `ChunkingChannel` bir bağlama öğesi uygulama gereksinimleri göstermek için örnek olarak.  
  
 A `ChunkingBindingElement` oluşturmaktan sorumlu `ChunkingChannelFactory` ve `ChunkingChannelListener`. Onu geçersiz kılar <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> ve <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> uygulamaları ve tür parametresi olup olmadığını denetler <xref:System.ServiceModel.Channels.IDuplexSessionChannel> (Bizim örneğimizde tarafından desteklenen tek kanal şekli budur `ChunkingChannel`) ve bağlamayı diğer bağlama öğeleri bu destek Kanal şekli.  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> ilk denetler istenen kanal şekli oluşturulabilir ve ardından öbekli için ileti eylemlerin bir listesini alır. Ardından yeni bir oluşturur `ChunkingChannelFactory`, iç kanal fabrikası geçirme. (Bir aktarım bağlama öğesi oluşturuyorsanız, o öğe bağlama yığınında sonuncu ise ve bu nedenle, bir kanal dinleyicisi veya kanal fabrikası oluşturmanız gerekir.)  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> oluşturmak için benzer bir uygulamaya sahip `ChunkingChannelListener` ve iç kanal dinleyicisi geçirme.  
  
 Bir taşıma kanalı kullanılarak başka bir örnek [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek, aşağıdaki geçersiz kılmayı sağlar.  
  
 Bu örnekte bağlama öğedir `UdpTransportBindingElement`, öğesinden türetildiğini <xref:System.ServiceModel.Channels.TransportBindingElement>. Bu kanal ile ilişkilendirilen fabrikaları oluşturmak için aşağıdaki yöntemleri geçersiz kılar.  
  
```csharp  
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 Kopyalama için de üyeleri içeren `BindingElement` ve bizim (soap.udp) şeması döndürüyor.  
  
#### <a name="protocol-binding-elements"></a>Protokol bağlama öğeleri  
 Yeni bağlama öğeleri, değiştirin veya herhangi bir yeni taşımaları, Kodlamalar ya da daha üst düzey protokolleri ekleme içerdiği bağlama öğelerinin artırabilir. Bağlama yeni bir protokol öğesi oluşturmak için başlangıç genişleterek <xref:System.ServiceModel.Channels.BindingElement> sınıfı. En azından, ardından uygulamalıdır <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType> ve uygulama `ChannelProtectionRequirements` kullanarak <xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType>. Bu döndürür <xref:System.ServiceModel.Security.ChannelProtectionRequirements> Bu bağlama öğesi için.  Daha fazla bilgi için bkz. <xref:System.ServiceModel.Security.ChannelProtectionRequirements>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> Bu bağlama öğesi yeni bir kopyasını döndürmelidir. En iyi uygulama, bu bağlama öğesi Uygulama yazarlarına olan öneririz <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> temel Kopyala oluşturucusunu çağırır bir kopya Oluşturucu kullanarak, ardından bu sınıftaki herhangi bir ek alanlar kopyalar.  
  
#### <a name="transport-binding-elements"></a>Aktarım bağlama öğeleriyle  
 Yeni bir aktarım bağlama öğesi oluşturmak için genişletme <xref:System.ServiceModel.Channels.TransportBindingElement> arabirimi. En azından, ardından uygulamalıdır <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> yöntemi ve <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType> özelliği.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> – Bu bağlama öğesi yeni bir kopyasını döndürmelidir.  En iyi uygulama, bağlama öğesi yazarların temel Kopyala oluşturucusunu çağırır ve ardından bu sınıftaki herhangi bir ek alanlar klonlar bir kopya Oluşturucusu yoluyla kopyalama uygulamak öneririz.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> – <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> Bağlama öğesi tarafından temsil edilen aktarım protokolü için URI şeması özelliği döndürür alın. Örneğin, <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> ve <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType> döndürür "http" ve "net.tcp" kendi ilgili <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> özellikleri.  
  
#### <a name="encoding-binding-elements"></a>Kodlama bağlama öğeleri  
 Yeni kodlama bağlama öğeleri oluşturmak için başlangıç genişleterek <xref:System.ServiceModel.Channels.BindingElement> sınıfı ve uygulama <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType> sınıfı. En azından, ardından uygulamalıdır <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> yöntemleri ve <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType> özelliği.  
  
-   <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>. Bu bağlama öğesi yeni bir kopyasını döndürür. En iyi uygulama, bu bağlama öğesi Uygulama yazarlarına olan öneririz <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> temel Kopyala oluşturucusunu çağırır bir kopya Oluşturucu kullanarak, ardından bu sınıftaki herhangi bir ek alanlar kopyalar.  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>. Döndürür bir <xref:System.ServiceModel.Channels.MessageEncoderFactory>, gerçek sınıfı için bir tanıtıcı, sağlayan yeni kodlayıcınız ve hangi genişletmelidir uygulayan <xref:System.ServiceModel.Channels.MessageEncoder>. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Channels.MessageEncoderFactory> ve <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>. Döndürür <xref:System.ServiceModel.Channels.MessageVersion> bu kodlama kullanıldığında, temsil eden SOAP ve WS-Addressing sürümlerini kullanılıyor.  
  
 İsteğe bağlı yöntemler ve özellikler kullanıcı tanımlı kodlama bağlama öğeleri için tam bir listesi için bkz. <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 Yeni bir bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [Creating User-Defined bağlamaları](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
 Bir bağlama öğesi için kanalınızı oluşturduktan sonra dönmek [geliştirme kanalları](../../../../docs/framework/wcf/extending/developing-channels.md) olup, bağlama öğeniz için yapılandırma dosyası desteği eklemek istiyorsanız ve meta veri yayımlama desteği ekleme görmek için konu ve olup olmadığını ve ne kadar bağlama öğesi kullanan kullanıcı tanımlı bir bağlama oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.BindingElement>
- [Geliştirme Kanalları](../../../../docs/framework/wcf/extending/developing-channels.md)
- [Taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
