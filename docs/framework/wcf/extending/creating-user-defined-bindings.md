---
title: Kullanıcı Tanımlı Bağlamalar Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
ms.openlocfilehash: 34100569dc5cd5a340abca66fedca40ba21c1e0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185640"
---
# <a name="creating-user-defined-bindings"></a>Kullanıcı Tanımlı Bağlamalar Oluşturma
Sistem tarafından sağlanmadı bağlamalar oluşturmak için çeşitli yollar vardır:  
  
- Bağlama öğeleriyle doldurduğunuz <xref:System.ServiceModel.Channels.CustomBinding> bir kapsayıcı olan sınıfa dayalı özel bir bağlama oluşturun. Özel bağlama daha sonra bir hizmet bitiş noktasına eklenir. Özel bağlamayı programlı olarak veya bir uygulama yapılandırma dosyasında oluşturabilirsiniz. Bir uygulama yapılandırma dosyasından bağlayıcı bir öğe kullanmak <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>için bağlama öğesi nin genişlemesi gerekir. Özel bağlamalar hakkında daha fazla bilgi <xref:System.ServiceModel.Channels.CustomBinding>için [Özel Bağlamalar](custom-bindings.md) ve .  
  
- Standart bir bağlamadan türeyen bir sınıf oluşturabilirsiniz. Örneğin, bağlama öğelerini elde <xref:System.ServiceModel.WSHttpBinding> etmek ve <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> özel bir bağlama öğesi eklemek veya güvenlik için belirli bir değer oluşturmak için bir sınıf türetebilir ve yöntemi geçersiz kılabilirsiniz.  
  
- Tüm bağlama uygulamasını <xref:System.ServiceModel.Channels.Binding> tamamen denetlemek için yeni bir tür oluşturabilirsiniz.  
  
## <a name="the-order-of-binding-elements"></a>Bağlayıcı Öğelerin Sırası  
 İleti gönderirken veya alırken her bağlama öğesi bir işleme adımını temsil eder. Çalışma zamanında, bağlama öğeleri giden ve gelen kanal yığınları oluşturmak için gerekli kanalları ve dinleyicileri oluşturur.  
  
 Üç ana bağlama öğesi türü vardır: Protokol Bağlama Elemanları, Bağlama Elemanlarının Kodlanması ve Aktarım Bağlama Elemanları.  
  
 Protokol Bağlama Öğeleri – Bu öğeler iletiler üzerinde hareket eden üst düzey işleme adımlarını temsil eder. Bu bağlayıcı öğeler tarafından oluşturulan kanallar ve dinleyiciler ileti içeriğini ekleyebilir, kaldırabilir veya değiştirebilir. Belirli bir bağlama, her biri 'den <xref:System.ServiceModel.Channels.BindingElement>devralan rasgele sayıda iletişim kuralı bağlayıcı öğeye sahip olabilir. Windows Communication Foundation (WCF) ve <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>dahil olmak üzere çeşitli protokol bağlama öğeleri içerir.  
  
 Kodlama Bağlama Öğesi – Bu öğeler, bir ileti ile kablo üzerinde iletim için hazır bir kodlama arasındaki dönüşümleri temsil eder. Tipik WCF bağlamaları tam olarak bir kodlama bağlama öğesi içerir. Kodlama bağlayıcı öğeleriörnekleri , <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>ve <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Bir bağlama için bir kodlama bağlama öğesi belirtilmemişse, varsayılan bir kodlama kullanılır. Aktarım http ve ikili aksi takdirde varsayılan metindir.  
  
 Aktarım Bağlama Öğesi – Bu öğeler, bir kodlama iletisinin aktarım protokolüne aktarılmasını temsil emzdir. Tipik WCF bağlamaları, 'den <xref:System.ServiceModel.Channels.TransportBindingElement>devralan tam bir aktarım bağlama öğesi içerir. Aktarım bağlama elemanlarına <xref:System.ServiceModel.Channels.TcpTransportBindingElement>örnek <xref:System.ServiceModel.Channels.HttpTransportBindingElement>olarak <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>, ve .  
  
 Yeni bağlamalar oluştururken, eklenen bağlama öğelerinin sırası önemlidir. Her zaman aşağıdaki sırada bağlayıcı öğeler ekleyin:  
  
|Katman|Seçenekler|Gerekli|  
|-----------|-------------|--------------|  
|İşlem Akışı|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|Hayır|  
|Güvenilirlik|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|Hayır|  
|Güvenlik|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|Hayır|  
|Kompozit Dubleks|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|Hayır|  
|Encoding|Metin, İkili, MTOM, Özel|Evet\*|  
|Aktarım|TCP, Adlandırılmış Borular, HTTP, HTTPS, MSMQ, Özel|Evet|  
  
