---
description: 'Daha fazla bilgi edinin: Kanal fabrikası ve önbelleğe alma'
title: Kanal Fabrikası ve Önbelleğe Alma
ms.date: 03/30/2017
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
ms.openlocfilehash: 6922191c2b99dea516d0e85aac9ed7bc12a67b81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705206"
---
# <a name="channel-factory-and-caching"></a><span data-ttu-id="799b6-103">Kanal Fabrikası ve Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="799b6-103">Channel Factory and Caching</span></span>

<span data-ttu-id="799b6-104">WCF istemci uygulamaları, <xref:System.ServiceModel.ChannelFactory%601> BIR WCF hizmeti ile iletişim kanalı oluşturmak için sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="799b6-104">WCF client applications use the <xref:System.ServiceModel.ChannelFactory%601> class to create a communication channel with a WCF service.</span></span>  <span data-ttu-id="799b6-105"><xref:System.ServiceModel.ChannelFactory%601>Aşağıdaki işlemleri içerdiğinden örnek oluşturma bazı ek yük doğurur:</span><span class="sxs-lookup"><span data-stu-id="799b6-105">Creating <xref:System.ServiceModel.ChannelFactory%601> instances incurs some overhead because it involves the following operations:</span></span>

- <span data-ttu-id="799b6-106">Ağacı oluşturma <xref:System.ServiceModel.Description.ContractDescription></span><span class="sxs-lookup"><span data-stu-id="799b6-106">Constructing the <xref:System.ServiceModel.Description.ContractDescription> tree</span></span>

- <span data-ttu-id="799b6-107">Tüm gerekli CLR türlerini yansıtma</span><span class="sxs-lookup"><span data-stu-id="799b6-107">Reflecting all of the required CLR types</span></span>

- <span data-ttu-id="799b6-108">Kanal yığınını oluşturma</span><span class="sxs-lookup"><span data-stu-id="799b6-108">Constructing the channel stack</span></span>

- <span data-ttu-id="799b6-109">Kaynakları elden atma</span><span class="sxs-lookup"><span data-stu-id="799b6-109">Disposing of resources</span></span>

<span data-ttu-id="799b6-110">Bu ek yükü en aza indirmenize yardımcı olmak için WCF istemci ara sunucusu kullanırken WCF kanal fabrikalarını önbelleğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="799b6-110">To help minimize this overhead, WCF can cache channel factories when you are using a WCF client proxy.</span></span>

> [!TIP]
> <span data-ttu-id="799b6-111">Sınıfını doğrudan kullandığınızda kanal fabrikası oluşturma üzerinde doğrudan denetiminiz vardır <xref:System.ServiceModel.ChannelFactory%601> .</span><span class="sxs-lookup"><span data-stu-id="799b6-111">You have direct control over channel factory creation when you use the <xref:System.ServiceModel.ChannelFactory%601> class directly.</span></span>

<span data-ttu-id="799b6-112">[ServiceModel meta veri yardımcı aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) Ile oluşturulan WCF istemci proxy 'leri, öğesinden türetilir <xref:System.ServiceModel.ClientBase%601> .</span><span class="sxs-lookup"><span data-stu-id="799b6-112">WCF client proxies generated with [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) are derived from <xref:System.ServiceModel.ClientBase%601>.</span></span> <span data-ttu-id="799b6-113"><xref:System.ServiceModel.ClientBase%601><xref:System.ServiceModel.ClientBase%601.CacheSetting%2A>kanal fabrikası önbelleğe alma davranışını tanımlayan bir statik özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="799b6-113"><xref:System.ServiceModel.ClientBase%601> defines a static <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property that defines channel factory caching behavior.</span></span> <span data-ttu-id="799b6-114">Belirli bir tür için önbellek ayarları yapılır.</span><span class="sxs-lookup"><span data-stu-id="799b6-114">Cache settings are made for a specific type.</span></span> <span data-ttu-id="799b6-115">Örneğin,  `ClientBase<ITest>.CacheSettings` aşağıda tanımlanan değerlerden birine ayarlandığında yalnızca türünün proxy/ClientBase değeri etkilenir `ITest` .</span><span class="sxs-lookup"><span data-stu-id="799b6-115">For example, setting  `ClientBase<ITest>.CacheSettings` to one of the values defined below will affect only those proxy/ClientBase of type `ITest`.</span></span> <span data-ttu-id="799b6-116"><xref:System.ServiceModel.ClientBase%601>İlk proxy/ClientBase örneği oluşturulduktan hemen sonra, belirli bir için önbellek ayarı sabittir.</span><span class="sxs-lookup"><span data-stu-id="799b6-116">The cache setting for a particular <xref:System.ServiceModel.ClientBase%601> is immutable as soon as the first proxy/ClientBase instance is created.</span></span>

