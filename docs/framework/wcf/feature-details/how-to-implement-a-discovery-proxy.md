---
title: "Nasıl yapılır: Keşif Proxy'si Uygulama"
ms.date: 03/30/2017
ms.assetid: 78d70e0a-f6c3-4cfb-a7ca-f66ebddadde0
ms.openlocfilehash: b3e0b5cef01998c1e509586ba1fab3924eb7bc0b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321022"
---
# <a name="how-to-implement-a-discovery-proxy"></a><span data-ttu-id="930dd-102">Nasıl yapılır: Keşif Proxy'si Uygulama</span><span class="sxs-lookup"><span data-stu-id="930dd-102">How to: Implement a Discovery Proxy</span></span>
<span data-ttu-id="930dd-103">Bu konuda, Keşif proxy'si uygulama açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="930dd-103">This topic explains how to implement a discovery proxy.</span></span> <span data-ttu-id="930dd-104">Windows Communication Foundation (WCF) bulma özelliği hakkında daha fazla bilgi için bkz. [WCF keşif genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="930dd-104">For more information about the discovery feature in Windows Communication Foundation (WCF), see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span> <span data-ttu-id="930dd-105">Keşif proxy'si genişleten bir sınıfı oluşturarak uygulanabilir <xref:System.ServiceModel.Discovery.DiscoveryProxy> soyut sınıf.</span><span class="sxs-lookup"><span data-stu-id="930dd-105">A discovery proxy can be implemented by creating a class that extends the <xref:System.ServiceModel.Discovery.DiscoveryProxy> abstract class.</span></span> <span data-ttu-id="930dd-106">Tanımlanan ve bu örnekte kullanılan diğer destek sınıfları vardır.</span><span class="sxs-lookup"><span data-stu-id="930dd-106">There are a number of other support classes defined and used in this sample.</span></span> <span data-ttu-id="930dd-107">`OnResolveAsyncResult`, `OnFindAsyncResult`, ve `AsyncResult`.</span><span class="sxs-lookup"><span data-stu-id="930dd-107">`OnResolveAsyncResult`, `OnFindAsyncResult`, and `AsyncResult`.</span></span> <span data-ttu-id="930dd-108">Bu sınıfların uygulamak <xref:System.IAsyncResult> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="930dd-108">These classes implement the <xref:System.IAsyncResult> interface.</span></span> <span data-ttu-id="930dd-109">Hakkında daha fazla bilgi için <xref:System.IAsyncResult> bkz [System.IAsyncResult arabirimi](xref:System.IAsyncResult).</span><span class="sxs-lookup"><span data-stu-id="930dd-109">For more information about <xref:System.IAsyncResult> see [System.IAsyncResult interface](xref:System.IAsyncResult).</span></span>

 <span data-ttu-id="930dd-110">Keşif proxy'si ekleme Bu konuda üç ana parçalara bölünmüştür:</span><span class="sxs-lookup"><span data-stu-id="930dd-110">Implementing a discovery proxy is broken down into three main parts in this topic:</span></span>

-   <span data-ttu-id="930dd-111">Bir veri deposunda ve Özet genişleten bir sınıf tanımlama <xref:System.ServiceModel.Discovery.DiscoveryProxy> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="930dd-111">Define a class that contains a data store and extends the abstract <xref:System.ServiceModel.Discovery.DiscoveryProxy> class.</span></span>

-   <span data-ttu-id="930dd-112">Yardımcı uygulama `AsyncResult` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="930dd-112">Implement the helper `AsyncResult` class.</span></span>

-   <span data-ttu-id="930dd-113">Keşif proxy'si barındırın.</span><span class="sxs-lookup"><span data-stu-id="930dd-113">Host the Discovery Proxy.</span></span>

### <a name="to-create-a-new-console-application-project"></a><span data-ttu-id="930dd-114">Yeni bir konsol uygulaması projesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="930dd-114">To create a new console application project</span></span>

