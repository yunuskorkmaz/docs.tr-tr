---
title: "Uç Noktası Adresleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 52c5dfd84a55e727e465e2bd6214462fd57c334f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="endpoint-addresses"></a>Uç Noktası Adresleri
Tüm uç bulun ve uç noktayı tanımlamak için kullanılan ilişkili bir adresi vardır. Bu adres, öncelikle bir Tekdüzen Kaynak Tanımlayıcısı (uç nokta konumunu belirten URI), oluşur. Uç nokta adresi temsil edilen [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] programlama modeli tarafından <xref:System.ServiceModel.EndpointAddress> isteğe bağlı bir içeren sınıf <xref:System.ServiceModel.EndpointAddress.Identity%2A> bitiş noktası ile ileti değiş tokuşu diğer uç noktaları tarafından kimlik doğrulamasını etkinleştirir özelliği ve İsteğe bağlı kümesi <xref:System.ServiceModel.EndpointAddress.Headers%2A> hizmete erişmek için gerekli diğer SOAP üstbilgileri tanımlayan özellikleri. İsteğe bağlı üstbilgi ek sağlar ve daha ayrıntılı tanımlamak veya hizmet uç noktası ile etkileşim kurmak için adresleme bilgi. Bir uç nokta adresi kablo WS adresleme uç noktası başvuru olarak (EPR) gösterilir.  
  
## <a name="uri-structure-of-an-address"></a>Bir adresi URI yapısı  
 Çoğu taşıma için URI adresi dört bölümden oluşur. Örneğin, dört URI'SİNİN bölümlerini http://www.fabrikam.com:322/mathservice.svc/secureEndpoint gibi dökümü:  
  
-   Düzen: http:  
  
-   Makine: www.fabrikam.com  
  
-   (isteğe bağlı) Bağlantı noktası: 322  
  
-   Yol: /mathservice.svc/secureEndpoint  
  
## <a name="defining-an-address-for-a-service"></a>Bir hizmet için bir adres tanımlama  
 Bir hizmet uç noktası adresi ya da imperatively kodu veya bildirimli olarak ile yapılandırma kullanılarak belirtilebilir. Bağlamalar ve dağıtılmış bir hizmet için adresleri hizmet geliştirildiği sırada kullanılan olanlardan genellikle farklı olduğu için uç noktalar kodda tanımlama genellikle pratik değildir. Genellikle, kod yerine Yapılandırması kullanılarak hizmet uç noktaları tanımlamak daha pratik olur. Bağlama tutulması ve adresleme bilgilerini kodu dışında yeniden derleyin veya uygulamayı yeniden dağıtmak zorunda kalmadan değiştirmek için bunları sağlar.  
  
