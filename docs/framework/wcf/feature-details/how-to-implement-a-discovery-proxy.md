---
title: "Nasıl yapılır: Keşif Proxy'si Uygulama"
ms.date: 03/30/2017
ms.assetid: 78d70e0a-f6c3-4cfb-a7ca-f66ebddadde0
ms.openlocfilehash: ca7ab2ee434aef7649d71cbfc33273f48020788f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597078"
---
# <a name="how-to-implement-a-discovery-proxy"></a><span data-ttu-id="5e3aa-102">Nasıl yapılır: Keşif Proxy'si Uygulama</span><span class="sxs-lookup"><span data-stu-id="5e3aa-102">How to: Implement a Discovery Proxy</span></span>

<span data-ttu-id="5e3aa-103">Bu konuda, bulma proxy 'nin nasıl uygulanacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-103">This topic explains how to implement a discovery proxy.</span></span> <span data-ttu-id="5e3aa-104">Windows Communication Foundation (WCF) içindeki bulma özelliği hakkında daha fazla bilgi için bkz. [WCF bulma 'Ya genel bakış](wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5e3aa-104">For more information about the discovery feature in Windows Communication Foundation (WCF), see [WCF Discovery Overview](wcf-discovery-overview.md).</span></span> <span data-ttu-id="5e3aa-105">Bir bulma proxy 'si, soyut sınıfı genişleten bir sınıf oluşturularak uygulanabilir <xref:System.ServiceModel.Discovery.DiscoveryProxy> .</span><span class="sxs-lookup"><span data-stu-id="5e3aa-105">A discovery proxy can be implemented by creating a class that extends the <xref:System.ServiceModel.Discovery.DiscoveryProxy> abstract class.</span></span> <span data-ttu-id="5e3aa-106">Bu örnekte tanımlanmış ve kullanılan çeşitli destek sınıfları vardır.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-106">There are a number of other support classes defined and used in this sample.</span></span> <span data-ttu-id="5e3aa-107">`OnResolveAsyncResult`, `OnFindAsyncResult` ve `AsyncResult` .</span><span class="sxs-lookup"><span data-stu-id="5e3aa-107">`OnResolveAsyncResult`, `OnFindAsyncResult`, and `AsyncResult`.</span></span> <span data-ttu-id="5e3aa-108">Bu sınıflar, <xref:System.IAsyncResult> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-108">These classes implement the <xref:System.IAsyncResult> interface.</span></span> <span data-ttu-id="5e3aa-109">Daha fazla bilgi için <xref:System.IAsyncResult> bkz. [System. IAsyncResult arabirimi](xref:System.IAsyncResult).</span><span class="sxs-lookup"><span data-stu-id="5e3aa-109">For more information about <xref:System.IAsyncResult> see [System.IAsyncResult interface](xref:System.IAsyncResult).</span></span>

 <span data-ttu-id="5e3aa-110">Keşif proxy 'si uygulamak, bu konunun üç ana bölümüne bölünür:</span><span class="sxs-lookup"><span data-stu-id="5e3aa-110">Implementing a discovery proxy is broken down into three main parts in this topic:</span></span>

- <span data-ttu-id="5e3aa-111">Bir veri deposu içeren ve soyut sınıfı genişleten bir sınıf tanımlayın <xref:System.ServiceModel.Discovery.DiscoveryProxy> .</span><span class="sxs-lookup"><span data-stu-id="5e3aa-111">Define a class that contains a data store and extends the abstract <xref:System.ServiceModel.Discovery.DiscoveryProxy> class.</span></span>

- <span data-ttu-id="5e3aa-112">Yardımcı sınıfını uygulayın `AsyncResult` .</span><span class="sxs-lookup"><span data-stu-id="5e3aa-112">Implement the helper `AsyncResult` class.</span></span>

- <span data-ttu-id="5e3aa-113">Bulma proxy 'sini barındırın.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-113">Host the Discovery Proxy.</span></span>

### <a name="to-create-a-new-console-application-project"></a><span data-ttu-id="5e3aa-114">Yeni bir konsol uygulaması projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5e3aa-114">To create a new console application project</span></span>

1. <span data-ttu-id="5e3aa-115">Visual Studio 2012 ' i başlatın.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-115">Start Visual Studio 2012.</span></span>

2. <span data-ttu-id="5e3aa-116">Yeni bir konsol uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-116">Create a new console application project.</span></span> <span data-ttu-id="5e3aa-117">Projeyi `DiscoveryProxy` ve çözümü adlandırın `DiscoveryProxyExample` .</span><span class="sxs-lookup"><span data-stu-id="5e3aa-117">Name the project `DiscoveryProxy` and the name the solution `DiscoveryProxyExample`.</span></span>

3. <span data-ttu-id="5e3aa-118">Aşağıdaki başvuruları projeye ekleyin</span><span class="sxs-lookup"><span data-stu-id="5e3aa-118">Add the following references to the project</span></span>

    1. <span data-ttu-id="5e3aa-119">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="5e3aa-119">System.ServiceModel.dll</span></span>

    2. <span data-ttu-id="5e3aa-120">System. ServiceModel. Discovery. dll</span><span class="sxs-lookup"><span data-stu-id="5e3aa-120">System.Servicemodel.Discovery.dll</span></span>

    > [!CAUTION]
    > <span data-ttu-id="5e3aa-121">Sürüm 4,0 veya bu derlemelerin daha büyük bir sürümüne başvurtığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-121">Ensure that you reference version 4.0 or greater of these assemblies.</span></span>

### <a name="to-implement-the-proxydiscoveryservice-class"></a><span data-ttu-id="5e3aa-122">ProxyDiscoveryService sınıfını uygulamak için</span><span class="sxs-lookup"><span data-stu-id="5e3aa-122">To implement the ProxyDiscoveryService class</span></span>

1. <span data-ttu-id="5e3aa-123">Projenize yeni bir kod dosyası ekleyin ve DiscoveryProxy.cs olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-123">Add a new code file to your project and name it DiscoveryProxy.cs.</span></span>

2. <span data-ttu-id="5e3aa-124">Aşağıdaki `using` deyimlerini DiscoveryProxy.cs öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-124">Add the following `using` statements to DiscoveryProxy.cs.</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    using System.Xml;
    ```

3. <span data-ttu-id="5e3aa-125">`DiscoveryProxyService`Öğesinden türet <xref:System.ServiceModel.Discovery.DiscoveryProxy> .</span><span class="sxs-lookup"><span data-stu-id="5e3aa-125">Derive the `DiscoveryProxyService` from <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span></span> <span data-ttu-id="5e3aa-126">`ServiceBehavior`Aşağıdaki örnekte gösterildiği gibi özniteliğini sınıfına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-126">Apply the `ServiceBehavior` attribute to the class as shown in the following example.</span></span>

    ```csharp
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
    }
    ```

4. <span data-ttu-id="5e3aa-127">Sınıfının içinde `DiscoveryProxy` kayıtlı Hizmetleri tutacak bir sözlük tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-127">Inside the `DiscoveryProxy` class define a dictionary to hold the registered services.</span></span>

    ```csharp
    // Repository to store EndpointDiscoveryMetadata.
    Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;
    ```

5. <span data-ttu-id="5e3aa-128">Sözlüğü Başlatan bir Oluşturucu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-128">Define a constructor that initializes the dictionary.</span></span>

    ```csharp
    public DiscoveryProxyService()
            {
                this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
            }
    ```

### <a name="to-define-the-methods-used-to-update-the-discovery-proxy-cache"></a><span data-ttu-id="5e3aa-129">Bulma proxy önbelleğini güncelleştirmek için kullanılan yöntemleri tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="5e3aa-129">To define the methods used to update the discovery proxy cache</span></span>

1. <span data-ttu-id="5e3aa-130">`AddOnlineservice`Önbelleğe hizmet eklemek için yöntemini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-130">Implement the `AddOnlineservice` method to add services to the cache.</span></span> <span data-ttu-id="5e3aa-131">Bu, proxy 'nin bir duyuru iletisi aldığı her seferinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-131">This is called every time the proxy receives an announcement message.</span></span>

    ```csharp
    void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
    {
        lock (this.onlineServices)
        {
            this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
        }

        PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
    }
    ```

2. <span data-ttu-id="5e3aa-132">`RemoveOnlineService`Önbellekten Hizmetleri kaldırmak için kullanılan yöntemi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-132">Implement the `RemoveOnlineService` method that is used to remove services from the cache.</span></span>

    ```csharp
    void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
    {
        if (endpointDiscoveryMetadata != null)
        {
            lock (this.onlineServices)
            {
                this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
        }
    }
    ```

3. <span data-ttu-id="5e3aa-133">`MatchFromOnlineService`Sözlük içindeki bir hizmetle eşleşen bir hizmeti eşleştirmeye çalışacak yöntemleri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-133">Implement the `MatchFromOnlineService` methods that attempt to match a service with a service in the dictionary.</span></span>

    ```csharp
    void MatchFromOnlineService(FindRequestContext findRequestContext)
    {
        lock (this.onlineServices)
        {
            foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
            {
                if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                {
                    findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                }
            }
        }
    }
    ```

    ```csharp
    EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
    {
        EndpointDiscoveryMetadata matchingEndpoint = null;
        lock (this.onlineServices)
        {
            foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
            {
                if (criteria.Address == endpointDiscoveryMetadata.Address)
                {
                    matchingEndpoint = endpointDiscoveryMetadata;
                }
            }
        }
        return matchingEndpoint;
    }
    ```

4. <span data-ttu-id="5e3aa-134">`PrintDiscoveryMetadata`Kullanıcıya bulma proxy 'sinin yaptığı işlemin konsol metni çıkışını sağlayan yöntemini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-134">Implement the `PrintDiscoveryMetadata` method that provides the user with console text output of what the discovery proxy is doing.</span></span>

    ```csharp
    void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
    {
        Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
        foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
        {
            Console.WriteLine("** " + contractName.ToString());
            break;
        }
        Console.WriteLine("**** Operation Completed");
    }
    ```

5. <span data-ttu-id="5e3aa-135">Aşağıdaki AsyncResult sınıflarını DiscoveryProxyService öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-135">Add the following AsyncResult classes to the DiscoveryProxyService.</span></span> <span data-ttu-id="5e3aa-136">Bu sınıflar, farklı zaman uyumsuz işlem sonuçları arasında ayrım yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-136">These classes are used to differentiate between the different asynchronous operation results.</span></span>

    ```csharp
    sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
    {
        public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
        }
    }

    sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
    {
        public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
        }
    }

    sealed class OnFindAsyncResult : AsyncResult
    {
        public OnFindAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnFindAsyncResult>(result);
        }
    }

    sealed class OnResolveAsyncResult : AsyncResult
    {
        EndpointDiscoveryMetadata matchingEndpoint;

        public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.matchingEndpoint = matchingEndpoint;
            this.Complete(true);
        }

        public static EndpointDiscoveryMetadata End(IAsyncResult result)
        {
            OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
            return thisPtr.matchingEndpoint;
        }
    }
    ```

### <a name="to-define-the-methods-that-implement-the-discovery-proxy-functionality"></a><span data-ttu-id="5e3aa-137">Bulma proxy işlevlerini uygulayan yöntemleri tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="5e3aa-137">To define the methods that implement the discovery proxy functionality</span></span>

1. <span data-ttu-id="5e3aa-138">Yöntemini geçersiz kılın <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e3aa-138">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5e3aa-139">Keşif proxy 'si bir çevrimiçi duyuru iletisi aldığında bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-139">This method is called when the discovery proxy receives an online announcement message.</span></span>

    ```csharp
    // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
    protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
    {
        this.AddOnlineService(endpointDiscoveryMetadata);
        return new OnOnlineAnnouncementAsyncResult(callback, state);
    }
    ```

2. <span data-ttu-id="5e3aa-140">Yöntemini geçersiz kılın <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e3aa-140">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5e3aa-141">Keşif proxy 'si bir duyuru iletisini işlemeyi bitirdiğinde, bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-141">This method is called when the discovery proxy finishes processing an announcement message.</span></span>

    ```csharp
    protected override void OnEndOnlineAnnouncement(IAsyncResult result)
    {
        OnOnlineAnnouncementAsyncResult.End(result);
    }
    ```

3. <span data-ttu-id="5e3aa-142">Yöntemini geçersiz kılın <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e3aa-142">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5e3aa-143">Bu yöntem, bulma proxy 'si ile birlikte çağrıldığında bir çevrimdışı duyuru iletisi alır.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-143">This method is called with the discovery proxy receives an offline announcement message.</span></span>

    ```csharp
    // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
    protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
    {
        this.RemoveOnlineService(endpointDiscoveryMetadata);
        return new OnOfflineAnnouncementAsyncResult(callback, state);
    }
    ```

4. <span data-ttu-id="5e3aa-144">Yöntemini geçersiz kılın <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e3aa-144">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5e3aa-145">Bu yöntem, bulma proxy 'si bir çevrimdışı duyuru iletisini işlemeyi bitirdiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-145">This method is called when the discovery proxy finishes processing an offline announcement message.</span></span>

    ```csharp
    protected override void OnEndOfflineAnnouncement(IAsyncResult result)
    {
        OnOfflineAnnouncementAsyncResult.End(result);
    }
    ```

5. <span data-ttu-id="5e3aa-146">Yöntemini geçersiz kılın <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e3aa-146">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5e3aa-147">Bulma proxy 'si bir bulma isteği aldığında bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-147">This method is called when the discovery proxy receives a find request.</span></span>

    ```csharp
    // OnBeginFind method is called when a Probe request message is received by the Proxy
    protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
    {
        this.MatchFromOnlineService(findRequestContext);
        return new OnFindAsyncResult(callback, state);
    }
    protected override IAsyncResult OnBeginFind(FindRequest findRequest, AsyncCallback callback, object state)
    {
        Collection<EndpointDiscoveryMetadata> matchingEndpoints = MatchFromCache(findRequest.Criteria);
        return new OnFindAsyncResult(
                    matchingEndpoints,
                    callback,
                    state);
    }
    ```

6. <span data-ttu-id="5e3aa-148">Yöntemini geçersiz kılın <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e3aa-148">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5e3aa-149">Bulma proxy 'si bir bul isteğini işlemeyi bitirdiğinde, bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-149">This method is called when the discovery proxy finishes processing a find request.</span></span>

    ```csharp
    protected override void OnEndFind(IAsyncResult result)
    {
        OnFindAsyncResult.End(result);
    }
    ```

7. <span data-ttu-id="5e3aa-150">Yöntemini geçersiz kılın <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e3aa-150">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5e3aa-151">Keşif proxy 'si bir çözüm iletisi aldığında bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-151">This method is called when the discovery proxy receives a resolve message.</span></span>

    ```csharp
    // OnBeginFind method is called when a Resolve request message is received by the Proxy
    protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
    }
    protected override IAsyncResult OnBeginResolve(ResolveRequest resolveRequest, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(
            this.proxy.MatchFromOnlineService(resolveRequest.Criteria),
            callback,
            state);
    }
    ```

8. <span data-ttu-id="5e3aa-152">Yöntemini geçersiz kılın <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e3aa-152">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5e3aa-153">Bu yöntem, bulma proxy 'sinin bir Resolve iletisini işlemeyi bitirdiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-153">This method is called when the discovery proxy finishes processing a resolve message.</span></span>

    ```csharp
    protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
    {
        return OnResolveAsyncResult.End(result);
    }
    ```

<span data-ttu-id="5e3aa-154">Onbegın..</span><span class="sxs-lookup"><span data-stu-id="5e3aa-154">The OnBegin..</span></span> <span data-ttu-id="5e3aa-155">/OnEnd..</span><span class="sxs-lookup"><span data-stu-id="5e3aa-155">/ OnEnd..</span></span> <span data-ttu-id="5e3aa-156">Yöntemler, sonraki bulma işlemlerine yönelik mantığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-156">methods provide the logic for the subsequent discovery operations.</span></span> <span data-ttu-id="5e3aa-157">Örneğin, <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> ve <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> yöntemleri bulma proxy 'si için Find mantığını uygular.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-157">For example the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> and <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> methods implement the find logic for discovery proxy.</span></span> <span data-ttu-id="5e3aa-158">Bulma proxy 'si bir araştırma iletisi aldığında, istemciye yanıt göndermek için bu yöntemler yürütülür.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-158">When the discovery proxy receives a probe message these methods are executed to send a response back to the client.</span></span> <span data-ttu-id="5e3aa-159">Find mantığını istediğiniz gibi değiştirebilirsiniz. Örneğin, bul işleminin bir parçası olarak algoritmalara veya uygulamaya özgü XML meta verileri ayrıştırmaya göre özel kapsam eşleştirmeyi birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-159">You may modify the find logic as you wish, for example you can incorporate custom scope matching by algorithms or application specific XML metadata parsing as part of your find operation.</span></span>

### <a name="to-implement-the-asyncresult-class"></a><span data-ttu-id="5e3aa-160">AsyncResult sınıfını uygulamak için</span><span class="sxs-lookup"><span data-stu-id="5e3aa-160">To implement the AsyncResult class</span></span>

1. <span data-ttu-id="5e3aa-161">Çeşitli zaman uyumsuz sonuç sınıflarını türetmek için kullanılan soyut temel sınıf AsyncResult öğesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-161">Define the abstract base class AsyncResult which is used to derive the various async result classes.</span></span>

2. <span data-ttu-id="5e3aa-162">AsyncResult.cs adlı yeni bir kod dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-162">Create a new code file called AsyncResult.cs.</span></span>

3. <span data-ttu-id="5e3aa-163">Aşağıdaki `using` deyimlerini AsyncResult.cs öğesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-163">Add the following `using` statements to AsyncResult.cs.</span></span>

    ```csharp
    using System;
    using System.Threading;
    ```

4. <span data-ttu-id="5e3aa-164">Aşağıdaki AsyncResult sınıfını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-164">Add the following AsyncResult class.</span></span>

    ```csharp
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    manualResetEvent ??= new ManualResetEvent(isCompleted);
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
    ```

### <a name="to-host-the-discoveryproxy"></a><span data-ttu-id="5e3aa-165">DiscoveryProxy 'yi barındırmak için</span><span class="sxs-lookup"><span data-stu-id="5e3aa-165">To host the DiscoveryProxy</span></span>

1. <span data-ttu-id="5e3aa-166">Program.cs dosyasını DiscoveryProxyExample projesinde açın.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-166">Open the Program.cs file in the DiscoveryProxyExample project.</span></span>

2. <span data-ttu-id="5e3aa-167">Aşağıdaki `using` deyimlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-167">Add the following `using` statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="5e3aa-168">Yöntemi içinde `Main()` aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-168">Within the `Main()` method, add the following code.</span></span> <span data-ttu-id="5e3aa-169">Bu, sınıfının bir örneğini oluşturur `DiscoveryProxy` .</span><span class="sxs-lookup"><span data-stu-id="5e3aa-169">This creates an instance of the `DiscoveryProxy` class.</span></span>

    ```csharp
    Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
    Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

    // Host the DiscoveryProxy service
    ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());
    ```

4. <span data-ttu-id="5e3aa-170">Sonra bulma uç noktası ve duyuru uç noktası eklemek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-170">Next add the following code to add a discovery endpoint and an announcement endpoint.</span></span>

    ```csharp
    try
    {
        // Add DiscoveryEndpoint to receive Probe and Resolve messages
        DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
        discoveryEndpoint.IsSystemEndpoint = false;

        // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
        AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

        proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
        proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

        proxyServiceHost.Open();

        Console.WriteLine("Proxy Service started.");
        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate the service.");
        Console.WriteLine();
        Console.ReadLine();

        proxyServiceHost.Close();
    }
    catch (CommunicationException e)
    {
        Console.WriteLine(e.Message);
    }
    catch (TimeoutException e)
    {
        Console.WriteLine(e.Message);
    }

    if (proxyServiceHost.State != CommunicationState.Closed)
    {
        Console.WriteLine("Aborting the service...");
        proxyServiceHost.Abort();
    }
    ```

<span data-ttu-id="5e3aa-171">Bulma proxy 'sini uygulamayı tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-171">You have completed implementing the discovery proxy.</span></span> <span data-ttu-id="5e3aa-172">[Nasıl yapılır: bulma proxy 'Sine kaydolduktan sonra bulunabilir bir hizmeti uygulama](discoverable-service-that-registers-with-the-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="5e3aa-172">Continue on to [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](discoverable-service-that-registers-with-the-discovery-proxy.md).</span></span>

## <a name="example"></a><span data-ttu-id="5e3aa-173">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e3aa-173">Example</span></span>

<span data-ttu-id="5e3aa-174">Bu, bu konuda kullanılan kodun tam listesidir.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-174">This is the full listing of the code used in this topic.</span></span>

```csharp
// DiscoveryProxy.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Collections.Generic;
using System.ServiceModel;
using System.ServiceModel.Discovery;
using System.Xml;

