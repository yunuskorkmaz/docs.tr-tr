---
title: WCF Keşif Nesnesi Modeli
ms.date: 03/30/2017
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
ms.openlocfilehash: debcb08802894a34e16d9aa65bbbb1b0282794f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184220"
---
# <a name="wcf-discovery-object-model"></a>WCF Keşif Nesnesi Modeli
WCF Discovery, çalışma zamanında bulunabilen hizmetleri ve bu hizmetleri bulup kullanan istemcileri yazmanıza olanak tanıyan birleştirilmiş programlama modeli sağlayan bir dizi türden oluşur.  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>Bir Hizmetin Keşfedilebilir Hale Getirilmesi ve Bulma Hizmetleri  
 Bir WCF hizmetini keşfedilebilir hale <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> getirmek <xref:System.ServiceModel.Description.ServiceDescription> için, hizmet ana bilgisayarının a'sını ekleyin ve bir keşif bitiş noktası ekleyin. Bir hizmet duyuru iletileri göndermek için yapılandırılırsa (bir <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>ekleyerek) duyuru, hizmet ana bilgisayarı açılıp kapandığında gönderilir.  
  
 Hizmet duyuru iletilerini dinlemek isteyen bir istemci bir duyuru hizmeti barındırıyor ve bir veya daha fazla duyuru bitiş noktası ekler. Duyuru hizmeti duyuru mesajları alır ve duyuru etkinlikleri yükseltir.  
  
 İstemci, <xref:System.ServiceModel.Discovery.DiscoveryClient> kullanılabilir hizmetleri aramak için sınıfı kullanır. İstemci uygulaması, keşif <xref:System.ServiceModel.Discovery.DiscoveryClient> iletilerinin nereye gönderilen yeri belirten bir keşif bitiş noktasından geçerek sınıfı anında alar. İstemci, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> istek `Probe` gönderen yöntemi çağırır. Keşif iletilerini dinleyen `Probe` hizmetler bu isteği alır. Hizmet, istemciye bir `Probe` `ProbeMatch` ileti gönderir, belirtilen ölçütleri eşleşirse.  
  
## <a name="object-model"></a>Nesne Modeli  
 WCF Discovery API aşağıdaki sınıfları tanımlar:  
  
- <xref:System.ServiceModel.Discovery.AnnouncementClient>  
  
- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
- <xref:System.ServiceModel.Discovery.AnnouncementService>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryClient>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>  
  
- <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryProxy>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryService>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryVersion>  
  
- <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
  
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>  
  
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>  
  
- <xref:System.ServiceModel.Discovery.FindCriteria>  
  
- <xref:System.ServiceModel.Discovery.FindRequestContext>  
  
- <xref:System.ServiceModel.Discovery.FindResponse>  
  
- <xref:System.ServiceModel.Discovery.ResolveCriteria>  
  
- <xref:System.ServiceModel.Discovery.ResolveResponse>  
  
- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>  

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
- <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="announcementclient"></a>DuyuruMüşteri  
 Sınıf, <xref:System.ServiceModel.Discovery.AnnouncementClient> duyuru iletileri göndermek için senkron ve eşzamanlı yöntemler sağlar. Merhaba ve Bye olmak üzere iki tür duyuru iletisi vardır. Bir hizmetin kullanılabilir hale geldiğini belirtmek için bir Merhaba iletisi gönderilir ve varolan bir hizmetin kullanılamadığını belirtmek için Bye iletisi gönderilir. Geliştirici, bir <xref:System.ServiceModel.Discovery.AnnouncementClient> oluşturucu parametre <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> olarak bir örnek geçirerek bir örnek oluşturur.  
  
## <a name="announcementendpoint"></a>Announcementendpoint  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>sabit bir duyuru sözleşmesi ile standart bir bitiş noktasını temsil eder. Duyuru iletileri göndermek ve almak için bir hizmet veya istemci tarafından kullanılır. Varsayılan olarak, <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> sınıf WS_Discovery 11 iletişim kuralı sürümünü kullanmak üzere ayarlanır.  
  
