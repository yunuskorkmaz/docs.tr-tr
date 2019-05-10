---
title: WCF Keşif Nesnesi Modeli
ms.date: 03/30/2017
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
ms.openlocfilehash: d305528c379bd4ded339854ee1f9fa55c76b40c0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614790"
---
# <a name="wcf-discovery-object-model"></a>WCF Keşif Nesnesi Modeli
WCF bulma çalışma zamanı ve bulun ve bu hizmetleri kullanan istemciler bulunabilir hizmetlerinizi yazmanızı sağlayan birleşik bir programlama modeli sağlayan türler kümesi oluşur.  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>Bir keşfedilebilir hizmeti ve bulma hizmetleri yapma  
 Bir WCF hizmeti bulunabilir hale getirmek için ekleme bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> için <xref:System.ServiceModel.Description.ServiceDescription> hizmeti ana bilgisayar ve bir bulma uç noktası ekleyin. Duyurunun ileti göndermek için bir hizmet yapılandırılmışsa (ekleyerek bir <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>) hizmet konağı açılır ve duyuru gönderilir.  
  
 Hizmet duyuru iletileri dinlemek için isteyen bir istemci bir duyuru hizmetini barındıran ve bir veya daha fazla duyuru uç noktası ekler. Duyuru hizmet duyuru iletileri alır ve duyuru olayları oluşturur.  
  
 Bir istemcinin kullandığı <xref:System.ServiceModel.Discovery.DiscoveryClient> kullanılabilir Hizmetleri aramak için sınıf. İstemci uygulamasının örneğini oluşturan <xref:System.ServiceModel.Discovery.DiscoveryClient> bulma iletileri nereye göndereceğini belirten bir bulma uç noktası geçirerek sınıfı. İstemci çağrıları <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> gönderen yöntemi bir `Probe` istek. Bu bulma iletileri almak için dinleme Hizmetleri `Probe` isteği. Hizmet içinde belirtilen ölçütlerle eşleşmesi durumunda `Probe`, gönderdiği bir `ProbeMatch` istemcisine ileti.  
  
## <a name="object-model"></a>Nesne modeli  
 WCF bulma API aşağıdaki sınıfları tanımlar:  
  
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
  
## <a name="announcementclient"></a>AnnouncementClient  
 <xref:System.ServiceModel.Discovery.AnnouncementClient> Sınıfı Duyurunun ileti göndermek için zaman uyumlu ve zaman uyumsuz yöntemler sağlar. Merhaba ve Bye Duyurunun ileti iki türü vardır. Hizmet kullanılabilir olur ve var olan bir hizmet kullanılamaz hale geldiğini gösteren bir Bye mesajın gönderilip gönderilmediği belirtmek için bir Hello ileti gönderilir. Geliştirici oluşturur bir <xref:System.ServiceModel.Discovery.AnnouncementClient> örneğini geçirerek örneği <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> Oluşturucu parametresi olarak.  
  
## <a name="announcementendpoint"></a>AnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> bir sabit duyuru sözleşmesiyle standart uç nokta temsil eder. Bu Duyurunun ileti göndermek ve almak için bir hizmet veya istemci tarafından kullanılır. Varsayılan olarak, <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> sınıfı WS_Discovery 11 protokol sürümünü kullanacak şekilde ayarlanır.  
  
