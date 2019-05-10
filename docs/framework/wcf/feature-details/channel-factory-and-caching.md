---
title: Kanal Fabrikası ve Önbelleğe Alma
ms.date: 03/30/2017
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
ms.openlocfilehash: 94b3cb22c76a215944d044db0f4392005e49f2ad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645412"
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="01a10-102">Kanal Fabrikası ve Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="01a10-102">Channel Factory and Caching</span></span>
<span data-ttu-id="01a10-103">WCF istemci uygulamalarının kullanın <xref:System.ServiceModel.ChannelFactory%601> bir WCF Hizmeti ile bir iletişim kanalı oluşturmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="01a10-103">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="01a10-104">Oluşturma <xref:System.ServiceModel.ChannelFactory%601> örnekleri aşağıdaki işlemleri içerdiğinden bazı ek yük doğurur:</span><span class="sxs-lookup"><span data-stu-id="01a10-104">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>  
  
- <span data-ttu-id="01a10-105">Oluşturma <xref:System.ServiceModel.Description.ContractDescription> ağacı</span><span class="sxs-lookup"><span data-stu-id="01a10-105">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>  
  
- <span data-ttu-id="01a10-106">Tüm gerekli CLR Türleri yansıtma</span><span class="sxs-lookup"><span data-stu-id="01a10-106">Reflecting all of the required CLR types</span></span>  
  
- <span data-ttu-id="01a10-107">Kanal yığını oluşturma</span><span class="sxs-lookup"><span data-stu-id="01a10-107">Constructing the channel stack</span></span>  
  
- <span data-ttu-id="01a10-108">Kaynaklarını atma</span><span class="sxs-lookup"><span data-stu-id="01a10-108">Disposing of resources</span></span>  
  
 <span data-ttu-id="01a10-109">WCF bu ek yükü en aza indirmek için bir WCF istemci proxy kullanırken kanal fabrikaları önbelleğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="01a10-109">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="01a10-110">Kullanırken kanal fabrikası oluşturma doğrudan denetime sahip <xref:System.ServiceModel.ChannelFactory%601> doğrudan sınıf.</span><span class="sxs-lookup"><span data-stu-id="01a10-110">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>  
  
 <span data-ttu-id="01a10-111">Oluşturulan WCF istemci proxy'leri [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) türetilmiştir <xref:System.ServiceModel.ClientBase%601>.</span><span class="sxs-lookup"><span data-stu-id="01a10-111">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <span data-ttu-id="01a10-112"><xref:System.ServiceModel.ClientBase%601> statik tanımlar <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> kanal fabrikası önbelleğe alma davranışını tanımlayan özellik.</span><span class="sxs-lookup"><span data-stu-id="01a10-112"><xref:System.ServiceModel.ClientBase%601> defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="01a10-113">Belirli bir türü için önbellek ayarları yapılır.</span><span class="sxs-lookup"><span data-stu-id="01a10-113">Cache settings are made for a specific type.</span></span> <span data-ttu-id="01a10-114">Örneğin, ayarlamak `ClientBase<ITest>.CacheSettings` aşağıda tanımlanan değerlerden biri olarak yalnızca bu proxy/ClientBase türü etkiler `ITest`.</span><span class="sxs-lookup"><span data-stu-id="01a10-114">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="01a10-115">Belirli bir önbellek ayarını <xref:System.ServiceModel.ClientBase%601> ilk proxy/ClientBase örneği oluşturulduktan hemen sonra sabittir.</span><span class="sxs-lookup"><span data-stu-id="01a10-115">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>  
  
## <a name="specifying-caching-behavior"></a><span data-ttu-id="01a10-116">Önbelleğe alma davranışını belirtme</span><span class="sxs-lookup"><span data-stu-id="01a10-116">Specifying Caching Behavior</span></span>  
 <span data-ttu-id="01a10-117">Önbelleğe alma davranışını belirtilen ayarlayarak <xref:System.ServiceModel.ClientBase%601.CacheSetting> özelliğini şu değerlerden biri.</span><span class="sxs-lookup"><span data-stu-id="01a10-117">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>  
  
