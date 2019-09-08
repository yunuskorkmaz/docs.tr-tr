---
title: Kullanıcı Tanımlı Bağlamalar Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
ms.openlocfilehash: 3b5feb0da86e11485fa7ca1c474a69002c8d43ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797246"
---
# <a name="creating-user-defined-bindings"></a>Kullanıcı Tanımlı Bağlamalar Oluşturma
Sistem tarafından sağlanmayan bağlamaları oluşturmanın birkaç yolu vardır:  
  
- Bağlama öğeleriyle doldurduğunuz bir kapsayıcı olan <xref:System.ServiceModel.Channels.CustomBinding> sınıfını temel alan özel bir bağlama oluşturun. Özel bağlama daha sonra bir hizmet uç noktasına eklenir. Özel bağlamayı program aracılığıyla veya bir uygulama yapılandırma dosyasında oluşturabilirsiniz. Bir uygulama yapılandırma dosyasından bağlama öğesi kullanmak için bağlama öğesi genişlemelidir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>. Özel Bağlamalar hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](custom-bindings.md) ve <xref:System.ServiceModel.Channels.CustomBinding>.  
  
- Standart bağlamadan türetilen bir sınıf oluşturabilirsiniz. Örneğin, bağlama öğelerini almak ve özel bir bağlama <xref:System.ServiceModel.WSHttpBinding> öğesi eklemek <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> veya güvenlik için belirli bir değer oluşturmak üzere bir sınıfından bir sınıf türetebilir ve geçersiz kılabilirsiniz.  
  
- Bağlama uygulamasının tamamını tamamen denetlemek <xref:System.ServiceModel.Channels.Binding> için yeni bir tür oluşturabilirsiniz.  
  
## <a name="the-order-of-binding-elements"></a>Bağlama öğelerinin sırası  
 Her bağlama öğesi ileti gönderirken veya alırken bir işleme adımını temsil eder. Çalışma zamanında, bağlama öğeleri, giden ve gelen kanal yığınları oluşturmak için gereken kanalları ve dinleyicileri oluşturur.  
  
 Üç ana tür bağlama öğesi vardır: Protokol bağlama öğeleri, kodlama bağlama öğeleri ve taşıma bağlama öğeleri.  
  
 Protokol bağlama öğeleri – bu öğeler, iletiler üzerinde işlem yapan üst düzey işleme adımlarını temsil eder. Bu bağlama öğeleri tarafından oluşturulan kanallar ve dinleyiciler ileti içeriğini ekleyebilir, kaldırabilir veya değiştirebilir. Verilen bağlama, her biri öğesinden <xref:System.ServiceModel.Channels.BindingElement>devralan rastgele sayıda protokol bağlama öğesine sahip olabilir. Windows Communication Foundation (WCF), <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>ve dahil olmak üzere çeşitli protokol bağlama öğeleri içerir.  
  
 Encoding bağlama öğesi – bu öğeler, bir ileti ve tel iletilmek üzere bir kodlama arasındaki dönüşümleri temsil eder. Tipik WCF bağlamaları tam olarak bir kodlama bağlama öğesi içerir. Bağlama öğelerinin kodlama örnekleri,, ve <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>' <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>i içerir. Bir bağlama için bir kodlama bağlama öğesi belirtilmemişse, varsayılan bir kodlama kullanılır. Aktarım HTTP olduğunda varsayılan metin, aksi durumda ikili olur.  
  
 Taşıma bağlama öğesi – bu öğeler bir Aktarım Protokolü üzerinde kodlama iletisinin aktarımını temsil eder. Tipik WCF bağlamaları, öğesinden <xref:System.ServiceModel.Channels.TransportBindingElement>devralan tam olarak bir aktarım bağlama öğesi içerir. Taşıma bağlama öğelerinin örnekleri,, ve <xref:System.ServiceModel.Channels.TcpTransportBindingElement> <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>' <xref:System.ServiceModel.Channels.HttpTransportBindingElement>i içerir.  
  
 Yeni bağlamalar oluştururken, eklenen bağlama öğelerinin sırası önemlidir. Bağlama öğelerini her zaman aşağıdaki sırada ekleyin:  
  
|Katman|Seçenekler|Gerekli|  
|-----------|-------------|--------------|  
|İşlem akışı|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|Hayır|  
|Güvenilirlik|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|Hayır|  
|Güvenlik|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|Hayır|  
|Bileşik çift yönlü|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|Hayır|  
|Encoding|Metin, Ikili, MTOM, özel|Yes\*|  
|Aktarım|TCP, adlandırılmış kanallar, HTTP, HTTPS, MSMQ, özel|Evet|  
  
