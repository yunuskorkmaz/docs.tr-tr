---
title: Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 101aab98a7d34ad45ad29efbe252cff0814ca290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185390"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="11ebc-102">Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="11ebc-102">Changing the Cache Sharing Levels for Send Activities</span></span>
<span data-ttu-id="11ebc-103">Uzantı, <xref:System.ServiceModel.Activities.SendMessageChannelCache> ileti etkinliklerini kullanarak <xref:System.ServiceModel.Activities.Send> hizmet bitiş noktalarına ileti gönderen iş akışları için önbellek paylaşım düzeylerini, kanal fabrika önbelleğinin ayarlarını ve kanal önbelleğinin ayarlarını özelleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="11ebc-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="11ebc-104">Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="11ebc-104">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="11ebc-105">Kanal fabrika önbelleği önbelleğe alınmış <xref:System.ServiceModel.ChannelFactory%601> nesneler içerir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-105">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="11ebc-106">Kanal önbelleği önbelleğe alınmış kanallar içerir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-106">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11ebc-107">İş akışları, <xref:System.ServiceModel.Activities.Send> ileti veya parametre göndermek için ileti etkinliklerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-107">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="11ebc-108"><xref:System.ServiceModel.Channels.IRequestChannel> İş akışı çalışma süresi, bir <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.Send> etkinlikle etkinlik kullandığınızda ve bir <xref:System.ServiceModel.Channels.IOutputChannel> <xref:System.ServiceModel.Activities.Send> etkinlik kullandığınızda (hayır) <xref:System.ServiceModel.Activities.ReceiveReply>tür kanalları oluşturan önbelleğe kanal fabrikaları ekler.</span><span class="sxs-lookup"><span data-stu-id="11ebc-108">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="11ebc-109">Önbellek Paylaşım Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="11ebc-109">The Cache Sharing Levels</span></span>  
 <span data-ttu-id="11ebc-110">Varsayılan olarak, ileti etkinlikleri tarafından <xref:System.ServiceModel.WorkflowServiceHost> kullanılan önbellek <xref:System.ServiceModel.Activities.Send> tarafından barındırılan bir iş akışında <xref:System.ServiceModel.WorkflowServiceHost> (ana bilgisayar düzeyinde önbelleğe alma) tüm iş akışı örnekleri nde paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="11ebc-110">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="11ebc-111">Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-111">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="11ebc-112">Önbellek, güvenli olmayan <xref:System.ServiceModel.Activities.Send> önbelleğe alma etkinleştirilmedikçe yalnızca yapılandırmada tanımlanan uç noktaları kullanmayan etkinlikler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-112">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="11ebc-113">İş akışındaki etkinlikler ve bunların <xref:System.ServiceModel.Activities.Send> önerilen kullanımı için kullanılabilen farklı önbellek paylaşım düzeyleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="11ebc-113">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
- <span data-ttu-id="11ebc-114">**Ana Bilgisayar Düzeyi**: Ana bilgisayar paylaşım düzeyinde önbellek yalnızca iş akışı hizmeti ana bilgisayarda barındırılan iş akışı örnekleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-114">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="11ebc-115">Önbellek, iş akışı hizmeti ana bilgisayarları arasında işlem genişliğinde bir önbellekte de paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-115">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
- <span data-ttu-id="11ebc-116">**Örnek Düzeyi**: Örnek paylaşım düzeyinde, önbellek ömrü boyunca belirli bir iş akışı örneği için kullanılabilir, ancak önbellek diğer iş akışı örnekleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="11ebc-116">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
- <span data-ttu-id="11ebc-117">**Önbellek Yok**: Yapılandırmada tanımlanan uç noktaları kullanan bir iş akışınız varsa önbellek varsayılan olarak kapatılır.</span><span class="sxs-lookup"><span data-stu-id="11ebc-117">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="11ebc-118">Bu durumda önbelleği kapalı tutmanın güvenli olmadığı için de önerilir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-118">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="11ebc-119">Örneğin, her gönderi için farklı bir kimlik (farklı kimlik bilgileri veya kimliğe bürünme kullanımı) gerekiyorsa.</span><span class="sxs-lookup"><span data-stu-id="11ebc-119">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="11ebc-120">İstemci İş Akışı için Önbellek Paylaşım Düzeyini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="11ebc-120">Changing the Cache Sharing Level for a Client Workflow</span></span>  
 <span data-ttu-id="11ebc-121">Önbellek paylaşımını istemci iş akışında ayarlamak için, <xref:System.ServiceModel.Activities.SendMessageChannelCache> istenen iş akışı örnekleri kümesine uzantı olarak sınıfın bir örneğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="11ebc-121">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="11ebc-122">Bu, önbelleğin tüm iş akışı örnekleri arasında paylaşılmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="11ebc-122">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="11ebc-123">Aşağıdaki kod örnekleri, bu adımların nasıl gerçekleştirileceğimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-123">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="11ebc-124">İlk olarak, tür <xref:System.ServiceModel.Activities.SendMessageChannelCache>bir örnek bildirin.</span><span class="sxs-lookup"><span data-stu-id="11ebc-124">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="11ebc-125">Ardından, önbellek uzantısını her istemci iş akışı örneğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="11ebc-125">Next, add the cache extension to each client workflow instance.</span></span>  
  