## <a name="specifying-caching-behavior"></a><span data-ttu-id="799b6-117">Önbelleğe alma davranışını belirtme</span><span class="sxs-lookup"><span data-stu-id="799b6-117">Specifying Caching Behavior</span></span>

<span data-ttu-id="799b6-118">Önbelleğe alma davranışı, <xref:System.ServiceModel.ClientBase%601.CacheSetting> özelliği aşağıdaki değerlerden birine ayarlanarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="799b6-118">Caching behavior is specified by setting the <xref:System.ServiceModel.ClientBase%601.CacheSetting> property to one of the following values.</span></span>

|<span data-ttu-id="799b6-119">Önbellek ayarı değeri</span><span class="sxs-lookup"><span data-stu-id="799b6-119">Cache Setting Value</span></span>|<span data-ttu-id="799b6-120">Description</span><span class="sxs-lookup"><span data-stu-id="799b6-120">Description</span></span>|
|-------------------------|-----------------|
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|<span data-ttu-id="799b6-121"><xref:System.ServiceModel.ClientBase%601>Uygulama etki alanı içindeki tüm örnekleri önbelleğe alma işlemine katılabilir.</span><span class="sxs-lookup"><span data-stu-id="799b6-121">All instances of <xref:System.ServiceModel.ClientBase%601> within the app-domain can participate in caching.</span></span> <span data-ttu-id="799b6-122">Geliştirici, önbelleğe alma işleminin olumsuz güvenlik etkilerine sahip olmadığını belirledi.</span><span class="sxs-lookup"><span data-stu-id="799b6-122">The developer has determined that there are no adverse security implications to caching.</span></span> <span data-ttu-id="799b6-123">"Güvenliğe duyarlı" özelliklere erişilmesi durumunda bile önbelleğe alma devre dışı bırakılır <xref:System.ServiceModel.ClientBase%601> .</span><span class="sxs-lookup"><span data-stu-id="799b6-123">Caching will not be turned off even if "security-sensitive" properties on <xref:System.ServiceModel.ClientBase%601> are accessed.</span></span> <span data-ttu-id="799b6-124">' Nin "güvenlik duyarlı" özellikleri <xref:System.ServiceModel.ClientBase%601> <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> ve ' dir <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A> .</span><span class="sxs-lookup"><span data-stu-id="799b6-124">The "security-sensitive" properties of <xref:System.ServiceModel.ClientBase%601> are <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> and <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.</span></span>|
|<xref:System.ServiceModel.CacheSetting.Default>|<span data-ttu-id="799b6-125">Yalnızca <xref:System.ServiceModel.ClientBase%601> yapılandırma dosyalarında tanımlanan bitiş noktalarından oluşturulan örnekleri, uygulama etki alanı içinde önbelleğe almaya katılır.</span><span class="sxs-lookup"><span data-stu-id="799b6-125">Only instances of <xref:System.ServiceModel.ClientBase%601> created from endpoints defined in configuration files participate in caching within the app-domain.</span></span> <span data-ttu-id="799b6-126"><xref:System.ServiceModel.ClientBase%601>Bu uygulama etki alanı içinde programlı olarak oluşturulan tüm örnekleri, önbelleğe alma işlemine katılmaz.</span><span class="sxs-lookup"><span data-stu-id="799b6-126">Any instances of <xref:System.ServiceModel.ClientBase%601> created programmatically within that app-domain will not participate in caching.</span></span> <span data-ttu-id="799b6-127">Ayrıca, <xref:System.ServiceModel.ClientBase%601> "güvenliğe duyarlı" özelliklerden birine erişildiğinde bir örneği için önbelleğe alma devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="799b6-127">Also, caching will be disabled for an instance of <xref:System.ServiceModel.ClientBase%601> once any of its "security-sensitive" properties is accessed.</span></span>|
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|<span data-ttu-id="799b6-128">Bu, <xref:System.ServiceModel.ClientBase%601> söz konusu App-Domain içindeki belirli bir türün tüm örnekleri için önbelleğe alma kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="799b6-128">Caching is turned off for all instances of <xref:System.ServiceModel.ClientBase%601> of a particular type within the app-domain in question.</span></span>|