## <a name="announcementservice"></a>AnnouncementService  
 <xref:System.ServiceModel.Discovery.AnnouncementService> bir sistem tarafından sağlanan alan ve duyuru iletileri işleyen bir duyuru hizmet uygulamasıdır. Merhaba veya Bye bir ileti alındığında <xref:System.ServiceModel.Discovery.AnnouncementService> örneği uygun sanal yöntemini çağırır <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> veya <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A>, duyuru olayları başlatır.  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Sınıfı bulun ve kullanılabilir hizmetlerin çözümlenmesi için bir istemci uygulaması tarafından kullanılır. Bulma ve çözümleme belirtilen tabanlı hizmetler için zaman uyumlu ve zaman uyumsuz yöntemler sağlar <xref:System.ServiceModel.Discovery.FindCriteria> ve <xref:System.ServiceModel.Discovery.ResolveCriteria> sırasıyla. Geliştirici oluşturur bir <xref:System.ServiceModel.Discovery.DiscoveryClient> örneği ve bir örneğini sağlar <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> Oluşturucu parametresi olarak.  
  
 Bir hizmet bulmak için geliştirici zaman uyumlu veya zaman uyumsuz çağırır `Find` sağlayan yöntemi bir <xref:System.ServiceModel.Discovery.FindCriteria> kullanmak için arama ölçütlerini içeren örneği. <xref:System.ServiceModel.Discovery.DiscoveryClient> Oluşturur bir `Probe` uygun üst bilgileri ile ileti ve bulma isteği gönderir. Olabilir çünkü birden fazla bekleyen `Find` isteği herhangi bir zamanda istemci alınan yanıtları ilişkilendirir ve yanıt doğrular. Ardından çağırana sonuçları sunar `Find` işlemi kullanarak <xref:System.ServiceModel.Discovery.FindResponse>.  
  
 Bilinen bir hizmet gidermek için geliştirici zaman uyumlu veya zaman uyumsuz çağırır `Resolve` örneği sağlayan yöntemi <xref:System.ServiceModel.Discovery.ResolveCriteria> içeren <xref:System.ServiceModel.EndpointAddress> bilinen hizmet. <xref:System.ServiceModel.Discovery.DiscoveryClient> Oluşturur `Resolve` uygun üst bilgileri ile ileti ve çözümleme isteği gönderir. Alınan yanıt bekleyen bir Çözümle istekler ilişkilendirilir ve sonucu çağırana teslim `Resolve` işlemi kullanarak <xref:System.ServiceModel.Discovery.ResolveResponse>.  
  
 Keşif proxy'si ağdaki mevcutsa ve <xref:System.ServiceModel.Discovery.DiscoveryClient> bulgu keşif proxy'si ile çok noktaya yayın gizleme selamlama iletisine yanıt vermek çok noktaya yayın bir şekilde isteği gönderir. <xref:System.ServiceModel.Discovery.DiscoveryClient> Başlatır `ProxyAvailable` yanıt olarak bekleyen Karışılama iletileri aldığında olay `Find` veya `Resolve` istekleri. `ProxyAvailable` Olay içeren <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> keşif proxy'si hakkında. Bu geliştiricinin geçici yönetilen moduna geçmek için bu bilgileri kullanın. en fazla olur.  
  
## <a name="discoveryendpoint"></a>DiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> bir sabit keşif sözleşmesiyle standart uç nokta temsil eder. Bu bulma ileti göndermek veya almak için bir hizmet veya istemci tarafından kullanılır. Varsayılan olarak, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> kullanmak üzere ayarlanmış <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Managed?displayProperty=nameWithType> modu ve WSDiscovery11 WS-bulma sürümü.  
  
## <a name="discoverymessagesequencegenerator"></a>DiscoveryMessageSequenceGenerator  
 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator> oluşturmak için kullanılan bir <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> hizmet bulma veya duyuru iletileri gönderdiğini zaman.  
  
