---
description: 'Daha fazla bilgi edinin: User-Defined bağlamaları oluşturma'
title: Kullanıcı Tanımlı Bağlamalar Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
ms.openlocfilehash: 9eabb1840f343439d8a8cc79fb0a9b1582b9126d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735406"
---
# <a name="creating-user-defined-bindings"></a>Kullanıcı Tanımlı Bağlamalar Oluşturma

Sistem tarafından sağlanmayan bağlamaları oluşturmanın birkaç yolu vardır:  
  
- Bağlama öğeleriyle doldurduğunuz bir kapsayıcı olan sınıfını temel alan özel bir bağlama oluşturun <xref:System.ServiceModel.Channels.CustomBinding> . Özel bağlama daha sonra bir hizmet uç noktasına eklenir. Özel bağlamayı program aracılığıyla veya bir uygulama yapılandırma dosyasında oluşturabilirsiniz. Bir uygulama yapılandırma dosyasından bağlama öğesi kullanmak için bağlama öğesi genişlemelidir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> . Özel Bağlamalar hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](custom-bindings.md) ve <xref:System.ServiceModel.Channels.CustomBinding> .  
  
- Standart bağlamadan türetilen bir sınıf oluşturabilirsiniz. Örneğin, <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> bağlama öğelerini almak ve özel bir bağlama öğesi eklemek veya güvenlik için belirli bir değer oluşturmak üzere bir sınıfından bir sınıf türetebilir ve geçersiz kılabilirsiniz.  
  
- <xref:System.ServiceModel.Channels.Binding>Bağlama uygulamasının tamamını tamamen denetlemek için yeni bir tür oluşturabilirsiniz.  
  
## <a name="the-order-of-binding-elements"></a>Bağlama öğelerinin sırası  

 Her bağlama öğesi ileti gönderirken veya alırken bir işleme adımını temsil eder. Çalışma zamanında, bağlama öğeleri, giden ve gelen kanal yığınları oluşturmak için gereken kanalları ve dinleyicileri oluşturur.  
  
 Üç ana tür bağlama öğesi vardır: protokol bağlama öğeleri, kodlama bağlama öğeleri ve taşıma bağlama öğeleri.  
  
 Protokol bağlama öğeleri – bu öğeler, iletiler üzerinde işlem yapan üst düzey işleme adımlarını temsil eder. Bu bağlama öğeleri tarafından oluşturulan kanallar ve dinleyiciler ileti içeriğini ekleyebilir, kaldırabilir veya değiştirebilir. Verilen bağlama, her biri öğesinden devralan rastgele sayıda protokol bağlama öğesine sahip olabilir <xref:System.ServiceModel.Channels.BindingElement> . Windows Communication Foundation (WCF), ve dahil olmak üzere çeşitli protokol bağlama öğeleri içerir <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .  
  
 Encoding bağlama öğesi – bu öğeler, bir ileti ve tel iletilmek üzere bir kodlama arasındaki dönüşümleri temsil eder. Tipik WCF bağlamaları tam olarak bir kodlama bağlama öğesi içerir. Bağlama öğelerinin kodlama örnekleri,, <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> ve ' i içerir <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> . Bir bağlama için bir kodlama bağlama öğesi belirtilmemişse, varsayılan bir kodlama kullanılır. Aktarım HTTP olduğunda varsayılan metin, aksi durumda ikili olur.  
  
 Taşıma bağlama öğesi – bu öğeler bir Aktarım Protokolü üzerinde kodlama iletisinin aktarımını temsil eder. Tipik WCF bağlamaları, öğesinden devralan tam olarak bir aktarım bağlama öğesi içerir <xref:System.ServiceModel.Channels.TransportBindingElement> . Taşıma bağlama öğelerinin örnekleri,, <xref:System.ServiceModel.Channels.TcpTransportBindingElement> ve ' i içerir <xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> .  
  
 Yeni bağlamalar oluştururken, eklenen bağlama öğelerinin sırası önemlidir. Bağlama öğelerini her zaman aşağıdaki sırada ekleyin:  
  
|Katman|Seçenekler|Gerekli|  
|-----------|-------------|--------------|  
|İşlem akışı|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|No|  
|Güvenilirlik|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|No|  
|Güvenlik|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|No|  
|Bileşik çift yönlü|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|No|  
|Encoding|Metin, Ikili, MTOM, özel|Yes\*|  
|Aktarım|TCP, adlandırılmış kanallar, HTTP, HTTPS, MSMQ, özel|Yes|  
  