```csharp
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="11ebc-126">Barındırılan İş Akışı Hizmeti için Önbellek Paylaşım Düzeyini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="11ebc-126">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  
 <span data-ttu-id="11ebc-127">Barındırılan bir iş akışı hizmetinde önbellek paylaşımını <xref:System.ServiceModel.Activities.SendMessageChannelCache> ayarlamak için, sınıfın bir örneğini tüm iş akışı hizmeti ana bilgisayarlarına uzantı olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="11ebc-127">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="11ebc-128">Bu, önbelleğin tüm iş akışı hizmeti ana bilgisayarlarında paylaşılmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="11ebc-128">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="11ebc-129">Aşağıdaki kod örnekleri, bu adımları gerçekleştirmek için gösterir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-129">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="11ebc-130">İlk olarak, sınıf <xref:System.ServiceModel.Activities.SendMessageChannelCache> düzeyinde bir tür örneği bildirin.</span><span class="sxs-lookup"><span data-stu-id="11ebc-130">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="11ebc-131">Ardından, her iş akışı hizmeti ana bilgisayarı için statik önbellek uzantısı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="11ebc-131">Next, add the static cache extension to each workflow service host.</span></span>  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="11ebc-132">Barındırılan iş akışı hizmetindeki önbellek paylaşımını örnek `Func<SendMessageChannelCache>` düzeyine ayarlamak için, iş akışı hizmeti ana bilgisayarının uzantısı olarak bir temsilci ekleyin <xref:System.ServiceModel.Activities.SendMessageChannelCache> ve bu temsilciyi sınıfın yeni bir örneğini anında atan koda atayın.</span><span class="sxs-lookup"><span data-stu-id="11ebc-132">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="11ebc-133">Bu, iş akışı hizmet ana bilgisayarındaki tüm iş akışı örnekleri tarafından paylaşılan tek bir önbellek yerine her iş akışı örneği için farklı bir önbellek sağlar.</span><span class="sxs-lookup"><span data-stu-id="11ebc-133">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="11ebc-134">Aşağıdaki kod örneği, temsilcinin işaret ettiği uzantıyı <xref:System.ServiceModel.Activities.SendMessageChannelCache> doğrudan tanımlamak için bir lambda ifadesi kullanarak bunu nasıl başarabilirsinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-134">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
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
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="11ebc-135">Önbellek Ayarlarını Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="11ebc-135">Customizing Cache Settings</span></span>  
 <span data-ttu-id="11ebc-136">Kanal fabrika önbelleği ve kanal önbelleği için önbellek ayarlarını özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11ebc-136">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="11ebc-137">Önbellek ayarları <xref:System.ServiceModel.Activities.ChannelCacheSettings> sınıfta tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="11ebc-137">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="11ebc-138">Sınıf, <xref:System.ServiceModel.Activities.SendMessageChannelCache> kanal fabrika önbelleği için varsayılan önbellek ayarlarını ve parametresiz oluşturucusundaki kanal önbelleği'ni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="11ebc-138">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its parameterless constructor.</span></span> <span data-ttu-id="11ebc-139">Aşağıdaki tabloda, her önbellek türü için bu önbellek ayarlarının varsayılan değerleri listelenir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-139">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="11ebc-140">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="11ebc-140">Settings</span></span>|<span data-ttu-id="11ebc-141">LeaseTimeout (dk)</span><span class="sxs-lookup"><span data-stu-id="11ebc-141">LeaseTimeout (min)</span></span>|<span data-ttu-id="11ebc-142">Boşta Zaman (dk)</span><span class="sxs-lookup"><span data-stu-id="11ebc-142">IdleTimeout (min)</span></span>|<span data-ttu-id="11ebc-143">MaxItemsInÖnbellek</span><span class="sxs-lookup"><span data-stu-id="11ebc-143">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="11ebc-144">Fabrika Önbellek Varsayılan</span><span class="sxs-lookup"><span data-stu-id="11ebc-144">Factory Cache Default</span></span>|<span data-ttu-id="11ebc-145">TimeSpan.MaxValue</span><span class="sxs-lookup"><span data-stu-id="11ebc-145">TimeSpan.MaxValue</span></span>|<span data-ttu-id="11ebc-146">2</span><span class="sxs-lookup"><span data-stu-id="11ebc-146">2</span></span>|<span data-ttu-id="11ebc-147">16</span><span class="sxs-lookup"><span data-stu-id="11ebc-147">16</span></span>|  
|<span data-ttu-id="11ebc-148">Kanal Önbelleği Varsayılan</span><span class="sxs-lookup"><span data-stu-id="11ebc-148">Channel Cache Default</span></span>|<span data-ttu-id="11ebc-149">5</span><span class="sxs-lookup"><span data-stu-id="11ebc-149">5</span></span>|<span data-ttu-id="11ebc-150">2</span><span class="sxs-lookup"><span data-stu-id="11ebc-150">2</span></span>|<span data-ttu-id="11ebc-151">16</span><span class="sxs-lookup"><span data-stu-id="11ebc-151">16</span></span>|  
  
 <span data-ttu-id="11ebc-152">Fabrika önbelleği ve kanal önbelleği ayarlarını özelleştirmek <xref:System.ServiceModel.Activities.SendMessageChannelCache> için, parametreli <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> oluşturucuyu kullanarak <xref:System.ServiceModel.Activities.ChannelCacheSettings> sınıfı anında anlayın `factorySettings` ve `channelSettings` özel değerlere sahip yeni bir örneğini her bir ve parametrelere geçirin.</span><span class="sxs-lookup"><span data-stu-id="11ebc-152">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="11ebc-153">Ardından, iş akışı hizmeti ana bilgisayarı veya iş akışı örneğine uzantı olarak bu sınıfın yeni örneğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="11ebc-153">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="11ebc-154">Aşağıdaki kod örneği, iş akışı örneği için bu adımların nasıl gerçekleştirilileceğigösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-154">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
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
  
 <span data-ttu-id="11ebc-155">İş akışı hizmetinizin yapılandırmada tanımlanan uç noktaları olduğunda önbelleğe alma sağlamak <xref:System.ServiceModel.Activities.SendMessageChannelCache> için, <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> `allowUnsafeCaching` `true`parametre olarak ayarlanmış parametreli oluşturucuyu kullanarak sınıfı anında</span><span class="sxs-lookup"><span data-stu-id="11ebc-155">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="11ebc-156">Ardından, iş akışı hizmeti ana bilgisayarı veya iş akışı örneğine uzantı olarak bu sınıfın yeni örneğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="11ebc-156">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="11ebc-157">Aşağıdaki kod örneği, iş akışı örneği için önbelleğe almanın nasıl etkinleştirileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-157">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="11ebc-158">Kanal fabrikaları ve kanallar için önbelleği tamamen devre dışı kakmak için kanal fabrika önbelleğini devre dışı edin.</span><span class="sxs-lookup"><span data-stu-id="11ebc-158">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="11ebc-159">Bunu yapmak, kanallar ilgili kanal fabrikalarına ait olduğundan kanal önbelleğini de kapatır.</span><span class="sxs-lookup"><span data-stu-id="11ebc-159">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="11ebc-160">Kanal fabrika önbelleğini devre dışı `factorySettings` katlamak için <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> parametreyi 0 <xref:System.ServiceModel.Activities.ChannelCacheSettings> <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> değeri olan bir örneğe başlatılan yapıya geçirin.</span><span class="sxs-lookup"><span data-stu-id="11ebc-160">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="11ebc-161">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-161">The following code example shows this.</span></span>  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="11ebc-162">Yalnızca kanal fabrika önbelleğini kullanmayı ve `channelSettings` parametreyi 0 <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> <xref:System.ServiceModel.Activities.ChannelCacheSettings> <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> değeri olan bir örneğe başlatılan yapıcıya geçirerek kanal önbelleğini devre dışı bırakmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11ebc-162">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="11ebc-163">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-163">The following code example shows this.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="11ebc-164">Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11ebc-164">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="11ebc-165">Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="11ebc-165">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="11ebc-166">Aşağıdaki örnek, özel fabrika önbelleği `MyChannelCacheBehavior` ve kanal önbelleği ayarlarıyla hizmet davranışını içeren bir yapılandırma dosyasının içeriğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-166">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="11ebc-167">Bu hizmet davranışı öznitelik aracılığıyla `behaviorConfiguration` hizmete eklenir.</span><span class="sxs-lookup"><span data-stu-id="11ebc-167">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
