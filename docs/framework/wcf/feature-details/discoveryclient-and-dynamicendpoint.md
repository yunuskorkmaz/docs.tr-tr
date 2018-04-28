---
title: DiscoveryClient ve DynamicEndpoint
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c652e58b20a6fe836e647ed07c6a84328ee4631e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="discoveryclient-and-dynamicendpoint"></a><span data-ttu-id="799cc-102">DiscoveryClient ve DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="799cc-102">DiscoveryClient and DynamicEndpoint</span></span>
<span data-ttu-id="799cc-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> ve <xref:System.ServiceModel.Discovery.DynamicEndpoint> istemci tarafında Hizmetleri aramak için kullanılan iki sınıf.</span><span class="sxs-lookup"><span data-stu-id="799cc-103"><xref:System.ServiceModel.Discovery.DiscoveryClient> and <xref:System.ServiceModel.Discovery.DynamicEndpoint> are two classes used on the client side to search for services.</span></span> <span data-ttu-id="799cc-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> belirli bir eşleşen hizmetlerin listesini sizinle ölçütünü ayarlamak ve hizmetlere bağlanmanıza olanak sağlayan sağlar.</span><span class="sxs-lookup"><span data-stu-id="799cc-104"><xref:System.ServiceModel.Discovery.DiscoveryClient> provides you with a list of services that match a specific set of criteria and allows you to connect to the services.</span></span> <span data-ttu-id="799cc-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> aynı işlemi gerçekleştirir ve otomatik olarak bağlanır bulundu hizmetlerden biri için ek olarak.</span><span class="sxs-lookup"><span data-stu-id="799cc-105"><xref:System.ServiceModel.Discovery.DynamicEndpoint> performs the same operation and in addition, automatically connects to one of the services that was found.</span></span> <span data-ttu-id="799cc-106">Herhangi bir uç nokta içine yapılabilir bir <xref:System.ServiceModel.Discovery.DynamicEndpoint>, arama ölçütlerini de yapılandırması, bu nedenle eklenebilir <xref:System.ServiceModel.Discovery.DynamicEndpoint> yararlı olduğunda bulma çözümünüzde gerekir, ancak istemci mantığı değiştirmek istiyor musunuz – uç noktalarını değiştirmek yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="799cc-106">Any endpoint can be made into a <xref:System.ServiceModel.Discovery.DynamicEndpoint>, the search criteria can also be added in configuration, thus <xref:System.ServiceModel.Discovery.DynamicEndpoint> is useful when you need discovery in your solution but do not want to modify the client logic – you only need to modify the endpoints.</span></span> <span data-ttu-id="799cc-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> Öte yandan, arama işlemi üzerinde daha hassas denetim kazanmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="799cc-107"><xref:System.ServiceModel.Discovery.DiscoveryClient> on the other hand can be used to gain finer control over your search operation.</span></span> <span data-ttu-id="799cc-108">Kullanır ve her birinin avantajları aşağıda ayrıntılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="799cc-108">The uses and benefits of each are elaborated below.</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="799cc-109">DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="799cc-109">DiscoveryClient</span></span>  
 <span data-ttu-id="799cc-110"><xref:System.ServiceModel.Discovery.DiscoveryClient> Zaman uyumlu ve zaman uyumsuz bulma yöntemleri tanımlar <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> ve <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> olaylar.</span><span class="sxs-lookup"><span data-stu-id="799cc-110">The <xref:System.ServiceModel.Discovery.DiscoveryClient> defines synchronous and asynchronous Find methods, <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events.</span></span>  <span data-ttu-id="799cc-111">Zaman uyumlu ve zaman uyumsuz Çözümleme yöntemleri de tanımlar ve <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> olay.</span><span class="sxs-lookup"><span data-stu-id="799cc-111">It also defines synchronous and asynchronous Resolve methods and a <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> event.</span></span> <span data-ttu-id="799cc-112">Kullanım <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> veya <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> Hizmetleri aramak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="799cc-112">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> or <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> methods to search for services.</span></span> <span data-ttu-id="799cc-113">Bu yöntemlerin her ikisi de ele bir <xref:System.ServiceModel.Discovery.FindCriteria> sözleşme tür adları, kapsamları, istenen sonuçlarının maksimum sayısını belirtmenize olanak tanır örneği ve eşleştirme kuralları kapsamı.</span><span class="sxs-lookup"><span data-stu-id="799cc-113">Both of these methods take a <xref:System.ServiceModel.Discovery.FindCriteria> instance that allows you to specify contract type names, scopes, maximum number of results requested, and scope matching rules.</span></span> <span data-ttu-id="799cc-114"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> Ve <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> çağrılırken olayları kullanılabilir <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="799cc-114">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> and <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> events can be used when calling the <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method.</span></span> <span data-ttu-id="799cc-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> Her tetiklenir <xref:System.ServiceModel.Discovery.DiscoveryClient> bir hizmetinden bir yanıt alır.</span><span class="sxs-lookup"><span data-stu-id="799cc-115"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> is fired whenever the <xref:System.ServiceModel.Discovery.DiscoveryClient> receives a response from a service.</span></span> <span data-ttu-id="799cc-116">Bir ilerleme çubuğu bulma işleminin ilerleme durumunu gösteren görüntülemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="799cc-116">It can be used to display a progress bar showing the progress of the find operation.</span></span> <span data-ttu-id="799cc-117">Ayrıca, bulma yanıtları alındıkları olarak hareket edecek de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="799cc-117">It can also be used to act on find responses as they are received.</span></span> <span data-ttu-id="799cc-118"><xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> Bulma işlemi tamamlandığında olay tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="799cc-118">The <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is fired when the find operation completes.</span></span> <span data-ttu-id="799cc-119">Bu yanıt maksimum sayısı aldığından veya varsa ortaya çıkabilir <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> geçti.</span><span class="sxs-lookup"><span data-stu-id="799cc-119">This may happen because the maximum number of responses has been received or if the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed.</span></span> <span data-ttu-id="799cc-120">Bulma işlemi tamamlandığında sonuçları döndürülür bir <xref:System.ServiceModel.Discovery.FindResponse> örneği.</span><span class="sxs-lookup"><span data-stu-id="799cc-120">When the find operation completes the results are returned in a <xref:System.ServiceModel.Discovery.FindResponse> instance.</span></span> <span data-ttu-id="799cc-121"><xref:System.ServiceModel.Discovery.FindResponse> Oluşan bir koleksiyon içeren <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> adresleri, sözleşme tür adları, uzantılar, dinleme URI'ler ve eşleşen hizmetleri kapsamını içerir.</span><span class="sxs-lookup"><span data-stu-id="799cc-121">The <xref:System.ServiceModel.Discovery.FindResponse> contains a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> which contains the addresses, contract type names, extensions, listen URIs, and scopes of the matching services.</span></span> <span data-ttu-id="799cc-122">Bu bilgiler daha sonra bağlanmak ve eşleşen hizmetlerden biri çağırmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="799cc-122">You can then use this information to connect to and call one of the matching services.</span></span> <span data-ttu-id="799cc-123">Aşağıdaki örnek System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) yöntemini çağırın ve bulunan hizmetini çağırmak için döndürülen meta veri nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="799cc-123">The following example shows how to call the System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria) method and use the returned metadata to call the found service.</span></span> <span data-ttu-id="799cc-124">Kullanmanın bir avantajı <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> olan buldunuz ve daha sonraki bir zamanda kullanmak bitiş noktaları listesini önbelleğe alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="799cc-124">A benefit of using <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> is that you can cache the list of endpoints you’ve found and use them at a later time.</span></span> <span data-ttu-id="799cc-125">Bu önbellek ile çeşitli hatası koşullarını işlemek için Özel mantık oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="799cc-125">With this cache, you can build custom logic to handle various failure conditions.</span></span>  
  
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
  
 <span data-ttu-id="799cc-126">Aşağıdaki örnek, bir bulma işlemi gerçekleştirip gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="799cc-126">The following example shows how to perform a find operation asynchronously.</span></span>  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="799cc-127"> zaman uyumsuz hale çağrıları bulmak için bkz [zaman uyumsuz bulma](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md).</span><span class="sxs-lookup"><span data-stu-id="799cc-127"> making asynchronous find calls, see [Asynchronous Find](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md).</span></span>  
  
 <span data-ttu-id="799cc-128">Kullanım <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> ve <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> bir hizmeti bulmak için yöntemleri temel uç nokta adresine.</span><span class="sxs-lookup"><span data-stu-id="799cc-128">Use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> and <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> methods to locate a service based on its endpoint address.</span></span> <span data-ttu-id="799cc-129">Uç nokta adresi adreslenebilir ağ olmadığında kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="799cc-129">This is useful when the endpoint address is not network addressable.</span></span> <span data-ttu-id="799cc-130">Çözümleme yöntemleri bir örneği ele <xref:System.ServiceModel.Discovery.ResolveCriteria> , çözümleme, çözümleme işlemi en uzun süresi ve uzantılar kümesi, hizmet uç noktası adresi belirtme sağlar.</span><span class="sxs-lookup"><span data-stu-id="799cc-130">The Resolve methods take an instance of <xref:System.ServiceModel.Discovery.ResolveCriteria> which allows you to specify the endpoint address of the service you are resolving, the maximum duration of the resolve operation, and a set of extensions.</span></span> <span data-ttu-id="799cc-131">Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> bir hizmeti çözümlemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="799cc-131">The following example shows how to use the <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> method to resolve a service.</span></span>  
  