## <a name="announcementservice"></a>Announcementservice  
 <xref:System.ServiceModel.Discovery.AnnouncementService>duyuru iletilerini alan ve işleyen bir duyuru hizmetinin sistem tarafından sağlanan bir uygulamasıdır. Bir Merhaba veya Bye iletisi alındığı zaman, <xref:System.ServiceModel.Discovery.AnnouncementService> örnek uygun sanal yöntemi <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> çağırır veya <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A>duyuru olaylarını yükseltir.  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 Sınıf, <xref:System.ServiceModel.Discovery.DiscoveryClient> kullanılabilir hizmetleri bulmak ve çözmek için bir istemci uygulaması tarafından kullanılır. Belirtilen <xref:System.ServiceModel.Discovery.FindCriteria> ve sırasıyla hizmet bulma ve çözme için senkron ve <xref:System.ServiceModel.Discovery.ResolveCriteria> eşzamanlı yöntemler sağlar. Geliştirici bir <xref:System.ServiceModel.Discovery.DiscoveryClient> örnek oluşturur ve bir <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> oluşturucu parametre olarak bir örnek sağlar.  
  
 Bir hizmeti bulmak için geliştirici, kullanılacak arama ölçütlerini `Find` içeren bir <xref:System.ServiceModel.Discovery.FindCriteria> örnek sağlayan senkron veya eşzamanlı yöntemi çağırır. Uygun <xref:System.ServiceModel.Discovery.DiscoveryClient> üstbilgi `Probe` içeren bir ileti oluşturur ve bulma isteğini gönderir. İstemci, herhangi bir `Find` zamanda birden fazla bekleyen istek olabileceğinden, istemci alınan yanıtları ilişkilendirer ve yanıtı doğrular. Daha sonra kullanarak `Find` işlemin arayan sonuçları <xref:System.ServiceModel.Discovery.FindResponse>sunar.  
  
 Bilinen bir hizmeti çözümlemek için geliştirici, bilinen hizmetin `Resolve` bir örneğini <xref:System.ServiceModel.Discovery.ResolveCriteria> sağlayan <xref:System.ServiceModel.EndpointAddress> senkron veya eşzamanlı yöntemi çağırır. İletiyi <xref:System.ServiceModel.Discovery.DiscoveryClient> `Resolve` uygun üstbilgiyle oluşturur ve çözüm isteğini gönderir. Alınan yanıt, bekleyen çözüm isteklerine karşı ilişkilendirilir ve sonuç `Resolve` işlemi <xref:System.ServiceModel.Discovery.ResolveResponse>çağırana 'yı kullanarak teslim edilir.  
  
 Ağda bir bulma proxy'si <xref:System.ServiceModel.Discovery.DiscoveryClient> varsa ve keşif isteğini çok noktaya yayın bir şekilde gönderirse, keşif proxy'si çok noktaya yayın bastırma Merhaba iletisiyle yanıt verebilir. Bekleyen <xref:System.ServiceModel.Discovery.DiscoveryClient> `ProxyAvailable` `Find` veya `Resolve` isteklere yanıt olarak Merhaba iletileri aldığında olayı yükseltir. Olay, `ProxyAvailable` keşif <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> proxy'si hakkında bir şey içerir. Bu bilgileri Ad hoc'tan Yönetilen moduna geçmek için kullanmak geliştiriciye bağlıdır.  
  
## <a name="discoveryendpoint"></a>Discoveryendpoint  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>sabit bir bulma sözleşmesi ile standart bir bitiş noktasını temsil eder. Bir hizmet veya istemci tarafından keşif iletileri göndermek veya almak için kullanılır. Varsayılan olarak, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> mod <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Managed?displayProperty=nameWithType> ve WSDiscovery11 WS-Discovery sürümü kullanmak için ayarlanır.  
  
## <a name="discoverymessagesequencegenerator"></a>Discoverymessagesequencegenerator  
 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>hizmet Keşif veya <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> Duyuru iletileri gönderirken bir oluşturmak için kullanılır.  
  