namespace Microsoft.Samples.Discovery
{
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
        // Repository to store EndpointDiscoveryMetadata. A database or a flat file could also be used instead.
        Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;

        public DiscoveryProxyService()
        {
            this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
        }

        // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
        protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.AddOnlineService(endpointDiscoveryMetadata);
            return new OnOnlineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOnlineAnnouncement(IAsyncResult result)
        {
            OnOnlineAnnouncementAsyncResult.End(result);
        }

        // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
        protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.RemoveOnlineService(endpointDiscoveryMetadata);
            return new OnOfflineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOfflineAnnouncement(IAsyncResult result)
        {
            OnOfflineAnnouncementAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Probe request message is received by the Proxy
        protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
        {
            this.MatchFromOnlineService(findRequestContext);
            return new OnFindAsyncResult(callback, state);
        }

        protected override void OnEndFind(IAsyncResult result)
        {
            OnFindAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Resolve request message is received by the Proxy
        protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
        {
            return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
        }

        protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
        {
            return OnResolveAsyncResult.End(result);
        }

        // The following are helper methods required by the Proxy implementation
        void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            lock (this.onlineServices)
            {
                this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
        }

        void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            if (endpointDiscoveryMetadata != null)
            {
                lock (this.onlineServices)
                {
                    this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
                }

                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
            }
        }

        void MatchFromOnlineService(FindRequestContext findRequestContext)
        {
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                    {
                        findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                    }
                }
            }
        }

        EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
        {
            EndpointDiscoveryMetadata matchingEndpoint = null;
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (criteria.Address == endpointDiscoveryMetadata.Address)
                    {
                        matchingEndpoint = endpointDiscoveryMetadata;
                    }
                }
            }
            return matchingEndpoint;
        }

        void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
        {
            Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
            foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
            {
                Console.WriteLine("** " + contractName.ToString());
                break;
            }
            Console.WriteLine("**** Operation Completed");
        }

        sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
        {
            public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
        {
            public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnFindAsyncResult : AsyncResult
        {
            public OnFindAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnFindAsyncResult>(result);
            }
        }

        sealed class OnResolveAsyncResult : AsyncResult
        {
            EndpointDiscoveryMetadata matchingEndpoint;

            public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.matchingEndpoint = matchingEndpoint;
                this.Complete(true);
            }

            public static EndpointDiscoveryMetadata End(IAsyncResult result)
            {
                OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
                return thisPtr.matchingEndpoint;
            }
        }
    }
}
```

```csharp
// AsyncResult.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Threading;

