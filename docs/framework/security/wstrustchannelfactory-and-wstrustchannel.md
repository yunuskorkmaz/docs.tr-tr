---
title: WSTrustChannelFactory ve WSTrustChannel
ms.date: 03/30/2017
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7dfe18a55d8c7f56db1906cb2aa982ab043841c7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197294"
---
# <a name="wstrustchannelfactory-and-wstrustchannel"></a>WSTrustChannelFactory ve WSTrustChannel
Windows Communication Foundation (WCF) bilginiz varsa, bir WCF istemcisi Federasyon uyumlu olduğunu bilirsiniz. Bir WCF istemcisi ile yapılandırarak bir <xref:System.ServiceModel.WSFederationHttpBinding> ya da benzer özel bağlama, bir hizmet için Federasyon kimlik doğrulamasını etkinleştirebilirsiniz.  
  
 WCF hizmetinde kimlik doğrulaması için bu belirteci kullanır ve arka planda güvenlik belirteci hizmeti (STS) tarafından verilen belirteci alır. Bu yaklaşımın sınırlaması hiçbir sunucu ile istemcinin iletişim görünürlük olmasıdır. WCF bağlama verilen belirteç parametrelere göre sts'ye isteği güvenlik belirteci (k) otomatik olarak oluşturur. Bu istemci olamaz lk parametreleri istek başına farklılık, istek güvenlik belirteci yanıt görünen talepler gibi daha fazla bilgi almak için (RSTR) incelemek veya gelecekte kullanım için belirteç önbelleğe anlamına gelir.  
  
 Şu anda, WCF istemcisini temel Federasyon senaryoları için uygundur. Ancak, Windows Identity Foundation (WIF) destekleyen bir ana senaryoları biri lk WCF kolayca izin vermeyen bir düzeyde denetime gerektirir. Bu nedenle, WIF STS ile iletişim hakkında daha fazla denetime size özellikler ekler.  
  
 WIF, aşağıdaki Federasyon senaryolarını destekler:  
  
-   WIF bağımlılıkları olmadan bir WCF istemcisi kullanarak bir Federasyon Hizmeti için kimlik doğrulaması  
  
-   Bir WCF istemcisi sts'ye lk ActAs veya OnBehalfOf bir öğe eklemek için WIF etkinleştirme  
  
-   WIF kullanarak tek başına STS'den bir belirteç almak ve daha sonra bu belirteci ile kimlik doğrulaması bir WCF istemcisi etkinleştirin. Daha fazla bilgi için [ClaimsAwareWebService](https://go.microsoft.com/fwlink/?LinkID=248406) örnek.  
  
 İlk senaryoda açıklayıcıdır: var olan WCF istemcileri WIF bağlı olan taraflar ve Sts'ler çalışmaya devam edecek. Bu konuda, kalan iki kullanıldığı senaryoları tartışır.  
  
## <a name="enhancing-an-existing-wcf-client-with-actas--onbehalfof"></a>Mevcut bir WCF istemcisi ActAs ile geliştirme / OnBehalfOf  
 Tipik kimlik temsili senaryosu bir istemci sonra bir arka uç hizmetini çağıran bir orta katman hizmeti çağırır. Orta katman hizmet görür veya istemci adına, görevi görür.  
  
> [!TIP]
>  ActAs OnBehalfOf arasındaki fark nedir?  
>   
>  WS-Trust Protokolü açısından:  
>   
> 1. İstek sahibi içeren bir belirteç talep yaklaşık iki ayrı varlık istediğini ActAs lk öğeyi gösterir: İstek sahibi ve belirteci ActAs öğesi tarafından temsil edilen bir dış varlığı.  
> 2. İstek sahibinin talepleri yalnızca bir varlık içeren bir belirteç istediği OnBehalfOf lk öğeyi gösterir: OnBehalfOf öğesi belirteci tarafından temsil edilen dış varlık.  
>   
>  ActAs özelliği, genellikle burada verilen belirtecin son alıcı tüm temsilci zinciri inceleyin ve yalnızca istemci, ancak tüm aracıların bkz bileşik temsilci gerektiren senaryolarda kullanılır. Denetim ve diğer tüm kimlik temsilcisi zincirine dayalı etkinlikler ilgili, bu erişim denetimi gerçekleştirmek sağlar. ActAs özelliği, çok katmanlı sistemlerinde kimlik doğrulaması ve kimlik bilgileri hakkındaki bu bilgileri uygulama/iş mantığı katmanında geçirmek zorunda kalmadan Katmanlar arasındaki geçirmek için yaygın olarak kullanılır.  
>   
>  OnBehalfOf özelliği yalnızca orijinal istemci kimliğini önemli ve etkili bir şekilde kimlik kimliğe bürünme özelliği kullanılabilir Windows ile aynı olduğu yerde senaryolarda kullanılır. OnBehalfOf kullanıldığında, verilen belirtecin son alıcı yalnızca orijinal istemci talepleri görebilirsiniz ve aracılar ile ilgili bilgileri korunmaz. Bir ortak desendir OnBehalfOf özelliğin kullanıldığı yeri istemci STS, ancak bunun yerine doğrudan erişemez proxy deseni bir ara ağ geçidi üzerinden iletişim kurar. Proxy ağ geçidi arayan kimliğini doğrular ve ardından işleme için gerçek STS'ye gönderir k ileti OnBehalfOf öğesinin içine arayanı hakkında bilgi getirir. Elde edilen belirteç yalnızca istemci proxy verilen belirtecin alıcı için tamamen saydam hale proxy'sinin ilgili talepleri içerir. WIF desteklemediği Not \<: SecurityTokenReference > veya \<wsa:EndpointReferences > bir alt öğesi olarak \<wst:OnBehalfOf >. WS-Güven belirtimini özgün istek sahibine (kim adına proxy davranıyorsa) tanımlamak üç yol sağlar. Bunlar:  
>   
>  -   Güvenlik belirteci başvurusu. Bir belirteç başvurusu, ileti veya büyük olasılıkla alınan / bant).  
> -   Uç nokta başvurusu. Yeniden bant dışından verileri aramak için bir anahtar olarak kullanılır.  
> -   Güvenlik belirteci. Özgün istek sahibine doğrudan tanımlar.  
>   
>  WIF, şifrelenmiş veya, şifrelenmemiş bir doğrudan alt öğesi olarak yalnızca güvenlik belirteçleri destekleyen \<wst:OnBehalfOf >.  
  
 Bu bilgiler lk ActAs ve OnBehalfOf belirteci öğeleri kullanarak bir WS-Trust veren için aktarılır.  
  
 WCF için lk eklenecek rasgele XML öğeleri sağlayan bağlama üzerinde bir genişletilebilirlik noktası kullanıma sunar. Ancak, genişletilebilirlik noktası bağlama bağlı olmadığından, çağrı başına değişen lk içeriği gerektiren senaryolar performansınızın her çağrı için istemciyi yeniden oluşturmalısınız. WIF kullanan genişletme yöntemleri üzerinde `ChannelFactory` lk için bant dışı elde edilen herhangi bir belirteci eklemek geliştiricilerin izin veren sınıfı. Aşağıdaki kod örneği, istemci (örneğin, bir X.509, kullanıcı adı veya güvenlik onaylama işlemi biçimlendirme dili (SAML) belirteci) temsil eden bir belirteci alıp yayınlayanla gönderilen lk ekleme gösterilmektedir.  
  
