---
title: Kullanıcı Tanımlı Bağlamalar Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
ms.openlocfilehash: 54a1c8e06991729ea8556d82d31897c522f6d173
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188727"
---
# <a name="creating-user-defined-bindings"></a>Kullanıcı Tanımlı Bağlamalar Oluşturma
Sistem tarafından sağlanmayan bağlamaları oluşturmanın birkaç yolu vardır:  
  
-   Temel, özel bir bağlama oluşturma <xref:System.ServiceModel.Channels.CustomBinding> sınıfını bağlama öğeleriyle doldurun bir kapsayıcıdır. Özel bağlama, ardından hizmet uç noktası eklenir. Özel bağlama ya da programlı olarak veya bir uygulama yapılandırma dosyasını oluşturabilirsiniz. Bir uygulama yapılandırma dosyasından bir bağlama öğesi kullanmak için bağlama öğesi genişletmelidir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>. Özel bağlamalar hakkında daha fazla bilgi için bkz: [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md) ve <xref:System.ServiceModel.Channels.CustomBinding>.  
  
-   Standart bir bağlama öğesinden türeyen bir sınıf oluşturabilirsiniz. Örneğin, bir sınıf türetebilirsiniz <xref:System.ServiceModel.WSHttpBinding> ve geçersiz kılma <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> bağlama öğeleri almak ve bir özel bağlama öğesi ekleyin veya güvenlik için belirli bir değer oluşturmak için bir yöntem.  
  
-   Yeni bir oluşturabilirsiniz <xref:System.ServiceModel.Channels.Binding> tamamen tüm bağlamayı uygulama denetlemek için türü.  
  
## <a name="the-order-of-binding-elements"></a>Bağlama öğelerinin sırası  
 Her bağlama öğesi gönderirken veya iletileri almak için bir işleme adımını temsil eder. Çalışma zamanında, Kanallar ve dinleyiciler bağlama öğeleri giden ve gelen kanal yığınları oluşturmak gerekli oluşturun.  
  
 Bağlama öğeleri üç ana türü vardır: Öğe, kodlama bağlama öğeleri ve bağlama öğeleri aktarım bağlama protokolü.  
  
 Protokol bağlama öğeleri – iletileri gibi davranan daha yüksek düzeyde işleme adımları bu öğeleri temsil eder. Kanallar ve dinleyiciler Bu bağlama öğeleri tarafından oluşturulan ekleyin, kaldırın veya ileti içeriğini değiştirin. Verilen bağlama Protokolü bağlama öğelerinin her dan devralan, rastgele bir sayıdan olabilir <xref:System.ServiceModel.Channels.BindingElement>. Windows Communication Foundation (WCF) dahil olmak üzere, çeşitli protokol bağlama öğeleri içeren <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> ve <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
 Kodlama. bağlama öğesi – iletilmesi kablo üzerinde bir ileti arasındaki bir kodlama dönüştürme hazır bu öğeleri temsil eder. Tipik WCF bağlamaları kodlama tam olarak bir bağlama öğesi içerir. Bağlama öğeleri kodlama örnekler <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>ve <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Bir kodlama bağlama öğesi için bir bağlama belirtilmemişse, kodlama varsayılan kullanılır. Varsayılan HTTP ve ikili taşıma Aksi durumda olduğunda metindir.  
  
 Aktarım bağlama öğesinin – Aktarım Protokolü bir kodlama iletisi iletimini bu öğeleri temsil eder. Tipik WCF bağlamaları dahil öğesinden devralan tam olarak bir aktarım bağlama öğesi <xref:System.ServiceModel.Channels.TransportBindingElement>. Aktarım bağlama öğelerinin örnekler <xref:System.ServiceModel.Channels.TcpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement>ve <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>.  
  
 Yeni bağlamalar oluştururken, eklenen bağlama öğelerinin sırası önemlidir. Her zaman bağlama öğeleri şu sırayla ekleyin:  
  
|Katman|Seçenekler|Gerekli|  
|-----------|-------------|--------------|  
|İşlem akışı|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|Hayır|  
|Güvenilirlik|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|Hayır|  
|Güvenlik|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|Hayır|  
|Bileşik çift yönlü|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|Hayır|  
|Encoding|İkili, MTOM, özel bir metin|Evet*|  
|Taşıma|TCP ve adlandırılmış kanallar, HTTP, HTTPS, MSMQ, özel|Evet|  
  
 * Bir kodlama belirtilmemişse, kodlama her bağlama için gerekli olduğu için bir varsayılan sizin için kodlama WCF ekler. Metin/XML ve ikili HTTP ve HTTPS aktarımı için Aksi takdirde varsayılandır.  
  
