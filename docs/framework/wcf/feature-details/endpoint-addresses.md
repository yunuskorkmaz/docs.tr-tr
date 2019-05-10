---
title: Uç Noktası Adresleri
ms.date: 03/30/2017
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
ms.openlocfilehash: a59e47e529a5002c806e37dba7267b2cf8318a35
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912707"
---
# <a name="endpoint-addresses"></a>Uç Noktası Adresleri
Her uç nokta bulun ve uç noktayı tanımlamak için kullanılır, ilişkili bir adresi vardır. Bu adres, öncelikle bir Tekdüzen Kaynak Tanımlayıcısı (uç nokta konumu belirten URI), oluşur. Uç nokta adresini Windows Communication Foundation (WCF) programlama modeli tarafından temsil edilir <xref:System.ServiceModel.EndpointAddress> isteğe bağlı içeren sınıf <xref:System.ServiceModel.EndpointAddress.Identity%2A> bitiş noktası diğer uç noktalar tarafından kimlik doğrulaması sağlayan özelliği, Exchange, iletileri ve isteğe bağlı bir dizi <xref:System.ServiceModel.EndpointAddress.Headers%2A> hizmete erişmek için gereken diğer bir SOAP üstbilgileri tanımlayan özellikleri. İsteğe bağlı üst bilgiler ek sağlayın ve daha ayrıntılı tanımlamak veya hizmet uç noktası ile etkileşime geçmek için adresleme bilgi. Bir uç nokta adresini kablo bir WS-Addressing uç nokta başvurusu (EPR) temsil edilir.  
  
## <a name="uri-structure-of-an-address"></a>URI bir adresinin yapısı  
 Çoğu taşımalar için URI adresi dört bölümden oluşur. Örneğin, dört bölümden URI'ın `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` aşağıda listelenen:  
  
- Düzeni: `http:`
  
- Makine: `www.fabrikam.com`  
  
- (isteğe bağlı) Bağlantı noktası: 322  
  
- Yol: /mathservice.svc/secureEndpoint  
  
## <a name="defining-an-address-for-a-service"></a>Bir hizmet için bir adres tanımlama  
 Bir hizmet için uç nokta adresi ya da kesin kod veya bildirimli olarak ile yapılandırma kullanılarak belirtilebilir. Bağlamalarında ve adreslerinde dağıtılan bir hizmette hizmet geliştirilen kullandığı olanlardan genellikle farklı olduğundan uç noktaları kodda tanımlama genellikle pratik değildir. Genel olarak, kod yerine yapılandırma kullanarak hizmet uç noktaları tanımlamak daha yararlı olur. Bağlama tutulması ve adresleme bilgilerini kodunun dışında yeniden derleyin veya uygulama yeniden dağıtmaya gerek kalmadan değiştirmek sağlar.  
  
