---
title: Uç Noktası Adresleri
ms.date: 03/30/2017
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
ms.openlocfilehash: 71358ed1c16c3c9b490a41f74dd6319af8eb2e7b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593535"
---
# <a name="endpoint-addresses"></a>Uç Noktası Adresleri
Her uç nokta kendisiyle ilişkili bir adrese sahiptir ve uç noktayı bulmak ve tanımlamak için kullanılır. Bu adres, birincil olarak bitiş noktasının konumunu belirten bir Tekdüzen Kaynak tanımlayıcısı 'nı (URI) içerir. Uç nokta adresi, Windows Communication Foundation (WCF) programlama modelinde temsil edilir. Bu, <xref:System.ServiceModel.EndpointAddress> <xref:System.ServiceModel.EndpointAddress.Identity%2A> ile ileti alışverişi yapan diğer uç noktalar tarafından bitiş noktasının kimlik doğrulamasını sağlayan isteğe bağlı bir özellik içerir ve <xref:System.ServiceModel.EndpointAddress.Headers%2A> hizmete erişmek IÇIN gereken diğer soap üstbilgilerini tanımlayan bir isteğe bağlı özellikler kümesidir. İsteğe bağlı üstbilgiler, hizmet uç noktasını tanımlamak veya bunlarla etkileşim kurmak için ek ve daha ayrıntılı adresleme bilgileri sağlar. Bir uç noktanın adresi, bir WS-Addressing uç nokta başvurusu (EPR) olarak Tel göre temsil edilir.  
  
## <a name="uri-structure-of-an-address"></a>Bir adresin URI yapısı  
 Çoğu taşımanın adres URI 'sinin dört bölümü vardır. Örneğin, URI 'nin dört bölümü `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` aşağıdaki gibi oluşturulabilir:  
  
- Şemadaki`http:`
  
- Makin`www.fabrikam.com`  
  
- seçim Bağlantı noktası: 322  
  
- Yol:/mathservice.svc/secureEndpoint  
  
## <a name="defining-an-address-for-a-service"></a>Bir hizmet için adres tanımlama  
 Bir hizmet için uç nokta adresi, kod kullanılarak veya bildirimli olarak yapılandırma yoluyla imperatively belirtilebilir. Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirildiğinde kullanılanlardan farklı olduğundan, koddaki uç noktaların tanımlanması genellikle pratik değildir. Genellikle, kod yerine yapılandırma kullanarak hizmet uç noktaları tanımlamak daha pratik bir yapılandırmadır. Bağlama ve adresleme bilgilerini koddan tutmanın, uygulamayı yeniden derlemek veya yeniden dağıtmak zorunda kalmadan değiştirilmesine izin verir.  
  
### <a name="defining-an-address-in-configuration"></a>Yapılandırmada bir adres tanımlama  
 Bir yapılandırma dosyasında bir uç nokta tanımlamak için [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) öğesini kullanın. Ayrıntılar ve bir örnek için bkz. [bir uç nokta adresi belirtme](../specifying-an-endpoint-address.md).  
  
### <a name="defining-an-address-in-code"></a>Kodda bir adres tanımlama  
 Sınıf ile kodda bir uç nokta adresi oluşturulabilir <xref:System.ServiceModel.EndpointAddress> . Ayrıntılar ve bir örnek için bkz. [bir uç nokta adresi belirtme](../specifying-an-endpoint-address.md).  
  
### <a name="endpoints-in-wsdl"></a>WSDL 'deki uç noktalar  
 Bir uç nokta adresi, WSDL 'de karşılık gelen uç noktanın öğesi içinde bir WS-Addressing EPR öğesi olarak da gösterilebilir `wsdl:port` . EPR, uç noktanın adresini ve tüm adres özelliklerini içerir. Ayrıntılar ve bir örnek için bkz. [bir uç nokta adresi belirtme](../specifying-an-endpoint-address.md).  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a>.NET Framework 3,5 ' de birden çok IIS bağlama desteği  
 Internet hizmet sağlayıcıları genellikle, site yoğunluğunu artırmak ve toplam sahiplik maliyetini azaltmak için aynı sunucu ve sitede birçok uygulamayı barındırır. Bu uygulamalar genellikle farklı temel adreslere bağlanır. Internet Information Services (IIS) Web sitesi, birden çok uygulama içerebilir. Bir sitedeki uygulamalara bir veya daha fazla IIS bağlaması aracılığıyla erişilebilir.  
  
 IIS bağlamaları iki bilgi parçasını sağlar: bağlama protokolü ve bağlama bilgileri. Bağlama protokolü, iletişimin gerçekleştiği düzeni tanımlar ve bağlama bilgileri siteye erişmek için kullanılan bilgiler.  
  
 Aşağıdaki örnek, bir IIS bağlamasında bulunabilecek bileşenleri göstermektedir:  
  
