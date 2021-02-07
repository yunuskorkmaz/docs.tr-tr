---
description: 'Daha fazla bilgi edinin: BindingElement oluşturma'
title: BindingElement Oluşturma
ms.date: 03/30/2017
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
ms.openlocfilehash: de5ef045f2e83985cabd36c53652d46536889fa2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735432"
---
# <a name="creating-a-bindingelement"></a>BindingElement Oluşturma

Bağlamalar ve bağlama öğeleri ( <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType> ve sırasıyla genişleyen nesneler <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> ) WINDOWS COMMUNICATION FOUNDATION (WCF) uygulama modelinin kanal fabrikaları ve kanal dinleyicileri ile ilişkilendirildiği yerdir. Bağlama olmadan, özel kanallar kullanıldığında, [Service Channel-Level programlama](service-channel-level-programming.md) ve [istemci Channel-Level programlama](client-channel-level-programming.md)bölümünde açıklandığı gibi kanal düzeyinde programlama yapmanız gerekir. Bu konuda, kanalınızın WCF 'de kullanılması, <xref:System.ServiceModel.Channels.BindingElement> kanalınız için bir geliştirme ve uygulamanın adım 4 ' te açıklandığı şekilde uygulamadan kullanımı etkinleştirme için en düşük gereksinim ele alınmaktadır. [](developing-channels.md)  
  
## <a name="overview"></a>Genel Bakış  

 <xref:System.ServiceModel.Channels.BindingElement>Kanala yönelik bir oluşturma, geliştiricilerin bunu BIR WCF uygulamasında kullanmasına olanak sağlar. <xref:System.ServiceModel.Channels.BindingElement> nesneler, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> kanalınızın kesin tür bilgilerine gerek kalmadan, BIR WCF uygulamasını kanalınıza bağlamak için sınıfından kullanılabilir.  
  
 Bir kez <xref:System.ServiceModel.Channels.BindingElement> oluşturulduktan sonra, [kanalları geliştirme](developing-channels.md)bölümünde açıklanan kalan Kanal geliştirme adımlarını izleyerek gereksinimlerinize bağlı olarak daha fazla işlevsellik sağlayabilirsiniz.  
  
## <a name="adding-a-binding-element"></a>Bağlama öğesi ekleme  

 Özel uygulamak için <xref:System.ServiceModel.Channels.BindingElement> , öğesinden devralan bir sınıf yazın <xref:System.ServiceModel.Channels.BindingElement> . Örneğin, `ChunkingChannel` büyük iletileri parçalara bölebilir ve bunları başka bir uçta yeniden ayırarak, bu kanalı kullanarak herhangi bir bağlamada kullanabilirsiniz <xref:System.ServiceModel.Channels.BindingElement> ve bunu kullanmak için bağlamayı yapılandırabilirsiniz. Bu konunun geri kalanında `ChunkingChannel` bir bağlama öğesi uygulama gereksinimlerini göstermek için bir örnek olarak kullanılmıştır.  
  
 `ChunkingBindingElement`, Ve oluşturmaktan sorumludur `ChunkingChannelFactory` `ChunkingChannelListener` . Bu <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> , ve uygulamalarını geçersiz kılar ve <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> tür parametresinin olduğunu denetler <xref:System.ServiceModel.Channels.IDuplexSessionChannel> (bizim örneğimizde bu, tarafından desteklenen tek kanal şekildir `ChunkingChannel` ) ve bağlamadaki diğer bağlama öğeleri bu kanal şeklini destekler.  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> İlk olarak, istenen kanal şeklinin oluşturulup oluşturulmadığını kontrol eder ve ardından, yığın olarak kullanılacak ileti eylemlerinin bir listesini alır. Daha sonra yeni bir oluşturur `ChunkingChannelFactory` ve bunu iç kanal fabrikasını geçirerek. (Bir aktarım bağlama öğesi oluşturuyorsanız, bu öğe bağlama yığınında son bir değer ve bu nedenle bir kanal dinleyicisi veya kanal fabrikası oluşturulmalıdır.)  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> , `ChunkingChannelListener` iç kanal dinleyicisi oluşturma ve geçirme için benzer bir uygulamaya sahiptir.  
  
 Bir taşıma kanalını kullanan başka bir örnek olarak, [Transport: UDP](../samples/transport-udp.md) örneği aşağıdaki geçersiz kılmayı sağlar.  
  
 Örnekte, bağlama öğesi `UdpTransportBindingElement` öğesinden türetilir <xref:System.ServiceModel.Channels.TransportBindingElement> . Kanalla ilişkili fabrikaları derlemek için aşağıdaki yöntemleri geçersiz kılar.  
  
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
  
 Ayrıca, `BindingElement` klonımızın (SOAP. UDP) kopyalanması ve döndürülmesi için Üyeler de bulunur.  
  