|<span data-ttu-id="01a10-118">Önbellek ayar değeri</span><span class="sxs-lookup"><span data-stu-id="01a10-118">Cache Setting Value</span></span>|<span data-ttu-id="01a10-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01a10-119">Description</span></span>|  
|-------------------------|-----------------|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="01a10-120">Tüm örneklerini <xref:System.ServiceModel.ClientBase%601> uygulama etki alanında önbelleğe katılabilir.</span><span class="sxs-lookup"><span data-stu-id="01a10-120">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="01a10-121">Geliştirici, önbelleğe alma için hiçbir olumsuz güvenlikle ilgili etkileri olduğunu belirledi.</span><span class="sxs-lookup"><span data-stu-id="01a10-121">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="01a10-122">Önbelleğe alma açık devre dışı bile "güvenlik açısından hassas" özellikleri <xref:System.ServiceModel.ClientBase%601> erişilir.</span><span class="sxs-lookup"><span data-stu-id="01a10-122">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="01a10-123">"Güvenlik açısından hassas" özelliklerini <xref:System.ServiceModel.ClientBase%601> olan <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> ve <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span><span class="sxs-lookup"><span data-stu-id="01a10-123">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="01a10-124">Yalnızca örneklerini <xref:System.ServiceModel.ClientBase%601> dosyaları katılmak uygulama etki alanında önbelleğe yapılandırmasında tanımlı uç noktalarından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="01a10-124">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="01a10-125">Tüm örneklerini <xref:System.ServiceModel.ClientBase%601> içinde program aracılığıyla oluşturulan bu uygulama etki alanı önbelleğe alırken katılmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="01a10-125">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="01a10-126">Ayrıca, önbelleğe alma bir örneği için devre dışı bırakılacak <xref:System.ServiceModel.ClientBase%601> "güvenlik açısından hassas" özelliklerinden birini erişilen sonra.</span><span class="sxs-lookup"><span data-stu-id="01a10-126">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="01a10-127">Önbelleğe alma devre dışı olduğundan tüm örnekleri için <xref:System.ServiceModel.ClientBase%601> belli bir türdeki app-etki alanı içinde söz konusu.</span><span class="sxs-lookup"><span data-stu-id="01a10-127">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|  
  
 <span data-ttu-id="01a10-128">Aşağıdaki kod parçacıkları nasıl kullanılacağını örneklendiren <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="01a10-128">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>  
  
```csharp  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase<ITest>.CacheSettings = CacheSettings.AlwaysOn;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient (new BasicHttpBinding(), new EndpointAddress(address)))   
         {   
            // ...  
            proxy.Test(msg);   
            // ...  
         }   
      }   
   }   
}  
// Generated by SvcUtil.exe     
public partial class TestClient : System.ServiceModel.ClientBase, ITest { }  
```  
  
 <span data-ttu-id="01a10-129">Yukarıdaki kodda, tüm örneklerini `TestClient` aynı kanal fabrikası kullanır.</span><span class="sxs-lookup"><span data-stu-id="01a10-129">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>  
  
```csharp  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase.CacheSettings = CacheSettings.Default;   
      int i = 1;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))   
         {   
            if (i == 4)   
            {   
               ServiceEndpoint endpoint = proxy.Endpoint;   
               ... // use endpoint in some way   
            }   
            proxy.Test(msg);   
         }   
         i++;   
   }   
}   
  
// Generated by SvcUtil.exe     
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}  
```  
  
 <span data-ttu-id="01a10-130">Tüm örneklerini yukarıdaki örnekte `TestClient` örneği #4 dışında aynı kanal fabrikası kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="01a10-130">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="01a10-131">#4 örneği oluşturulan kanal fabrikası kullanımına özellikle kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="01a10-131">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="01a10-132">Bu ayar, belirli bir uç noktası diğer uç noktalar aynı kanal fabrikası türde farklı güvenlik ayarlarından gereken yere senaryoları için işe yarar (Bu durumda `ITest`).</span><span class="sxs-lookup"><span data-stu-id="01a10-132">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>  
  
```csharp  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase.CacheSettings = CacheSettings.AlwaysOff;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))   
         {   
            proxy.Test(msg);   
         }           
      }   
   }  
}  
  
// Generated by SvcUtil.exe   
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}  
```  
  
 <span data-ttu-id="01a10-133">Tüm örneklerini yukarıdaki örnekte `TestClient` farklı kanal fabrikaları kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="01a10-133">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="01a10-134">Bu, her bir uç nokta farklı güvenlik gereksinimlerine sahip olduğunda ve önbellek için hiçbir mantıklı kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="01a10-134">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01a10-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01a10-135">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="01a10-136">İstemci Derleme</span><span class="sxs-lookup"><span data-stu-id="01a10-136">Building Clients</span></span>](../../../../docs/framework/wcf/building-clients.md)
- [<span data-ttu-id="01a10-137">İstemciler</span><span class="sxs-lookup"><span data-stu-id="01a10-137">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)
- [<span data-ttu-id="01a10-138">WCF İstemcisi Kullanarak Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="01a10-138">Accessing Services Using a WCF Client</span></span>](../../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="01a10-139">Nasıl yapılır: ChannelFactory kullanma</span><span class="sxs-lookup"><span data-stu-id="01a10-139">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
