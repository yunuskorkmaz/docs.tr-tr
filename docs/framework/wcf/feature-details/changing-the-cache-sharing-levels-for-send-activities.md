---
description: 'Hakkında daha fazla bilgi edinin: gönderme etkinlikleri için önbellek paylaşımı düzeylerini değiştirme'
title: Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 7ced6a8a18779a0c0d5914e63fde658b6d0130ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705219"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="0cbff-103">Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="0cbff-103">Changing the Cache Sharing Levels for Send Activities</span></span>

<span data-ttu-id="0cbff-104"><xref:System.ServiceModel.Activities.SendMessageChannelCache>Uzantı, önbellek paylaşım düzeylerini, kanal fabrikası önbelleğinin ayarlarını ve mesajlaşma etkinliklerini kullanarak hizmet uç noktalarına ileti gönderen iş akışları için kanal önbelleğinin ayarlarını özelleştirmenize olanak sağlar <xref:System.ServiceModel.Activities.Send> .</span><span class="sxs-lookup"><span data-stu-id="0cbff-104">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="0cbff-105">Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="0cbff-105">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="0cbff-106">Kanal fabrikası önbelleğinde önbelleğe alınmış <xref:System.ServiceModel.ChannelFactory%601> nesneler bulunur.</span><span class="sxs-lookup"><span data-stu-id="0cbff-106">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="0cbff-107">Kanal önbelleği, önbelleğe alınmış kanalları içerir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-107">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cbff-108">İş akışları ileti <xref:System.ServiceModel.Activities.Send> ya da parametre göndermek için mesajlaşma etkinliklerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-108">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="0cbff-109">İş akışı çalışma zamanı, etkinlik ile bir etkinlik kullandığınızda <xref:System.ServiceModel.Channels.IRequestChannel> <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Channels.IOutputChannel> yalnızca bir <xref:System.ServiceModel.Activities.Send> etkinlik (Hayır) kullandığınızda, bir <xref:System.ServiceModel.Activities.ReceiveReply> türü kanallar oluşturan önbelleğe kanal fabrikaları ekler.</span><span class="sxs-lookup"><span data-stu-id="0cbff-109">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="0cbff-110">Önbellek paylaşım düzeyleri</span><span class="sxs-lookup"><span data-stu-id="0cbff-110">The Cache Sharing Levels</span></span>  

 <span data-ttu-id="0cbff-111">Varsayılan olarak, <xref:System.ServiceModel.WorkflowServiceHost> ileti etkinlikleri tarafından kullanılan önbellek tarafından barındırılan bir iş akışında <xref:System.ServiceModel.Activities.Send> , <xref:System.ServiceModel.WorkflowServiceHost> (konak düzeyinde önbelleğe alma) içindeki tüm iş akışı örnekleri arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="0cbff-111">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="0cbff-112">Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-112">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="0cbff-113">Önbellek yalnızca, <xref:System.ServiceModel.Activities.Send> güvenli olmayan önbelleğe alma etkin olmadığı takdirde yapılandırmada tanımlanan uç noktaları kullanmayan etkinliklerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-113">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="0cbff-114">Aşağıda, bir iş akışındaki etkinlikler için kullanılabilen farklı önbellek paylaşım düzeyleri <xref:System.ServiceModel.Activities.Send> ve bunların önerilen kullanımları verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0cbff-114">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
- <span data-ttu-id="0cbff-115">**Konak düzeyi**: konak paylaşım düzeyinde, önbellek yalnızca iş akışı hizmeti ana bilgisayarında barındırılan iş akışı örnekleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-115">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="0cbff-116">Bir önbellek, işlem genelinde bir önbellekte iş akışı hizmeti konakları arasında da paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-116">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
- <span data-ttu-id="0cbff-117">**Örnek düzeyi**: örnek paylaşım düzeyinde önbellek, süresi boyunca belirli bir iş akışı örneği tarafından kullanılabilir, ancak önbellek diğer iş akışı örnekleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0cbff-117">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
- <span data-ttu-id="0cbff-118">**Önbellek yok**: yapılandırmada tanımlanan uç noktaları kullanan bir iş akışınız varsa, önbellek varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="0cbff-118">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="0cbff-119">Bu durumda, önbelleğin açık olması güvenli hale getirildiğinden önbelleğin kapalı tutulması de önerilir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-119">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="0cbff-120">Örneğin, her gönderme için farklı bir kimlik (farklı kimlik bilgileri veya kimliğe bürünme kullanılarak) gerekliyse.</span><span class="sxs-lookup"><span data-stu-id="0cbff-120">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="0cbff-121">Istemci Iş akışı için önbellek paylaşım düzeyini değiştirme</span><span class="sxs-lookup"><span data-stu-id="0cbff-121">Changing the Cache Sharing Level for a Client Workflow</span></span>  

 <span data-ttu-id="0cbff-122">Bir istemci iş akışında önbellek paylaşımını ayarlamak için, <xref:System.ServiceModel.Activities.SendMessageChannelCache> istenen iş akışı örnekleri kümesine uzantı olarak sınıfın bir örneğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0cbff-122">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="0cbff-123">Bu, önbelleğin tüm iş akışı örnekleri arasında paylaşılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="0cbff-123">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="0cbff-124">Aşağıdaki kod örnekleri, bu adımların nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-124">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="0cbff-125">İlk olarak, türünün bir örneğini bildirin <xref:System.ServiceModel.Activities.SendMessageChannelCache> .</span><span class="sxs-lookup"><span data-stu-id="0cbff-125">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="0cbff-126">Ardından, her bir istemci iş akışı örneğine önbellek uzantısını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0cbff-126">Next, add the cache extension to each client workflow instance.</span></span>  
  