\*Her bağlama için bir kodlama gerektiğinden, bir kodlama belirtilmemişse, WCF sizin için varsayılan bir kodlama ekler. Varsayılan değer HTTP ve HTTPS aktarımları için Text/XML, aksi durumda binary.  
  
## <a name="creating-a-new-binding-element"></a>Yeni bağlama öğesi oluşturma  

 <xref:System.ServiceModel.Channels.BindingElement>WCF tarafından sağlanarak türetilen türlerin yanı sıra kendi bağlama öğelerinizi de oluşturabilirsiniz. Bu, bağlama yığınının oluşturulma şeklini ve <xref:System.ServiceModel.Channels.BindingElement> yığın içindeki diğer sistem tarafından sunulan türlerle birleştirilebilen kendi oluşturduğunuz bileşenlerini özelleştirmenizi sağlar.  
  
 Örneğin, bir `LoggingBindingElement` veritabanını bir veritabanına kaydetme özelliğini sağlayan bir uygularsanız, kanal yığınında bir aktarım kanalının üzerine yerleştirmeniz gerekir. Bu durumda, uygulama, `LoggingBindingElement` `TcpTransportBindingElement` Aşağıdaki örnekte olduğu gibi ile içeren bir özel bağlama oluşturur.  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),
  new TcpTransportBindingElement()  
);  
```  
  
 Yeni bağlama öğesini nasıl yazdığınız, tam işlevselliğine bağlıdır. Örnek, [taşıma: UDP](../samples/transport-udp.md), tek bir tür bağlama öğesinin nasıl uygulanacağı hakkında ayrıntılı bir açıklama sağlar.  
  
## <a name="creating-a-new-binding"></a>Yeni bağlama oluşturma  

 Kullanıcı tarafından oluşturulan bağlama öğesi iki şekilde kullanılabilir. Önceki bölümde ilk yol gösterilmektedir: özel bir bağlama. Özel bir bağlama, kullanıcının, Kullanıcı tarafından oluşturulan bir bağlama öğesi kümesini temel alarak kendi bağlamasını oluşturmalarına olanak tanır.  
  
 Bağlamayı birden fazla uygulamada kullanırsanız, kendi bağlamayı oluşturun ve genişletin <xref:System.ServiceModel.Channels.Binding> . Bu, bir özel bağlamayı her kullanmak istediğinizde el ile oluşturmayı önler. Kullanıcı tanımlı bir bağlama, bağlamanın davranışını tanımlamanızı ve Kullanıcı tanımlı bağlama öğelerini dahil etmenizi sağlar. *Önceden paketlenmiştir*: bağlamayı her kullandığınızda yeniden oluşturmanız gerekmez.  
  
 En azından, Kullanıcı tanımlı bir bağlamanın <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> yöntemini ve özelliğini uygulaması gerekir <xref:System.ServiceModel.Channels.Binding.Scheme%2A> .  
  
 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>Yöntemi, <xref:System.ServiceModel.Channels.BindingElementCollection> bağlama yönelik bağlama öğelerini içeren yeni bir döndürür. Koleksiyon sıralanmıştır ve önce protokol bağlama öğelerini, sonra Encoding bağlama öğesini, ardından da taşıma bağlama öğesini içermelidir. WCF sistem tarafından sağlanmış bağlama öğelerini kullanırken, [özel bağlamalarda](custom-bindings.md)belirtilen bağlama öğesi sıralama kurallarını izlemeniz gerekir. Bu koleksiyon, Kullanıcı tanımlı bağlama sınıfında başvurulan nesnelere asla başvurmamalıdır; Sonuç olarak, bağlama yazarları `Clone()` <xref:System.ServiceModel.Channels.BindingElementCollection> öğesine her çağrısının bir öğesini döndürmelidir <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> .  
  
 <xref:System.ServiceModel.Channels.Binding.Scheme%2A>Özelliği, bağlamada kullanılan Aktarım protokolünün URI düzenini temsil eder. Örneğin, *WSHttpBinding* ve *NetTcpBinding* ilgili özelliklerinden "http" ve "net. TCP" döndürür <xref:System.ServiceModel.Channels.Binding.Scheme%2A> .  
  
 Kullanıcı tanımlı bağlamalara yönelik isteğe bağlı yöntemlerin ve özelliklerin tam listesi için bkz <xref:System.ServiceModel.Channels.Binding> ..  
  
### <a name="example"></a>Örnek  

 Bu örnek ' de `SampleProfileUdpBinding` ' den türetilen profil bağlamasını uygular <xref:System.ServiceModel.Channels.Binding> . , `SampleProfileUdpBinding` İçinde en fazla dört bağlama öğesi içerir: bir kullanıcı tarafından oluşturulan `UdpTransportBindingElement` ve üç sistem tarafından sunulan: `TextMessageEncodingBindingElement` , `CompositeDuplexBindingElement` , ve `ReliableSessionBindingElement` .  
  
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
  
### <a name="one-shot-security"></a>One-Shot güvenliği  

 `negotiateServiceCredential`Yapılandırma öğesinin özniteliğini olarak ayarlayarak, tüm gerekli güvenlik bilgilerinin tek bir iletiyle gönderildiği "tek yönlü" bir güvenlik uygulayabilirsiniz \<message> `false` .  
  
 Tek çizgili kimlik doğrulama, çift yönlü sözleşmelerle çalışmaz.  
  
 Request-Reply sözleşmeler için, yalnızca güvenlik bağlama öğesinin altındaki bağlama yığını oluşturmayı veya örneklerini destekliyorsa, tek seferlik kimlik doğrulama kullanılır <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel> .  
  
 Tek yönlü sözleşmeler için, güvenlik bağlama öğesinin altındaki bağlama yığını <xref:System.ServiceModel.Channels.IRequestChannel> ,, <xref:System.ServiceModel.Channels.IRequestSessionChannel> <xref:System.ServiceModel.Channels.IOutputChannel> veya örneklerini oluşturmayı destekliyorsa, tek seferlik kimlik doğrulama işe yarar <xref:System.ServiceModel.Channels.IOutputSessionChannel> .  
  
### <a name="cookie-mode-security-context-tokens"></a>Tanımlama bilgisi modu güvenlik bağlamı belirteçleri  

 Tanımlama bilgisi modu güvenlik bağlamı belirteçleri çift yönlü sözleşmelerle kullanılamaz.  
  
 Request-Reply sözleşmeler için, tanımlama bilgisi modu güvenlik bağlamı belirteçleri yalnızca güvenlik bağlama öğesinin altındaki bağlama yığını, oluşturma veya örnek oluşturmayı destekliyorsa <xref:System.ServiceModel.Channels.IRequestChannel> çalışır <xref:System.ServiceModel.Channels.IRequestSessionChannel> .  
  
 Tek yönlü sözleşmeler için, güvenlik bağlama öğesinin altındaki bağlama yığını oluşturmayı veya örneklerini destekliyorsa, tanımlama bilgisi modu güvenlik bağlamı belirteçleri işe yarar <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Channels.IRequestSessionChannel> .  
  
### <a name="session-mode-security-context-tokens"></a>Oturum modu güvenlik bağlamı belirteçleri  

 Güvenlik bağlama öğesinin altındaki bağlama yığını oluşturmayı veya örneklerini destekliyorsa, oturum modu SCT çift yönlü sözleşmeler için <xref:System.ServiceModel.Channels.IDuplexChannel> kullanılır <xref:System.ServiceModel.Channels.IDuplexSessionChannel> .  
  
 Güvenlik bağlama öğesinin altındaki bağlama yığını <xref:System.ServiceModel.Channels.IDuplexChannel> ,, <xref:System.ServiceModel.Channels.IDuplexSessionChannel> <xref:System.ServiceModel.Channels.IRequestChannel> veya örneklerini oluşturmayı destekliyorsa, oturum modu SCT Request-Reply sözleşmeler için geçerlidir <xref:System.ServiceModel.Channels.IRequestSessionChannel> .  
  
 Güvenlik bağlama öğesinin altındaki bağlama yığını <xref:System.ServiceModel.Channels.IDuplexChannel> ,, <xref:System.ServiceModel.Channels.IDuplexSessionChannel> <xref:System.ServiceModel.Channels.IRequestChannel> veya örnekleri oluşturmayı destekliyorsa, oturum modu SCT, 1 yönlü sözleşmeler için kullanılır <xref:System.ServiceModel.Channels.IRequestSessionChannel> .  
  
## <a name="deriving-from-a-standard-binding"></a>Standart bir bağlamadan türetme  

 Tamamen yeni bir bağlama sınıfı oluşturmak yerine, sistem tarafından sağlanmış mevcut bağlamalardan birini genişletmeniz mümkün olabilir. Yukarıdaki örnekte olduğu gibi, <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> yöntemini ve özelliğini geçersiz kılmanız gerekir <xref:System.ServiceModel.Channels.Binding.Scheme%2A> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.Binding>
- [Özel Bağlamalar](custom-bindings.md)
