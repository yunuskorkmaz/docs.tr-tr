---
title: "WCF Keşif Nesnesi Modeli"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6d9ee9c1331c5c8754b336024f4b11a040c8a201
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-discovery-object-model"></a>WCF Keşif Nesnesi Modeli
WCF keşif çalışma zamanı ve bulmak ve bu hizmetleri kullanan istemciler bulunabilirlik Hizmetleri yazmanızı sağlayan birleşik bir programlama modeli sağlayan türleri kümesi oluşur.  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>Bir hizmeti bulunabilir ve bulma hizmetleri yapma  
 Bir WCF hizmeti bulunabilir duruma getirmek için ekleme bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> için <xref:System.ServiceModel.Description.ServiceDescription> hizmetinin ana bilgisayar ve bir bulma uç noktası ekleyin. Bir hizmet duyuru iletileri göndermek için yapılandırıldıysa (ekleyerek bir <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>) hizmet konağı açık ve kapalı olduğunda duyuruyu gönderilir.  
  
 İçin hizmet duyuru iletileri dinlemek istediğini bir istemci bir duyuru hizmeti barındıran ve bir veya daha fazla duyuru uç noktaları ekler. Duyuru hizmeti duyuru iletileri alır ve duyuru olayları başlatır.  
  
 Bir istemcinin kullandığı <xref:System.ServiceModel.Discovery.DiscoveryClient> kullanılabilir Hizmetleri aramak için sınıf. İstemci uygulamasının örneğini oluşturan <xref:System.ServiceModel.Discovery.DiscoveryClient> sınıfı, bulma iletileri göndermek konumu belirtir bulma uç noktası geçirme. İstemci çağrılarını <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> gönderir yöntemi bir `Probe` isteği. Bu bulma iletileri almak için dinleme Hizmetleri `Probe` isteği. Hizmet belirtilen ölçütlere uyuyorsa `Probe`, gönderdiği bir `ProbeMatch` istemciye ileti.  
  
## <a name="object-model"></a>Nesne modeli  
 WCF keşif API aşağıdaki sınıflar tanımlar:  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementClient>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementService>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryClient>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>  
  
-   <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryProxy>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryService>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryVersion>  
  
-   <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>  
  
-   <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria>  
  
-   <xref:System.ServiceModel.Discovery.FindRequestContext>  
  
-   <xref:System.ServiceModel.Discovery.FindResponse>  
  
-   <xref:System.ServiceModel.Discovery.ResolveCriteria>  
  
-   <xref:System.ServiceModel.Discovery.ResolveResponse>  
  
-   <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>  
  