1. <span data-ttu-id="930dd-115">Visual Studio 2012 başlatın.</span><span class="sxs-lookup"><span data-stu-id="930dd-115">Start Visual Studio 2012.</span></span>

2. <span data-ttu-id="930dd-116">Yeni bir konsol uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="930dd-116">Create a new console application project.</span></span> <span data-ttu-id="930dd-117">Projeyi adlandırın `DiscoveryProxy` ve çözüm adı `DiscoveryProxyExample`.</span><span class="sxs-lookup"><span data-stu-id="930dd-117">Name the project `DiscoveryProxy` and the name the solution `DiscoveryProxyExample`.</span></span>

3. <span data-ttu-id="930dd-118">Aşağıdaki başvuruları projeye ekleyin</span><span class="sxs-lookup"><span data-stu-id="930dd-118">Add the following references to the project</span></span>

    1.  <span data-ttu-id="930dd-119">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="930dd-119">System.ServiceModel.dll</span></span>

    2.  <span data-ttu-id="930dd-120">System.Servicemodel.Discovery.dll</span><span class="sxs-lookup"><span data-stu-id="930dd-120">System.Servicemodel.Discovery.dll</span></span>

    > [!CAUTION]
    >  <span data-ttu-id="930dd-121">Sürüm 4.0 ya da bu derlemeleri daha büyük başvuru emin olun.</span><span class="sxs-lookup"><span data-stu-id="930dd-121">Ensure that you reference version 4.0 or greater of these assemblies.</span></span>

### <a name="to-implement-the-proxydiscoveryservice-class"></a><span data-ttu-id="930dd-122">ProxyDiscoveryService sınıf uygulamak için</span><span class="sxs-lookup"><span data-stu-id="930dd-122">To implement the ProxyDiscoveryService class</span></span>

1. <span data-ttu-id="930dd-123">Yeni bir kod dosyası projenize ekleyin ve DiscoveryProxy.cs adlandırın.</span><span class="sxs-lookup"><span data-stu-id="930dd-123">Add a new code file to your project and name it DiscoveryProxy.cs.</span></span>

2. <span data-ttu-id="930dd-124">Aşağıdaki `using` DiscoveryProxy.cs deyimleriyle.</span><span class="sxs-lookup"><span data-stu-id="930dd-124">Add the following `using` statements to DiscoveryProxy.cs.</span></span>

    ```
    using System;
    using System.Collections.Generic;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    using System.Xml;
    ```

3. <span data-ttu-id="930dd-125">Türetilen `DiscoveryProxyService` gelen <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span><span class="sxs-lookup"><span data-stu-id="930dd-125">Derive the `DiscoveryProxyService` from <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span></span> <span data-ttu-id="930dd-126">Uygulama `ServiceBehavior` aşağıdaki örnekte gösterildiği gibi sınıfı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="930dd-126">Apply the `ServiceBehavior` attribute to the class as shown in the following example.</span></span>

    ```
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
    }
    ```

4. <span data-ttu-id="930dd-127">İçinde `DiscoveryProxy` sınıfı tanımlayın kayıtlı Hizmetleri tutan sözlük.</span><span class="sxs-lookup"><span data-stu-id="930dd-127">Inside the `DiscoveryProxy` class define a dictionary to hold the registered services.</span></span>

    ```
    // Repository to store EndpointDiscoveryMetadata.
    Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;
    ```

5. <span data-ttu-id="930dd-128">Sözlük başlatan bir oluşturucu tanımlayamaz.</span><span class="sxs-lookup"><span data-stu-id="930dd-128">Define a constructor that initializes the dictionary.</span></span>

    ```
    public DiscoveryProxyService()
            {
                this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
            }
    ```

