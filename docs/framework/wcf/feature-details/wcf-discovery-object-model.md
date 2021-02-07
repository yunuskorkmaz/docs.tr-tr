---
description: 'Daha fazla bilgi edinin: WCF bulma nesne modeli'
title: WCF Keşif Nesnesi Modeli
ms.date: 03/30/2017
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
ms.openlocfilehash: e0d1c569329e0f6c5d4a6cfe4271b954299efdac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732923"
---
# <a name="wcf-discovery-object-model"></a>WCF Keşif Nesnesi Modeli

WCF bulma, çalışma zamanında keşfedilen Hizmetleri ve bu hizmetleri bulup kullanan istemcileri yazmanızı sağlayan Birleşik bir programlama modeli sağlayan bir tür kümesinden oluşur.  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>Hizmeti keşfedilebilir hale getirme ve Hizmetleri bulma  

 Bir WCF hizmetini bulunabilir hale getirmek için, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> <xref:System.ServiceModel.Description.ServiceDescription> hizmet ana bilgisayarına bir ekleyin ve bir bulma uç noktası ekleyin. Bir hizmet duyuru iletileri gönderecek şekilde yapılandırıldıysa (bir ekleyerek <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> ), hizmet ana bilgisayarı açılıp kapatıldığında duyuru gönderilir.  
  
 Hizmet duyurusu iletilerini dinlemek isteyen bir istemci bir duyuru hizmeti barındırır ve bir veya daha fazla duyuru uç noktası ekler. Duyuru hizmeti, duyuru iletileri alır ve duyuru olayları oluşturur.  
  
 İstemci, <xref:System.ServiceModel.Discovery.DiscoveryClient> kullanılabilir hizmetleri aramak için sınıfını kullanır. İstemci uygulaması, <xref:System.ServiceModel.Discovery.DiscoveryClient> bulma iletilerinin nereye gönderileceğini belirten bir bulma uç noktası geçirerek sınıfı başlatır. İstemci <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> bir istek gönderen yöntemini çağırır `Probe` . Bulma iletilerini dinleyen hizmetler bu isteği alır `Probe` . Hizmet, içinde belirtilen ölçütlerle eşleşiyorsa `Probe` , `ProbeMatch` istemciye geri bir ileti gönderir.  
  
## <a name="object-model"></a>Nesne modeli  

 WCF bulma API 'SI aşağıdaki sınıfları tanımlar:  
  
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

 <xref:System.ServiceModel.Discovery.AnnouncementClient>Sınıfı, duyuru iletileri göndermek için zaman uyumlu ve zaman uyumsuz yöntemler sağlar. Merhaba ve bye olmak üzere iki tür duyuru iletisi vardır. Bir hizmetin kullanılabilir olduğunu göstermek için bir Hello iletisi gönderilir ve var olan bir hizmetin kullanılamaz hale geldiğini göstermek için bir bye iletisi gönderilir. Geliştirici, bir örneğini <xref:System.ServiceModel.Discovery.AnnouncementClient> Oluşturucu parametresi olarak geçirerek bir örnek oluşturur <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> .  
  
## <a name="announcementendpoint"></a>AnnouncementEndpoint  

 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> bir sabit duyuru sözleşmesiyle standart uç noktayı temsil eder. Duyuru iletileri göndermek ve almak için bir hizmet veya istemci tarafından kullanılır. Varsayılan olarak, <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> sınıfı WS_Discovery 11 protokol sürümünü kullanacak şekilde ayarlanır.  
  
## <a name="announcementservice"></a>AnnouncementService  

 <xref:System.ServiceModel.Discovery.AnnouncementService> , duyuru iletilerini alan ve işleyen bir duyuru hizmetinin sistem tarafından sağlanmış bir uygulamasıdır. Bir Hello veya bye iletisi alındığında, <xref:System.ServiceModel.Discovery.AnnouncementService> örnek uygun sanal yöntemi çağırır <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> veya <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A> bildiri olaylarını başlatır.  
  