## <a name="creating-a-new-binding-element"></a>Yeni bir bağlama öğesi oluşturma  
 Öğesinden türetilen türler yanı sıra <xref:System.ServiceModel.Channels.BindingElement> olan sağlanan WCF tarafından kendi bağlama öğeleri oluşturabilirsiniz. Bu şekilde bağlamaları yığınını oluşturulur ve içinde kendi oluşturarak Git bileşenlerin özelleştirmenize olanak tanır <xref:System.ServiceModel.Channels.BindingElement> , oluşan yığındaki bir diğer sistem tarafından sağlanan tür.  
  
 Örneğin, uygulamanız bir `LoggingBindingElement` ileti bir veritabanında oturum olanağı sağlayan, bir kanal yığınındaki taşıma kanalı yukarıda yerleştirmelisiniz. Bu durumda, bağlama oluşan özel bir uygulama oluşturur `LoggingBindingElement` ile `TcpTransportBindingElement`, aşağıdaki örnekte olduğu gibi.  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),   
  new TcpTransportBindingElement()  
);  
```  
  
 Yeni bağlama öğeniz nasıl yazdığınız tam işlevselliğini bağlıdır. Örneklerden birini [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md), bağlama öğesi bir tür uygulama ayrıntılı bir açıklaması verilmiştir.  
  
## <a name="creating-a-new-binding"></a>Yeni bir bağlama oluşturma  
 Bir kullanıcı tarafından oluşturulmuş bir bağlama öğesi iki şekilde kullanılabilir. Önceki bölümde ilk yol gösterir: özel bağlama üzerinden. Özel bağlama bağlama öğelerinin, kullanıcı tarafından oluşturulmuş olanlar da dahil olmak üzere bir rastgele kümesi temel alınarak kendi bağlama oluşturmasına olanak tanır.  
  
 Birden fazla uygulama bağlama kullanırsanız, kendi bağlama oluşturur ve genişletmek <xref:System.ServiceModel.Channels.Binding>. Bu, kullanmak istediğiniz her zaman el ile özel bir bağlama oluşturma önler. Bir kullanıcı tanımlı bağlama bağlama davranışını tanımlayın ve kullanıcı tanımlı bağlama öğeleri içeren sağlar. Ve *önceden paketlenmiş*: bağlamayı her kullanışınızda yeniden başlatmanız gerekmez.  
  
 En az bir kullanıcı tanımlı bağlama uygulamalıdır <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> yöntemi ve <xref:System.ServiceModel.Channels.Binding.Scheme%2A> özelliği.  
  
 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> Yöntemi yeni bir döndürür <xref:System.ServiceModel.Channels.BindingElementCollection> bağlamaya ait bağlama öğelerini içeren. Koleksiyon sıralanır ve protokolü bağlama öğeleri ilk içermelidir, aktarım bağlama öğesi tarafından izlenen kodlama bağlama öğesi, ardından. WCF sistem tarafından sağlanan bir bağlamayı öğeleri kullanılarak, belirtilen kuralları sıralama bağlama öğesi izlemelidir [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md). Bu koleksiyonun hiç kullanıcı tanımlı bağlama sınıfı içinde başvurulan nesneleri başvurmalıdır; Sonuç olarak, bağlama yazarlar döndürmelidir bir `Clone()` , <xref:System.ServiceModel.Channels.BindingElementCollection> her çağrıda <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>.  
  
 <xref:System.ServiceModel.Channels.Binding.Scheme%2A> Özelliği, bağlama kullanımda Aktarım Protokolü için URI şeması temsil eder. Örneğin, *WSHttpBinding* ve *NetTcpBinding* döndürür "http" ve "net.tcp" kendi ilgili <xref:System.ServiceModel.Channels.Binding.Scheme%2A> özellikleri.  
  
 İsteğe bağlı yöntemler ve özellikler için kullanıcı tanımlı bağlamalar tam listesi için bkz: <xref:System.ServiceModel.Channels.Binding>.  
  
### <a name="example"></a>Örnek  
 Bu örnekte profil bağlamasında uygulayan `SampleProfileUdpBinding`, öğesinden türetildiğini <xref:System.ServiceModel.Channels.Binding>. `SampleProfileUdpBinding` İçindeki en fazla dört bağlama öğeleri içerir: bir kullanıcı tarafından oluşturulmuş `UdpTransportBindingElement`; ve sistem tarafından sağlanan üç: `TextMessageEncodingBindingElement`, `CompositeDuplexBindingElement`, ve `ReliableSessionBindingElement`.  
  
```csharp
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
  
