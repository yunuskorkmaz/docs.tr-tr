---
title: DiscoveryClient ve DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 1f3e9a25e82c4515ee649736ed162ab858aa6ff7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205036"
---
# <a name="discoveryclient-and-dynamicendpoint"></a>DiscoveryClient ve DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient> ve <xref:System.ServiceModel.Discovery.DynamicEndpoint> istemci tarafında Hizmetleri aramak için kullanılan iki sınıf. <xref:System.ServiceModel.Discovery.DiscoveryClient> belirli bir eşleşen hizmetlerin listesini sizinle ölçütü ayarlayın ve hizmetlere bağlanmasına olanak sağlayan sağlar. <xref:System.ServiceModel.Discovery.DynamicEndpoint> aynı işlemi gerçekleştirir ve otomatik olarak bağlanan bulundu hizmetlerden biri için ek olarak. İçinde herhangi bir uç noktaya yapılan bir <xref:System.ServiceModel.Discovery.DynamicEndpoint>, arama ölçütlerini de yapılandırması, bu nedenle eklenebilir <xref:System.ServiceModel.Discovery.DynamicEndpoint> yararlıdır bulma çözümünüzde gerekir, ancak istemci mantığı değiştirmek istiyor musunuz – yalnızca uç noktaları değiştirmeniz gerekir. <xref:System.ServiceModel.Discovery.DiscoveryClient> Öte yandan, arama işlemi üzerinde daha hassas denetim elde etmek için kullanılabilir. Kullanır ve her birinin avantajları aşağıda ayrıntılandırılmıştır.  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Zaman uyumlu ve zaman uyumsuz bulma yöntemleri tanımlar <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> ve <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> olayları.  Ayrıca, zaman uyumlu ve zaman uyumsuz Çözümleme yöntemleri tanımlar ve <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> olay. Kullanım <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> veya <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> Hizmetleri aramak için yöntemleri. Bu yöntemlerin ikisi de ele bir <xref:System.ServiceModel.Discovery.FindCriteria> sözleşme türü adları, kapsamları, istenen sonuçlarının maksimum sayısını belirtmenizi sağlayan örnek ve kapsam kuralları eşleşen. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> Ve <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> çağırırken olayları kullanılabilir <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> yöntemi. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> Her tetiklendiğinde <xref:System.ServiceModel.Discovery.DiscoveryClient> hizmetten bir yanıt alır. Bir ilerleme çubuğu bulma işleminin ilerleme durumunu gösteren görüntülemek için kullanılabilir. Bul yanıtları alındıkları gibi davranmasını de kullanılabilir. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> Bulma işlemi tamamlandığında olay tetiklenir. Bu yanıt sayısı aldığından veya oluşabilir <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> geçti. Bulma işlemi tamamlandığında sonuçlar döndürülür bir <xref:System.ServiceModel.Discovery.FindResponse> örneği. <xref:System.ServiceModel.Discovery.FindResponse> Koleksiyonunu içeren <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> adresleri, sözleşme türü adları, uzantılar, dinleme URI'ler ve kapsamları eşleşen hizmetleri içerir. Bu bilgiler daha sonra bağlanmak ve eşleşen hizmetlerden biri çağırmak için de kullanabilirsiniz. Aşağıdaki örnek System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) yöntemini çağırın ve döndürülen meta verilere bulunan hizmeti çağırmak nasıl gösterir. Kullanmanın bir avantajı <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> olan buldunuz ve daha sonra bunları kullanmak bitiş noktaları listesini önbelleğe alabilirsiniz. Bu önbellek ile çeşitli hata koşullarını işlemek için özel bir mantık oluşturabilirsiniz.  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
FindCriteria criteria = new FindCriteria(typeof(ICalculatorService));  
FindResponse fr = dc.Find(criteria);  
  
if (fr.Endpoints.Count > 0)  
{  
   EndpointAddress ep = fr.Endpoints[0].Address;  
   CalculatorServiceClient client = new CalculatorServiceClient();  
  
    // Connect to the discovered service endpoint  
   client.Endpoint.Address = endpointAddress;  
   Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
}  
else  
   Console.WriteLine("No matching endpoints found");  
```  
  
 Aşağıdaki örnek, bir bulma işlemi gerçekleştirip gösterilmektedir.  
  
```  
static void FindServiceAsync()  
{  
   DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());   
   dc.FindCompleted += new EventHandler<FindCompletedEventArgs>( discoveryClient_FindCompleted);  
   dc.FindProgressChanged += new EventHandler<FindProgressChangedEventArgs>(discoveryClient_FindProgressChanged);  
   dc.FindAsync(new FindCriteria(typeof(ICalculatorService)));   
}   
static void discoveryClient_FindProgressChanged(object sender, FindProgressChangedEventArgs e)  
{  
   Console.WriteLine("Found service at: " + e.EndpointDiscoveryMetadata.Address  
}   
  
static void discoveryClient_FindCompleted(object sender, FindCompletedEventArgs e)  
{    
      if (e.Result.Endpoints.Count > 0)  
            {  
                EndpointAddress ep = e.Result.Endpoints[0].Address;  
                CalculatorServiceClient client = new CalculatorServiceClient();  
  
                // Connect to the discovered service endpoint  
                client.Endpoint.Address = ep;  
                Console.WriteLine("Invoking CalculatorService at {0}", ep);  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
            }  
            else  
                Console.WriteLine("No matching endpoints found");  
  
        }  
```
  
 Kullanım <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> ve <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> hizmet bulmak için yöntemleri temel uç nokta adresini. Uç nokta adresini adreslenebilir ağ olmadığında kullanışlıdır. Çözümleme yöntemleri bir örneğini alır <xref:System.ServiceModel.Discovery.ResolveCriteria> çözümleme, çözümleme işlemi en uzun süresi ve uzantıları kümesi Hizmeti uç nokta adresini belirtmenize olanak tanıyan. Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> hizmet çözmek için yöntemi.  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint> bir standart uç noktası (daha fazla bilgi için [standart uç noktaları](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) bulma işlemini gerçekleştirir ve eşleşen bir hizmeti otomatik olarak seçer. Yalnızca oluşturma bir <xref:System.ServiceModel.Discovery.DynamicEndpoint> arayın ve bağlama ve geçirmek için sözleşmedeki geçirme <xref:System.ServiceModel.Discovery.DynamicEndpoint> WCF istemcisini örneği. Aşağıdaki örnek nasıl oluşturup kullanacağınızı gösteren bir <xref:System.ServiceModel.Discovery.DynamicEndpoint> hesaplayıcı hizmeti çağırmak için. İstemci her açıldığında bulma gerçekleştirilir. Herhangi bir uç nokta yapılandırmasında tanımlı de dönüştürülebilir bir <xref:System.ServiceModel.Discovery.DynamicEndpoint> ekleyerek `kind ="dynamicEndpoint"` özniteliği için uç nokta yapılandırma öğesi.  
  
```  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kapsamlarla Bulma](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [Temel](../../../../docs/framework/wcf/samples/basic-sample.md)