#### <a name="protocol-binding-elements"></a>Protokol bağlama öğeleri  

 Yeni bağlama öğeleri, eklenen bağlama öğelerinden herhangi birini değiştirebilir veya artırabilir, yeni aktarımlar, kodlamalar veya daha yüksek düzeyde protokoller ekler. Yeni bir protokol bağlama öğesi oluşturmak için, sınıfını genişleterek ' ı başlatın <xref:System.ServiceModel.Channels.BindingElement> . En azından, öğesini uygulamanız ve kullanarak uygulamasını uygulamanız gerekir <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType> `ChannelProtectionRequirements` <xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType> . Bu, <xref:System.ServiceModel.Security.ChannelProtectionRequirements> Bu Binding öğesi için döndürür.  Daha fazla bilgi için bkz. <xref:System.ServiceModel.Security.ChannelProtectionRequirements>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> Bu bağlama öğesinin yeni bir kopyasını döndürmelidir. En iyi uygulama olarak, bağlama öğesi yazarlarının <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> temel kopya oluşturucusunu çağıran bir kopya Oluşturucu kullanarak uygulamasını ve sonra bu sınıftaki ek alanları klonlanmasını öneririz.  
  
#### <a name="transport-binding-elements"></a>Taşıma bağlama öğeleri  

 Yeni bir taşıma bağlama öğesi oluşturmak için <xref:System.ServiceModel.Channels.TransportBindingElement> arabirimi genişletin. En azından, <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> yöntemini ve özelliğini uygulamanız gerekir <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType> .  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> – Bu bağlama öğesinin yeni bir kopyasını döndürmelidir.  En iyi uygulama olarak, bağlama öğesi yazarlarının, temel kopya oluşturucusunu çağıran bir kopya Oluşturucu aracılığıyla klonlanmasını, ardından bu sınıftaki ek alanları klonlanmasını öneririz.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> – <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> Get özelliği, Binding öğesi tarafından temsil edilen Aktarım Protokolü IÇIN URI düzenini döndürür. Örneğin, ve, <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType> ilgili özelliklerinden "http" ve "net. TCP" döndürür <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> .  
  
#### <a name="encoding-binding-elements"></a>Bağlama öğelerini kodlama  

 Yeni kodlama bağlama öğeleri oluşturmak için, <xref:System.ServiceModel.Channels.BindingElement> sınıfını genişleterek ve sınıfını uygulayarak başlayın <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType> . En azından, <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> yöntemlerini ve özelliğini uygulamanız gerekir <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType> .  
  
- <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>. Bu bağlama öğesinin yeni bir kopyasını döndürür. En iyi uygulama olarak, bağlama öğesi yazarlarının <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> temel kopya oluşturucusunu çağıran bir kopya Oluşturucu kullanarak uygulamasını ve sonra bu sınıftaki ek alanları klonlanmasını öneririz.  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>. <xref:System.ServiceModel.Channels.MessageEncoderFactory>Yeni kodlayıcıyı uygulayan ve genişletecek olan gerçek sınıfa yönelik bir tanıtıcı sağlayan bir döndürür <xref:System.ServiceModel.Channels.MessageEncoder> . Daha fazla bilgi için <xref:System.ServiceModel.Channels.MessageEncoderFactory> ve <xref:System.ServiceModel.Channels.MessageEncoder> bölümlerine bakın.  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>. <xref:System.ServiceModel.Channels.MessageVersion>Bu kodlamada kullanılan soap ve kullanımdaki WS-Addressing sürümlerini temsil eden bir değer döndürür.  
  
 Kullanıcı tanımlı kodlama bağlama öğeleri için isteğe bağlı yöntemlerin ve özelliklerin tam listesi için bkz <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> ..  
  
 Yeni bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [User-Defined bağlamaları oluşturma](creating-user-defined-bindings.md).  
  
 Kanalınız için bir bağlama öğesi oluşturduktan sonra, bağlama öğesine yapılandırma dosyası desteği eklemek isteyip istemediğinizi öğrenmek için [geliştirme kanalları](developing-channels.md) konusuna geri dönün, meta veri yayını desteğinin nasıl ekleneceğini ve bağlama öğesini kullanan kullanıcı tanımlı bir bağlamanın oluşturulup oluşturulmayacağını öğrenin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.BindingElement>
- [Geliştirme Kanalları](developing-channels.md)
- [Taşıma: UDP](../samples/transport-udp.md)
