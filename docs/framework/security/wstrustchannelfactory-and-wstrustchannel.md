---
title: WSTrustChannelFactory ve WSTrustChannel
ms.date: 03/30/2017
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
author: BrucePerlerMS
ms.openlocfilehash: e00f3ae25a50c2fb3f34f4c04d02cde574b3da17
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044911"
---
# <a name="wstrustchannelfactory-and-wstrustchannel"></a>WSTrustChannelFactory ve WSTrustChannel
Zaten Windows Communication Foundation (WCF) hakkında bilginiz varsa, bir WCF istemcisinin zaten Federasyon duyarlı olduğunu bilirsiniz. <xref:System.ServiceModel.WSFederationHttpBinding> Veya benzer bir özel bağlamaya sahip bir WCF istemcisi yapılandırarak bir hizmette federal kimlik doğrulamasını etkinleştirebilirsiniz.

 WCF, arka planda güvenlik belirteci hizmeti (STS) tarafından verilen belirteci alır ve bu belirteci hizmette kimlik doğrulamak için kullanır. Bu yaklaşımın ana sınırlaması, istemcinin sunucuyla olan iletişimleriyle ilgili bir görünürlük olmaması olabilir. WCF, bağlamada verilen belirteç parametrelerine göre istek güvenlik belirtecini (RST) STS 'ye otomatik olarak oluşturur. Bu, istemcinin istek başına RST parametrelerini değiştiremediği, görüntüleme talepleri gibi bilgileri almak için istek güvenlik belirteci yanıtını (RSTR) inceleyerek veya gelecekte kullanılmak üzere belirtecin önbelleğe alabileceği anlamına gelir.

 Şu anda WCF istemcisi temel Federasyon senaryoları için uygundur. Ancak, Windows Identity Foundation 'ın (WıF) desteklediği önemli senaryolardan biri, WCF 'nin kolayca izin vermediği bir düzeyde RST üzerinde denetim gerektirir. Bu nedenle, WıF, STS ile iletişim üzerinde size daha fazla denetim sağlayan özellikler ekler.

 WıF aşağıdaki Federasyon senaryolarını destekler:

- Federasyon hizmetinde kimlik doğrulaması yapmak için herhangi bir WıF bağımlılığı olmadan bir WCF istemcisi kullanma

- Bir WCF istemcisinde WıF 'yi, STS 'ye RST 'ye bir ActAs veya OnBehalfOf öğesi eklemek için etkinleştirme