## <a name="security-restrictions-with-duplex-contracts"></a>Çift yönlü sözleşme ile güvenlik kısıtlamaları  
 Tüm bağlama öğeleri birbiriyle uyumlu değildir. Özellikle, çift yönlü sözleşme ile kullanıldığında bağlama öğeleri güvenlikle ilgili bazı kısıtlamalar vardır.  
  
### <a name="one-shot-security"></a>Kesin güvenlik  
 Burada tüm gerekli güvenlik kimlik bilgileri gönderilen tek bir ileti ayarlayarak "kesin" güvenlik uygulayabilirsiniz `negotiateServiceCredential` özniteliği \<ileti > yapılandırma öğesi `false`.  
  
 Kesin kimlik doğrulaması ile çift yönlü anlaşma çalışmaz.  
  
 İstek-yanıt sözleşmeleriyle için kesin bir kimlik doğrulaması, yalnızca güvenlik bağlama öğesinin altındaki bağlama yığın oluşturmayı destekliyorsa çalışır <xref:System.ServiceModel.Channels.IRequestChannel> veya <xref:System.ServiceModel.Channels.IRequestSessionChannel> örnekleri.  
  
 Tek yönlü sözleşmeler için kesin authentication çalışır güvenlik bağlama öğesinin altındaki bağlama yığın oluşturmayı destekliyorsa <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>, <xref:System.ServiceModel.Channels.IOutputChannel> veya <xref:System.ServiceModel.Channels.IOutputSessionChannel> örnekleri.  
  
### <a name="cookie-mode-security-context-tokens"></a>Tanımlama bilgisi modunu güvenlik bağlamı belirteçleri  
 Tanımlama bilgisi modu güvenlik bağlamı belirteçleri ile çift yönlü anlaşma kullanılamaz.  
  
 İstek-yanıt sözleşmeleriyle için tanımlama bilgisi modunu güvenlik bağlamı belirteçler iş yalnızca güvenlik bağlama öğesinin altındaki bağlama yığın oluşturmayı destekliyorsa <xref:System.ServiceModel.Channels.IRequestChannel> veya <xref:System.ServiceModel.Channels.IRequestSessionChannel> örnekleri.  
  
 Tek yönlü sözleşmeler için güvenlik bağlama öğesinin altındaki bağlama yığın oluşturmayı destekliyorsa, tanımlama bilgisi modunu güvenlik bağlamı çalışır belirteçler. <xref:System.ServiceModel.Channels.IRequestChannel> veya <xref:System.ServiceModel.Channels.IRequestSessionChannel> örnekleri.  
  
### <a name="session-mode-security-context-tokens"></a>Oturum modu güvenlik bağlamı belirteçleri  
 Aşağıdaki güvenlik bağlama öğesi bağlama yığın oluşturmayı destekliyorsa SCT çalıştığı için çift yönlü sözleşmeler oturum modu <xref:System.ServiceModel.Channels.IDuplexChannel> veya <xref:System.ServiceModel.Channels.IDuplexSessionChannel> örnekleri.  
  
 Aşağıdaki güvenlik bağlama öğesi bağlama yığın oluşturmayı destekliyorsa, istek-yanıt sözleşmeleri için oturum modu SCT çalışır <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> veya <xref:System.ServiceModel.Channels.IRequestSessionChannel>, örnekleri.  
  
 Oturum modu SCT çalışır 1 yönlü sözleşmeler için aşağıdaki güvenlik bağlama öğesi bağlama yığın oluşturmayı destekliyorsa <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> veya <xref:System.ServiceModel.Channels.IRequestSessionChannel> örnekleri.  
  
## <a name="deriving-from-a-standard-binding"></a>Standart bir bağlama öğesinden türetme  
 Tamamen yeni bir bağlama sınıfı oluşturmak yerine var olan sistem tarafından sağlanan bağlamalar birini genişletmek için mümkün olabilir. Daha önceki bir durumda gibi geçersiz kılmanız gerekir <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> yöntemi ve <xref:System.ServiceModel.Channels.Binding.Scheme%2A> özelliği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.Binding>
- [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)
