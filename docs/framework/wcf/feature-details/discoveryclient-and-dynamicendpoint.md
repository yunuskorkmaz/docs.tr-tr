---
title: DiscoveryClient ve DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: d9bf5bf0032a299589292e51ad9bc273c56ced3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="discoveryclient-and-dynamicendpoint"></a>DiscoveryClient ve DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient> ve <xref:System.ServiceModel.Discovery.DynamicEndpoint> istemci tarafında Hizmetleri aramak için kullanılan iki sınıf. <xref:System.ServiceModel.Discovery.DiscoveryClient> belirli bir eşleşen hizmetlerin listesini sizinle ölçütünü ayarlamak ve hizmetlere bağlanmanıza olanak sağlayan sağlar. <xref:System.ServiceModel.Discovery.DynamicEndpoint> aynı işlemi gerçekleştirir ve otomatik olarak bağlanır bulundu hizmetlerden biri için ek olarak. Herhangi bir uç nokta içine yapılabilir bir <xref:System.ServiceModel.Discovery.DynamicEndpoint>, arama ölçütlerini de yapılandırması, bu nedenle eklenebilir <xref:System.ServiceModel.Discovery.DynamicEndpoint> yararlı olduğunda bulma çözümünüzde gerekir, ancak istemci mantığı değiştirmek istiyor musunuz – uç noktalarını değiştirmek yeterlidir. <xref:System.ServiceModel.Discovery.DiscoveryClient> Öte yandan, arama işlemi üzerinde daha hassas denetim kazanmak için kullanılabilir. Kullanır ve her birinin avantajları aşağıda ayrıntılandırılmıştır.  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Zaman uyumlu ve zaman uyumsuz bulma yöntemleri tanımlar <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> ve <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> olaylar.  Zaman uyumlu ve zaman uyumsuz Çözümleme yöntemleri de tanımlar ve <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> olay. Kullanım <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> veya <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> Hizmetleri aramak için yöntemleri. Bu yöntemlerin her ikisi de ele bir <xref:System.ServiceModel.Discovery.FindCriteria> sözleşme tür adları, kapsamları, istenen sonuçlarının maksimum sayısını belirtmenize olanak tanır örneği ve eşleştirme kuralları kapsamı. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> Ve <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> çağrılırken olayları kullanılabilir <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> yöntemi. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> Her tetiklenir <xref:System.ServiceModel.Discovery.DiscoveryClient> bir hizmetinden bir yanıt alır. Bir ilerleme çubuğu bulma işleminin ilerleme durumunu gösteren görüntülemek için kullanılabilir. Ayrıca, bulma yanıtları alındıkları olarak hareket edecek de kullanılabilir. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> Bulma işlemi tamamlandığında olay tetiklenir. Bu yanıt maksimum sayısı aldığından veya varsa ortaya çıkabilir <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> geçti. Bulma işlemi tamamlandığında sonuçları döndürülür bir <xref:System.ServiceModel.Discovery.FindResponse> örneği. <xref:System.ServiceModel.Discovery.FindResponse> Oluşan bir koleksiyon içeren <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> adresleri, sözleşme tür adları, uzantılar, dinleme URI'ler ve eşleşen hizmetleri kapsamını içerir. Bu bilgiler daha sonra bağlanmak ve eşleşen hizmetlerden biri çağırmak için de kullanabilirsiniz. Aşağıdaki örnek System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) yöntemini çağırın ve bulunan hizmetini çağırmak için döndürülen meta veri nasıl kullanılacağını gösterir. Kullanmanın bir avantajı <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> olan buldunuz ve daha sonraki bir zamanda kullanmak bitiş noktaları listesini önbelleğe alabilirsiniz. Bu önbellek ile çeşitli hatası koşullarını işlemek için Özel mantık oluşturabilirsiniz.  
  
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
  
 Bulma çağrıları zaman uyumsuz yapma hakkında daha fazla bilgi için bkz: [zaman uyumsuz bulma](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md).  
  
 Kullanım <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> ve <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> bir hizmeti bulmak için yöntemleri temel uç nokta adresine. Uç nokta adresi adreslenebilir ağ olmadığında kullanışlıdır. Çözümleme yöntemleri bir örneği ele <xref:System.ServiceModel.Discovery.ResolveCriteria> , çözümleme, çözümleme işlemi en uzun süresi ve uzantılar kümesi, hizmet uç noktası adresi belirtme sağlar. Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> bir hizmeti çözümlemek için yöntem.  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint> Standart uç noktası (daha fazla bilgi için bkz: [standart uç noktaları](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) bulma işlemini gerçekleştirir ve eşleşen hizmet otomatik olarak seçer. Yalnızca oluşturmanız bir <xref:System.ServiceModel.Discovery.DynamicEndpoint> aramak ve kullanın ve geçirmek için bağlama sözleşmesindeki geçirme <xref:System.ServiceModel.Discovery.DynamicEndpoint> WCF istemcisini örneğine. Aşağıdaki örnekte, oluşturma ve kullanma gösterilmektedir bir <xref:System.ServiceModel.Discovery.DynamicEndpoint> hesaplayıcı hizmetini çağırmak için. İstemci her açıldığında bulma gerçekleştirilir. Yapılandırmada tanımlanan herhangi bir uç nokta da dönüştürülebilir bir <xref:System.ServiceModel.Discovery.DynamicEndpoint> ekleyerek `kind ="dynamicEndpoint"` özniteliği için uç nokta yapılandırma öğesi.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kapsamlarla Bulma](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [Zaman Uyumsuz Bulma](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)  
 [Temel](../../../../docs/framework/wcf/samples/basic-sample.md)
