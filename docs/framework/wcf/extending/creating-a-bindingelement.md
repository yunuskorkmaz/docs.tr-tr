---
title: BindingElement Oluşturma
ms.date: 03/30/2017
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
ms.openlocfilehash: 4b760f9373e64e153bd5a21469eb7a503283d35c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795830"
---
# <a name="creating-a-bindingelement"></a>BindingElement Oluşturma
Bağlamalar ve bağlama öğeleri (ve <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>sırasıyla genişleyen nesneler) Windows Communication Foundation (WCF) uygulama modelinin kanal fabrikaları ve kanal dinleyicileri ile ilişkilendirildiği yerdir. Bağlama olmadan, özel kanallar kullanıldığında, [hizmet kanalı düzeyi programlama](service-channel-level-programming.md) ve [Istemci kanal düzeyi programlama](client-channel-level-programming.md)bölümünde açıklandığı gibi kanal düzeyinde programlama yapmanız gerekir. Bu konuda [, kanalınızın](developing-channels.md)WCF 'de kullanılması, kanalınız için bir <xref:System.ServiceModel.Channels.BindingElement> geliştirme ve uygulamanın adım 4 ' te açıklandığı şekilde uygulamadan kullanımı etkinleştirme için en düşük gereksinim ele alınmaktadır.  
  
## <a name="overview"></a>Genel Bakış  
 Kanala yönelik <xref:System.ServiceModel.Channels.BindingElement> bir oluşturma, geliştiricilerin bunu bir WCF uygulamasında kullanmasına olanak sağlar. <xref:System.ServiceModel.Channels.BindingElement>nesneler, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> kanalınızın kesin tür bilgilerine gerek kalmadan, bir WCF uygulamasını kanalınıza bağlamak için sınıfından kullanılabilir.  
  
 Bir <xref:System.ServiceModel.Channels.BindingElement> kez oluşturulduktan sonra, [kanalları geliştirme](developing-channels.md)bölümünde açıklanan kalan Kanal geliştirme adımlarını izleyerek gereksinimlerinize bağlı olarak daha fazla işlevsellik sağlayabilirsiniz.  
  
## <a name="adding-a-binding-element"></a>Bağlama öğesi ekleme  
 Özel <xref:System.ServiceModel.Channels.BindingElement>uygulamak için, öğesinden <xref:System.ServiceModel.Channels.BindingElement>devralan bir sınıf yazın. Örneğin, büyük iletileri parçalara bölebilir ve bunları `ChunkingChannel` başka bir uçta yeniden ayırarak, bu kanalı kullanarak herhangi bir <xref:System.ServiceModel.Channels.BindingElement> bağlamada kullanabilirsiniz ve bunu kullanmak için bağlamayı yapılandırabilirsiniz. Bu konunun geri kalanında bir bağlama öğesi `ChunkingChannel` uygulama gereksinimlerini göstermek için bir örnek olarak kullanılmıştır.  
  
 `ChunkingBindingElement` ,`ChunkingChannelFactory` Ve oluşturmaktan`ChunkingChannelListener`sorumludur. Bu, <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> ve <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> uygulamalarını geçersiz kılar ve tür parametresinin olduğunu <xref:System.ServiceModel.Channels.IDuplexSessionChannel> denetler (bizim örneğimizde bu, `ChunkingChannel`tarafından desteklenen tek kanal şekildir) ve bağlamadaki diğer bağlama öğeleri bunu desteklemelidir Kanal şekli.  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A>İlk olarak, istenen kanal şeklinin oluşturulup oluşturulmadığını kontrol eder ve ardından, yığın olarak kullanılacak ileti eylemlerinin bir listesini alır. Daha sonra yeni `ChunkingChannelFactory`bir oluşturur ve bunu iç kanal fabrikasını geçirerek. (Bir aktarım bağlama öğesi oluşturuyorsanız, bu öğe bağlama yığınında son bir değer ve bu nedenle bir kanal dinleyicisi veya kanal fabrikası oluşturulmalıdır.)  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A>, iç kanal dinleyicisi oluşturma `ChunkingChannelListener` ve geçirme için benzer bir uygulamaya sahiptir.  
  
 Taşıma kanalını kullanan başka bir örnek olarak, [taşıma: UDP](../samples/transport-udp.md) örneği aşağıdaki geçersiz kılmayı sağlar.  
  
 Örnekte, bağlama öğesi `UdpTransportBindingElement`öğesinden <xref:System.ServiceModel.Channels.TransportBindingElement>türetilir. Kanalla ilişkili fabrikaları derlemek için aşağıdaki yöntemleri geçersiz kılar.  
  
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
 Yeni bağlama öğeleri, eklenen bağlama öğelerinden herhangi birini değiştirebilir veya artırabilir, yeni aktarımlar, kodlamalar veya daha yüksek düzeyde protokoller ekler. Yeni bir protokol bağlama öğesi oluşturmak için, <xref:System.ServiceModel.Channels.BindingElement> sınıfını genişleterek ' ı başlatın. En azından, öğesini uygulamanız <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType> ve `ChannelProtectionRequirements` kullanarak <xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType>uygulamasını uygulamanız gerekir. Bu, <xref:System.ServiceModel.Security.ChannelProtectionRequirements> bu Binding öğesi için döndürür.  Daha fazla bilgi için bkz. <xref:System.ServiceModel.Security.ChannelProtectionRequirements>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>Bu bağlama öğesinin yeni bir kopyasını döndürmelidir. En iyi uygulama olarak, bağlama öğesi yazarlarının <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> temel kopya oluşturucusunu çağıran bir kopya Oluşturucu kullanarak uygulamasını ve sonra bu sınıftaki ek alanları klonlanmasını öneririz.  
  
