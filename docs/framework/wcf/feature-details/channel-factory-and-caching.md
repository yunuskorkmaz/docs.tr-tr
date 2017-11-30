---
title: "Kanal Fabrikası ve Önbelleğe Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 137696547619477dd68ead5ecfa3f3de7af44727
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="22c71-102">Kanal Fabrikası ve Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="22c71-102">Channel Factory and Caching</span></span>
<span data-ttu-id="22c71-103">WCF istemci uygulamalarını kullanan <xref:System.ServiceModel.ChannelFactory%601> bir WCF Hizmeti ile bir iletişim kanalı oluşturmak için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="22c71-103">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="22c71-104">Oluşturma <xref:System.ServiceModel.ChannelFactory%601> örnekleri aşağıdaki işlemleri içerdiğinden bazı ek yük doğurur:</span><span class="sxs-lookup"><span data-stu-id="22c71-104">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>  
  
-   <span data-ttu-id="22c71-105">Oluşturma <xref:System.ServiceModel.Description.ContractDescription> ağacı</span><span class="sxs-lookup"><span data-stu-id="22c71-105">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>  
  
-   <span data-ttu-id="22c71-106">Tüm gerekli CLR Türleri yansıtma</span><span class="sxs-lookup"><span data-stu-id="22c71-106">Reflecting all of the required CLR types</span></span>  
  
-   <span data-ttu-id="22c71-107">Kanal yığın oluşturma</span><span class="sxs-lookup"><span data-stu-id="22c71-107">Constructing the channel stack</span></span>  
  
-   <span data-ttu-id="22c71-108">Kaynaklarını atma</span><span class="sxs-lookup"><span data-stu-id="22c71-108">Disposing of resources</span></span>  
  
 <span data-ttu-id="22c71-109">WCF bu yükünü en aza indirmek için bir WCF istemcisi proxy kullanılırken kanal fabrikaları önbelleğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="22c71-109">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="22c71-110">Kullandığınızda kanal fabrikası oluşturma doğrudan denetime sahip <xref:System.ServiceModel.ChannelFactory%601> doğrudan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="22c71-110">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>  
  
 <span data-ttu-id="22c71-111">WCF istemci proxy'leri ile oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) türetilmiş <xref:System.ServiceModel.ClientBase%601>.</span><span class="sxs-lookup"><span data-stu-id="22c71-111">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <span data-ttu-id="22c71-112"><xref:System.ServiceModel.ClientBase%601>statik tanımlar <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> kanal fabrikası önbelleğe alma davranışını tanımlayan özelliği.</span><span class="sxs-lookup"><span data-stu-id="22c71-112"><xref:System.ServiceModel.ClientBase%601> defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="22c71-113">Önbellek ayarları, belirli bir türü için yapılır.</span><span class="sxs-lookup"><span data-stu-id="22c71-113">Cache settings are made for a specific type.</span></span> <span data-ttu-id="22c71-114">Örneğin, ayarlama `ClientBase<ITest>.CacheSettings` aşağıda tanımlanan değerlerden biri için yalnızca bu proxy/ClientBase türü etkiler `ITest`.</span><span class="sxs-lookup"><span data-stu-id="22c71-114">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="22c71-115">Belirli bir önbellek ayarını <xref:System.ServiceModel.ClientBase%601> ilk proxy/ClientBase örneği oluşturulduktan hemen sabittir.</span><span class="sxs-lookup"><span data-stu-id="22c71-115">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>  
  
## <a name="specifying-caching-behavior"></a><span data-ttu-id="22c71-116">Önbelleğe alma davranışını belirtme</span><span class="sxs-lookup"><span data-stu-id="22c71-116">Specifying Caching Behavior</span></span>  
 <span data-ttu-id="22c71-117">Önbelleğe alma davranışı belirtilen ayarlayarak <xref:System.ServiceModel.ClientBase%601.CacheSetting> özelliğini aşağıdaki değerlerden birine.</span><span class="sxs-lookup"><span data-stu-id="22c71-117">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>  
  