### <a name="to-define-the-methods-used-to-update-the-discovery-proxy-cache"></a><span data-ttu-id="930dd-129">Keşif proxy önbelleği güncelleştirmek için kullanılan yöntemleri tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="930dd-129">To define the methods used to update the discovery proxy cache</span></span>

1. <span data-ttu-id="930dd-130">Uygulama `AddOnlineservice` Hizmetleri önbelleğine eklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="930dd-130">Implement the `AddOnlineservice` method to add services to the cache.</span></span> <span data-ttu-id="930dd-131">Bu proxy her bir Duyurunun ileti aldığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="930dd-131">This is called every time the proxy receives an announcement message.</span></span>

    ```
    void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
            {
                lock (this.onlineServices)
                {
                    this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
                }

                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
            }
    ```

2. <span data-ttu-id="930dd-132">Uygulama `RemoveOnlineService` önbellekten hizmetlerini kaldırmak için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="930dd-132">Implement the `RemoveOnlineService` method that is used to remove services from the cache.</span></span>

    ```
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

3. <span data-ttu-id="930dd-133">Uygulama `MatchFromOnlineService` sözlük hizmetinde hizmetiyle eşleştirme yapmayı denemek yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="930dd-133">Implement the `MatchFromOnlineService` methods that attempt to match a service with a service in the dictionary.</span></span>

    ```
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

    ```
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

4. <span data-ttu-id="930dd-134">Uygulama `PrintDiscoveryMetadata` konsol metni ile kullanıcı sağlayan yöntemi çıkış proxy hangi bulma işlemi yapıyor.</span><span class="sxs-lookup"><span data-stu-id="930dd-134">Implement the `PrintDiscoveryMetadata` method that provides the user with console text output of what the discovery proxy is doing.</span></span>

    ```
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

5. <span data-ttu-id="930dd-135">Aşağıdaki AsyncResult sınıflar için DiscoveryProxyService ekleyin.</span><span class="sxs-lookup"><span data-stu-id="930dd-135">Add the following AsyncResult classes to the DiscoveryProxyService.</span></span> <span data-ttu-id="930dd-136">Bu sınıflar farklı zaman uyumsuz işlem sonuçlarını ayırt etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="930dd-136">These classes are used to differentiate between the different asynchronous operation results.</span></span>

    ```
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

### <a name="to-define-the-methods-that-implement-the-discovery-proxy-functionality"></a><span data-ttu-id="930dd-137">Bulma Ara sunucusu işlevleri uygulayan yöntemler tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="930dd-137">To define the methods that implement the discovery proxy functionality</span></span>

1. <span data-ttu-id="930dd-138">Geçersiz kılma <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="930dd-138">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="930dd-139">Keşif proxy'si bir çevrimiçi Duyurunun ileti aldığında, bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="930dd-139">This method is called when the discovery proxy receives an online announcement message.</span></span>

    ```
    // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
            protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
            {
                this.AddOnlineService(endpointDiscoveryMetadata);
                return new OnOnlineAnnouncementAsyncResult(callback, state);
            }
    ```

2. <span data-ttu-id="930dd-140">Geçersiz kılma <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="930dd-140">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="930dd-141">Keşif proxy'si, bir duyuru iletiyi işlemeyi tamamladıktan sonra bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="930dd-141">This method is called when the discovery proxy finishes processing an announcement message.</span></span>

    ```
    protected override void OnEndOnlineAnnouncement(IAsyncResult result)
            {
                OnOnlineAnnouncementAsyncResult.End(result);
            }
    ```

3. <span data-ttu-id="930dd-142">Geçersiz kılma <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="930dd-142">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="930dd-143">Bu yöntem çağrılır ile keşif proxy çevrimdışı Duyurunun ileti alır.</span><span class="sxs-lookup"><span data-stu-id="930dd-143">This method is called with the discovery proxy receives an offline announcement message.</span></span>

    ```
    // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
            protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
            {
                this.RemoveOnlineService(endpointDiscoveryMetadata);
                return new OnOfflineAnnouncementAsyncResult(callback, state);
            }
    ```

4. <span data-ttu-id="930dd-144">Geçersiz kılma <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="930dd-144">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="930dd-145">Keşif proxy'si, bir çevrimdışı duyuru iletiyi işlemeyi tamamladıktan sonra bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="930dd-145">This method is called when the discovery proxy finishes processing an offline announcement message.</span></span>

    ```
    protected override void OnEndOfflineAnnouncement(IAsyncResult result)
            {
                OnOfflineAnnouncementAsyncResult.End(result);
            }
    ```

5. <span data-ttu-id="930dd-146">Geçersiz kılma <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="930dd-146">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="930dd-147">Keşif proxy'si bir bulma isteği aldığında, bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="930dd-147">This method is called when the discovery proxy receives a find request.</span></span>

    ```
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