#### <a name="transport-binding-elements"></a>Taşıma bağlama öğeleri  
 Yeni bir taşıma bağlama öğesi oluşturmak için <xref:System.ServiceModel.Channels.TransportBindingElement> arabirimi genişletin. En azından, <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> yöntemini <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType> ve özelliğini uygulamanız gerekir.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>– Bu bağlama öğesinin yeni bir kopyasını döndürmelidir.  En iyi uygulama olarak, bağlama öğesi yazarlarının, temel kopya oluşturucusunu çağıran bir kopya Oluşturucu aracılığıyla klonlanmasını, ardından bu sınıftaki ek alanları klonlanmasını öneririz.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A><xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> – Get özelliği, Binding öğesi tarafından temsil edilen aktarım protokolü için URI düzenini döndürür. Örneğin <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> ,<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType> ve, ilgili özelliklerinden "http" ve "net. TCP" döndürür.  
  
#### <a name="encoding-binding-elements"></a>Bağlama öğelerini kodlama  
 Yeni kodlama bağlama öğeleri oluşturmak için, <xref:System.ServiceModel.Channels.BindingElement> sınıfını genişleterek ve <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType> sınıfını uygulayarak başlayın. En azından, <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> yöntemlerini ve <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType> özelliğini uygulamanız gerekir.  
  
- <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>. Bu bağlama öğesinin yeni bir kopyasını döndürür. En iyi uygulama olarak, bağlama öğesi yazarlarının <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> temel kopya oluşturucusunu çağıran bir kopya Oluşturucu kullanarak uygulamasını ve sonra bu sınıftaki ek alanları klonlanmasını öneririz.  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>. Yeni kodlayıcıyı uygulayan ve genişletecek <xref:System.ServiceModel.Channels.MessageEncoderFactory> <xref:System.ServiceModel.Channels.MessageEncoder>olan gerçek sınıfa yönelik bir tanıtıcı sağlayan bir döndürür. Daha fazla bilgi için bkz. <xref:System.ServiceModel.Channels.MessageEncoderFactory> ve <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>. Bu kodlamada <xref:System.ServiceModel.Channels.MessageVersion> kullanılan soap ve ws-Addressing sürümlerini temsil eden ' i döndürür.  
  
 Kullanıcı tanımlı kodlama bağlama öğeleri için isteğe bağlı yöntemlerin ve özelliklerin tam listesi için bkz <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 Yeni bağlama öğesi oluşturma hakkında daha fazla bilgi için bkz. [Kullanıcı Tanımlı Bağlamalar Oluşturma](creating-user-defined-bindings.md).  
  
 Kanalınız için bir bağlama öğesi oluşturduktan sonra, bağlama öğesine yapılandırma dosyası desteği eklemek isteyip istemediğinizi öğrenmek için [geliştirme kanalları](developing-channels.md) konusuna geri dönün, meta veri yayını desteğinin nasıl ekleneceğini ve bunların nasıl ve nasıl yapılacağını öğrenin Bağlama öğesini kullanan kullanıcı tanımlı bir bağlama oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.BindingElement>
- [Geliştirme Kanalları](developing-channels.md)
- [Aktarım PROTOKOLLERINDEN](../samples/transport-udp.md)