```  
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>( clientSamlToken );  
serviceChannel.Hello("Hi!");  
```  
  
 WIF aşağıdaki avantajları sağlar:  
  
-   Kanal başına lk değiştirilebilir; Bu nedenle, orta katman Hizmetleri kanal fabrikası performansı geliştirir her istemci için yeniden oluşturmanız gerekmez.  
  
-   Bu, kolay bir yükseltme yolu Kimlik temsilcisi semantiği etkinleştirmek istediğiniz var olan orta katman için WCF hizmetleri mümkün kılar, var olan WCF istemcileri ile çalışır.  
  
 Ancak, var. yine de istemcinin iletişim STS ile hiçbir görünürlük Bu üçüncü senaryoda inceleyeceğiz.  
  
## <a name="communicating-directly-with-an-issuer-and-using-the-issued-token-to-authenticate"></a>Doğrudan bir verici ile iletişim kuran ve kimlik doğrulaması için verilen belirteç kullanma  
 Bazı Gelişmiş senaryolar için bir WCF istemcisi geliştirme yeterli değildir. Yalnızca WCF genellikle kullanan geliştiriciler kullanım ileti / Out ileti sözleşmeleri ve istemci tarafı işleme veren yanıtı el ile ayrıştırma.  
  
 WIF tanıtır <xref:System.ServiceModel.Security.WSTrustChannelFactory> ve <xref:System.ServiceModel.Security.WSTrustChannel> istemci doğrudan bir WS-Güven verici ile iletişim kurmasına izin vermek için sınıflar. <xref:System.ServiceModel.Security.WSTrustChannelFactory> Ve <xref:System.ServiceModel.Security.WSTrustChannel> aşağıdaki kod örneğinde gösterildiği gibi veren ve istemci arasında akmasına izin türü kesin belirlenmiş lk ve RSTR nesne sınıflarını etkinleştir.  
  
```  
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory( stsBinding, stsAddress );  
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();  
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);  
rst.AppliesTo = new EndpointAddress(serviceAddress);  
RequestSecurityTokenResponse rstr = null;  
SecurityToken token = channel.Issue(rst, out rstr);  
```  
  
 Unutmayın `out` parametresi <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> yöntemi, istemci tarafı İnceleme RSTR erişim sağlar.  
  
 Şu ana kadar biz yalnızca bir belirtecin nasıl edinileceğini gördünüz. Öğesinden döndürülen belirteci <xref:System.ServiceModel.Security.WSTrustChannel> nesnesi bir `GenericXmlSecurityToken` tüm bağlı olan taraf için kimlik doğrulaması için gerekli olan bilgileri içeren. Aşağıdaki kod örneği, bu belirteç kullanma işlemini gösterir.  
  
```  
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token ); serviceChannel.Hello("Hi!");  
```  
  
 <xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> Genişletme yöntemini `ChannelFactory` nesnesini, bant dışı bir belirteç almış ve bu veren normal WCF çağrısı ve bunun yerine bağlı olan taraf için kimlik doğrulaması için elde edilen belirteç WIF gösterir. Bu, aşağıdaki faydaları vardır:  
  
-   Bu belirteç verme işlemi üzerinde tam denetim verir.  
  
-   ActAs destekler / doğrudan üzerinde giden lk bu özellikleri ayarlayarak OnBehalfOf senaryoları.  
  
-   Bu, kararlarına RSTR içeriklerine dayanan dinamik istemci-tarafı güven sağlar.  
  
-   Önbelleğe alma ve öğesinden döndürülen belirteci yeniden sağlar <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> yöntemi.  
  
-   <xref:System.ServiceModel.Security.WSTrustChannelFactory> ve <xref:System.ServiceModel.Security.WSTrustChannel> kanalı önbelleğe alma, hata ve kurtarma semantiğine göre WCF en iyi denetimi için izin verin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WIF Özellikleri](../../../docs/framework/security/wif-features.md)