<span data-ttu-id="799b6-129">Aşağıdaki kod parçacıkları, özelliğinin nasıl kullanılacağını gösterir <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> .</span><span class="sxs-lookup"><span data-stu-id="799b6-129">The following code snippets illustrate how to use the <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> property.</span></span>

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

<span data-ttu-id="799b6-130">Yukarıdaki kodda, tüm örnekleri `TestClient` aynı kanal fabrikasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="799b6-130">In the above code, all instances of `TestClient` will use the same channel factory.</span></span>

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

<span data-ttu-id="799b6-131">Yukarıdaki örnekte, öğesinin tüm örnekleri, `TestClient` örnek #4 dışında aynı kanal fabrikası kullanır.</span><span class="sxs-lookup"><span data-stu-id="799b6-131">In the example above, all instances of `TestClient` would use the same channel factory except instance #4.</span></span> <span data-ttu-id="799b6-132">Örnek #4, kullanımı için özel olarak oluşturulan bir kanal fabrikası kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="799b6-132">Instance #4 would use a channel factory that is created specifically for its use.</span></span> <span data-ttu-id="799b6-133">Bu ayar, belirli bir uç noktanın aynı kanal fabrikası türünün diğer uç noktalarından farklı güvenlik ayarlarına ihtiyacı olan senaryolarda (Bu durumda `ITest` ) çalışır.</span><span class="sxs-lookup"><span data-stu-id="799b6-133">This setting would work for scenarios where a particular endpoint needs different security settings from the other endpoints of the same channel factory type (in this case `ITest`).</span></span>

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

<span data-ttu-id="799b6-134">Yukarıdaki örnekte, öğesinin tüm örnekleri `TestClient` farklı kanal fabrikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="799b6-134">In the example above, all instances of `TestClient` would use different channel factories.</span></span> <span data-ttu-id="799b6-135">Bu, her bir uç nokta farklı güvenlik gereksinimlerine sahip olduğunda ve önbelleğe alma mantıklı olmadığında yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="799b6-135">This is useful when each endpoint has different security requirements and it makes no sense to cache.</span></span>

## <a name="see-also"></a><span data-ttu-id="799b6-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="799b6-136">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="799b6-137">İstemci Derleme</span><span class="sxs-lookup"><span data-stu-id="799b6-137">Building Clients</span></span>](../building-clients.md)
- [<span data-ttu-id="799b6-138">İstemciler</span><span class="sxs-lookup"><span data-stu-id="799b6-138">Clients</span></span>](clients.md)
- [<span data-ttu-id="799b6-139">WCF İstemcisi Kullanarak Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="799b6-139">Accessing Services Using a WCF Client</span></span>](../accessing-services-using-a-wcf-client.md)
- [<span data-ttu-id="799b6-140">Nasıl yapılır: ChannelFactory Kullanma</span><span class="sxs-lookup"><span data-stu-id="799b6-140">How to: Use the ChannelFactory</span></span>](how-to-use-the-channelfactory.md)