```  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a><span data-ttu-id="799cc-132">DynamicEndpoint</span><span class="sxs-lookup"><span data-stu-id="799cc-132">DynamicEndpoint</span></span>  
 <span data-ttu-id="799cc-133"><xref:System.ServiceModel.Discovery.DynamicEndpoint> Standart uç noktası (daha fazla bilgi için bkz: [standart uç noktaları](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) bulma işlemini gerçekleştirir ve eşleşen hizmet otomatik olarak seçer.</span><span class="sxs-lookup"><span data-stu-id="799cc-133"><xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint (For more information, see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) which performs discovery and automatically selects a matching service.</span></span> <span data-ttu-id="799cc-134">Yalnızca oluşturmanız bir <xref:System.ServiceModel.Discovery.DynamicEndpoint> aramak ve kullanın ve geçirmek için bağlama sözleşmesindeki geçirme <xref:System.ServiceModel.Discovery.DynamicEndpoint> WCF istemcisini örneğine.</span><span class="sxs-lookup"><span data-stu-id="799cc-134">Just create a <xref:System.ServiceModel.Discovery.DynamicEndpoint> passing in the contract to search for and the binding to use and pass the <xref:System.ServiceModel.Discovery.DynamicEndpoint> instance to the WCF client.</span></span> <span data-ttu-id="799cc-135">Aşağıdaki örnekte, oluşturma ve kullanma gösterilmektedir bir <xref:System.ServiceModel.Discovery.DynamicEndpoint> hesaplayıcı hizmetini çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="799cc-135">The following example shows how to create and use a <xref:System.ServiceModel.Discovery.DynamicEndpoint> to call the calculator service.</span></span> <span data-ttu-id="799cc-136">İstemci her açıldığında bulma gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="799cc-136">The discovery is performed every time the client is opened.</span></span> <span data-ttu-id="799cc-137">Yapılandırmada tanımlanan herhangi bir uç nokta da dönüştürülebilir bir <xref:System.ServiceModel.Discovery.DynamicEndpoint> ekleyerek `kind ="dynamicEndpoint"` özniteliği için uç nokta yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="799cc-137">Any endpoint defined in configuration can also be turned into a <xref:System.ServiceModel.Discovery.DynamicEndpoint> by adding the `kind ="dynamicEndpoint"` attribute to the endpoint configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="799cc-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="799cc-138">See Also</span></span>  
 [<span data-ttu-id="799cc-139">Kapsamlarla Bulma</span><span class="sxs-lookup"><span data-stu-id="799cc-139">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [<span data-ttu-id="799cc-140">Zaman Uyumsuz Bulma</span><span class="sxs-lookup"><span data-stu-id="799cc-140">Asynchronous Find</span></span>](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)  
 [<span data-ttu-id="799cc-141">Temel</span><span class="sxs-lookup"><span data-stu-id="799cc-141">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)