\*Her bağlama için bir kodlama gerektiğinden, bir kodlama belirtilmemişse, WCF sizin için varsayılan bir kodlama ekler. Varsayılan değer HTTP ve HTTPS aktarımları için Text/XML, aksi durumda binary.  
  
## <a name="creating-a-new-binding-element"></a>Yeni bağlama öğesi oluşturma  
 WCF tarafından sağlanarak türetilen <xref:System.ServiceModel.Channels.BindingElement> türlerin yanı sıra kendi bağlama öğelerinizi de oluşturabilirsiniz. Bu, bağlama yığınının oluşturulma şeklini ve yığın içindeki diğer sistem tarafından sunulan türlerle birleştirilebilen kendi <xref:System.ServiceModel.Channels.BindingElement> oluşturduğunuz bileşenlerini özelleştirmenizi sağlar.  
  
 Örneğin, bir veritabanını bir veritabanına kaydetme `LoggingBindingElement` özelliğini sağlayan bir uygularsanız, kanal yığınında bir aktarım kanalının üzerine yerleştirmeniz gerekir. Bu durumda, uygulama, aşağıdaki örnekte olduğu gibi `LoggingBindingElement` ile içeren `TcpTransportBindingElement`bir özel bağlama oluşturur.  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),   
  new TcpTransportBindingElement()  
);  
```  
  
 Yeni bağlama öğesini nasıl yazdığınız, tam işlevselliğine bağlıdır. Örneklerden biri, [taşıma: UDP](../samples/transport-udp.md), bir tür bağlama öğesinin nasıl uygulanacağı hakkında ayrıntılı bir açıklama sağlar.  
  
## <a name="creating-a-new-binding"></a>Yeni bağlama oluşturma  
 Kullanıcı tarafından oluşturulan bağlama öğesi iki şekilde kullanılabilir. Önceki bölümde ilk yol gösterilmektedir: özel bir bağlama. Özel bir bağlama, kullanıcının, Kullanıcı tarafından oluşturulan bir bağlama öğesi kümesini temel alarak kendi bağlamasını oluşturmalarına olanak tanır.  
  
 Bağlamayı birden fazla uygulamada kullanırsanız, kendi bağlamayı oluşturun ve genişletin <xref:System.ServiceModel.Channels.Binding>. Bu, bir özel bağlamayı her kullanmak istediğinizde el ile oluşturmayı önler. Kullanıcı tanımlı bir bağlama, bağlamanın davranışını tanımlamanızı ve Kullanıcı tanımlı bağlama öğelerini dahil etmenizi sağlar. *Önceden paketlenmiştir*: bağlamayı her kullandığınızda yeniden oluşturmanız gerekmez.  
  
 En azından, Kullanıcı tanımlı bir bağlamanın <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> yöntemini <xref:System.ServiceModel.Channels.Binding.Scheme%2A> ve özelliğini uygulaması gerekir.  
  
 Yöntemi, bağlama yönelik bağlama <xref:System.ServiceModel.Channels.BindingElementCollection> öğelerini içeren yeni bir döndürür. <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> Koleksiyon sıralanmıştır ve önce protokol bağlama öğelerini, sonra Encoding bağlama öğesini, ardından da taşıma bağlama öğesini içermelidir. WCF sistem tarafından sağlanmış bağlama öğelerini kullanırken, [özel bağlamalarda](custom-bindings.md)belirtilen bağlama öğesi sıralama kurallarını izlemeniz gerekir. Bu koleksiyon, Kullanıcı tanımlı bağlama sınıfında başvurulan nesnelere asla başvurmamalıdır; Sonuç olarak, bağlama yazarları öğesine `Clone()` <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>her çağrısının bir <xref:System.ServiceModel.Channels.BindingElementCollection> öğesini döndürmelidir.  
  
 <xref:System.ServiceModel.Channels.Binding.Scheme%2A> Özelliği, bağlamada kullanılan Aktarım protokolünün URI düzenini temsil eder. Örneğin, *WSHttpBinding* ve *NetTcpBinding* ilgili <xref:System.ServiceModel.Channels.Binding.Scheme%2A> özelliklerinden "http" ve "net. TCP" döndürür.  
  
 Kullanıcı tanımlı bağlamalara yönelik isteğe bağlı yöntemlerin ve özelliklerin tam listesi için bkz <xref:System.ServiceModel.Channels.Binding>.  
  
### <a name="example"></a>Örnek  
 Bu örnek ' de `SampleProfileUdpBinding`' den <xref:System.ServiceModel.Channels.Binding>türetilen profil bağlamasını uygular. , `SampleProfileUdpBinding` İçinde en fazla dört bağlama öğesi içerir: bir kullanıcı tarafından oluşturulan `UdpTransportBindingElement`ve üç sistem tarafından sunulan: `TextMessageEncodingBindingElement`, `CompositeDuplexBindingElement`, ve `ReliableSessionBindingElement`.  
  
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
  
## <a name="security-restrictions-with-duplex-contracts"></a>Çift yönlü sözleşmelerle güvenlik kısıtlamaları  
 Bağlama öğelerinin hepsi birbirleriyle uyumlu değildir. Özellikle, çift yönlü sözleşmelerle kullanıldığında güvenlik bağlama öğelerinde bazı kısıtlamalar vardır.  
  
### <a name="one-shot-security"></a>Tek kararlı güvenlik  
 İleti > yapılandırma öğesinin `negotiateServiceCredential` özniteliğini `false`olarak ayarlayarak, tüm gerekli güvenlik bilgilerinin tek bir iletiyle gönderildiği "tek kararlı" bir güvenlik uygulayabilirsiniz. \<  
  
 Tek çizgili kimlik doğrulama, çift yönlü sözleşmelerle çalışmaz.  
  
 İstek-yanıt sözleşmeleri için, tek seferlik kimlik doğrulaması yalnızca güvenlik bağlama öğesinin altındaki bağlama yığını, oluşturma veya <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel> örnek oluşturmayı destekliyorsa kullanılabilir.  
  
 Tek yönlü sözleşmeler için, güvenlik bağlama öğesinin altındaki <xref:System.ServiceModel.Channels.IRequestChannel>bağlama yığını <xref:System.ServiceModel.Channels.IOutputChannel> , <xref:System.ServiceModel.Channels.IRequestSessionChannel>, veya <xref:System.ServiceModel.Channels.IOutputSessionChannel> örneklerini oluşturmayı destekliyorsa, tek seferlik kimlik doğrulama işe yarar.  
  
### <a name="cookie-mode-security-context-tokens"></a>Tanımlama bilgisi modu güvenlik bağlamı belirteçleri  
 Tanımlama bilgisi modu güvenlik bağlamı belirteçleri çift yönlü sözleşmelerle kullanılamaz.  
  
 İstek-yanıt sözleşmeleri için, tanımlama bilgisi modu güvenlik bağlamı belirteçleri yalnızca güvenlik bağlama öğesinin altındaki bağlama yığını, oluşturma veya <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel> örnek oluşturmayı destekliyorsa çalışır.  
  
 Tek yönlü sözleşmeler için, güvenlik bağlama öğesinin altındaki bağlama yığını oluşturmayı <xref:System.ServiceModel.Channels.IRequestChannel> veya <xref:System.ServiceModel.Channels.IRequestSessionChannel> örneklerini destekliyorsa, tanımlama bilgisi modu güvenlik bağlamı belirteçleri işe yarar.  
  
### <a name="session-mode-security-context-tokens"></a>Oturum modu güvenlik bağlamı belirteçleri  
 Güvenlik bağlama öğesinin altındaki bağlama yığını oluşturmayı <xref:System.ServiceModel.Channels.IDuplexChannel> veya <xref:System.ServiceModel.Channels.IDuplexSessionChannel> örneklerini destekliyorsa, oturum modu SCT çift yönlü sözleşmeler için kullanılır.  
  
 Güvenlik bağlama öğesinin altındaki <xref:System.ServiceModel.Channels.IDuplexChannel>bağlama yığını <xref:System.ServiceModel.Channels.IRequestChannel> , <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, veya <xref:System.ServiceModel.Channels.IRequestSessionChannel>örneklerini oluşturmayı destekliyorsa, oturum modu SCT, istek-yanıt sözleşmeleri için geçerlidir.  
  
 Güvenlik bağlama öğesinin altındaki <xref:System.ServiceModel.Channels.IDuplexChannel>bağlama yığını <xref:System.ServiceModel.Channels.IRequestChannel> ,, veya <xref:System.ServiceModel.Channels.IRequestSessionChannel> örnekleri oluşturmayı destekliyorsa, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>oturum modu SCT, 1 yönlü sözleşmeler için kullanılır.  
  
## <a name="deriving-from-a-standard-binding"></a>Standart bir bağlamadan türetme  
 Tamamen yeni bir bağlama sınıfı oluşturmak yerine, sistem tarafından sağlanmış mevcut bağlamalardan birini genişletmeniz mümkün olabilir. Yukarıdaki örnekte olduğu gibi, <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> yöntemini <xref:System.ServiceModel.Channels.Binding.Scheme%2A> ve özelliğini geçersiz kılmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.Binding>
- [Özel Bağlamalar](custom-bindings.md)