## <a name="discoveryclient"></a>DiscoveryClient  

 <xref:System.ServiceModel.Discovery.DiscoveryClient>Sınıfı, kullanılabilir hizmetleri bulmak ve çözmek için bir istemci uygulaması tarafından kullanılır. Belirtilen ve sırasıyla hizmetleri bulmak ve çözmek için zaman uyumlu ve zaman uyumsuz yöntemler sağlar <xref:System.ServiceModel.Discovery.FindCriteria> <xref:System.ServiceModel.Discovery.ResolveCriteria> . Geliştirici bir örnek oluşturur <xref:System.ServiceModel.Discovery.DiscoveryClient> ve bir <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> Oluşturucu parametresi olarak bir örneği sağlar.  
  
 Bir hizmeti bulmak için, geliştirici zaman uyumlu veya zaman uyumsuz yöntemini çağırır, bu da `Find` <xref:System.ServiceModel.Discovery.FindCriteria> kullanılacak arama ölçütlerini içeren bir örnek sağlar. , <xref:System.ServiceModel.Discovery.DiscoveryClient> `Probe` Uygun üst bilgilerle bir ileti oluşturur ve bulma isteğini gönderir. Herhangi bir zamanda birden fazla bekleyen istek olabileceğinden `Find` , istemci alınan yanıtları ilişkilendirir ve yanıtı doğrular. Daha sonra, kullanarak işlemi çağıran için sonuçları gönderir `Find` <xref:System.ServiceModel.Discovery.FindResponse> .  
  
 Bilinen bir hizmeti çözmek için, Geliştirici `Resolve` <xref:System.ServiceModel.Discovery.ResolveCriteria> bilinen hizmeti içeren bir örneğini sağlayan zaman uyumlu veya zaman uyumsuz yöntemi çağırır <xref:System.ServiceModel.EndpointAddress> . , <xref:System.ServiceModel.Discovery.DiscoveryClient> `Resolve` Uygun üst bilgilerle ileti oluşturur ve Resolve isteğini gönderir. Alınan yanıt, bekleyen çözümleme isteklerine göre bağıntılı olur ve sonuç, kullanarak işlem çağıranına dağıtılır `Resolve` <xref:System.ServiceModel.Discovery.ResolveResponse> .  
  
 Ağda bir bulma proxy 'si varsa ve <xref:System.ServiceModel.Discovery.DiscoveryClient> bulma isteğini çok noktaya yayın olarak gönderirse, bulma proxy 'si çok noktaya yayın gizleme Hello iletisi ile yanıt verebilir. , <xref:System.ServiceModel.Discovery.DiscoveryClient> `ProxyAvailable` Bekleyen veya isteklere yanıt olarak Hello iletileri aldığında olayı oluşturur `Find` `Resolve` . `ProxyAvailable`Olay, <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> bulma proxy hakkında ' yı içerir. Bu bilgileri kullanarak, geçici olarak bir ad hoc 'dan yönetilen moda geçiş yapın.  
  
## <a name="discoveryendpoint"></a>DiscoveryEndpoint  

 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> sabit bir bulma sözleşmesiyle standart uç noktayı temsil eder. Bulma iletilerini göndermek veya almak için bir hizmet veya istemci tarafından kullanılır. Varsayılan olarak, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> kullanım <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Managed?displayProperty=nameWithType> modu ve WSDiscovery11 WS-Discovery sürümü olarak ayarlanır.  
  
## <a name="discoverymessagesequencegenerator"></a>DiscoveryMessageSequenceGenerator  

 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator><xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>hizmet, bulma veya duyuru iletileri gönderirken bir oluşturmak için kullanılır.  
  
