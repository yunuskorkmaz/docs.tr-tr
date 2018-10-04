---
title: Keşif Bulma ve FindCriteria
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: bd54a7bc896870035972daf1ea6f56d84dc5414e
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583941"
---
# <a name="discovery-find-and-findcriteria"></a>Keşif Bulma ve FindCriteria
Bir bulma bulma işlemi bir veya daha fazla Hizmetleri bulmak için bir istemci tarafından başlatılan ve bulma ana eylemleri biridir. Bir bulma gerçekleştirme ağ üzerinden bir WS-bulma işlemi araştırma iletisi gönderir. Ölçütlerle eşleşen Hizmetleri yanıt WS-bulma ProbeMatch iletileriyle belirtilen. Bulma iletileri hakkında daha fazla bilgi için bkz. [WS-bulma belirtimi](https://go.microsoft.com/fwlink/?LinkID=122347).  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Sınıfı bulma istemci işlemlerini kolay hale getirir ve bulma işlemlerinin gerçekleştirmek için bir mekanizma sağlar. İçerdiği bir <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> (engelleme) zaman uyumlu bulma gerçekleştiren yöntemi ve bir <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> engelleyici olmayan bir zaman uyumsuz bulma başlatan yöntem. Her iki yöntem de ele bir <xref:System.ServiceModel.Discovery.FindCriteria> parametresi ve sonuçları kullanıcının üzerinden sağlamak bir <xref:System.ServiceModel.Discovery.FindResponse> nesne.  
  
## <a name="findcriteria"></a>FindCriteria  
 <xref:System.ServiceModel.Discovery.FindCriteria> sonlandırma ölçütünü (ne kadar süreyle arama son) bulun ve aradığınız hangi hizmetlerin belirtin, arama ölçütleri gruplandırılabilir birçok özelliğe sahiptir. A <xref:System.ServiceModel.Discovery.FindCriteria> birden çok ölçüt içerebilir. Varsayılan olarak, tüm bileşenlerin eşleşecek şekilde hizmet vardır. Aksi takdirde, kendisini eşleşen hizmet göz önünde bulundurmaz. Yalnızca bazı ölçütlerle eşleşen Hizmetleri bulmak istiyorsanız, hizmette özel bulma mantığını uygulayabilir veya birden çok sorgu kullanabilirsiniz.  
  
 Arama ölçütleri şunlardır:  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> -İsteğe bağlı. Aranan hizmet ve genellikle bir hizmet için ararken kullanılan ölçütü sözleşme adı. Birden fazla sözleşme adı belirtilirse, yalnızca hizmet uç noktaları tüm sözleşmelerin eşleşen yanıtlayın. WCF'de bir uç nokta yalnızca bir sözleşme destekleyebileceğini unutmayın.  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ScopeElement> -İsteğe bağlı. Belirli hizmet uç noktalarını sınıflandırmak için kullanılan mutlak bir URI'leri kapsamlardır. Bu senaryolarda, burada aynı anlaşmaya birden fazla uç nokta kullanıma sunmak ve aramak için bir yol uç noktaları bir alt kümesi için istediğiniz kullanmak isteyebilirsiniz. Birden fazla kapsam belirtilmezse, yalnızca hizmet uç noktaları tüm kapsamlar eşleşen yanıtlayın.  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> -Kapsamlar araştırma iletisi ve onun uç noktasında alanları eşleştirirken kullanılan eşleştirme algoritmasını belirtir. Desteklenen beş kapsam eşleşen kural vardır:  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType> Karşılaştırma büyük/küçük harfe temel dize.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> eşleşme parçaları tarafından ayrılmış "/". Bir arama http://contoso/building1 kapsamlı bir hizmet eşleşen http://contoso/building/floor1. Eşleşmemesi Not http://contoso/building100 son iki Segment eşleşmediğinden.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType> kapsamlar tarafından kesimleri kullanarak bir LDAP URL'si ile eşleşir.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType> kapsamları bir UUID dizesiyle tam olarak eşleşir.  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> bir kapsam belirtmeyen Hizmetleri eşleşir.  
  
     Bir kapsam eşleşen kural belirtilmezse <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> kullanılır.  
  
 Sonlandırma ölçütünü şunlardır:  
  
1.  <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> -Ağdaki hizmetlerden yanıtları için beklenecek en uzun süre. Varsayılan süre 20 saniyedir.  
  
2.  <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> -İçin beklenilecek en fazla sayısı. Varsa <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> önce alınan yanıtları <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> geçti, bulma işlemi sona erer.  
  
## <a name="findresponse"></a>FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse> sahip bir <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> içeren bus'dan eşleşen ağ üzerindeki hizmet tarafından gönderilen koleksiyon özelliği. Hizmet yanıtlandı, boş bir koleksiyondur. Bir veya daha fazla hizmet yanıt verdi, her yanıt depolanan bir <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> adresi, sözleşme ve hizmetle ilgili bazı ek bilgiler içeren nesne.  
  
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
 [WCF Bulmaya Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Keşif İstemcisi Kanalını Kullanma](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [Kapsamlarla Bulma](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [Temel](../../../../docs/framework/wcf/samples/basic-sample.md)