## <a name="discoveryservice"></a>DiscoveryService  
 <xref:System.ServiceModel.Discovery.DiscoveryService> Özet sınıf, alma ve işleme için bir çerçeve sağlar `Probe` ve `Resolve` iletileri. Olduğunda bir `Probe` ileti alındığında, <xref:System.ServiceModel.Discovery.DiscoveryService> örneği oluşturur <xref:System.ServiceModel.Discovery.FindRequestContext> çağırır ve gelen iletisini temel alarak <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> sanal yöntem. Olduğunda bir `Resolve` ileti alındığında, <xref:System.ServiceModel.Discovery.DiscoveryService> çağırır <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A> sanal yöntem. Özel bir bulma hizmeti uygulama sağlamak için bu sınıfı devralabilirsiniz.  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 <xref:System.ServiceModel.Discovery.DiscoveryProxy> Özet sınıf, alma ve bulma ve duyuru iletileri işlemek için bir çerçeve sağlar. Özel keşif proxy'si uygularken bu sınıftan devralınan. Olduğunda bir `Probe` ileti çok noktaya yayın alınan <xref:System.ServiceModel.Discovery.DiscoveryProxy> sınıf çağrıları `BeginShouldRedirectFind` bir çok noktaya yayın gizleme ileti gönderilmesi gerekip gerekmediğini belirlemek için sanal bir yöntem. Çok noktaya yayın gizleme ileti göndermek geliştiricinin karar verirse veya `Probe` tek noktaya yayın ileti alınmazsa, bir örneğini oluşturur <xref:System.ServiceModel.Discovery.FindRequestContext> sınıfı gelen iletileri alan ve çağıran `OnBeginFind` sanal yöntem. Olduğunda bir `Resolve` ileti çok noktaya yayın alınan <xref:System.ServiceModel.Discovery.DiscoveryProxy> sınıf çağrıları `ShouldRedirectResolve` bir çok noktaya yayın gizleme ileti gönderilmesi gerekip gerekmediğini belirlemek için sanal bir yöntem. Çok noktaya yayın gizleme ileti göndermek geliştiricinin karar verirse veya `Resolve` tek noktaya yayın ileti alınmazsa, bir örneğini oluşturur <xref:System.ServiceModel.Discovery.ResolveCriteria> sınıfı gelen iletileri alan ve çağıran `OnBeginResolve` sanal yöntem. Merhaba veya Bye bir ileti alındığında <xref:System.ServiceModel.Discovery.DiscoveryProxy> uygun sanal yöntemini çağırır (`OnBeginOnlineAnnouncement` veya `OnBeingOfflineAnnouncement`), duyuru olayları başlatır.  
  
## <a name="discoveryversion"></a>DiscoveryVersion  
 <xref:System.ServiceModel.Discovery.DiscoveryVersion> Sınıf kullanılacak Bulma Protokolü sürümünü temsil eder.  
  
## <a name="endpointdiscoverybehavior"></a>EndpointDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Sınıfı bir bitiş noktası bulunabilirliğini kontrol, uzantıları, ek sözleşme türü adlarını belirtmek için kullanılır. ve bu uç noktası ile ilişkili kapsam. Bu davranışı yapılandırmak için bir uygulama uç noktasına eklenir, <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Zaman <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> eklenir hizmet ana bilgisayarı için varsayılan olarak hizmet ana bilgisayar tarafından barındırılan tüm uygulama uç noktaları olur bulunabilir. Geliştirici bulma için belirli bir uç ayarlayarak devre dışı bırakabilirsiniz <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> özelliğini `false`.  
  
## <a name="endpointdiscoverymetadata"></a>EndpointDiscoveryMetadata  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> Sınıfı, bir hizmet tarafından yayımlanan bir uç nokta sürümden bağımsız gösterimini sağlar. Uç nokta adresleri içerir, URI'ler, sözleşme türü adları, kapsamları, meta veri sürümü ve hizmet geliştirici tarafından belirtilen uzantılar dinleyin. <xref:System.ServiceModel.Discovery.FindCriteria> Sırasında istemci tarafından gönderilen bir `Probe` işlemi karşı eşleşir <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Ölçütler ile eşleşiyorsa, ardından <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> istemciye döndürülür. Uç nokta adresi <xref:System.ServiceModel.Discovery.ResolveCriteria> karşı uç nokta adresini eşleşen <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Ölçütler ile eşleşiyorsa, ardından <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> istemciye döndürülür.  
  