- Bağlama protokolü: HTTP  
  
- Bağlama bilgileri: IP adresi, bağlantı noktası, ana bilgisayar üstbilgisi  
  
 IIS her bir site için birden çok bağlama belirtebilir ve bu, her bir şema için birden çok temel adrese neden olur. .NET Framework 3,5 ' den önce, WCF bir şema için birden çok adresi desteklememiş ve belirtilmişse, <xref:System.ArgumentException> etkinleştirme sırasında bir oluşturdu.  
  
 .NET Framework 3,5, Internet servis sağlayıcılarının aynı sitede aynı düzen için farklı temel adreslere sahip birden çok uygulamayı barındırmalarını sağlar.  
  
 Örneğin, bir site aşağıdaki temel adresleri içerebilir:  
  
- `http://payroll.myorg.com/Service.svc`
  
- `http://shipping.myorg.com/Service.svc`
  
 .NET Framework 3,5 ile yapılandırma dosyasında AppDomain düzeyinde bir önek filtresi belirtirsiniz. Bunu [\<baseAddressPrefixFilters>](../../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) , ön eklerin bir listesini içeren öğesiyle yapabilirsiniz. IIS tarafından sağlanan gelen temel adresler, isteğe bağlı önek listesine göre filtrelenir. Varsayılan olarak, bir ön ek belirtilmediğinde tüm adresler geçirilir. Ön ek belirtildiğinde, bu düzenin geçirilmesi için yalnızca eşleşen temel adreste sonuç elde olur.  
  
 Aşağıda, ön ek filtrelerini kullanan yapılandırma kodu örneği verilmiştir.  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://payroll.myorg.com:8000"/>  
        <add prefix="http://shipping.myorg.com:8000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 Önceki örnekte, `net.tcp://payroll.myorg.com:8000` ve `http://shipping.myorg.com:8000` kendisine geçirilen kendi şemaları için tek temel adreslerdir.  
  
 `baseAddressPrefixFilter`Joker karakterleri desteklemez.  
  
 IIS tarafından sağlanan temel adresler, listede bulunmayan diğer şemalara göre adreslere sahip olabilir `baseAddressPrefixFilters` . Bu adresler filtrelenmez.  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a>.NET Framework 4 ve üzeri sürümlerde birden çok IIS bağlama desteği  
 .NET 4 ' te başlayarak, tek bir temel adres seçmek zorunda kalmadan IIS 'de birden çok bağlama desteğini etkinleştirerek ayarı <xref:System.ServiceModel.ServiceHostingEnvironment> <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> true olarak ayarlayabilirsiniz. Bu destek HTTP protokol şemaları ile sınırlıdır.  
  
 Aşağıda, Çoğulsitebindingsenabled on kullanan bir yapılandırma kodu örneği verilmiştir [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) .  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 Bu ayar kullanılarak birden çok site bağlaması etkinleştirildiğinde, hem HTTP hem de HTTP olmayan protokoller için herhangi bir baseAddressPrefixFilters ayarı yok sayılır.  
  
 Ayrıntılar ve örnekler için bkz. [birden fazla IIS site bağlamasını destekleme](supporting-multiple-iis-site-bindings.md) ve <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> .  
  
## <a name="extending-addressing-in-wcf-services"></a>WCF Hizmetlerinde adresleme 'yi genişletme  
 WCF hizmetlerinin varsayılan adresleme modeli, aşağıdaki amaçlar için uç nokta adresi URI 'sini kullanır:  
  
- Hizmet dinleme adresini belirtmek için uç noktanın iletileri dinlediği konum,  
  
- SOAP adres filtresini belirtmek için, bir uç noktanın bir SOAP üst bilgisi beklediği adres.  
  
 Bu amaçların her biri için değerler ayrı olarak belirlenebilir ve yararlı senaryolar kapsayan çeşitli adresleme uzantılarına izin verir:  
  