\*Her bağlama için bir kodlama gerektiğinden, bir kodlama belirtilmemişse, WCF sizin için varsayılan bir kodlama ekler. Varsayılan, HTTP ve HTTPS aktarımları için Metin/XML ve bunun dışında Ikilidir.  
  
## <a name="creating-a-new-binding-element"></a>Yeni Bir Bağlama Öğesi Oluşturma  
 WCF tarafından sağlanan <xref:System.ServiceModel.Channels.BindingElement> türlerden türetilen türlere ek olarak, kendi bağlama öğelerinizi oluşturabilirsiniz. Bu, yığındaki diğer sistem tarafından sağlanan türlerle oluşturulabilecek kendi <xref:System.ServiceModel.Channels.BindingElement> bağlarınızı oluşturarak bağlama yığınının oluşturulma biçimini ve içinde bulunan bileşenleri özelleştirmenize olanak tanır.  
  
 Örneğin, iletiyi `LoggingBindingElement` veritabanında günlüğe kaydetme olanağı sağlayan bir uygulama uygularsanız, iletiyi kanal yığınındaki bir aktarım kanalının üzerine yerleştirmeniz gerekir. Bu durumda, uygulama aşağıdaki örnekte olduğu `LoggingBindingElement` gibi `TcpTransportBindingElement`, ile oluşan özel bir bağlama oluşturur.  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),
  new TcpTransportBindingElement()  
);  
```  
  
 Yeni bağlama öğenizi nasıl yazdığınız tam işlevselliği bağlıdır. Örneklerden biri olan [Transport: UDP,](../samples/transport-udp.md)bir tür bağlama öğesinin nasıl uygulanacağı hakkında ayrıntılı bir açıklama sağlar.  
  
## <a name="creating-a-new-binding"></a>Yeni Bir Bağlama Oluşturma  
 Kullanıcı tarafından oluşturulan bağlama öğesi iki şekilde kullanılabilir. Önceki bölümde ilk yol gösteriş: özel bir bağlama yoluyla. Özel bir bağlama, kullanıcı tarafından oluşturulan öğeler de dahil olmak üzere rasgele bir bağlama öğeleri kümesine dayalı olarak kendi bağlama oluşturmanıza olanak sağlar.  
  
 Bağlayıcıyı birden fazla uygulamada kullanırsanız, kendi bağlamanızı <xref:System.ServiceModel.Channels.Binding>oluşturun ve .'yi genişletin. Bu, her kullanmak istediğinizde özel bir bağlamanın el ile oluşturulmasını önler. Kullanıcı tanımlı bağlama, bağlamanın davranışını tanımlamanıza ve kullanıcı tanımlı bağlama öğelerieklemenize olanak tanır. Ve *önceden paketlenmiştir:* her kullandığınızda bağlamayı yeniden oluşturmanız gerekmez.  
  
 En azından, kullanıcı tanımlı bir <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> bağlama yöntemi <xref:System.ServiceModel.Channels.Binding.Scheme%2A> ve özelliği uygulamalıdır.  
  
 Yöntem, <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> bağlama <xref:System.ServiceModel.Channels.BindingElementCollection> için bağlayıcı öğeleri içeren yeni bir döndürür. Koleksiyon sıralanır ve önce protokol bağlama öğelerini içermeli, ardından kodlama bağlama öğesi, ardından aktarım bağlama öğesi olmalıdır. WCF sistemi tarafından sağlanan bağlama öğelerini kullanırken, [Özel Bağlamalarda](custom-bindings.md)belirtilen bağlama öğesi sıralama kurallarına uymanız gerekir. Bu koleksiyon, kullanıcı tanımlı bağlama sınıfında başvurulan nesnelere asla başvurmamalıdır; sonuç olarak, bağlayıcı yazarlar `Clone()` her <xref:System.ServiceModel.Channels.BindingElementCollection> çağrıda <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>bir dönmek gerekir.  
  
 Özellik, <xref:System.ServiceModel.Channels.Binding.Scheme%2A> bağlama da kullanılan taşıma protokolü için URI düzenini temsil eder. Örneğin, *WSHttpBinding* ve *NetTcpBinding* kendi <xref:System.ServiceModel.Channels.Binding.Scheme%2A> özelliklerinden "http" ve "net.tcp" döndürülme.  
  
 Kullanıcı tanımlı bağlamalar için isteğe bağlı yöntemlerin <xref:System.ServiceModel.Channels.Binding>ve özelliklerin tam listesi için bkz.  
  
### <a name="example"></a>Örnek  
 Bu `SampleProfileUdpBinding`örnek, <xref:System.ServiceModel.Channels.Binding>'den türeyen profil bağlama' uygular. İçinde `SampleProfileUdpBinding` en fazla dört bağlama öğesi içerir: `UdpTransportBindingElement`bir kullanıcı tarafından oluşturulan; ve üç sistem `TextMessageEncodingBindingElement`sağlanan: `CompositeDuplexBindingElement` `ReliableSessionBindingElement`, , ve .  
  
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
  
## <a name="security-restrictions-with-duplex-contracts"></a>Çift Yönlü Sözleşmelerle Güvenlik Kısıtlamaları  
 Tüm bağlama öğeleri birbiriyle uyumlu değildir. Özellikle, çift yönlü sözleşmelerde kullanıldığında güvenlik bağlama öğelerine ilişkin bazı kısıtlamalar vardır.  
  
### <a name="one-shot-security"></a>Tek Çekim güvenlik  
 Tüm gerekli güvenlik kimlik bilgilerinin tek bir iletide gönderildiği "tek çekimlik" `negotiateServiceCredential` güvenliği, \<ileti> yapılandırma `false`öğesinin özniteliğini ayarlayarak uygulayabilirsiniz.  
  
 Tek çekimkimlik doğrulama çift yönlü sözleşmeler ile çalışmaz.  
  
 İstek-Yanıt sözleşmeleri için tek çekimlik kimlik doğrulama yalnızca güvenlik bağlama öğesinin altındaki bağlama yığını oluşturmayı <xref:System.ServiceModel.Channels.IRequestChannel> veya <xref:System.ServiceModel.Channels.IRequestSessionChannel> örnekleri destekliyorsa çalışır.  
  
 Tek yönlü sözleşmeler için, güvenlik bağlama öğesinin altındaki bağlama <xref:System.ServiceModel.Channels.IRequestChannel>yığını <xref:System.ServiceModel.Channels.IRequestSessionChannel> <xref:System.ServiceModel.Channels.IOutputChannel> ,, veya <xref:System.ServiceModel.Channels.IOutputSessionChannel> örnekleri oluşturmayı destekliyorsa, tek çekimlik kimlik doğrulama çalışır.  
  
### <a name="cookie-mode-security-context-tokens"></a>Çerez modu Güvenlik Bağlam Belirteçleri  
 Çerez modu güvenlik bağlam belirteçleri çift yönlü sözleşmeler ile kullanılamaz.  
  
 İstek-Yanıt sözleşmeleri için çerez modu güvenlik bağlam belirteçleri yalnızca güvenlik bağlama <xref:System.ServiceModel.Channels.IRequestChannel> öğesinin altındaki bağlama yığını oluşturmayı veya <xref:System.ServiceModel.Channels.IRequestSessionChannel> örnekleri destekliyorsa çalışır.  
  
 Tek yönlü sözleşmeler için, güvenlik bağlama öğesinin altındaki bağlama yığını oluşturmayı <xref:System.ServiceModel.Channels.IRequestChannel> veya <xref:System.ServiceModel.Channels.IRequestSessionChannel> örnekleri destekliyorsa, çerez modu güvenlik bağlam belirteçleri çalışır.  
  
### <a name="session-mode-security-context-tokens"></a>Oturum modu Güvenlik Bağlam Belirteçleri  
 Güvenlik bağlama öğesinin altındaki bağlama yığını oluşturmayı <xref:System.ServiceModel.Channels.IDuplexChannel> veya <xref:System.ServiceModel.Channels.IDuplexSessionChannel> örnekleri destekliyorsa, oturum modu SCT çift yönlü sözleşmeler için çalışır.  
  
 Güvenlik bağlama öğesinin altındaki bağlama <xref:System.ServiceModel.Channels.IDuplexChannel>yığını , <xref:System.ServiceModel.Channels.IDuplexSessionChannel> <xref:System.ServiceModel.Channels.IRequestChannel> veya <xref:System.ServiceModel.Channels.IRequestSessionChannel>, örnekleri oluşturmayı destekliyorsa, oturum modu SCT İstek-Yanıt sözleşmeleri için çalışır.  
  
 Oturum modu SCT, güvenlik bağlama öğesinin altındaki bağlama yığını <xref:System.ServiceModel.Channels.IDuplexChannel> <xref:System.ServiceModel.Channels.IDuplexSessionChannel> <xref:System.ServiceModel.Channels.IRequestChannel> ,, <xref:System.ServiceModel.Channels.IRequestSessionChannel> veya örnekleri oluşturmayı destekliyorsa, tek yönlü sözleşmeler için çalışır.  
  
## <a name="deriving-from-a-standard-binding"></a>Standart Bağlamadan Kaynaklanan  
 Tamamen yeni bir bağlama sınıfı oluşturmak yerine, varolan sistem tarafından sağlanan bağlamalardan birini genişletmeniz mümkün olabilir. Tıpkı önceki durumda olduğu gibi, <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> yöntemi ve <xref:System.ServiceModel.Channels.Binding.Scheme%2A> özelliği geçersiz kılmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.Binding>
- [Özel Bağlamalar](custom-bindings.md)