## <a name="findcriteria"></a>FindCriteria  
 <xref:System.ServiceModel.Discovery.FindCriteria> Kullanılması için bir hizmet bulma ölçütlerini belirtmek için kullanılan bir sürümden bağımsız sınıfı. Hizmetleri eşleştirmek için WS bulma tanımlanan ölçütler tam olarak destekler. Ayrıca, geliştiricilerin eşleştirme işlemi sırasında kullanılabilir özel değerler belirtmek için kullanabileceğiniz uzantılar vardır. Geliştirici sonlandırma ölçütünü sağlayabilir `Find` belirterek işlemi <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>, geliştirici ararken veya belirten hizmetlerin toplam sayısını belirten <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>, değeri olan, İstemci yanıtlar için bekleyeceği süreyi belirtir.  
  
## <a name="findrequestcontext"></a>FindRequestContext  
 <xref:System.ServiceModel.Discovery.FindRequestContext> Göre bulma hizmeti tarafından sınıfının örneği `Probe` ileti aldığında istemci başlattığında bir `Find` işlemi. Örneğini içeren <xref:System.ServiceModel.Discovery.FindCriteria> istemci tarafından belirtildi.  
  
## <a name="findresponse"></a>FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse> Sınıfı, çağırana döndürülür <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> yanıtların ile `Find` işlemi. Ayrıca mevcut <xref:System.ServiceModel.Discovery.FindCompletedEventArgs>. Bir koleksiyonunu içeren <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, bulunan uç noktaları koleksiyonu ve bir sözlükten <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> ve <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="resolvecriteria"></a>ResolveCriteria  
 <xref:System.ServiceModel.Discovery.ResolveCriteria> Zaten bilinen bir hizmet çözülürken kullanılan ölçütlerini belirtmek için kullanılan bir sürümden bağımsız sınıfı. Bu bilinen bir hizmet uç noktası adresini içerir. Geliştirici sonlandırma ölçütünü çözümleme işlemi için belirterek sağlayabilir <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A>, istemci yanıtlar için bekleyeceği süreyi belirtir.  
  
## <a name="resolveresponse"></a>ResolveResponse  
 <xref:System.ServiceModel.Discovery.ResolveResponse> Çağırana döndürülür <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> yanıtı yöntemiyle `Resolve` işlemi. Ayrıca mevcut <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs>. Örneğini içeren <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, bulunan uç noktaları ve bir örneği olduğu <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="servicediscoverybehavior"></a>ServiceDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Sınıfı, bulma özelliği için bir hizmet eklemek Geliştirici olanak tanır. Bu davranışların eklenmesi <xref:System.ServiceModel.ServiceHost>. <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Sınıf hizmet ana bilgisayarı için eklenen uygulama uç noktaları üzerinden yinelenir ve koleksiyonunu oluşturur <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> bulunabilir uç noktalarından. Tüm uç noktalar, varsayılan olarak bulunabilir. Belirli bir bitiş noktası bulunabilirliğini ekleyerek denetlenebilir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> belirli Bu uç noktaya. Duyurunun bitiş noktası eklenmişse <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> sonra hizmet ana bilgisayarı açıldığında veya duyuru bulunabilirlik tüm uç noktaların her duyuru uç noktaları gönderilir.  
  
## <a name="udpannouncementendpoint"></a>Udptransportsettings  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Sınıfı bir UDP üzerinden duyuru için önceden yapılandırılmış olan bir standart duyuru uç noktası, çok noktaya yayın bağlaması. Varsayılan olarak, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> WSApril2005 WS_Discovery sürümünü kullanacak şekilde ayarlanır.  
  
## <a name="udpdiscoveryendpoint"></a>UdpDiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Sınıfı bir UDP üzerinden keşfi için önceden yapılandırılmış olan bir standart bulma uç noktası, çok noktaya yayın bağlaması. Varsayılan olarak, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> WSDiscovery11 WS-bulma sürümünü kullanacak şekilde ayarlanır ve <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Adhoc?displayProperty=nameWithType> modu.