- SOAP aracıları: istemci tarafından gönderilen bir ileti, son hedefine ulaşmadan önce iletiyi işleyen bir veya daha fazla ek hizmetten geçer. SOAP aracıları, iletilerde önbelleğe alma, yönlendirme, Yük Dengeleme veya şema doğrulama gibi çeşitli görevleri gerçekleştirebilir. Bu senaryo, `via` yalnızca üst hedefi hedefleyen bir mantıksal adres () yerine aracıyı hedefleyen ayrı bir fiziksel adrese () ileti gönderilerek gerçekleştirilir `wsa:To` .  
  
- Uç noktanın dinleme adresi özel bir URI 'dir ve özelliğinden farklı bir değere ayarlanır `listenURI` .  
  
 ' In belirttiği Aktarım adresi, `via` bir iletinin başlangıçta `to` hizmetin bulunduğu parametre tarafından belirtilen başka bir uzak adresle birlikte gönderilmesi gerektiği konumdur. Çoğu Internet senaryosunda `via` URI, <xref:System.ServiceModel.EndpointAddress.Uri%2A> hizmetin son adresinin özelliğiyle aynıdır `to` . El ile yönlendirme yapmanız gerektiğinde, bu iki adres arasında ayrım yapmanız gerekir.  
  
### <a name="addressing-headers"></a>Adresleme üstbilgileri  
 Bir uç nokta, temel URI 'sine ek olarak bir veya daha fazla SOAP üst bilgisi tarafından çözülebilir. Bu çok sayıda senaryo kümesi, bir uç noktanın, bu uç noktanın istemcilerine, aracıların hedeflediği SOAP üstbilgilerini içermesini gerektiren bir dizi SOAP aracı senaryolarından biridir.  
  
 Özel adres üstbilgilerini, kod ya da yapılandırma kullanarak iki şekilde tanımlayabilirsiniz:  
  
- Kod içinde, sınıfını kullanarak özel adres üstbilgileri oluşturun <xref:System.ServiceModel.Channels.AddressHeader> ve ardından bir ' ın yapımını kullanın <xref:System.ServiceModel.EndpointAddress> .  
  
- Yapılandırmada özel, [\<headers>](../../configure-apps/file-schema/wcf/headers.md) öğesinin alt öğesi olarak belirtilir [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) .  
  
 Yapılandırma genellikle kod için tercih edilir, çünkü dağıtımdan sonra üst bilgileri değiştirmenizi sağlar.  
  
### <a name="custom-listening-addresses"></a>Özel dinleme adresleri  
 Dinleme adresini bitiş noktasının URI 'sinden farklı bir değere ayarlayabilirsiniz. Bu, genel bir SOAP aracısıyla gösterilen ve uç noktanın gerçekten dinlediği adresin özel bir ağ adresi olduğu bir genel SOAP aracı olan ara senaryolarda yararlıdır.  
  
 Kod ya da yapılandırma kullanarak özel bir dinleme adresi belirtebilirsiniz:  
  
- Kod içinde, <xref:System.ServiceModel.Description.ClientViaBehavior> uç noktanın davranış koleksiyonuna bir sınıf ekleyerek özel bir dinleme adresi belirtin.  
  
- Yapılandırma bölümünde, hizmet öğesinin özniteliğiyle birlikte özel bir dinleme adresi belirtin `ListenUri` [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) .  
  
### <a name="custom-soap-address-filter"></a>Özel SOAP adresi filtresi  
 , <xref:System.ServiceModel.EndpointAddress.Uri%2A> <xref:System.ServiceModel.EndpointAddress.Headers%2A> Bir uç noktanın SOAP adres filtresi () tanımlamak için herhangi bir özellikle birlikte kullanılır <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> . Bu filtre, varsayılan olarak, gelen bir iletinin `To` bitiş noktasının URI 'siyle eşleşen bir ileti üst bilgisi olduğunu ve tüm gerekli uç nokta üstbilgilerinin iletide bulunduğunu doğrular.  
  
 Bazı senaryolarda, bir uç nokta, yalnızca uygun üst bilgiyle değil, temel alınan aktarıma gelen tüm iletileri alır `To` . Bunu etkinleştirmek için Kullanıcı <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> sınıfını kullanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir Uç Noktası Adresi Belirtme](../specifying-an-endpoint-address.md)
- [Kimlik Doğrulama ile Hizmet Kimliği](service-identity-and-authentication.md)
