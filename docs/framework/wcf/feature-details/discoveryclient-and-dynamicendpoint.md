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
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="ace38-102">DiscoveryClient ve DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="ace38-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="ace38-103"><xref:System.ServiceModel.Discovery.DiscoveryClient>ve <xref:System.ServiceModel.Discovery.DynamicEndpoint> hizmetleri aramak için istemci tarafında kullanılan iki sınıftır.</span><span class="sxs-lookup"><span data-stu-id="ace38-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="ace38-104"><xref:System.ServiceModel.Discovery.DiscoveryClient>belirli bir ölçüt kümesiyle eşleşen ve hizmetlere bağlanmanızı sağlayan hizmetlerin bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ace38-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="ace38-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint>aynı işlemi gerçekleştirir ve ek olarak, bulunan hizmetlerden birine otomatik olarak bağlanır.</span><span class="sxs-lookup"><span data-stu-id="ace38-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="ace38-106">Herhangi bir bitiş noktası <xref:System.ServiceModel.Discovery.DynamicEndpoint>içine yapılabilir , arama ölçütleri <xref:System.ServiceModel.Discovery.DynamicEndpoint> de yapılandırmada eklenebilir, bu nedenle çözüm bulma gerektiğinde yararlıdır ama istemci mantığı değiştirmek istemiyorum - sadece uç noktaları değiştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="ace38-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="ace38-107"><xref:System.ServiceModel.Discovery.DiscoveryClient>diğer taraftan arama işlemi üzerinde daha ince kontrol elde etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ace38-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="ace38-108">Her birinin kullanım ları ve yararları aşağıda ayrıntılı olarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ace38-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="ace38-109">DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="ace38-109">DiscoveryClient</span></span>  
 <span data-ttu-id="ace38-110">Senkron <xref:System.ServiceModel.Discovery.DiscoveryClient> ve eşzamanlı Bul yöntemlerini <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> ve <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> olayları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ace38-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="ace38-111">Ayrıca senkron ve eşzamanlı Çözüm yöntemlerini ve <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> bir olayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ace38-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="ace38-112">Hizmetleri <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> aramak <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> için veya yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="ace38-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="ace38-113">Bu yöntemlerin her <xref:System.ServiceModel.Discovery.FindCriteria> ikisi de sözleşme türü adlarını, kapsamları, istenen en yüksek sonuç sayısını ve kapsam eşleştirme kurallarını belirtmenize olanak tanıyan bir örnek alır.</span><span class="sxs-lookup"><span data-stu-id="ace38-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="ace38-114">Ve <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> olaylar <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> yöntemi ararken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ace38-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="ace38-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>bir hizmetten <xref:System.ServiceModel.Discovery.DiscoveryClient> yanıt aldığında ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="ace38-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="ace38-116">Bulma işleminin ilerlemesini gösteren bir ilerleme çubuğu görüntülemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ace38-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="ace38-117">Ayrıca, alınan yanıtları bulmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ace38-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="ace38-118">Bulma <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> işlemi tamamlandığında olay ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="ace38-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="ace38-119">Bu, en fazla yanıt sayısı alındığı veya <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> yanıtın geçmiş olması nedeniyle oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="ace38-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="ace38-120">Bulma işlemi tamamlandığında sonuçlar bir <xref:System.ServiceModel.Discovery.FindResponse> örnekte döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ace38-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="ace38-121">Bu <xref:System.ServiceModel.Discovery.FindResponse> koleksiyon, <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> eşleşen hizmetlerin adreslerini, sözleşme türü adlarını, uzantılarını, dinleme URL'lerini ve kapsamlarını içeren bir koleksiyon içerir.</span><span class="sxs-lookup"><span data-stu-id="ace38-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="ace38-122">Daha sonra bu bilgileri eşleşen hizmetlerden birine bağlanmak ve aramak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ace38-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="ace38-123">Aşağıdaki örnek, System.ServiceModel.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) yöntemini nasıl arayacağımı ve bulunan hizmeti aramak için döndürülen meta verileri nasıl kullanacağımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ace38-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="ace38-124">Kullanmanın <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> bir yararı, bulduğunuz uç noktaların listesini önbelleğe alıp daha sonra kullanabilmektir.</span><span class="sxs-lookup"><span data-stu-id="ace38-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="ace38-125">Bu önbellekle, çeşitli hata koşullarını işlemek için özel mantık oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ace38-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
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
  
 <span data-ttu-id="ace38-126">Aşağıdaki örnek, bir bulma işleminin nasıl eşzamanlı olarak gerçekleştirildirilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ace38-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
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
  
 <span data-ttu-id="ace38-127">Bir <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> hizmeti <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> bitiş noktası adresine göre bulmak için ve yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="ace38-127">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="ace38-128">Bu, uç nokta adresi ağ adresi ne zaman kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="ace38-128">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="ace38-129">Çözümleme yöntemleri, çözümlediğiniz hizmetin bitiş noktası adresini, çözümleme işleminin maksimum süresini ve bir dizi uzantıkümesini belirtmenize olanak <xref:System.ServiceModel.Discovery.ResolveCriteria> tanıyan bir örnek alır.</span><span class="sxs-lookup"><span data-stu-id="ace38-129">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="ace38-130">Aşağıdaki örnekte, bir <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> hizmeti çözümlemek için yöntemin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ace38-130">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="ace38-131">Dynamicendpoint</span><span class="sxs-lookup"><span data-stu-id="ace38-131">DynamicEndpoint</span></span>  
 <span data-ttu-id="ace38-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint>bulma gerçekleştiren ve otomatik olarak eşleşen bir hizmeti seçen standart bir bitiş noktasıdır (Daha fazla bilgi için Standart [Uç Noktaları'na](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)bakın).</span><span class="sxs-lookup"><span data-stu-id="ace38-132"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="ace38-133">Sadece aramak <xref:System.ServiceModel.Discovery.DynamicEndpoint> için sözleşmede bir geçiş oluşturmak ve kullanmak <xref:System.ServiceModel.Discovery.DynamicEndpoint> ve WCF istemcisine örnek geçmek için bağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="ace38-133">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="ace38-134">Aşağıdaki örnek, hesap makinesi hizmetini <xref:System.ServiceModel.Discovery.DynamicEndpoint> aramak için a'nın nasıl oluşturulacağı ve kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ace38-134">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="ace38-135">Bulma, istemci her açıldığında gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ace38-135">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="ace38-136">Yapılandırmada tanımlanan herhangi bir uç nokta, bitiş `kind ="dynamicEndpoint"` noktası yapılandırma öğesine öznitelik eklenerek de bir <xref:System.ServiceModel.Discovery.DynamicEndpoint> noktaya dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="ace38-136">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ace38-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ace38-137">See also</span></span>

- [<span data-ttu-id="ace38-138">Kapsam ile Keşif</span><span class="sxs-lookup"><span data-stu-id="ace38-138">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="ace38-139">Temel</span><span class="sxs-lookup"><span data-stu-id="ace38-139">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)