### <a name="defining-an-address-in-configuration"></a>Yapılandırmada bir adresi tanımlama  
 Bir uç nokta yapılandırma dosyasında tanımlamak için [ \<uç noktası >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesi. Ayrıntılar ve bir örnek için bkz. [bir uç nokta adresi belirtme](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="defining-an-address-in-code"></a>Kodda bir adresi tanımlama  
 Bir uç nokta adresi koduyla oluşturulabilir <xref:System.ServiceModel.EndpointAddress> sınıfı. Ayrıntılar ve bir örnek için bkz. [bir uç nokta adresi belirtme](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="endpoints-in-wsdl"></a>WSDL, uç noktaları  
 Bir uç nokta adresi de NWSDL içine bir WS-Addressing EPR öğesi içinde karşılık gelen uç noktanın temsil edilebilir `wsdl:port` öğesi. EPR uç noktanın adresini ve bunun yanı sıra herhangi bir adres özelliklerini içerir. Ayrıntılar ve bir örnek için bkz. [bir uç nokta adresi belirtme](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a>Birden fazla IIS desteği, .NET Framework 3.5 bağlama  
 Internet hizmet sağlayıcıları, genellikle site yoğunluğu ve daha düşük toplam sahip olma maliyeti artırmak için birçok uygulama aynı sunucu ve site üzerinde barındırın. Bu uygulamalar genellikle farklı temel adreslerine bağlıdır. Bir Internet Information Services (IIS) Web sitesi, birden çok uygulama içerebilir. Bir sitedeki uygulamaları bir veya daha fazla IIS bağlamaları erişilebilir.  
  
 IIS bağlamaları, iki bilgi parçasını sağlar: bir bağlama protokolü ve bağlama bilgileri. Bağlama Protokolü iletişim oluştuğu düzenini tanımlar ve bağlama bilgileri siteye erişmek için kullanılan bilgiler bunlardır.  
  
 Aşağıdaki örnek, bir IIS bağlaması içinde mevcut olabilecek bileşenleri gösterilmektedir:  
  
- Bağlama protokolü: HTTP  
  
- Bağlama bilgileri: IP adresi, bağlantı noktası, ana bilgisayar üstbilgisi  
  
 IIS her şeması için birden çok taban adresi sonuçlanır her site için birden çok bağlamaları belirtebilirsiniz. Öncesinde [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], WCF birden çok adresi için bir şema desteklemiyor ve belirtilmiş olması durumunda, oluşturdu bir <xref:System.ArgumentException> etkinleştirme sırasında.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] Birden çok uygulama ile aynı sitede aynı düzeni için farklı temel adresler barındırmak Internet hizmet sağlayıcıları sağlar.  
  
 Örneğin, bir site aşağıdaki temel adresler içerebilir:  
  
- `http://payroll.myorg.com/Service.svc`
  
- `http://shipping.myorg.com/Service.svc`
  
 İle [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], AppDomain düzeyinde bir önek filtresi yapılandırma dosyasında belirtirsiniz. Bunu [ \<baseAddressPrefixFilters >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) önekleri listesini içeren öğe. IIS tarafından sağlanan gelen temel adresler, isteğe bağlı bir ön ek listesini göre filtrelenir. Öneki belirtilmediğinde, varsayılan olarak, tüm adresleri üzerinden geçirilir. Doğrudan geçiş yapılacak bu şema için yalnızca eşleşen temel adres ön eki sonuçları belirterek.  
  
 Önek filtreleri kullanan yapılandırma koduna ilişkin bir örnek verilmiştir.  
  
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
  
 Önceki örnekte `net.tcp://payroll.myorg.com:8000` ve `http://shipping.myorg.com:8000` aracılığıyla geçirilir, kendi şemaları için yalnızca temel adresler.  
  
 `baseAddressPrefixFilter` Joker karakterleri desteklemiyor.  
  
 IIS tarafından sağlanan temel adresler adresleri yok diğer düzenleri bağlı olabilir `baseAddressPrefixFilters` listesi. Bu adresleri filtrelenir değil.  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a>Birden fazla IIS bağlama desteği .NET Framework 4 ve üzeri  
 .NET 4'te başlayarak, IIS'de birden çok bağlamaları desteğini ayarlayarak tek bir temel adresi seçmek zorunda kalmadan etkinleştirebilirsiniz <xref:System.ServiceModel.ServiceHostingEnvironment>'s <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> ayarı TRUE. Bu destek, HTTP protokol şemaları için sınırlıdır.  
  
 MultipleSiteBindingsEnabled kullanan yapılandırma koduna ilişkin bir örnek verilmiştir [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md).  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 Bu ayar kullanılarak birden çok site bağlamaları etkinleştirildiğinde baseAddressPrefixFilters ayarları, hem HTTP hem de HTTP olmayan protokolleri için göz ardı edilir.  
  
 Ayrıntılar ve örnekler için bkz. [birden fazla IIS Site bağlamasını destekleme](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md) ve <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>.  
  
## <a name="extending-addressing-in-wcf-services"></a>WCF hizmetlerinde adresleme genişletme  
 WCF hizmetleri modeli ele alan varsayılan uç nokta adresini URI aşağıdaki amaçlarla kullanır:  
  
- Uç nokta için iletileri dinleyen konum hizmeti dinleme adresini belirtmek için  
  
- SOAP adresi filtresi belirtmek için bir uç nokta adresi SOAP üst bilgi olarak bekler.  
  
 Değerlerin her biri bu amaçlar için ayrı ayrı yararlı senaryoları kapsıyor adresleme birkaç uzantılarına olanak veren belirtilebilir:  
  
- SOAP aracıları: bir istemci tarafından gönderilen bir iletinin son hedefine erişmeden önce iletiyi işleyen bir veya daha fazla ek hizmetler erişir. SOAP aracıları, önbelleğe alma, yönlendirme, Yük Dengeleme veya şema doğrulama iletilerinde gibi çeşitli görevler gerçekleştirebilirsiniz. Bu senaryo için ayrı bir fiziksel adresi iletiler göndererek gerçekleştirilir (`via`) aracı yerine yalnızca bir mantıksal adresine hedefleyen (`wsa:To`) ultimate hedef hedefleyen.  
  
- Dinleme bitiş noktasının adresini özel bir URI ve farklı bir değere ayarlamak, `listenURI` özelliği.  
  
 Taşıma adres `via` olduğu bir ileti başlangıçta göndermesi gereken diğer bir uzak adres çekmek konumu tarafından belirtilen belirtir `to` parametresi hizmet olduğu yer. Çoğu Internet senaryoda `via` URI aynıdır <xref:System.ServiceModel.EndpointAddress.Uri%2A> son özelliği `to` hizmetinin adresini. Yalnızca el ile yönlendirme yapmanız gerekir, bu iki adreslerini birbirinden ayırt edecek.  
  
### <a name="addressing-headers"></a>Adres üstbilgileri  
 Bir uç nokta temel URI'sini ek olarak bir veya daha fazla SOAP üstbilgileri çözülebilir. Bu faydalı olduğu senaryolar bir kümesi, burada aracıların hedeflenen SOAP başlıkları da eklediğinizden istemcilerin bu uç noktanın bir uç nokta gerektiriyor SOAP Ara senaryoları kümesidir.  
  
 Özel adres üstbilgileri iki yolla tanımlayabilirsiniz — kod veya yapılandırma kullanarak:  
  
- Kullanarak kod içinde özel adres üstbilgileri oluşturma <xref:System.ServiceModel.Channels.AddressHeader> sınıfı ve ardından oluşumunu kullanılan bir <xref:System.ServiceModel.EndpointAddress>.  
  
- Özel bir yapılandırmada [ \<üstbilgileri >](../../configure-apps/file-schema/wcf/headers.md) altı olarak belirtilen [ \<uç noktası >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) öğesi.  
  
 Dağıtımdan sonra üstbilgileri değiştirmenize izin verdiğinden, yapılandırma kod, genellikle tercih edilir.  
  
### <a name="custom-listening-addresses"></a>Özel dinleme adresleri  
 Dinleme adresi uç noktasının URI'sini farklı bir değere ayarlayabilirsiniz. Uç nokta aslında burada dinler adresi bir özel ağ adresi bilgileriyse sağlamak SOAP adresi, aracı, genel bir SOAP olduğu Ara senaryolarda kullanışlıdır.  
  
 Kod veya yapılandırma kullanarak özel bir dinleme adresi belirtebilirsiniz:  
  
- Kod içinde ekleyerek bir özel dinleme adresi belirtin. bir <xref:System.ServiceModel.Description.ClientViaBehavior> uç noktanın davranışı koleksiyon sınıfı.  
  
- Yapılandırması, bir özel dinleme adresiyle belirtin `ListenUri` hizmetinin özniteliği [ \<uç noktası >](../../configure-apps/file-schema/wcf/endpoint-element.md) öğesi.  
  
### <a name="custom-soap-address-filter"></a>Özel SOAP adresi filtresi  
 <xref:System.ServiceModel.EndpointAddress.Uri%2A> Birlikte kullanılan <xref:System.ServiceModel.EndpointAddress.Headers%2A> uç noktanın SOAP adresi filtresi tanımlamak için özellik (<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>). Varsayılan olarak, bu filtre gelen iletisine sahip olduğunu doğrular bir `To` uç noktayla eşleşen ileti üst bilgisi kullanıcının URI ve tüm gerekli uç nokta üstbilgileri iletide.  
  
 Bazı senaryolarda, bir uç nokta, temel alınan aktarımda ve yalnızca bunlar uygun gelen tüm iletileri alır. `To` başlığı. Kullanıcı bunu etkinleştirmek için kullanabilir <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uç Nokta Adresi Belirtme](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