-   <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension`  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="announcementclient"></a>AnnouncementClient  
 <xref:System.ServiceModel.Discovery.AnnouncementClient> Sınıfı duyuru iletileri göndermek için zaman uyumlu ve zaman uyumsuz yöntemleri sağlar. Duyuru iletileri, Hello ve Bye iki tür vardır. Merhaba ileti, bir hizmet kullanılabilir hale gelmiştir ve var olan bir hizmeti kullanılamıyor belirtmek için Bye iletiye gönderilen göstermek için gönderilir. Geliştirici oluşturur bir <xref:System.ServiceModel.Discovery.AnnouncementClient> örneğini geçirerek örneği <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> Oluşturucusu parametre olarak.  
  
## <a name="announcementendpoint"></a>AnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>bir sabit duyuru sözleşme ile standart bir uç noktasını temsil eder. Duyurunun ileti gönderme ve alma için bunu bir hizmet veya istemci tarafından kullanılır. Varsayılan olarak, <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> sınıfı WS_Discovery 11 protokol sürümünü kullanacak şekilde ayarlanır.  
  
## <a name="announcementservice"></a>AnnouncementService  
 <xref:System.ServiceModel.Discovery.AnnouncementService>bir sistem tarafından sağlanan duyuru iletilerini alan ve işleyen bir duyuru hizmet uygulamasıdır. Merhaba veya Bye bir ileti alındığında <xref:System.ServiceModel.Discovery.AnnouncementService> örneği uygun sanal yöntemini çağırır <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> veya <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A>, duyuru olayları başlatır.  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Sınıfı bulun ve kullanılabilir hizmetler çözümlemek için bir istemci uygulaması tarafından kullanılır. Bulma ve belirtilen temel Hizmetleri çözme için zaman uyumlu ve zaman uyumsuz yöntemleri sağlar <xref:System.ServiceModel.Discovery.FindCriteria> ve <xref:System.ServiceModel.Discovery.ResolveCriteria> sırasıyla. Geliştirici oluşturur bir <xref:System.ServiceModel.Discovery.DiscoveryClient> örneği ve bir örneğini sağlar <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> Oluşturucusu parametre olarak.  
  
 Bir hizmet bulmak için geliştirici zaman uyumlu veya zaman uyumsuz çağırır `Find` sağlar yöntemi bir <!--zz <xref:System.ServiceModel.Discription.FindCriteria> --> `FindCriteria` kullanmak için arama ölçütlerini içeren örneği. <xref:System.ServiceModel.Discovery.DiscoveryClient> Oluşturur bir `Probe` uygun üstbilgileri iletisiyle ve bulma isteği gönderir. Olabileceğinden birden fazla bekleyen `Find` istek herhangi bir zamanda istemci alınan yanıtların karşılık gelen ve yanıt doğrular. Ardından çağırana sonuçları sunar `Find` işlemi kullanılarak <xref:System.ServiceModel.Discovery.FindResponse>.  
  
 Bilinen bir hizmet çözümlemek için geliştirici zaman uyumlu veya zaman uyumsuz çağırır `Resolve` örneği sağlayan yöntemi <!--zz <xref:System.ServiceModel.ResolveCriteria>--> `ResolveCriteria` içeren <xref:System.ServiceModel.EndpointAddress> bilinen hizmet. <xref:System.ServiceModel.Discovery.DiscoveryClient> Oluşturur `Resolve` uygun üstbilgileri iletisiyle ve çözümleme isteği gönderir. Alınan yanıt karşı bekleyen çözümleme isteği bağıntılı ve sonucu çağırana teslim `Resolve` işlemi kullanılarak <xref:System.ServiceModel.Discovery.ResolveResponse>.  
  
 Ağ üzerinde keşif proxy'si varsa ve <!--zz <xref:System.ServiceModel.Discover.DiscoveryClient> --> `DiscoveryClient` bulma isteği bir çok noktaya yayın biçimde keşif proxy'si ile çok noktaya yayın gizleme selamlama iletisine yanıt gönderir. <!--zz <xref:System.ServiceModel.Discover.DiscoveryClient> --> `DiscoveryClient` Başlatır `ProxyAvailable` yanıt olarak bekleyen Merhaba iletileri aldığında, olay `Find` veya `Resolve` istekleri. `ProxyAvailable` Olayı içeren <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> keşif proxy'si hakkında. Geçici yönetilen moduna geçmek için bu bilgileri kullanmak için geliştirici kadar olur.  
  
## <a name="discoveryendpoint"></a>DiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>bir sabit bulma sözleşme ile standart bir uç noktasını temsil eder. Bu bulma ileti göndermek veya almak için bir hizmet veya istemci tarafından kullanılır. Varsayılan olarak, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> kullanmak üzere ayarlanmış <!--zz <xref:System.ServiceModel.Discovery.DiscoveryMode.Managed>--> `Managed` modu ve WSDiscovery11 WS-bulma sürümü.  
  
## <a name="discoverymessagesequencegenerator"></a>DiscoveryMessageSequenceGenerator  
 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>oluşturmak için kullanılan bir <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> hizmet bulma veya duyuru iletilerini göndermeyi zaman.  
  
## <a name="discoveryservice"></a>DiscoveryService  
 <xref:System.ServiceModel.Discovery.DiscoveryService> Soyut sınıf alınması ve işlenmesi için bir çerçeve sağlar `Probe` ve `Resolve` iletileri. Zaman bir `Probe` iletisi alındığında, <xref:System.ServiceModel.Discovery.DiscoveryService> bir örneğini oluşturur <xref:System.ServiceModel.Discovery.FindRequestContext> gelen iletisini temel alarak ve çağırır <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> sanal yöntemi. Zaman bir `Resolve` iletisi alındığında, <xref:System.ServiceModel.Discovery.DiscoveryService> çağırır <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A> sanal yöntemi. Özel bir bulma hizmeti uygulama sağlamak için bu sınıfı devralabilirsiniz.  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 <xref:System.ServiceModel.Discovery.DiscoveryProxy> Soyut sınıf alırken ve bulma ve duyuru iletileri işleme için bir çerçeve sağlar. Özel keşif proxy'si uygularken bu sınıftan devralın. Zaman bir `Probe` ileti çok noktaya yayın alınan <xref:System.ServiceModel.Discovery.DiscoveryProxy> sınıfı çağrıları `BeginShouldRedirectFind` bir çok noktaya yayın gizleme ileti gönderilmesi gerekip gerekmediğini belirlemek için sanal bir yöntem. Çok noktaya yayın gizleme ileti göndermek geliştiricinin karar verirse veya `Probe` iletisi tek noktaya yayın alınan, bir örneğini oluşturur <xref:System.ServiceModel.Discovery.FindRequestContext> sınıf gelen iletisini temel alarak ve çağırır `OnBeginFind` sanal yöntemi. Zaman bir `Resolve` ileti çok noktaya yayın alınan <xref:System.ServiceModel.Discovery.DiscoveryProxy> sınıfı çağrıları `ShouldRedirectResolve` bir çok noktaya yayın gizleme ileti gönderilmesi gerekip gerekmediğini belirlemek için sanal bir yöntem. Çok noktaya yayın gizleme ileti göndermek geliştiricinin karar verirse veya `Resolve` iletisi tek noktaya yayın alınan, bir örneğini oluşturur <xref:System.ServiceModel.Discovery.ResolveCriteria> sınıf gelen iletisini temel alarak ve çağırır `OnBeginResolve` sanal yöntemi. Merhaba veya Bye bir ileti alındığında <xref:System.ServiceModel.Discovery.DiscoveryProxy> uygun sanal yöntemini çağıran (`OnBeginOnlineAnnouncement` veya `OnBeingOfflineAnnouncement`), duyuru olayları başlatır.  
  
## <a name="discoveryversion"></a>discoveryVersion  
 <xref:System.ServiceModel.Discovery.DiscoveryVersion> Sınıfı, kullanılacak Bulma Protokolü sürüm temsil eder.  
  
## <a name="endpointdiscoverybehavior"></a>EndpointDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Sınıfı bir uç nokta bulunabilirliğini denetlemek, uzantılar, ek sözleşme tür adları belirlemek için kullanılır. ve o uç noktası ile ilişkili kapsam. Bu davranışı yapılandırmak için bir uygulama uç noktasına eklenir, <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Zaman <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> eklenir hizmet ana bilgisayarı için varsayılan olarak hizmet ana bilgisayar tarafından barındırılan tüm uygulama uç noktaları hale bulunabilir. Geliştirici bulma belirli bir uç noktası için ayarlayarak devre dışı bırakabilirsiniz <!--zz <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enable%2A>--> `Enable` özelliğine `false`.  
  
## <a name="endpointdiscoverymetadata"></a>EndpointDiscoveryMetadata  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> Sınıfı, bir hizmet tarafından yayımlanan bir uç nokta sürüm bağımsız gösterimini sağlar. URI, sözleşme tür adları, kapsamları, meta veri sürümü ve hizmet geliştirici tarafından belirtilen uzantıları dinleme, uç nokta adresleri içerir. <xref:System.ServiceModel.Discovery.FindCriteria> Sırasında istemci tarafından gönderilen bir `Probe` işlemi eşleşen karşı <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Ölçütler ile eşleşiyorsa, sonra <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> istemciye döndürülür. Uç nokta adresi <xref:System.ServiceModel.Discovery.ResolveCriteria> karşı uç noktası adresi eşleşen <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Ölçütler ile eşleşiyorsa, sonra <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> istemciye döndürülür.  
  
## <a name="findcriteria"></a>FindCriteria  
 <xref:System.ServiceModel.Discovery.FindCriteria> Hizmet bulma işleminde kullanılan ölçütlerini belirtmek için kullanılan bir sürüm bağımsız sınıf bir sınıftır. Hizmetleri eşleştirmek için WS bulma tanımlanan ölçütleri tam olarak destekler. Ayrıca, geliştiricilerin eşleştirme işlemi sırasında kullanılan özel değerler belirtmek için kullanabileceği uzantıları sahiptir. Geliştirici sonlandırma ölçütlerini sağlayabilir `Find` belirterek işlemi <!--zz <xref:System.ServiceModel.Discovery.FindCriteria.MaxResult%2A>--> `MaxResult`, geliştirici aramakta ya da belirten hizmetlerin toplam sayısını belirten <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>, olduğu İstemci yanıtlar için bekleyeceği süreyi belirten değer.  
  
## <a name="findrequestcontext"></a>FindRequestContext  
 <xref:System.ServiceModel.Discovery.FindRequestContext> Sınıfının örneği göre bulma hizmeti tarafından `Probe` istemci başlattığında aldığı ileti bir `Find` işlemi. Örneğini içeren <xref:System.ServiceModel.Discovery.FindCriteria> istemci tarafından belirtildi.  
  
## <a name="findresponse"></a>FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse> Sınıfı çağırana döndürülen <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yanıtların ile `Find` işlemi. Ayrıca, mevcut <xref:System.ServiceModel.Discovery.FindCompletedEventArgs>. Bir koleksiyonu içerir <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, keşfedilen uç noktaları koleksiyonu ve bir sözlükten olduğu <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> ve <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="resolvecriteria"></a>ResolveCriteria  
 <xref:System.ServiceModel.Discovery.ResolveCriteria> Bir sürüm bağımsız sınıf zaten bilinen bir hizmet çözülürken kullanılan ölçütlerini belirtmek için kullanılan bir sınıftır. Bilinen bir hizmet uç noktası adresini içerir. Geliştirici sonlandırma ölçütleri çözümleme işlemi için belirterek sağlayabilir <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A>, istemci yanıtlar için bekleyeceği süreyi belirtir.  
  
## <a name="resolveresponse"></a>ResolveResponse  
 <xref:System.ServiceModel.Discovery.ResolveResponse> Çağırana döndürülen <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> yanıtını yöntemiyle `Resolve` işlemi. Ayrıca, mevcut <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs>. Örneğini içeren <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, keşfedilen uç noktaları ve örneği olduğu <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="servicediscoverybehavior"></a>ServiceDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Sınıfı, bir hizmete bulma özelliği eklemek Geliştirici olanak tanır. Bu davranış eklemek <xref:System.ServiceModel.ServiceHost>. <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Sınıfı hizmet ana bilgisayara eklenen uygulama uç noktaları üzerinden ilerler ve bir koleksiyonunu oluşturur <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> bulunabilirlik uç noktaları gelen. Tüm uç noktaları varsayılan olarak bulunabilir. Belirli bir uç nokta bulunabilirliğini ekleyerek denetlenebilir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> bu belirli uç noktası. Duyuru uç noktaları için eklenirse <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> sonra da hizmet konağı açılır ya da kapalı olduğunda tüm bulunabilirlik uç noktaları duyuru her duyuru uç noktaları gönderilir.  
  
## <a name="servicediscoveryextension"></a>ServiceDiscoveryExtension  
 <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension` Sınıfı tarafından oluşturulan <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> sınıfı. Bulunabilirlik yapılan uç noktaları elde edilebilir <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension`. Bu sınıf ayrıca özel bulma hizmet uygulaması belirtmek için kullanılır.  
  
## <a name="udpannouncementendpoint"></a>Udptransportsettings  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Sınıfı bir UDP üzerinden duyuru için önceden yapılandırılmış bir standart duyuru uç noktası, çok noktaya yayın bağlama. Varsayılan olarak, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> WSApril2005 WS_Discovery sürümünü kullanacak şekilde ayarlayın.  
  
## <a name="udpdiscoveryendpoint"></a>UdpDiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Sınıfı bir UDP üzerinden bulma için önceden yapılandırılmış bir standart bulma uç noktası, çok noktaya yayın bağlama. Varsayılan olarak, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> WSDiscovery11 WS-bulma sürümünü kullanacak şekilde ayarlanır ve <!--zz <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.Adhoc>--> `Adhoc` modu.
