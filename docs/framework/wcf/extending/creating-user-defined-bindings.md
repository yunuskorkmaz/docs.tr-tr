---
title: "Kullanıcı Tanımlı Bağlamalar Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe9be6ed74569875fd26f9a4913756e0366d757a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-user-defined-bindings"></a>Kullanıcı Tanımlı Bağlamalar Oluşturma
Sistem tarafından sağlanmayan bağlamaları oluşturmanın birkaç yolu vardır:  
  
-   Temel bir özel bağlama oluşturma <xref:System.ServiceModel.Channels.CustomBinding> bağlama öğeleri ile doldurun kapsayıcıdır sınıfı. Özel bağlama daha sonra bir hizmet uç noktası olarak eklenir. Özel bağlama ya da program aracılığıyla veya bir uygulama yapılandırma dosyasını oluşturabilirsiniz. Bir bağlama öğesi bir uygulama yapılandırma dosyasından kullanılacak bağlama öğesi genişletmelidir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Özel bağlamalar bkz [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md) ve <xref:System.ServiceModel.Channels.CustomBinding>.  
  
-   Standart bir bağlama öğesinden türeyen bir sınıf oluşturabilirsiniz. Örneğin, bir sınıftan türetilemeyeceğini <xref:System.ServiceModel.WSHttpBinding> ve geçersiz kılma <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> bağlama öğeleri almak ve bir özel bağlama öğesi ekleyin veya güvenlik için belirli bir değer oluşturmak için bir yöntem.  
  
-   Yeni bir oluşturabilirsiniz <xref:System.ServiceModel.Channels.Binding> tamamen tüm bağlamayı uygulama denetlemek için türü.  
  