## <a name="discoveryservice"></a>DiscoveryService  

 <xref:System.ServiceModel.Discovery.DiscoveryService>Soyut sınıf, ileti alma ve işleme için bir çerçeve `Probe` sağlar `Resolve` . Bir `Probe` ileti alındığında, <xref:System.ServiceModel.Discovery.DiscoveryService> gelen iletiye göre bir örneği oluşturur <xref:System.ServiceModel.Discovery.FindRequestContext> ve <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> sanal yöntemi çağırır. Bir `Resolve` ileti alındığında, <xref:System.ServiceModel.Discovery.DiscoveryService> <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A> sanal yöntemi çağırır. Özel bir keşif hizmeti uygulamasını sağlamak için bu sınıftan devralma yapabilirsiniz.  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  

 <xref:System.ServiceModel.Discovery.DiscoveryProxy>Soyut sınıf bulma ve duyuru iletilerini almak ve işlemek için bir çerçeve sağlar. Özel bir keşif proxy 'si uygularken bu sınıftan kalıtılır. `Probe`Çok noktaya yayın üzerinden bir ileti alındığında, <xref:System.ServiceModel.Discovery.DiscoveryProxy> sınıf, `BeginShouldRedirectFind` çok noktaya yayın gizleme iletisi gönderilip gönderilmeyeceğini anlamak için sanal yöntemi çağırır. Geliştirici, çok noktaya yayın gizleme iletisi göndermemeye karar verirse veya `Probe` ileti tek noktaya yayın üzerinden alınmışsa, <xref:System.ServiceModel.Discovery.FindRequestContext> gelen iletiye göre sınıfın bir örneğini oluşturur ve `OnBeginFind` sanal yöntemi çağırır. `Resolve`Çok noktaya yayın üzerinden bir ileti alındığında, <xref:System.ServiceModel.Discovery.DiscoveryProxy> sınıf, `ShouldRedirectResolve` çok noktaya yayın gizleme iletisi gönderilip gönderilmeyeceğini anlamak için sanal yöntemi çağırır. Geliştirici, çok noktaya yayın gizleme iletisi göndermemeye karar verirse veya `Resolve` ileti tek noktaya yayın üzerinden alınmışsa, <xref:System.ServiceModel.Discovery.ResolveCriteria> gelen iletiye göre sınıfın bir örneğini oluşturur ve `OnBeginResolve` sanal yöntemi çağırır. Bir Hello veya bye iletisi alındığında, <xref:System.ServiceModel.Discovery.DiscoveryProxy> uygun sanal yöntemi ( `OnBeginOnlineAnnouncement` veya `OnBeingOfflineAnnouncement` ) çağırır, bu da duyuru olaylarını başlatır.  
  
## <a name="discoveryversion"></a>DiscoveryVersion  

 <xref:System.ServiceModel.Discovery.DiscoveryVersion>Sınıfı, kullanılacak bulma protokolü sürümünü temsil eder.  
  
## <a name="endpointdiscoverybehavior"></a>EndpointDiscoveryBehavior  

 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>Sınıfı, bir uç noktanın bulunabilirliği denetlemek için kullanılır, uzantıları, ek sözleşme türü adlarını belirtin. ve bu uç noktayla ilişkili kapsamlar. Bu davranış, yapılandırmak için bir uygulama uç noktasına eklenir <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> . <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>Hizmet ana bilgisayarına eklendiğinde, varsayılan olarak hizmet ana bilgisayarı tarafından barındırılan tüm uygulama uç noktaları bulunabilir hale gelir. Geliştirici, özelliğini olarak ayarlayarak belirli bir uç nokta için bulmayı kapatabilir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> `false` .  
  
## <a name="endpointdiscoverymetadata"></a>EndpointDiscoveryMetadata  

 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>Sınıfı, hizmet tarafından yayımlanan bir uç noktanın sürümden bağımsız bir gösterimini sağlar. Hizmet geliştiricisi tarafından belirtilen uç nokta adresleri, dinleme URI 'Leri, sözleşme türü adları, kapsamlar, meta veri sürümü ve uzantıları içerir. <xref:System.ServiceModel.Discovery.FindCriteria>Bir işlem sırasında istemci tarafından gönderilen, ile `Probe` eşleştirilir <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> . Kriterler eşleşiyorsa, <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> istemciye döndürülür. ' Deki bitiş noktası adresi, <xref:System.ServiceModel.Discovery.ResolveCriteria> öğesinin uç nokta adresiyle eşleştirilir <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> . Kriterler eşleşiyorsa, <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> istemciye döndürülür.  
  