6. <span data-ttu-id="930dd-148">Geçersiz kılma <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="930dd-148">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="930dd-149">Keşif proxy'si bir bulma isteği işleme tamamlandığında, bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="930dd-149">This method is called when the discovery proxy finishes processing a find request.</span></span>

    ```
    protected override void OnEndFind(IAsyncResult result)
            {
                OnFindAsyncResult.End(result);
            }
    ```

7. <span data-ttu-id="930dd-150">Geçersiz kılma <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="930dd-150">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="930dd-151">Keşif proxy'si bir Çözümle ileti aldığında, bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="930dd-151">This method is called when the discovery proxy receives a resolve message.</span></span>

    ```
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

8. <span data-ttu-id="930dd-152">Geçersiz kılma <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="930dd-152">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="930dd-153">Keşif proxy'si bir Çözümle iletiyi işlemeyi tamamladığında bu yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="930dd-153">This method is called when the discovery proxy finishes processing a resolve message.</span></span>

    ```
    protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
    {
        return OnResolveAsyncResult.End(result);
    }
    ```

 <span data-ttu-id="930dd-154">OnBegin...</span><span class="sxs-lookup"><span data-stu-id="930dd-154">The OnBegin..</span></span> <span data-ttu-id="930dd-155">/ OnEnd...</span><span class="sxs-lookup"><span data-stu-id="930dd-155">/ OnEnd..</span></span> <span data-ttu-id="930dd-156">yöntemler sonraki bulma işlemleri için mantığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="930dd-156">methods provide the logic for the subsequent discovery operations.</span></span> <span data-ttu-id="930dd-157">Örneğin <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> ve <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> yöntemleri keşif proxy'si bulma mantığını uygulayın.</span><span class="sxs-lookup"><span data-stu-id="930dd-157">For example the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> and <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> methods implement the find logic for discovery proxy.</span></span> <span data-ttu-id="930dd-158">Keşif proxy'si bir yoklama iletisi aldığında bu yöntemler bir yanıtı istemciye geri gönderilecek yürütülür.</span><span class="sxs-lookup"><span data-stu-id="930dd-158">When the discovery proxy receives a probe message these methods are executed to send a response back to the client.</span></span> <span data-ttu-id="930dd-159">İstediğiniz gibi bulma mantığını değiştirebilir, örneğin algoritmalar veya ayrıştırma, bulma işleminin bir parçası uygulama belirli XML meta verileri tarafından eşleşen özel kapsam ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="930dd-159">You may modify the find logic as you wish, for example you can incorporate custom scope matching by algorithms or application specific XML metadata parsing as part of your find operation.</span></span>

### <a name="to-implement-the-asyncresult-class"></a><span data-ttu-id="930dd-160">AsyncResult sınıf uygulamak için</span><span class="sxs-lookup"><span data-stu-id="930dd-160">To implement the AsyncResult class</span></span>

1. <span data-ttu-id="930dd-161">Soyut temel sınıf çeşitli zaman uyumsuz sonuç sınıfların türetilmesi için kullanılan AsyncResult tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="930dd-161">Define the abstract base class AsyncResult which is used to derive the various async result classes.</span></span>

2. <span data-ttu-id="930dd-162">AsyncResult.cs adlı yeni bir kod dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="930dd-162">Create a new code file called AsyncResult.cs.</span></span>

3. <span data-ttu-id="930dd-163">Aşağıdaki `using` AsyncResult.cs deyimleriyle.</span><span class="sxs-lookup"><span data-stu-id="930dd-163">Add the following `using` statements to AsyncResult.cs.</span></span>

    ```
    using System;
    using System.Threading;
    ```

4. <span data-ttu-id="930dd-164">Aşağıdaki AsyncResult sınıfı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="930dd-164">Add the following AsyncResult class.</span></span>

    ```
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
                        if (manualResetEvent == null)
                        {
                            manualResetEvent = new ManualResetEvent(isCompleted);
                        }
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

