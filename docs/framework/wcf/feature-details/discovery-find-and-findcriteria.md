---
title: "Keşif Bulma ve FindCriteria"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b367b5133cd765fe7e160cd2706589c1773eeb59
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-find-and-findcriteria"></a>Keşif Bulma ve FindCriteria
Bir bulma bulma işlemi bir veya daha fazla Hizmetleri bulmak için bir istemci tarafından başlatılan ve bulma ana Eylemler biridir. Bir bulma gerçekleştirme WS-bulma araştırma ileti ağ üzerinden gönderir. Ölçütlere uyan Hizmetleri yanıt WS-bulma ProbeMatch iletileriyle belirtilen. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bulma iletilerini görmek [WS-bulma belirtimi](http://go.microsoft.com/fwlink/?LinkID=122347).  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Sınıfı, bulma işlemleri ve kolay bulma istemci işlemlerini gerçekleştirme sağlar yapmak için bir mekanizma sağlar. İçerdiği bir <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> (engelleme) olarak zaman uyumlu bir bulma gerçekleştirir, yöntemi ve <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> engelleyici olmayan bir zaman uyumsuz bulma başlatan yöntem. Her iki yöntem ele bir <xref:System.ServiceModel.Discovery.FindCriteria> parametresi ve kullanıcı sonuçları sağlamak bir <xref:System.ServiceModel.Discovery.FindResponse> nesnesi.  
  
## <a name="findcriteria"></a>FindCriteria  
 <xref:System.ServiceModel.Discovery.FindCriteria>Aradığınız hangi hizmetlerin belirtin, arama ölçütleri gruplandırılır ve (ne kadar süreyle arama son) sonlandırma ölçütleri Bul çeşitli özelliklere sahiptir. A <xref:System.ServiceModel.Discovery.FindCriteria> birden fazla arama ölçütü içerebilir. Varsayılan olarak, hizmet bileşenlerinin tümünü eşleşmelidir Aksi takdirde, kendisini eşleşen hizmet dikkate almaz. Yalnızca bazı ölçütlerle eşleşen Hizmetleri bulmak istiyorsanız, hizmette özel bulma mantığını uygulayabilirsiniz veya birden çok sorgu kullanabilirsiniz.  
  
 Arama ölçütlerini şunları içerir:  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement>-İsteğe bağlı. Aranan hizmeti ve genellikle bir hizmet için arama yaparken kullanılan ölçütleri sözleşme adı. Birden fazla sözleşme adı belirtilirse, yalnızca hizmet uç noktaları tüm sözleşmeleri eşleşen yanıtlayın. İçinde unutmayın [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir uç nokta yalnızca bir sözleşme destekleyebilir.  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ScopeElement>-İsteğe bağlı. Tek tek hizmet uç noktaları kategorilere ayırmak için kullanılan mutlak URI kapsamlardır. Bu burada aynı sözleşme birden çok uç noktalarını kullanıma sunar ve uç noktaları kısmı için bir şekilde aramak istediğiniz senaryolarda kullanmak isteyebilirsiniz. Birden çok kapsam belirtilmezse, yalnızca tüm kapsamlar eşleşen hizmet uç yanıtlayın.  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A>-Bitiş Noktası'nın araştırma iletiyle kapsamlarda eşleşen sırasında kullanılacak eşleşen algoritmasını belirtir. Beş desteklenen kapsam eşleşen kural vardır:  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType>büyük küçük harfe duyarlı temel bir karşılaştırma dizesi.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType>eşleşme kesimleri tarafından ayrılmış "/". Http://contoso/building1 için bir arama hizmeti kapsam http://contoso/building/floor1 ile eşleşir. Son iki bölümü eşleşmediği için http://contoso/building100 eşleşmiyor unutmayın.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType>kapsamları bir LDAP URL'si kullanarak kesimleri ile eşleşir.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType>tam olarak bir UUID dizesi kullanarak kapsamları eşleşir.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType>bir kapsam belirtmeyen Hizmetleri eşleşir.  
  
     Bir kapsam eşleşen kural belirtilmezse, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> kullanılır.  
  
 Sonlandırma kriterleri içerir:  
  
1.  <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>-Ağ üzerinde yanıtları Hizmetleri'nden beklemek en uzun süre. Varsayılan süre 20 saniye kullanılır.  
  
2.  <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>-En fazla bekleme yanıt sayısı. Varsa <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> önce alınan yanıtların <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> geçtikten, bulma işlemi sona erer.  
  
## <a name="findresponse"></a>FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse>sahip bir <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> eşleşen ağ üzerindeki hizmet tarafından gönderilen yanıtı içeren koleksiyon özelliği. Hiçbir hizmet yanıtlanan, boş bir koleksiyonudur. Bir veya daha fazla hizmet yanıt verdi, her yanıt depolanan bir <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> adresi, sözleşme ve hizmet hakkında bazı ek bilgiler içeren nesne.  
  
 Aşağıdaki örnek kodda bir bulma işlemi gösterilmektedir.  
  
```  
// Create DiscoveryClient  
DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
// Create FindCriteria  
FindCriteria findCriteria = new FindCriteria(typeof(IPrinterService));  
findCriteria.Scopes.Add(new Uri("http://www.contoso.com/building1/floor1"));  
findCriteria.Duration = TimeSpan.FromSeconds(10);   
  
// Find ICalculatorService endpoints              
FindResponse findResponse = discoveryClient.Find(findCriteria);  
  
Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count)  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF keşif genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Keşif istemcisi kanalını kullanma](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [Kapsam ile keşif](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [Zaman uyumsuz bulma](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)  
 [Temel](../../../../docs/framework/wcf/samples/basic-sample.md)