```csharp
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="0cbff-127">Barındırılan Iş akışı hizmeti için önbellek paylaşım düzeyini değiştirme</span><span class="sxs-lookup"><span data-stu-id="0cbff-127">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  

 <span data-ttu-id="0cbff-128">Barındırılan iş akışı hizmetinde önbellek paylaşımını ayarlamak için, sınıfın bir örneğini bir <xref:System.ServiceModel.Activities.SendMessageChannelCache> uzantı olarak tüm iş akışı hizmeti konaklarına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0cbff-128">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="0cbff-129">Bu, önbelleğin tüm iş akışı hizmeti konakları arasında paylaşılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="0cbff-129">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="0cbff-130">Aşağıdaki kod örnekleri, bu adımları gerçekleştirmek için gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-130">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="0cbff-131">İlk olarak, sınıf düzeyinde türünün bir örneğini bildirin <xref:System.ServiceModel.Activities.SendMessageChannelCache> .</span><span class="sxs-lookup"><span data-stu-id="0cbff-131">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="0cbff-132">Sonra, her iş akışı hizmeti konağına statik önbellek uzantısını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0cbff-132">Next, add the static cache extension to each workflow service host.</span></span>  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="0cbff-133">Barındırılan bir iş akışı hizmetindeki önbellek paylaşımını örnek düzeyine ayarlamak için, bir `Func<SendMessageChannelCache>` temsilciyi iş akışı hizmet konağına uzantı olarak ekleyin ve bu temsilciyi, sınıfının yeni bir örneğini örnekleyen koda atayın <xref:System.ServiceModel.Activities.SendMessageChannelCache> .</span><span class="sxs-lookup"><span data-stu-id="0cbff-133">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="0cbff-134">Bu, iş akışı hizmet ana bilgisayarındaki tüm iş akışı örnekleri tarafından paylaşılan tek bir önbellek yerine her bir iş akışı örneği için farklı bir önbellekte sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="0cbff-134">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="0cbff-135">Aşağıdaki kod örneği <xref:System.ServiceModel.Activities.SendMessageChannelCache> , temsilcinin işaret ettiği uzantıyı doğrudan tanımlamak için bir lambda ifadesi kullanarak bunu nasıl elde ettiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-135">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
```csharp
serviceHost.WorkflowExtensions.Add(() => new SendMessageChannelCache  
{  
    // Use FactorySettings property to add custom factory cache settings.  
    FactorySettings = new ChannelCacheSettings
    { MaxItemsInCache = 5, },  
    // Use ChannelSettings property to add custom channel cache settings.  
    ChannelSettings = new ChannelCacheSettings
    { MaxItemsInCache = 10 },  
});  
```  
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="0cbff-136">Önbellek ayarlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="0cbff-136">Customizing Cache Settings</span></span>  

 <span data-ttu-id="0cbff-137">Kanal fabrikası önbelleği ve kanal önbelleği için önbellek ayarlarını özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cbff-137">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="0cbff-138">Önbellek ayarları <xref:System.ServiceModel.Activities.ChannelCacheSettings> sınıfta tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0cbff-138">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="0cbff-139"><xref:System.ServiceModel.Activities.SendMessageChannelCache>Sınıfı, kanal fabrikası önbelleğinin varsayılan önbellek ayarlarını ve parametresiz oluşturucusunda kanal önbelleğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0cbff-139">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its parameterless constructor.</span></span> <span data-ttu-id="0cbff-140">Aşağıdaki tabloda her önbellek türü için bu önbellek ayarlarının varsayılan değerleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-140">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="0cbff-141">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="0cbff-141">Settings</span></span>|<span data-ttu-id="0cbff-142">LeaseTimeout (dk)</span><span class="sxs-lookup"><span data-stu-id="0cbff-142">LeaseTimeout (min)</span></span>|<span data-ttu-id="0cbff-143">IdleTimeout (dk)</span><span class="sxs-lookup"><span data-stu-id="0cbff-143">IdleTimeout (min)</span></span>|<span data-ttu-id="0cbff-144">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="0cbff-144">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="0cbff-145">Fabrika önbelleği varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0cbff-145">Factory Cache Default</span></span>|<span data-ttu-id="0cbff-146">TimeSpan. MaxValue</span><span class="sxs-lookup"><span data-stu-id="0cbff-146">TimeSpan.MaxValue</span></span>|<span data-ttu-id="0cbff-147">2</span><span class="sxs-lookup"><span data-stu-id="0cbff-147">2</span></span>|<span data-ttu-id="0cbff-148">16</span><span class="sxs-lookup"><span data-stu-id="0cbff-148">16</span></span>|  
|<span data-ttu-id="0cbff-149">Kanal önbelleği varsayılanı</span><span class="sxs-lookup"><span data-stu-id="0cbff-149">Channel Cache Default</span></span>|<span data-ttu-id="0cbff-150">5</span><span class="sxs-lookup"><span data-stu-id="0cbff-150">5</span></span>|<span data-ttu-id="0cbff-151">2</span><span class="sxs-lookup"><span data-stu-id="0cbff-151">2</span></span>|<span data-ttu-id="0cbff-152">16</span><span class="sxs-lookup"><span data-stu-id="0cbff-152">16</span></span>|  
  
 <span data-ttu-id="0cbff-153">Fabrika önbelleğini ve kanal önbelleği ayarlarını özelleştirmek için <xref:System.ServiceModel.Activities.SendMessageChannelCache> parametreli oluşturucuyu kullanarak sınıfı örneğini oluşturun <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> ve <xref:System.ServiceModel.Activities.ChannelCacheSettings> her bir ve parametresi için özel değerleri olan yeni bir örneğini geçirin `factorySettings` `channelSettings` .</span><span class="sxs-lookup"><span data-stu-id="0cbff-153">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="0cbff-154">Sonra, bu sınıfın yeni örneğini bir iş akışı hizmet konağına veya bir iş akışı örneğine uzantı olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0cbff-154">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="0cbff-155">Aşağıdaki kod örneği, bir iş akışı örneği için bu adımların nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-155">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(5),
                        LeaseTimeout = TimeSpan.FromMinutes(20)};  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(2),  
                        LeaseTimeout = TimeSpan.FromMinutes(10) };  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="0cbff-156">İş akışı hizmetiniz yapılandırmada tanımlı uç noktalara sahip olduğunda önbelleğe almayı etkinleştirmek için, <xref:System.ServiceModel.Activities.SendMessageChannelCache> <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> `allowUnsafeCaching` parametresi olarak ayarlanmış parametreli oluşturucuyu kullanarak sınıfı örneğini oluşturun `true` .</span><span class="sxs-lookup"><span data-stu-id="0cbff-156">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="0cbff-157">Sonra, bu sınıfın yeni örneğini bir iş akışı hizmet konağına veya bir iş akışı örneğine uzantı olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0cbff-157">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="0cbff-158">Aşağıdaki kod örneğinde, bir iş akışı örneği için önbelleğe almanın nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-158">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="0cbff-159">Kanal fabrikaları ve kanallar için önbelleği tamamen devre dışı bırakmak için, kanal fabrikası önbelleğini devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="0cbff-159">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="0cbff-160">Bunun yapılması, kanalların ilgili kanal fabrikalarına ait olduğu için kanal önbelleğini de kapatır.</span><span class="sxs-lookup"><span data-stu-id="0cbff-160">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="0cbff-161">Kanal fabrikası önbelleğini devre dışı bırakmak için, `factorySettings` parametresini <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> <xref:System.ServiceModel.Activities.ChannelCacheSettings> 0 değerine sahip bir örneğe başlatılan oluşturucuya geçirin <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> .</span><span class="sxs-lookup"><span data-stu-id="0cbff-161">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="0cbff-162">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-162">The following code example shows this.</span></span>  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="0cbff-163">Yalnızca kanal fabrikası önbelleğini kullanmayı seçebilir ve `channelSettings` parametresini <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> <xref:System.ServiceModel.Activities.ChannelCacheSettings> 0 değerine sahip bir örneğe başlatılan oluşturucuya geçirerek kanal önbelleğini devre dışı bırakabilirsiniz <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> .</span><span class="sxs-lookup"><span data-stu-id="0cbff-163">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="0cbff-164">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-164">The following code example shows this.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="0cbff-165">Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cbff-165">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="0cbff-166">Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0cbff-166">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="0cbff-167">Aşağıdaki örnek, `MyChannelCacheBehavior` özel fabrika önbelleği ve kanal önbelleği ayarları ile hizmet davranışını içeren bir yapılandırma dosyasının içeriğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cbff-167">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="0cbff-168">Bu hizmet davranışı, özelliği aracılığıyla hizmete eklenir `behaviorConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="0cbff-168">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>  
    <!-- List of other config sections here -->
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```