### <a name="to-host-the-discoveryproxy"></a><span data-ttu-id="930dd-165">Konağa DiscoveryProxy</span><span class="sxs-lookup"><span data-stu-id="930dd-165">To host the DiscoveryProxy</span></span>

1. <span data-ttu-id="930dd-166">Program.cs dosyasının DiscoveryProxyExample projeyi açın.</span><span class="sxs-lookup"><span data-stu-id="930dd-166">Open the Program.cs file in the DiscoveryProxyExample project.</span></span>

2. <span data-ttu-id="930dd-167">Aşağıdaki `using` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="930dd-167">Add the following `using` statements.</span></span>

    ```
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="930dd-168">İçinde `Main()` yöntemine aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="930dd-168">Within the `Main()` method, add the following code.</span></span> <span data-ttu-id="930dd-169">Bu örneği oluşturur `DiscoveryProxy` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="930dd-169">This creates an instance of the `DiscoveryProxy` class.</span></span>

    ```
    Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
                Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

                // Host the DiscoveryProxy service
                ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());
    ```

4. <span data-ttu-id="930dd-170">Ardından bir bulma uç noktası ve duyuru uç nokta eklemek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="930dd-170">Next add the following code to add a discovery endpoint and an announcement endpoint.</span></span>

    ```
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

 <span data-ttu-id="930dd-171">Keşif proxy'si ekleme tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="930dd-171">You have completed implementing the discovery proxy.</span></span> <span data-ttu-id="930dd-172">Geçin [nasıl yapılır: Keşif proxy'sine kayıtlı bir bulunabilir hizmet uygulamak](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="930dd-172">Continue on to [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md).</span></span>

## <a name="example"></a><span data-ttu-id="930dd-173">Örnek</span><span class="sxs-lookup"><span data-stu-id="930dd-173">Example</span></span>
 <span data-ttu-id="930dd-174">Bu konu başlığında kullanılan kod tam listesi budur.</span><span class="sxs-lookup"><span data-stu-id="930dd-174">This is the full listing of the code used in this topic.</span></span>

```
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

```
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
                    if (manualResetEvent == null)
                    {
                        manualResetEvent = new ManualResetEvent(isCompleted);
                    }
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

```
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

## <a name="see-also"></a><span data-ttu-id="930dd-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="930dd-175">See also</span></span>

- [<span data-ttu-id="930dd-176">WCF Bulmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="930dd-176">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="930dd-177">Nasıl yapılır: Keşif proxy'sine bir bulunabilir hizmet ekleme</span><span class="sxs-lookup"><span data-stu-id="930dd-177">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="930dd-178">Nasıl yapılır: Bir hizmet bulmak için keşif proxy'sini kullanan bir istemci uygulama</span><span class="sxs-lookup"><span data-stu-id="930dd-178">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
- [<span data-ttu-id="930dd-179">Nasıl yapılır: Keşif proxy'sini test etme</span><span class="sxs-lookup"><span data-stu-id="930dd-179">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)