namespace Microsoft.Samples.Discovery
{
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    manualResetEvent ??= new ManualResetEvent(isCompleted);
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
}
```

```csharp
// program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            // Host the DiscoveryProxy service
            ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());

            try
            {
                // Add DiscoveryEndpoint to receive Probe and Resolve messages
                DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
                discoveryEndpoint.IsSystemEndpoint = false;

                // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

                proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
                proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

                proxyServiceHost.Open();

                Console.WriteLine("Proxy Service started.");
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                proxyServiceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (proxyServiceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                proxyServiceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="5e3aa-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e3aa-175">See also</span></span>

- [<span data-ttu-id="5e3aa-176">WCF Keşif Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5e3aa-176">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="5e3aa-177">Nasıl yapılır: Keşif Proxy'sine Kayıtlı Bir Bulunabilir Hizmet Ekleme</span><span class="sxs-lookup"><span data-stu-id="5e3aa-177">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="5e3aa-178">Nasıl yapılır: Hizmet Bulmak için Keşif Proxy'si Kullanan Bir İstemci Uygulaması Kullanma</span><span class="sxs-lookup"><span data-stu-id="5e3aa-178">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
- [<span data-ttu-id="5e3aa-179">Nasıl yapılır: Keşif Proxy'sini Test Etme</span><span class="sxs-lookup"><span data-stu-id="5e3aa-179">How to: Test the Discovery Proxy</span></span>](how-to-test-the-discovery-proxy.md)