|<span data-ttu-id="22c71-118">Değer ayarını önbelleği</span><span class="sxs-lookup"><span data-stu-id="22c71-118">Cache Setting Value</span></span>|<span data-ttu-id="22c71-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="22c71-119">Description</span></span>|  
|-------------------------|-----------------|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="22c71-120">Tüm örneklerini <xref:System.ServiceModel.ClientBase%601> önbelleğe alma app-etki alanı içinde katılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22c71-120">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="22c71-121">Geliştirici, önbelleğe alma için hiçbir olumsuz güvenlik uygulamalarını olduğunu belirledi.</span><span class="sxs-lookup"><span data-stu-id="22c71-121">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="22c71-122">Önbelleğe alma değil açık devre dışı "güvenlik açısından duyarlı ise" bile özellikleri <xref:System.ServiceModel.ClientBase%601> erişilir.</span><span class="sxs-lookup"><span data-stu-id="22c71-122">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="22c71-123">"Güvenlik açısından duyarlı" özelliklerini <xref:System.ServiceModel.ClientBase%601> olan <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> ve <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span><span class="sxs-lookup"><span data-stu-id="22c71-123">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="22c71-124">Yalnızca örneklerini <xref:System.ServiceModel.ClientBase%601> dosyaları katılmak app-etki alanı içinde önbelleğe alma yapılandırmasında tanımlı uç noktaları oluşturulduğu.</span><span class="sxs-lookup"><span data-stu-id="22c71-124">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="22c71-125">Tüm örneklerini <xref:System.ServiceModel.ClientBase%601> program aracılığıyla içinde oluşturulan bu uygulama etki alanı önbelleğe alma içinde yer almaz.</span><span class="sxs-lookup"><span data-stu-id="22c71-125">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="22c71-126">Ayrıca, önbelleğe alma örneği için devre dışı bırakılacak <xref:System.ServiceModel.ClientBase%601> "güvenlik açısından duyarlı" özelliklerinden birini erişildiğinde sonra.</span><span class="sxs-lookup"><span data-stu-id="22c71-126">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="22c71-127">Önbelleğe alma kapatıldı tüm örnekleri için <xref:System.ServiceModel.ClientBase%601> uygulama etki alanı söz konusu içinde belirli bir türde.</span><span class="sxs-lookup"><span data-stu-id="22c71-127">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|  
  
 <span data-ttu-id="22c71-128">Aşağıdaki kod parçacıkları nasıl kullanılacağını göstermek <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="22c71-128">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>  
  
```  
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
  
 <span data-ttu-id="22c71-129">Yukarıdaki kodda, tüm örneklerini `TestClient` aynı kanal fabrikası kullanır.</span><span class="sxs-lookup"><span data-stu-id="22c71-129">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>  
  
```  
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
  
 <span data-ttu-id="22c71-130">Tüm örneklerini yukarıdaki örnekte `TestClient` örneği #4 dışında aynı kanal fabrikası kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="22c71-130">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="22c71-131">Örnek #4 oluşturulan bir kanal fabrikası özellikle kullanımı için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="22c71-131">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="22c71-132">Bu ayar, burada özel bir uç nokta gereken diğer bitiş noktaları aynı kanal fabrikası türü farklı güvenlik ayarlarından senaryoları için çalışır (Bu durumda `ITest`).</span><span class="sxs-lookup"><span data-stu-id="22c71-132">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>  
  
```  
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
  
 <span data-ttu-id="22c71-133">Tüm örneklerini yukarıdaki örnekte `TestClient` farklı kanal fabrikaları kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="22c71-133">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="22c71-134">Bu, her bitiş farklı güvenlik gereksinimlerine sahip olduğunda ve hiçbir önbelleğine mantıklıdır yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="22c71-134">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22c71-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="22c71-135">See Also</span></span>  
 <xref:System.ServiceModel.ClientBase%601>  
 [<span data-ttu-id="22c71-136">İstemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="22c71-136">Building Clients</span></span>](../../../../docs/framework/wcf/building-clients.md)  
 [<span data-ttu-id="22c71-137">İstemciler</span><span class="sxs-lookup"><span data-stu-id="22c71-137">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)  
 [<span data-ttu-id="22c71-138">Bir WCF istemcisi kullanarak hizmetlere erişme</span><span class="sxs-lookup"><span data-stu-id="22c71-138">Accessing Services Using a WCF Client</span></span>](../../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 [<span data-ttu-id="22c71-139">Nasıl yapılır: ChannelFactory kullanma</span><span class="sxs-lookup"><span data-stu-id="22c71-139">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
