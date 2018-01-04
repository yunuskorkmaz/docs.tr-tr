---
title: WSTrustChannelFactory ve WSTrustChannel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 35f4449f7a826ea49be750cd750cb989c8c455fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wstrustchannelfactory-and-wstrustchannel"></a>WSTrustChannelFactory ve WSTrustChannel
Windows Communication Foundation (WCF) bilginiz varsa, bir WCF istemcisi zaten Federasyon uyumlu olduğunu biliyor. Bir WCF istemcisi ile yapılandırarak bir <xref:System.ServiceModel.WSFederationHttpBinding> veya benzer özel bağlama, bir hizmete federe kimlik doğrulamasını etkinleştirebilirsiniz.  
  
 WCF arka planda güvenlik belirteci hizmeti (STS) tarafından verilen ve bu belirteç hizmetin kimliğini kullanan belirteci alır. Bu yaklaşımın ana sınırlaması hiçbir sunucu ile istemcinin iletişim görünürlük olmasıdır. WCF bağlama belirteci verilen parametrelere göre STS isteği güvenlik belirteci (RST) otomatik olarak oluşturur. Bu istemci olamaz istek başına RST parametreleri farklılık, istek güvenlik belirteci yanıt görüntü talep gibi bilgileri almak için (RSTR) inceleyin veya gelecekte kullanım için belirteç önbelleğe anlamına gelir.  
  
 Şu anda, WCF istemcisini temel Federasyon senaryoları için uygundur. Ancak, Windows Identity Foundation (WIF) destekleyen ana senaryolardan biri, WCF kolayca izin vermeyen bir düzeyde RST üzerinde denetim gerektirir. Bu nedenle, WIF STS ile iletişim üzerinde daha fazla denetime özellikleri ekler.  
  
 WIF aşağıdaki Federasyon senaryoları destekler:  
  
-   Federe bir hizmetin kimliğini WIF bağımlılıkları olmadan WCF istemcisi kullanarak  
  
-   WIF sts'ye RST ActAs veya OnBehalfOf öğesi eklemek için bir WCF istemcisi etkinleştirme  
  
-   Tek başına bir belirteç STS elde edilir ve bu belirteci kimliğini doğrulamak bir WCF istemcisi etkinleştirmek için WIF kullanma. Daha fazla bilgi için bkz: [ClaimsAwareWebService](http://go.microsoft.com/fwlink/?LinkID=248406) örnek.  
  
 İlk senaryoda kendinden açıklamalıdır: var olan WCF istemcileri WIF bağlı olan taraflar ve Sts'ler ile çalışmaya devam edecek. Bu konuda kalan iki senaryo açıklanmaktadır.  
  
## <a name="enhancing-an-existing-wcf-client-with-actas--onbehalfof"></a>Varolan bir WCF istemcisi ActAs ile geliştirme / OnBehalfOf  
 Tipik kimlik temsili senaryosu bir istemci bir arka uç hizmeti çağıran bir orta katman hizmet çağırır. Orta katman hizmet görür veya istemci adına, davranır.  
  
> [!TIP]
>  ActAs OnBehalfOf arasındaki fark nedir?  
>   
>  WS-Trust alınırken açısından:  
>   
>  1.  İstek sahibi içeren bir belirteç talep yaklaşık iki ayrı varlık istediği ActAs RST öğeyi gösterir: İstek sahibi ve belirtecin ActAs öğesindeki tarafından temsil edilen bir dış varlık.  
> 2.  İstek sahibinin talepleri yalnızca bir varlık içeren bir belirteç istediği OnBehalfOf RST öğeyi gösterir: OnBehalfOf öğesi belirteçte tarafından temsil edilen dış varlık.  
>   
>  ActAs özelliği, genellikle burada verilen belirteç son alıcısı tüm temsilci zinciri inceleyin ve yalnızca istemci, ancak tüm aracıların bkz bileşik temsilci gerektiren senaryolarda kullanılır. Bu, erişim denetimi gerçekleştirmek sağlar, Denetim ve diğer ilgili tüm kimlik temsilcisi zincirine dayalı etkinlikleri. ActAs özelliği, çok katmanlı sistemlerinde kimlik doğrulaması ve bu bilgileri uygulama/iş mantığı katmanında geçirmek zorunda kalmadan katmanları arasında kimlikler hakkında bilgileri geçirmek için yaygın olarak kullanılır.  
>   
>  OnBehalfOf özelliği, burada yalnızca orijinal istemci kimliğini önemli ve etkili bir şekilde bulunan kimlik kimliğe bürünme özelliğini Windows ile aynı olduğu senaryolarda kullanılır. OnBehalfOf kullanıldığında, verilen belirteç son alıcısı yalnızca orijinal istemci hakkındaki talepler görebilir ve aracılar hakkında bilgi korunmaz. Bir ortak deseni OnBehalfOf özelliğin kullanıldığı burada istemci STS doğrudan ancak bunun yerine erişemez proxy düzeni proxy ağ geçidi üzerinden iletişim kurar. Proxy ağ geçidi arayanın kimliğini doğrular ve ardından işleme için gerçek STS gönderir RST iletinin OnBehalfOf öğesi çağıran hakkında bilgi yerleştirir. Elde edilen belirteç yalnızca istemci proxy verilen belirteç alıcı için tamamen saydam hale getirme proxy'sinin ilgili talepleri içerir. WIF desteklemediği Not \<: SecurityTokenReference > veya \<wsa:EndpointReferences > bir alt öğesi olarak \<wst:OnBehalfOf >. WS-Trust belirtimine (kim adına proxy hareket) özgün istek tanımlamak için üç yol sağlar. Bunlar:  
>   
>  -   Güvenlik belirteci başvurusu. Bir belirteç başvurusu, ileti veya büyük olasılıkla alınan dışı bant).  
> -   Bitiş noktası başvurusu. Yeniden bant dışından veri aramak için anahtar olarak kullanılır.  
> -   Güvenlik belirteci. Özgün istek doğrudan tanımlar.  
>   
>  WIF şifrelenmiş veya şifrelenmemiş, doğrudan alt öğesi olarak yalnızca güvenlik belirteçleri destekler \<wst:OnBehalfOf >.  
  
 Bu bilgiler bir WS-Trust veren RST ActAs ve OnBehalfOf belirteci öğeleri kullanılarak aktarılır.  
  
 WCF RST eklenecek rasgele XML öğeleri sağlayan bağlama genişletilebilirliği noktasında kullanıma sunar. Genişletilebilirlik noktası bağlama bağlı olduğundan, ancak, çağrı değiştirecek şekilde RST içeriği gerektiren senaryolar istemci performansı düşürür her çağrı için yeniden oluşturmanız gerekir. WIF kullanan genişletme yöntemleri üzerinde `ChannelFactory` RST için bant dışı elde herhangi bir belirteci eklemek geliştiricilere izin veren sınıfı. Aşağıdaki kod örneğinde, istemcinin (örneğin, bir X.509, kullanıcı adı veya güvenlik onaylama işlemi biçimlendirme dili (SAML) belirteci) temsil eden bir belirteci alın ve vereni gönderilen RST ekleme gösterilmektedir.  
  