- STS 'den bir belirteç elde etmek ve ardından bu belirteçle kimlik doğrulaması yapmak için bir WCF istemcisini etkinleştirmek üzere WıF 'yi tek başına kullanma. Daha fazla bilgi için bkz. [ClaimsAwareWebService](https://go.microsoft.com/fwlink/?LinkID=248406) örneği.

 İlk senaryo kendi kendine açıklayıcıdır: Mevcut WCF istemcileri WıF bağlı tarafları ve STSs ile çalışmaya devam edecektir. Bu konuda, kalan iki senaryo ele alınmaktadır.

## <a name="enhancing-an-existing-wcf-client-with-actas--onbehalfof"></a>Mevcut bir WCF Istemcisini ActAs/OnBehalfOf ile geliştirme
Tipik bir kimlik temsili senaryosunda istemci, bir arka uç hizmeti çağıran bir orta katman hizmeti çağırır. Orta katman hizmeti, istemcisini, veya adına göre davranır.

> [!TIP]
> ActAs ve OnBehalfOf arasındaki fark nedir?
>
> WS-Trust protokol açısından:
>
> 1. ActAs RST öğesi, istek sahibinin iki farklı varlık hakkında talepler içeren bir belirteç istediğini belirtir: istek sahibi ve ActAs öğesinde belirteç tarafından temsil edilen bir dış varlık.
> 2. OnBehalfOf RST öğesi, istek sahibinin yalnızca bir varlık hakkında talepler içeren bir belirteç istediğini belirtir: OnBehalfOf öğesinde belirteç tarafından temsil edilen dış varlık.
>
> ActAs özelliği genellikle, verilen belirtecin son alıcısının tüm atama zincirini inceleyebilir ve yalnızca istemciyi değil, ancak tüm aracılar ' ı görebildiği bileşik temsili gerektiren senaryolarda kullanılır. Bu, tüm kimlik temsili zinciri temelinde erişim denetimi, denetim ve diğer ilgili etkinlikleri gerçekleştirmesine olanak sağlar. ActAs özelliği, bu bilgileri uygulama/iş mantığı katmanında iletmek zorunda kalmadan, Katmanlar arasındaki kimlikler hakkında bilgi edinmek ve bu bilgileri iletmek için çok katmanlı sistemlerde yaygın olarak kullanılır.
>
> OnBehalfOf özelliği, yalnızca özgün istemcinin kimliğinin önemli olduğu ve Windows 'da bulunan kimlik kimliğe bürünme özelliği ile etkin şekilde olduğu senaryolarda kullanılır. OnBehalfOf kullanıldığında, verilen belirtecin son alıcısı yalnızca özgün istemciyle ilgili talepleri görebilir ve aracılar hakkındaki bilgiler korunmaz. OnBehalfOf özelliğinin kullanıldığı yaygın bir model, istemcinin doğrudan STS 'ye erişebildiği ancak proxy ağ geçidi üzerinden iletişim kuracağı proxy modelidir. Proxy ağ geçidi, arayanın kimliğini doğrular ve çağıran hakkındaki bilgileri, daha sonra işlenmek üzere gerçek STS 'ye gönderdiği RST iletisinin OnBehalfOf öğesine koyar. Elde edilen belirteç yalnızca Proxy istemcisiyle ilgili talepleri içerir ve proxy 'nin verilen belirtecin alıcısı için tamamen saydam hale getirir. WIF, bir \< \<wst: OnBehalfOf > alt öğesi olarak > WSO: SecurityTokenReference > veya \<wsa: EndPointReferences ' i desteklemediğini unutmayın. WS-Trust belirtimi, özgün istek sahibinin (proxy 'nin hareket eteceği adına) tanımlanması için üç yol sağlar. Bunlar:
>
> - Güvenlik belirteci başvurusu. Bir belirteç başvurusu, iletide, ya da bant dışında alınmış olabilir.
> - Uç nokta başvurusu. Verileri aramak için bir anahtar olarak kullanılır ve bant dışı.
> - Güvenlik belirteci. Özgün istek sahibine doğrudan tanıtır.
>
> WIF, yalnızca bir wst: OnBehalfOf > doğrudan alt öğesi olarak şifrelenmiş veya şifrelenmemiş olan \<güvenlik belirteçlerini destekler.

 Bu bilgiler, RST 'deki ActAs ve OnBehalfOf belirteci öğelerini kullanarak WS-Trust veren 'e aktarılır.

 WCF, bağlamada rastgele XML öğelerinin eklenmesine izin veren bir genişletilebilirlik noktası sunar. Ancak, genişletilebilirlik noktası bağlamaya bağlı olduğundan, her çağrı için değişiklik yapmak üzere RST içeriklerinin gerekli olduğu senaryolar, performansı azaltan her çağrı için istemciyi yeniden oluşturmanız gerekir. WIF, geliştiricilerin bant dışı alınan `ChannelFactory` bir belirteci RST 'ye eklemesine izin vermek için sınıfında genişletme yöntemleri kullanır. Aşağıdaki kod örneği, istemciyi temsil eden bir belirteci (örneğin, bir X. 509.952, Kullanıcı adı veya Security Assertion Markup Language (SAML) belirteci) alma ve Sertifikayı verenden gönderilen RST 'ye iliştirme şeklini gösterir.

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>(clientSamlToken);
serviceChannel.Hello("Hi!");
```

 WıF aşağıdaki avantajları sağlar:

- RST, kanal başına değiştirilebilir; Bu nedenle, orta katmanlı hizmetlerin her istemci için kanal fabrikasını yeniden oluşturması gerekmez, bu da performansı geliştirir.

- Bu, mevcut WCF istemcileriyle birlikte çalışarak, kimlik temsili semantiğini etkinleştirmek isteyen mevcut WCF orta katman hizmetleri için kolay bir yükseltme yolu sağlar.

 Bununla birlikte, istemci STS ile iletişimin üzerinde hala hiçbir görünürlük yoktur. Bunu üçüncü senaryoda inceleyeceğiz.

## <a name="communicating-directly-with-an-issuer-and-using-the-issued-token-to-authenticate"></a>Doğrudan veren ile iletişim kurma ve kimlik doğrulaması için verilen belirteci kullanma
Bazı Gelişmiş senaryolarda, bir WCF istemcisini geliştirmek yeterli değildir. Yalnızca WCF kullanan geliştiriciler tipik olarak Ileti Içinde Ileti kullanır/Iletiyordu ve sertifikayı verenin yanıtını el ile ayrıştırır.

WIF, <xref:System.ServiceModel.Security.WSTrustChannelFactory> istemcinin bir <xref:System.ServiceModel.Security.WSTrustChannel> WS-Trust verenle doğrudan iletişim kurmasına izin vermek için ve sınıflarını tanıtır. <xref:System.ServiceModel.Security.WSTrustChannelFactory> Ve<xref:System.ServiceModel.Security.WSTrustChannel> sınıfları, aşağıdaki kod örneğinde gösterildiği gibi, kesin olarak belirlenmiş RST ve rstr nesnelerini istemci ve veren arasında akışa almak üzere etkinleştirir.

```csharp
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory(stsBinding, stsAddress);
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);
rst.AppliesTo = new EndpointAddress(serviceAddress);
RequestSecurityTokenResponse rstr = null;
SecurityToken token = channel.Issue(rst, out rstr);
```

<xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> Yöntemdeki parametresinin, istemci tarafı incelemesi için rstr erişimine izin verdiğini unutmayın. `out`

Şimdiye kadar, yalnızca bir belirtecin nasıl alınacağını gördünüz. <xref:System.ServiceModel.Security.WSTrustChannel> Nesnesinden döndürülen belirteç, bağlı olan tarafa kimlik doğrulaması için `GenericXmlSecurityToken` gerekli tüm bilgileri içeren bir ' tır. Aşağıdaki kod örneği, bu belirtecin nasıl kullanılacağını göstermektedir.

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token );
serviceChannel.Hello("Hi!");
```

Nesne üzerindeki genişletme yöntemi, bant dışı bir belirteç elde ediyorsanız ve veren için normal WCF çağrısını durdurup bunun yerine, bağlı olan tarafın kimliğini doğrulamak için edindiğiniz belirteci kullanması durumunda W'e gösterir. <xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> `ChannelFactory` Bu, aşağıdaki avantajlara sahiptir:

- Belirteç verme işlemi üzerinde tamamen denetim elde etmenizi sağlar.

- Bu özellikleri giden RST üzerinde doğrudan ayarlayarak ActAs/OnBehalfOf senaryolarını destekler.

- RSTR içeriğine göre dinamik istemci tarafı güven kararlarının yapılmasını sağlar.

- <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> Yönteminden döndürülen belirteci önbelleğe almanızı ve yeniden kullanmanızı sağlar.

- <xref:System.ServiceModel.Security.WSTrustChannelFactory>ve <xref:System.ServiceModel.Security.WSTrustChannel> WCF en iyi uygulamalarına göre kanal önbelleğe alma, hata ve kurtarma semantiğinin denetimine izin verin.

## <a name="see-also"></a>Ayrıca bkz.

- [WIF Özellikleri](wif-features.md)