## <a name="the-order-of-binding-elements"></a>Bağlama öğelerinin sırasını  
 Her bağlama öğesi iletileri alırken veya gönderirken bir işleme adımı temsil eder. Çalışma zamanında Kanallar ve dinleyiciler bağlama öğeleri gelen ve giden kanal yığınları oluşturmak gerekli oluşturun.  
  
 Bağlama öğeleri üç ana türü vardır: Protokolü bağlama öğeleri, kodlama bağlama öğeleri ve aktarım bağlama öğeleriyle.  
  
 Protokol bağlama öğeleri – iletileri hareket üst düzey işlem adımları bu öğeleri temsil eder. Kanallar ve dinleyiciler Bu bağlama öğeleri tarafından oluşturulan eklemek, kaldırmak veya ileti içeriği değiştirmek için. Belirtilen bağlama Protokolü bağlama öğeleri, her içinden devralma rastgele sayıda olabilir <xref:System.ServiceModel.Channels.BindingElement>. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]dahil olmak üzere, çeşitli protokol bağlama öğeleri içeren <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> ve <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
 Kodlama bağlama öğesi – hattaki iletim için bir ileti arasındaki bir kodlama dönüşümleri hazır bu öğeleri temsil eder. Tipik [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlamaları tam olarak bir kodlama bağlama öğesi içerir. Bağlama öğeleri kodlama örnekler <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>ve <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Bir kodlama bağlama öğesi için bir bağlama belirtilmezse, kodlama varsayılan kullanılır. Taşıma HTTP ve ikili Aksi takdirde varsayılan metin olur.  
  
 Aktarım bağlama öğesi – bu öğeleri Aktarım Protokolü bir kodlama iletisi iletimini temsil eder. Tipik [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlamaları dahil olduğu devraldığı tam olarak bir aktarım bağlama öğesi <xref:System.ServiceModel.Channels.TransportBindingElement>. Bağlama öğeleri taşıma örneklerindendir <xref:System.ServiceModel.Channels.TcpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement>ve <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>.  
  
 Yeni bağlamalar oluştururken, eklenen bağlama öğeleri sıralama önemlidir. Her zaman bağlama öğeleri aşağıdaki sırayla ekleyin:  
  
|Katman|Seçenekler|Gerekli|  
|-----------|-------------|--------------|  
|İşlem akışı|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|Hayır|  
|Güvenilirlik|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|Hayır|  
|Güvenlik|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|Hayır|  
|Bileşik çift yönlü|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|Hayır|  
|Kodlama|İkili, MTOM, özel bir metin|Evet*|  
|Taşıma|TCP ve adlandırılmış kanallar, HTTP, HTTPS, MSMQ, özel|Evet|  
  
 * Bir kodlama belirtilmezse, bir kodlama her bağlama için gerekli olduğu için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir varsayılan sizin için kodlama ekler. Text/XML ve ikili HTTP ve HTTPS aktarımları için aksi varsayılandır.  
  
## <a name="creating-a-new-binding-element"></a>Yeni bir bağlama öğesi oluşturma  
 Türetilen türler yanı sıra <xref:System.ServiceModel.Channels.BindingElement> tarafından sağlanan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], kendi bağlama öğeleri oluşturabilirsiniz. Bu bağlamaları yığınını oluşturulur yolu ve içinde kendi oluşturarak Git bileşenleri özelleştirmenize olanak tanır <xref:System.ServiceModel.Channels.BindingElement> yığınında bir diğer sistem tarafından sağlanan türleri ile birleştirilebilen.  
  
 Örneğin, uygulama, bir `LoggingBindingElement` ileti bir veritabanında oturum olanağı sağlar, kanal yığınındaki taşıma kanalı yukarıda yerleştirmelisiniz. Bu durumda, uygulama bir özel oluşan bağlama oluşturur `LoggingBindingElement` ile `TcpTransportBindingElement`, aşağıdaki örnekte olduğu gibi.  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),   
  new TcpTransportBindingElement()  
);  
```  
  
 Yeni bir bağlama öğesi yazma biçimini tam işlevselliğini bağlıdır. Örnekleri birini [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md), bağlama öğesi bir tür uygulama ayrıntılı bir açıklaması verilmiştir.  
  
## <a name="creating-a-new-binding"></a>Yeni bir bağlama oluşturma  
 Bir kullanıcı tarafından oluşturulan bağlama öğesi iki şekilde kullanılabilir. İlk yol önceki bölümde gösterilmektedir: özel bağlama üzerinden. Özel bağlama bağlama öğeleri, kullanıcı tarafından oluşturulan olanlar da dahil olmak üzere bir rastgele kümesini temel alan kendi bağlama oluşturmasına olanak tanır.  
  
 Bağlama birden fazla uygulamada kullanmak, kendi bağlama oluşturur ve genişletme <xref:System.ServiceModel.Channels.Binding>. Bu, kullanmak istediğiniz her zaman el ile özel bağlama oluşturma önler. Kullanıcı tanımlı bir bağlama bağlamanın davranışını tanımlayın ve kullanıcı tanımlı bağlama öğeleri dahil etmesini sağlar. Ve *önceden paketlenmiş*: her kullanışınızda bağlama yeniden başlatmanız gerekmez.  
  
 En azından bir kullanıcı tarafından tanımlanan bağlama uygulamalıdır <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> yöntemi ve <xref:System.ServiceModel.Channels.Binding.Scheme%2A> özelliği.  
  
 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> Yöntem yeni bir <xref:System.ServiceModel.Channels.BindingElementCollection> bağlamaya ait bağlama öğelerini içerir. Koleksiyon sipariş edilir ve protokolü bağlama öğeleri ilk içermelidir, aktarım bağlama öğesi tarafından izlenen kodlama bağlama öğesi arkasından. Kullanırken [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sistem tarafından sağlanan bağlama öğeleri kuralları içinde belirtilen sıralama bağlama öğesi uymalıdır [özel bağlamaları](../../../../docs/framework/wcf/extending/custom-bindings.md). Bu koleksiyonun hiç kullanıcı tanımlı bağlama sınıfı içinde başvurulan nesneler başvuruda bulunmalıdır; Sonuç olarak, bağlama yazarlar döndürmelidir bir `Clone()` , <xref:System.ServiceModel.Channels.BindingElementCollection> her çağrıda <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>.  
  
 <xref:System.ServiceModel.Channels.Binding.Scheme%2A> Özelliği, bağlama kullanımda Aktarım Protokolü için URI şeması'ı temsil eder. Örneğin, *WSHttpBinding* ve *NetTcpBinding* döndürmek "http" ve "net.tcp" kendi ilgili <xref:System.ServiceModel.Channels.Binding.Scheme%2A> özellikleri.  
  
 İsteğe bağlı yöntemlerini ve kullanıcı tanımlı bağlamalar özelliklerini tam listesi için bkz: <xref:System.ServiceModel.Channels.Binding>.  
  
### <a name="example"></a>Örnek  
 Bu örnekte profil bağlamasında uygulayan `SampleProfileUdpBinding`, den türetilen <xref:System.ServiceModel.Channels.Binding>. `SampleProfileUdpBinding` İçindeki en fazla dört bağlama öğeleri içerir: bir kullanıcı tarafından oluşturulan `UdpTransportBindingElement`; ve üç sistem tarafından sağlanan: `TextMessageEncodingBindingElement`, `CompositeDuplexBindingElement`, ve `ReliableSessionBindingElement`.  
  
```  
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
## <a name="security-restrictions-with-duplex-contracts"></a>Çift yönlü sözleşmeler ile güvenlik kısıtlamaları  
 Tüm bağlama öğeleri birbirleri ile uyumludur. Özellikle, çift yönlü sözleşmeler ile kullanıldığında bağlama öğeleri güvenlik bazı kısıtlamalar vardır.  
  