## <a name="findcriteria"></a>FindCriteria  

 <xref:System.ServiceModel.Discovery.FindCriteria>Sınıfı, bir hizmeti ararken kullanılan ölçütü belirtmek için kullanılan sürümden bağımsız bir sınıftır. Bu, eşleşen hizmetler için WS-bulma tanımlı ölçütlerini tam olarak destekler. Ayrıca, geliştiricilerin eşleşen işlem sırasında kullanılabilecek özel değerleri belirtmek için kullanabilecekleri uzantıları vardır. Geliştirici, `Find` <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> geliştiricinin Aradığınız toplam hizmet sayısını belirten veya belirten, <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> istemcinin yanıtları ne kadar bekleyeceğini belirten değer olan öğesini belirterek, işlem için sonlandırma ölçütlerini sağlayabilir.  
  
## <a name="findrequestcontext"></a>FindRequestContext  

 <xref:System.ServiceModel.Discovery.FindRequestContext>Sınıfı, `Probe` bir istemci bir işlemi başlattığında aldığı iletiyi temel alan bulma hizmeti tarafından oluşturulur `Find` . <xref:System.ServiceModel.Discovery.FindCriteria>İstemci tarafından belirtilen bir örneğini içerir.  
  
## <a name="findresponse"></a>FindResponse  

 <xref:System.ServiceModel.Discovery.FindResponse>Sınıfı, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> işlem yanıtları ile çağıranına döndürülür `Find` . Ayrıca, içinde de mevcuttur <xref:System.ServiceModel.Discovery.FindCompletedEventArgs> . <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>Bulunan, ve ' nin bir sözlüğü olan bir koleksiyonunu içerir <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> .  
  
## <a name="resolvecriteria"></a>ResolveCriteria  

 <xref:System.ServiceModel.Discovery.ResolveCriteria>Sınıfı, zaten bilinen bir hizmet çözümlenirken kullanılan ölçütü belirtmek için kullanılan sürümden bağımsız bir sınıftır. Bilinen hizmetin uç nokta adresini içerir. Geliştirici, <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A> istemcinin yanıtları ne kadar bekleyeceğini belirten öğesini belirterek, Çözümle işlemi için sonlandırma ölçütlerini sağlayabilir.  
  
## <a name="resolveresponse"></a>Resolveres,  

 , <xref:System.ServiceModel.Discovery.ResolveResponse> <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> Yöntemi, işlem yanıtı ile çağırana döndürülür `Resolve` . Ayrıca, içinde de mevcuttur <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs> . <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>Bulunan, bulunan uç noktalar ve bir örneği olan bir örneğini içerir <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> .  
  
## <a name="servicediscoverybehavior"></a>ServiceDiscoveryBehavior  

 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>Sınıfı, geliştiricinin bulma özelliğini bir hizmete eklemesini sağlar. Bu davranışı öğesine eklersiniz <xref:System.ServiceModel.ServiceHost> . <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>Sınıfı, hizmet konağına eklenen uygulama uç noktaları üzerinde yinelenir ve bulunabilir uç noktalardan bir koleksiyon oluşturur <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> . Tüm uç noktalar varsayılan olarak bulunabilir. Belirli bir uç noktanın bulunabilirliği <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> söz konusu uç noktaya eklenerek denetlenebilir. Duyuru uç noktaları ' na eklenirse, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hizmet ana bilgisayarı açıldığında veya kapandığında her duyuru uç noktası üzerinden tüm keşfedilebilir uç noktalar üzerinden gönderilir.  
  
## <a name="udpannouncementendpoint"></a>UdpTransportSettings  

 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>Sınıfı, BIR UDP çok noktaya yayın bağlaması üzerinden duyuru için önceden yapılandırılmış standart bir duyuru uç noktasıdır. Varsayılan olarak, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> WSApril2005 WS_Discovery sürümünü kullanacak şekilde ayarlanır.  
  
## <a name="udpdiscoveryendpoint"></a>UdpDiscoveryEndpoint  

 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>Sınıfı, BIR UDP çok noktaya yayın bağlaması üzerinde bulma için önceden yapılandırılmış standart bir bulma uç noktasıdır. Varsayılan olarak, <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> WSDiscovery11 WS-Discovery sürümünü ve modunu kullanacak şekilde ayarlanır <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Adhoc?displayProperty=nameWithType> .