## <a name="discoveryservice"></a>Discoveryservice  
 Soyut <xref:System.ServiceModel.Discovery.DiscoveryService> sınıf alma ve işleme `Probe` ve `Resolve` iletiler için bir çerçeve sağlar. İleti `Probe` alındığı zaman, <xref:System.ServiceModel.Discovery.DiscoveryService> gelen iletiye <xref:System.ServiceModel.Discovery.FindRequestContext> dayalı bir örnek oluşturur ve <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> sanal yöntemi çağırır. Bir `Resolve` ileti alındığı <xref:System.ServiceModel.Discovery.DiscoveryService> zaman, <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A> sanal yöntemi çağırır. Özel bir Bulma Hizmeti uygulaması sağlamak için bu sınıftan devralabilirsiniz.  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 Soyut <xref:System.ServiceModel.Discovery.DiscoveryProxy> sınıf, keşif ve duyuru iletilerini almak ve işlemek için bir çerçeve sağlar. Özel bir bulma proxy'si uygularken bu sınıftan miras kalırsınız. Çok `Probe` noktaya yayın üzerinden bir <xref:System.ServiceModel.Discovery.DiscoveryProxy> ileti alındığı `BeginShouldRedirectFind` zaman, sınıf çok noktaya yayın bastırma iletisinin gönderilmesi gerekip gerekmediğini belirlemek için sanal yöntemi çağırır. Geliştirici çok noktaya yayın alameti göndermemeye karar `Probe` verirse veya ileti tek noktaya yayın üzerinden <xref:System.ServiceModel.Discovery.FindRequestContext> alınmışsa, gelen iletiyi `OnBeginFind` temel alan sınıfın bir örneğini oluşturur ve sanal yöntemi çağırır. Çok `Resolve` noktaya yayın üzerinden bir <xref:System.ServiceModel.Discovery.DiscoveryProxy> ileti alındığı `ShouldRedirectResolve` zaman, sınıf, çok noktaya yayın bastırma iletisinin gönderilmesi gerekip gerekmediğini belirlemek için sanal yöntemi çağırır. Geliştirici çok noktaya yayın alameti göndermemeye karar `Resolve` verirse veya ileti tek noktaya yayın üzerinden <xref:System.ServiceModel.Discovery.ResolveCriteria> alınmışsa, gelen iletiyi `OnBeginResolve` temel alan sınıfın bir örneğini oluşturur ve sanal yöntemi çağırır. Bir Merhaba veya Bye iletisi alındığı <xref:System.ServiceModel.Discovery.DiscoveryProxy> zaman, `OnBeingOfflineAnnouncement`duyuru olaylarını gündeme getiren uygun sanal yöntemi (veya)`OnBeginOnlineAnnouncement` çağırır.  
  
## <a name="discoveryversion"></a>Discoveryversion  
 Sınıf, <xref:System.ServiceModel.Discovery.DiscoveryVersion> kullanılacak bulma protokolü sürümünü temsil eder.  
  
## <a name="endpointdiscoverybehavior"></a>Endpointdiscoverybehavior  
 Sınıf, <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> bir bitiş noktasının kullanılabilirliğini denetlemek, uzantıları, ek sözleşme türü adlarını belirtmek için kullanılır. ve bu bitiş noktası ile ilişkili kapsamları. Bu davranış, onun <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Hizmet <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ana bilgisayara eklendiğinde, varsayılan olarak hizmet ana bilgisayarı tarafından barındırılan tüm uygulama uç noktaları keşfedilebilir hale gelir. Geliştirici özelliği ' ye ayarlayarak <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> belirli bir bitiş `false`noktası için keşfi kapatabilir.  
  
## <a name="endpointdiscoverymetadata"></a>Endpointdiscoverymetadata  
 Sınıf, <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> hizmet tarafından yayımlanan bir bitiş noktasının sürümden bağımsız bir temsilini sağlar. Uç nokta adresleri, dinleme URL'leri, sözleşme türü adları, kapsamlar, meta veri sürümü ve hizmet geliştiricisi tarafından belirtilen uzantıları içerir. Bir <xref:System.ServiceModel.Discovery.FindCriteria> `Probe` işlem sırasında istemci tarafından <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>gönderilen. Ölçütler eşleşirse, istemciye <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> döndürülür. Son nokta adresi, <xref:System.ServiceModel.Discovery.ResolveCriteria> .'nin bitiş noktası <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>adresiyle eşleşir. Ölçütler eşleşirse, istemciye <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> döndürülür.  
  