### <a name="one-shot-security"></a>Tek adımda güvenlik  
 Burada tüm gerekli güvenlik kimlik bilgilerini gönderilen tek bir iletide ayarlayarak "tek adımda" güvenlik uygulayabilirsiniz `negotiateServiceCredential` özniteliği \<ileti > yapılandırma öğesi için `false`.  
  
 Tek adımda kimlik doğrulaması ile çift yönlü sözleşmeler çalışmaz.  
  
 İstek-yanıt sözleşmeleri için tek adımda kimlik doğrulaması çalışır ancak güvenlik bağlama öğesi aşağıda bağlama yığın oluşturma destekliyorsa <xref:System.ServiceModel.Channels.IRequestChannel> veya <xref:System.ServiceModel.Channels.IRequestSessionChannel> örnekleri.  
  
 Tek yönlü sözleşmeler için tek adımda kimlik doğrulaması çalışır güvenlik bağlama öğesi aşağıda bağlama yığın oluşturma destekliyorsa <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>, <xref:System.ServiceModel.Channels.IOutputChannel> veya <xref:System.ServiceModel.Channels.IOutputSessionChannel> örnekleri.  
  
### <a name="cookie-mode-security-context-tokens"></a>Tanımlama bilgisi modu güvenlik bağlamı belirteçleri  
 Tanımlama bilgisi modu güvenlik bağlamı belirteçleri ile çift yönlü sözleşmeler kullanılamaz.  
  
 İstek-yanıt sözleşmeleri için tanımlama bilgisi modu güvenlik bağlamı belirteçler iş yalnızca güvenlik bağlama öğesi aşağıda bağlama yığın oluşturma destekliyorsa <xref:System.ServiceModel.Channels.IRequestChannel> veya <xref:System.ServiceModel.Channels.IRequestSessionChannel> örnekleri.  
  
 Güvenlik bağlama öğesi aşağıda bağlama yığın oluşturma destekliyorsa tek yönlü sözleşmeler için tanımlama bilgisi modu güvenlik bağlamı works belirteçler: <xref:System.ServiceModel.Channels.IRequestChannel> veya <xref:System.ServiceModel.Channels.IRequestSessionChannel> örnekleri.  
  
### <a name="session-mode-security-context-tokens"></a>Oturum modu güvenlik bağlamı belirteçleri  
 Oturum modu SCT çalışır çift yönlü sözleşmeler için güvenlik bağlama öğesi aşağıda bağlama yığın oluşturma destekliyorsa <xref:System.ServiceModel.Channels.IDuplexChannel> veya <xref:System.ServiceModel.Channels.IDuplexSessionChannel> örnekleri.  
  
 Oturum modu SCT çalışır güvenlik bağlama öğesi aşağıda bağlama yığın oluşturma destekliyorsa istek-yanıt sözleşmeleri için <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> veya <xref:System.ServiceModel.Channels.IRequestSessionChannel>, örnekleri.  
  
 Oturum modu SCT çalışır 1 yönlü sözleşmeler için güvenlik bağlama öğesi aşağıda bağlama yığın oluşturma destekliyorsa <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> veya <xref:System.ServiceModel.Channels.IRequestSessionChannel> örnekleri.  
  
## <a name="deriving-from-a-standard-binding"></a>Standart bir bağlama öğesinden türetme  
 Tamamen yeni bir bağlama sınıfı oluşturmak yerine var olan sistem tarafından sağlanan bağlamalar birini genişletmek için mümkün olabilir. Daha önceki durum gibi kılmalıdır <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> yöntemi ve <xref:System.ServiceModel.Channels.Binding.Scheme%2A> özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.Binding>  
 [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)