```  
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>( clientSamlToken );  
serviceChannel.Hello("Hi!");  
```  
  
 WIF aşağıdaki avantajları sağlar:  
  
-   Kanal başına RST değiştirilebilir; Bu nedenle, orta katman Hizmetleri kanal fabrikası performansını artıran her istemci için yeniden oluşturmanız gerekmez.  
  
-   Bu, var olan WCF istemcileri ile hangi kolay yükseltme yolu Kimlik temsilcisi semantiği etkinleştirmek istediğiniz var olan orta katman için WCF hizmetleri mümkün kılar çalışır.  
  
 Ancak, yoktur hala STS ile istemcinin iletişim hiçbir görünürlük. Biz bu üçüncü senaryoda inceleyeceğiz.  
  
## <a name="communicating-directly-with-an-issuer-and-using-the-issued-token-to-authenticate"></a>Bir veren ile doğrudan iletişim kurmasını ve kimlik doğrulaması için verilen belirteç kullanma  
 Bazı Gelişmiş senaryolar için bir WCF istemcisi geliştirme yeterli değil. Genellikle yalnızca WCF kullanan geliştiriciler kullanın ileti / ileti sözleşmeleri ve istemci tarafı işleme veren yanıtını el ile ayrıştırma.  
  
 WIF tanıtır <xref:System.ServiceModel.Security.WSTrustChannelFactory> ve <xref:System.ServiceModel.Security.WSTrustChannel> WS-Trust veren ile doğrudan iletişim istemci izin vermek için sınıflar. <xref:System.ServiceModel.Security.WSTrustChannelFactory> Ve <xref:System.ServiceModel.Security.WSTrustChannel> sınıflarını aşağıdaki kod örneğinde gösterildiği gibi veren ve istemci akış için kesin türü belirtilmiş RST ve RSTR nesneleri etkinleştirin.  
  
```  
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory( stsBinding, stsAddress );  
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();  
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);  
rst.AppliesTo = new EndpointAddress(serviceAddress);  
RequestSecurityTokenResponse rstr = null;  
SecurityToken token = channel.Issue(rst, out rstr);  
```  
  
 Unutmayın `out` parametresini <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> yöntemi istemci-tarafı denetleme RSTR için erişim sağlar.  
  
 Şu ana kadar yalnızca bir belirteç elde etme gördük. Sunucudan döndürülen belirteç <xref:System.ServiceModel.Security.WSTrustChannel> nesne bir `GenericXmlSecurityToken` tüm bağlı olan taraf için kimlik doğrulaması için gerekli bilgileri içeren. Aşağıdaki kod örneği, bu belirteç kullanmayı gösterir.  
  
```  
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token ); serviceChannel.Hello("Hi!");  
```  
  
 <xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> Genişletme yöntemi `ChannelFactory` nesnesini WIF bant dışı bir belirteç elde ve veren normal WCF çağrısı durdurmak ve bunun yerine bağlı olan taraf için kimlik doğrulaması için elde edilen belirteci kullanın olduğunu gösterir. Bu, aşağıdaki faydaları vardır:  
  
-   Belirteç verme işlem üzerinde tam denetim verir.  
  
-   ActAs destekler / doğrudan üzerinde giden RST bu özellikleri ayarlayarak OnBehalfOf senaryoları.  
  
-   Yapılması gereken karar RSTR içeriğine göre dinamik istemci-tarafı güven sağlar.  
  
-   Önbellek ve sunucudan döndürülen belirteç yeniden sağlar <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> yöntemi.  
  
-   <xref:System.ServiceModel.Security.WSTrustChannelFactory>ve <xref:System.ServiceModel.Security.WSTrustChannel> kanal önbelleğe alma, hata ve kurtarma semantiği WCF en iyi yöntemler göre denetimi için izin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WIF Özellikleri](../../../docs/framework/security/wif-features.md)