## <a name="findcriteria"></a>Findcriteria  
 Sınıf, <xref:System.ServiceModel.Discovery.FindCriteria> bir hizmeti bulurken kullanılan ölçütleri belirtmek için kullanılan sürümden bağımsız bir sınıftır. Hizmetleri eşleştirmek için WS-Discovery tanımlı ölçütleri tam olarak destekler. Ayrıca, geliştiricilerin eşleştirme işlemi sırasında kullanılabilecek özel değerleri belirtmek için kullanabileceği uzantıları da vardır. Geliştirici, geliştiricinin aradığı toplam `Find` hizmet sayısını <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>belirten veya <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>istemcinin yanıtları ne kadar beklediğini belirten değeri belirten , işlemi sonlandırma ölçütlerini sağlayabilir.  
  
## <a name="findrequestcontext"></a>Findrequestcontext  
 Sınıf, <xref:System.ServiceModel.Discovery.FindRequestContext> istemci bir `Probe` `Find` işlem başlattığında aldığı iletiye göre bulma hizmeti tarafından anında doldurulır. İstemci <xref:System.ServiceModel.Discovery.FindCriteria> tarafından belirtilen bir örneğini içerir.  
  
## <a name="findresponse"></a>FindResponse  
 Sınıf, <xref:System.ServiceModel.Discovery.FindResponse> işlemin yanıtlarıyla <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> arayana döndürülür. `Find` Ayrıca . <xref:System.ServiceModel.Discovery.FindCompletedEventArgs> Bu keşfedilen uç <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>noktaları ve bir sözlük <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> ve bir koleksiyon <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>, bir koleksiyon içerir .  
  
## <a name="resolvecriteria"></a>Resolvecriteria  
 Sınıf, <xref:System.ServiceModel.Discovery.ResolveCriteria> zaten bilinen bir hizmeti çözerken kullanılan ölçütleri belirtmek için kullanılan sürümden bağımsız bir sınıftır. Bilinen hizmetin bitiş noktası adresini içerir. <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A>Geliştirici, istemcinin yanıtları ne kadar beklediğini belirten sonlandırma ölçütlerini, çözüm işlemi için sağlayabilir.  
  
## <a name="resolveresponse"></a>Resolveresponse  
 İşlemin <xref:System.ServiceModel.Discovery.ResolveResponse> yanıtı <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> `Resolve` ile yöntemin arayana döndürülür. Ayrıca . <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs> Keşfedilen uç noktaları <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>ve bir örneği olan bir örneğini <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>içerir.  
  
## <a name="servicediscoverybehavior"></a>Servicediscoverybehavior  
 Sınıf, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> geliştiricinin bir hizmete bulma özelliğini eklemesine olanak tanır. Bu davranışı <xref:System.ServiceModel.ServiceHost>. Sınıf, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hizmet ana bilgisayara eklenen uygulama bitiş noktaları üzerinde yineler ve keşfedilebilir uç <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> noktalardan bir koleksiyon oluşturur. Tüm uç noktalar varsayılan olarak keşfedilebilir. Belirli bir bitiş noktasının bulunabilirliği, belirli <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> bir uç noktaya eklenerek denetlenebilir. Duyuru bitiş noktaları eklenirse, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> servis ana bilgisayarı açıldığında veya kapatıldığında, tüm keşfedilebilir uç noktaların duyurusu duyurunun duyurulması duyurunun her biri üzerinden gönderilir.  
  
## <a name="udpannouncementendpoint"></a>Udpannouncementendpoint  
 Sınıf, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> UDP çok noktaya yayın bağlama üzerinden duyuru için önceden yapılandırılan standart bir duyuru bitiş noktasıdır. Varsayılan olarak, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> WSApril2005 WS_Discovery sürümünü kullanmak üzere ayarlanır.  
  
## <a name="udpdiscoveryendpoint"></a>Udpdiscoveryendpoint  
 Sınıf, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> UDP çok noktaya yayın bağlama üzerinde keşif için önceden yapılandırılan standart bir bulma bitiş noktasıdır. Varsayılan olarak, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> WSDiscovery11 WS-Discovery sürümü ve <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Adhoc?displayProperty=nameWithType> modunu kullanmak üzere ayarlanır.
