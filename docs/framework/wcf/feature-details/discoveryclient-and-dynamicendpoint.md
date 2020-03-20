---
title: DiscoveryClient ve DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: c6d87a04a6787725ad7c4546650485af932882b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185188"
---
# <a name="discoveryclient-and-dynamicendpoint"></a>DiscoveryClient ve DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient>ve <xref:System.ServiceModel.Discovery.DynamicEndpoint> hizmetleri aramak için istemci tarafında kullanılan iki sınıftır. <xref:System.ServiceModel.Discovery.DiscoveryClient>belirli bir ölçüt kümesiyle eşleşen ve hizmetlere bağlanmanızı sağlayan hizmetlerin bir listesini sağlar. <xref:System.ServiceModel.Discovery.DynamicEndpoint>aynı işlemi gerçekleştirir ve ek olarak, bulunan hizmetlerden birine otomatik olarak bağlanır. Herhangi bir bitiş noktası <xref:System.ServiceModel.Discovery.DynamicEndpoint>içine yapılabilir , arama ölçütleri <xref:System.ServiceModel.Discovery.DynamicEndpoint> de yapılandırmada eklenebilir, bu nedenle çözüm bulma gerektiğinde yararlıdır ama istemci mantığı değiştirmek istemiyorum - sadece uç noktaları değiştirmek gerekir. <xref:System.ServiceModel.Discovery.DiscoveryClient>diğer taraftan arama işlemi üzerinde daha ince kontrol elde etmek için kullanılabilir. Her birinin kullanım ları ve yararları aşağıda ayrıntılı olarak verilmiştir.  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 Senkron <xref:System.ServiceModel.Discovery.DiscoveryClient> ve eşzamanlı Bul yöntemlerini <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> ve <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> olayları tanımlar.  Ayrıca senkron ve eşzamanlı Çözüm yöntemlerini ve <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> bir olayı tanımlar. Hizmetleri <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> aramak <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> için veya yöntemleri kullanın. Bu yöntemlerin her <xref:System.ServiceModel.Discovery.FindCriteria> ikisi de sözleşme türü adlarını, kapsamları, istenen en yüksek sonuç sayısını ve kapsam eşleştirme kurallarını belirtmenize olanak tanıyan bir örnek alır. Ve <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> olaylar <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> yöntemi ararken kullanılabilir. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>bir hizmetten <xref:System.ServiceModel.Discovery.DiscoveryClient> yanıt aldığında ateşlenir. Bulma işleminin ilerlemesini gösteren bir ilerleme çubuğu görüntülemek için kullanılabilir. Ayrıca, alınan yanıtları bulmak için de kullanılabilir. Bulma <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> işlemi tamamlandığında olay ateşlenir. Bu, en fazla yanıt sayısı alındığı veya <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> yanıtın geçmiş olması nedeniyle oluşabilir. Bulma işlemi tamamlandığında sonuçlar bir <xref:System.ServiceModel.Discovery.FindResponse> örnekte döndürülür. Bu <xref:System.ServiceModel.Discovery.FindResponse> koleksiyon, <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> eşleşen hizmetlerin adreslerini, sözleşme türü adlarını, uzantılarını, dinleme URL'lerini ve kapsamlarını içeren bir koleksiyon içerir. Daha sonra bu bilgileri eşleşen hizmetlerden birine bağlanmak ve aramak için kullanabilirsiniz. Aşağıdaki örnek, System.ServiceModel.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) yöntemini nasıl arayacağımı ve bulunan hizmeti aramak için döndürülen meta verileri nasıl kullanacağımı gösterir. Kullanmanın <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> bir yararı, bulduğunuz uç noktaların listesini önbelleğe alıp daha sonra kullanabilmektir. Bu önbellekle, çeşitli hata koşullarını işlemek için özel mantık oluşturabilirsiniz.  
  
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
  
 Aşağıdaki örnek, bir bulma işleminin nasıl eşzamanlı olarak gerçekleştirildirilebildiğini gösterir.  
  
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
  
 Bir <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> hizmeti <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> bitiş noktası adresine göre bulmak için ve yöntemleri kullanın. Bu, uç nokta adresi ağ adresi ne zaman kullanışlıdır. Çözümleme yöntemleri, çözümlediğiniz hizmetin bitiş noktası adresini, çözümleme işleminin maksimum süresini ve bir dizi uzantıkümesini belirtmenize olanak <xref:System.ServiceModel.Discovery.ResolveCriteria> tanıyan bir örnek alır. Aşağıdaki örnekte, bir <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> hizmeti çözümlemek için yöntemin nasıl kullanılacağı gösterilmektedir.  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>Dynamicendpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>bulma gerçekleştiren ve otomatik olarak eşleşen bir hizmeti seçen standart bir bitiş noktasıdır (Daha fazla bilgi için Standart [Uç Noktaları'na](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)bakın). Sadece aramak <xref:System.ServiceModel.Discovery.DynamicEndpoint> için sözleşmede bir geçiş oluşturmak ve kullanmak <xref:System.ServiceModel.Discovery.DynamicEndpoint> ve WCF istemcisine örnek geçmek için bağlayıcı. Aşağıdaki örnek, hesap makinesi hizmetini <xref:System.ServiceModel.Discovery.DynamicEndpoint> aramak için a'nın nasıl oluşturulacağı ve kullanılacağını gösterir. Bulma, istemci her açıldığında gerçekleştirilir. Yapılandırmada tanımlanan herhangi bir uç nokta, bitiş `kind ="dynamicEndpoint"` noktası yapılandırma öğesine öznitelik eklenerek de bir <xref:System.ServiceModel.Discovery.DynamicEndpoint> noktaya dönüştürülebilir.  
  
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

- [Kapsam ile Keşif](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [Temel](../../../../docs/framework/wcf/samples/basic-sample.md)
