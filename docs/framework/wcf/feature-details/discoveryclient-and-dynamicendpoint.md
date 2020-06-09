---
title: DiscoveryClient ve DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 6144a3fb528e64fd55fa125b6254d415ec3e8b26
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599171"
---
# <a name="discoveryclient-and-dynamicendpoint"></a>DiscoveryClient ve DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient>ve <xref:System.ServiceModel.Discovery.DynamicEndpoint> istemci tarafında Hizmetleri aramak için kullanılan iki sınıftır. <xref:System.ServiceModel.Discovery.DiscoveryClient>belirli bir ölçüt kümesiyle eşleşen hizmetlerin listesini sağlar ve hizmetlere bağlanmanızı sağlar. <xref:System.ServiceModel.Discovery.DynamicEndpoint>aynı işlemi gerçekleştirir ve ek olarak, bulunan hizmetlerden birine otomatik olarak bağlanır. Herhangi bir uç nokta bir ile yapılabilir <xref:System.ServiceModel.Discovery.DynamicEndpoint> , arama ölçütleri de de eklenebilir, bu nedenle <xref:System.ServiceModel.Discovery.DynamicEndpoint> çözümünüzde bulmaya ihtiyacınız olduğunda ancak istemci mantığını değiştirmek istemediğinizde yararlı olur; yalnızca uç noktaları değiştirmeniz gerekir. <xref:System.ServiceModel.Discovery.DiscoveryClient>Diğer taraftan, arama işlemi üzerinde daha hassas denetim elde etmek için kullanılabilir. Her birinin kullanımları ve avantajları aşağıda ayrıntılı.  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 , <xref:System.ServiceModel.Discovery.DiscoveryClient> Zaman uyumlu ve zaman uyumsuz bulma yöntemlerini <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> ve <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> olaylarını tanımlar.  Ayrıca, zaman uyumlu ve zaman uyumsuz çözümleme yöntemlerini ve bir <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> olayı tanımlar. <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> Hizmet aramak için veya yöntemlerini kullanın. Bu yöntemlerin her ikisi de <xref:System.ServiceModel.Discovery.FindCriteria> sözleşme türü adlarını, kapsamları, istenen en fazla sonuç sayısını ve kapsam eşleştirme kurallarını belirtmenize olanak tanıyan bir örnek alır. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> Yöntemi çağrılırken ve olayları kullanılabilir <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> . <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>, <xref:System.ServiceModel.Discovery.DiscoveryClient> bir hizmetten her yanıt aldığında tetiklenir. Bul işleminin ilerleme durumunu gösteren bir ilerleme çubuğunu göstermek için kullanılabilir. Ayrıca, alındıkları yanıtları bulmaya çalışmak için de kullanılabilir. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted>Olay, bulma işlemi tamamlandığında tetiklenir. Bu durum, en fazla yanıt sayısı alındı veya <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> süresi geçtiğinde oluşabilir. Bulma işlemi tamamlandığında sonuçlar bir örnek içinde döndürülür <xref:System.ServiceModel.Discovery.FindResponse> . , <xref:System.ServiceModel.Discovery.FindResponse> <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> Eşleşen hizmetlerin adreslerini, sözleşme türü adlarını, uzantıları, dinleme URI 'lerini ve kapsamlarını içeren bir koleksiyon içerir. Daha sonra bu bilgileri kullanarak, eşleşen hizmetlerden birine bağlanabilir ve bu hizmetleri çağırabilirsiniz. Aşağıdaki örnek, System. ServiceModel. Discovery. DiscoveryClient. Find (System. ServiceModel. Discovery. FindCriteria) yönteminin nasıl çağrılacağını ve bulunan hizmeti çağırmak için döndürülen meta verileri nasıl kullanacağınızı gösterir. Kullanmanın bir avantajı <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> , bulduğunuz uç noktaların listesini önbelleğe alabilir ve bunları daha sonra kullanabilirsiniz. Bu önbellek ile çeşitli hata koşullarını işlemek için özel mantık oluşturabilirsiniz.  
  
```csharp
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
  
 Aşağıdaki örnek, bir bulma işleminin zaman uyumsuz olarak nasıl gerçekleştirileceğini gösterir.  
  
```csharp
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
  
 <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A>Ve yöntemlerini, <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> uç nokta adresini temel alarak bir hizmeti bulmak için kullanın. Bu, uç nokta adresi ağ adreslenebilir olmadığında yararlıdır. Resolve yöntemleri, <xref:System.ServiceModel.Discovery.ResolveCriteria> çözümlüğiniz hizmetin uç nokta adresini, çözüm işleminin en uzun süresini ve bir dizi uzantıyı belirtmenizi sağlayan bir örneğini alır. Aşağıdaki örnek, <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> bir hizmeti çözmek için yönteminin nasıl kullanılacağını gösterir.  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>, standart bir uç noktasıdır (daha fazla bilgi Için, bkz. bulma işlemini gerçekleştiren ve otomatik olarak eşleşen hizmeti seçen [standart uç noktalar](standard-endpoints.md)). Yalnızca arama yapmak için sözleşmede bir geçiş oluşturun ve <xref:System.ServiceModel.Discovery.DynamicEndpoint> kullanılacak bağlamayı ve <xref:System.ServiceModel.Discovery.DynamicEndpoint> örneği WCF istemcisine geçirin. Aşağıdaki örnek, <xref:System.ServiceModel.Discovery.DynamicEndpoint> hesap makinesi hizmetini çağırmak için oluşturma ve kullanma işlemlerinin nasıl yapılacağını gösterir. Bulma işlemi, istemci her açılışında gerçekleştirilir. Yapılandırma içinde tanımlı herhangi bir uç nokta, <xref:System.ServiceModel.Discovery.DynamicEndpoint> `kind ="dynamicEndpoint"` uç nokta yapılandırma öğesine özniteliği eklenerek de bir öğesine açılabilir.  
  
```csharp  
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

- [Kapsamlarla Bulma](../samples/discovery-with-scopes-sample.md)
- [Temel](../samples/basic-sample.md)