### <a name="defining-an-address-in-configuration"></a>Yapılandırmada bir adresi tanımlama  
 Bir yapılandırma dosyasında bir uç nokta tanımlamak için [ \<uç noktası >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesi. Ayrıntılar ve bir örnek için bkz: [bir uç noktası adresi belirtme](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="defining-an-address-in-code"></a>Bir adresi kodda tanımlama  
 Bir uç nokta adresi koduyla oluşturulabilir <xref:System.ServiceModel.EndpointAddress> sınıfı. Ayrıntılar ve bir örnek için bkz: [bir uç noktası adresi belirtme](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
### <a name="endpoints-in-wsdl"></a>WSDL içindeki uç noktaları  
 Bir uç nokta adresi de WSDL içinde karşılık gelen uç noktanın içinde WS adresleme EPR öğe olarak temsil edilebilir `wsdl:port` öğesi. EPR, uç noktanın adresi herhangi bir adres özelliği içerir. Ayrıntılar ve bir örnek için bkz: [bir uç noktası adresi belirtme](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a>Birden çok IIS .NET Framework 3.5 destek bağlama  
 Internet hizmet sağlayıcıları, genellikle site yoğunluğu ve düşük toplam sahip olma maliyetini artırmak için birçok uygulama aynı sunucu ve site üzerinde barındırır. Bu uygulamalar genellikle farklı temel adreslerine bağlıdır. Internet Information Services (IIS) Web sitesini birden çok uygulama içerebilir. Bir sitedeki uygulamaları bir veya daha fazla IIS bağlamaları erişilebilir.  
  
 IIS bağlamaları iki parça bilgi sağlar: bir bağlama protokolü ve bağlama bilgileri. Bağlama protokolü üzerinden iletişimin şeması tanımlar ve bağlama bilgileri siteye erişmek için kullanılan bilgilerdir.  
  
 Aşağıdaki örnek, bir IIS bağlaması mevcut olabilecek bileşenleri gösterir:  
  
-   Bağlama iletişim kuralı: HTTP  
  
-   Bağlama bilgileri: IP adresi, bağlantı noktası, ana bilgisayar üstbilgisi  
  
 IIS her şeması için birden çok taban adresi sonuçlanan her site için birden fazla bağlama belirtebilirsiniz. Öncesinde [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] birden çok adresi için bir şema desteklemiyor ve belirtilmiş olması durumunda belirtti bir <xref:System.ArgumentException> etkinleştirme sırasında.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] Birden çok uygulama aynı sitedeki aynı düzeni için farklı temel adresleriyle barındırmak Internet hizmet sağlayıcıları sağlar.  
  
 Örneğin, bir site aşağıdaki temel adresler içerebilir:  
  
-   http://Payroll.myOrg.com/Service.svc  
  
-   http://shipping.myOrg.com/Service.svc  
  
 İle [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], yapılandırma dosyasında bir önek filtre AppDomain düzeyinde belirtin. Bunu ile [ \<baseAddressPrefixFilters >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) öneklerinin bir listesini içeren öğe. IIS tarafından sağlanan gelen temel adresler, isteğe bağlı önek listesi göre filtrelenir. Bir önek belirtilmediğinde, varsayılan olarak, tüm adresleri üzerinden geçirilir. Önek sonuçları yalnızca eşleşen taban adresi üzerinden iletilecek bu düzeni için belirterek.  
  
 Önek filtreleri kullanan yapılandırma kodu örneği verilmiştir.  
  
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
  
 Önceki örnekte, net.tcp://payroll.myorg.com: 8000 ve http://shipping.myorg.com:8000 geçirilecek kendi ilgili şemaları için yalnızca temel adres.  
  
 `baseAddressPrefixFilter` Joker karakterleri desteklemez.  
  
 IIS tarafından sağlanan temel adresler adresleri değil diğer düzenleri bağlı olabilir `baseAddressPrefixFilters` listesi. Bu adresler filtrelendi değil.  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a>Birden çok IIS bağlama desteği .NET Framework 4 ve üzeri  
 .NET 4'ten başlayarak, birden fazla bağlama IIS'de desteği tek bir taban adresi ayarlayarak çekme gerek kalmadan etkinleştirebilirsiniz <xref:System.ServiceModel.ServiceHostingEnvironment>'s <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> ayarı TRUE. Bu destek, HTTP protokol düzenleri sınırlıdır.  
  
 Aşağıdaki multipleSiteBindingsEnabled kullanır yapılandırma kodu örneğidir [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md).  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 Bu ayarı kullanarak birden çok site bağlamaları etkin olduğunda baseAddressPrefixFilters ayarları, hem HTTP hem de HTTP olmayan protokolleri için göz ardı edilir.  
  
 Ayrıntılı bilgi ve örnekler için bkz: [birden fazla IIS Site bağlamasını destekleme](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md) ve <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>.  
  
## <a name="extending-addressing-in-wcf-services"></a>WCF hizmetlerinde adresleme genişletme  
 Varsayılan adresleme modelini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri uç noktası adresi URI aşağıdaki amaçlarla kullanır:  
  
-   Hizmet dinleme adresi, bitiş noktası için iletileri dinleyen konumu belirtmek için  
  
-   SOAP adresi filtresi belirtmek için adres SOAP üstbilgi olarak bir uç nokta bekler.  
  
 Değerlerin her biri bu amaçlar için ayrı olarak, bu yararlı senaryoları adresleme birkaç uzantılarına olanak veren belirtilebilir:  
  
-   SOAP aracılar: bir istemci tarafından gönderilen bir ileti son hedefine ulaşmadan önce iletiyi işleyen bir veya daha fazla ek hizmet erişir. SOAP aracılar önbelleğe alma, yönlendirme, Yük Dengeleme veya şema doğrulama iletileri gibi çeşitli görevleri gerçekleştirebilirsiniz. Bu senaryo için ayrı bir fiziksel adresi iletileri göndererek yapıldığını (`via`) aracı yerine yalnızca bir mantıksal adresine hedefleyen (`wsa:To`) ultimate hedef hedefleyen.  
  
-   Uç nokta dinleme adresini özel bir URI ve farklı bir değere ayarlamak, `listenURI` özelliği.  
  
 Taşıma adres `via` olduğu bir ileti başlangıçta gönderilmesi gerektiğini başka bir uzak adres yolu üzerindeki konumu tarafından belirtilir belirtir `to` hizmet bulunduğu parametresi. Çoğu Internet senaryoda `via` URI aynıdır <xref:System.ServiceModel.EndpointAddress.Uri%2A> son özelliğinin `to` hizmetinin adresi. Yalnızca el ile üretim yapmanız gerekir, bu iki adresler arasında ayrım yapmak.  
  
### <a name="addressing-headers"></a>Adres üstbilgileri  
 Bir uç nokta temel URI'sini yanı sıra bir veya daha fazla SOAP üstbilgileri çözülebilir. Bu faydalı olduğu senaryolar bir dizi, burada bir uç nokta aracılar hedeflenen SOAP üstbilgileri dahil etmek Bu uç noktanın gerektirir. istemciler SOAP Ara senaryoları kümesidir.  
  
 İki yolla özel adres üstbilgileri tanımlayabilirsiniz — kod veya yapılandırma kullanarak:  
  
-   Kullanarak kod içinde özel adres üstbilgileri oluşturma <xref:System.ServiceModel.Channels.AddressHeader> sınıfı ve yapımı içinde kullanılan bir <xref:System.ServiceModel.EndpointAddress>.  
  
-   Yapılandırmada, özel [ \<üstbilgiler >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) alt olarak belirtilen [ \<uç noktası >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) öğesi.  
  
 Dağıtımdan sonra üstbilgileri değiştirmenize izin verdiğinden yapılandırma kod, genellikle tercih edilir.  
  
### <a name="custom-listening-addresses"></a>Özel dinleme adresleri  
 Uç noktanın URI farklı bir değere dinleme adresini ayarlayabilirsiniz. Burada uç nokta gerçekte dinler adresi bir özel ağ adresi iken açığa çıkarılması SOAP adresi, aracı, bir ortak SOAP olduğu Ara senaryolarda kullanışlıdır.  
  
 Kod veya yapılandırma kullanarak özel bir dinleme adresi belirtebilirsiniz:  
  
-   Kodda ekleyerek özel dinleme adresi belirtin. bir <xref:System.ServiceModel.Description.ClientViaBehavior> uç noktanın davranış koleksiyonu sınıfı.  
  
-   Özel bir dinleme adresiyle Yapılandırması'nda belirtin `ListenUri` özniteliği hizmetinin [ \<uç noktası >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) öğesi.  
  
### <a name="custom-soap-address-filter"></a>Özel SOAP adresi filtresi  
 <xref:System.ServiceModel.EndpointAddress.Uri%2A> Herhangi ile birlikte kullanılan <xref:System.ServiceModel.EndpointAddress.Headers%2A> bir uç noktanın SOAP adresi filtresi tanımlamak için özelliği (<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>). Varsayılan olarak, bu filtre gelen iletiyi sahip olduğunu doğrular bir `To` uç noktayla eşleşen ileti üstbilgisi kullanıcının URI ve tüm gerekli uç nokta üstbilgilerinin iletide.  
  
 Bazı senaryolarda, bir uç nokta temel aktarımı ve uygun yalnızca olanlar gelen tüm iletileri alır `To` üstbilgi. Bunu etkinleştirmek için kullanıcı kullanabilir <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir uç noktası adresi belirtme](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 [Hizmet kimliği ve kimlik doğrulaması](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
