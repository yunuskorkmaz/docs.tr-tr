---
title: Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 359a9189cee34eeb814a2303be3d2da725456e39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494550"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="cdc6a-102">Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="cdc6a-102">Changing the Cache Sharing Levels for Send Activities</span></span>
<span data-ttu-id="cdc6a-103"><xref:System.ServiceModel.Activities.SendMessageChannelCache> Uzantısı düzeyleri, kanal fabrikası önbellek ayarlarını paylaşımı önbellek özelleştirmenize olanak sağlar ve kanal ayarlarını önbelleğe kullanarak hizmet uç noktaları için ileti gönderme iş akışları için <xref:System.ServiceModel.Activities.Send> Mesajlaşma etkinlikleri.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="cdc6a-104">Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-104">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="cdc6a-105">Kanal fabrikası önbellek içeren önbelleğe alınmış <xref:System.ServiceModel.ChannelFactory%601> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-105">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="cdc6a-106">Kanal önbelleği önbelleğe alınmış kanalları içerir.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-106">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdc6a-107">İş akışları kullanabilirsiniz <xref:System.ServiceModel.Activities.Send> Mesajlaşma etkinlikleri iletileri veya parametreleri göndermek için.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-107">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="cdc6a-108">İş akışı çalışma zamanı tür kanallar oluşturmak önbelleğine kanal fabrikaları ekler <xref:System.ServiceModel.Channels.IRequestChannel> kullandığınızda, bir <xref:System.ServiceModel.Activities.ReceiveReply> etkinliği ile bir <xref:System.ServiceModel.Activities.Send> etkinliği ve bir <xref:System.ServiceModel.Channels.IOutputChannel> yalnızca kullanırken bir <xref:System.ServiceModel.Activities.Send> etkinlik (hiçbir <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="cdc6a-108">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="cdc6a-109">Önbellek paylaşımı düzeylerini</span><span class="sxs-lookup"><span data-stu-id="cdc6a-109">The Cache Sharing Levels</span></span>  
 <span data-ttu-id="cdc6a-110">Varsayılan olarak, bir iş akışı tarafından barındırılan bir <xref:System.ServiceModel.WorkflowServiceHost> tarafından kullanılan önbellek <xref:System.ServiceModel.Activities.Send> Mesajlaşma etkinlikleri tüm iş akışı örnekleri arasında paylaşılır <xref:System.ServiceModel.WorkflowServiceHost> (ana bilgisayar önbelleğe alma düzeyi).</span><span class="sxs-lookup"><span data-stu-id="cdc6a-110">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="cdc6a-111">Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-111">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="cdc6a-112">Önbellek yalnızca için kullanılabilir <xref:System.ServiceModel.Activities.Send> güvensiz önbelleğe alma etkin değilse yapılandırmasında tanımlanmış uç nokta kullanmayın etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-112">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="cdc6a-113">Düzeyleri için kullanılabilir paylaşımı farklı önbellek şunlardır <xref:System.ServiceModel.Activities.Send> bir iş akışı ve önerilen kullanımlarını etkinlikleri:</span><span class="sxs-lookup"><span data-stu-id="cdc6a-113">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
-   <span data-ttu-id="cdc6a-114">**Ana bilgisayar düzeyinde**: paylaşım düzeyi konak içinde önbellek iş akışı hizmeti ana bilgisayarında barındırılan iş akışı örnekleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-114">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="cdc6a-115">Bir önbellek de bir işlem genelinde önbellekte iş akışı hizmeti ana bilgisayarlar arasında paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-115">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
-   <span data-ttu-id="cdc6a-116">**Örnek düzeyi**: paylaşım düzeyi örneğinde önbellek belirli iş akışı örneği ömrü boyunca kullanılabilir, ancak önbellek diğer iş akışı örnekleri kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-116">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
-   <span data-ttu-id="cdc6a-117">**Önbellek yok**: yapılandırmasında tanımlanmış uç noktaları kullanan bir iş akışı varsa önbelleği varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-117">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="cdc6a-118">Ayrıca, açma güvensiz olabilir çünkü bu durumda kapalı önbellek tutmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-118">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="cdc6a-119">Örneğin, farklı bir kimlik (farklı kimlik bilgileri veya kimliğe bürünme özelliğini kullanarak) her gönderme için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-119">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="cdc6a-120">Paylaşım düzeyi için bir istemci iş akışı önbellek değiştirme</span><span class="sxs-lookup"><span data-stu-id="cdc6a-120">Changing the Cache Sharing Level for a Client Workflow</span></span>  
 <span data-ttu-id="cdc6a-121">Bir istemci iş akışında paylaşımı önbelleği ayarlamak için bir örnek ekler <xref:System.ServiceModel.Activities.SendMessageChannelCache> sınıfı istenen iş akışı örnekleri kümesi bir uzantısı olarak.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-121">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="cdc6a-122">Bu, tüm iş akışı örnekleri arasında önbellek paylaşımı ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-122">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="cdc6a-123">Aşağıdaki kod örnekleri, bu adımların nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-123">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="cdc6a-124">Öncelikle, türünün bir örneği bildirin <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-124">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="cdc6a-125">Ardından, her istemci iş akışı örneğine önbellek uzantısı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-125">Next, add the cache extension to each client workflow instance.</span></span>  
  
```  
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="cdc6a-126">Paylaşım düzeyi barındırılan iş akışı hizmeti için önbellek değiştirme</span><span class="sxs-lookup"><span data-stu-id="cdc6a-126">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  
 <span data-ttu-id="cdc6a-127">Barındırılan iş akışı hizmetinde paylaşımı önbelleği ayarlamak için bir örnek ekler <xref:System.ServiceModel.Activities.SendMessageChannelCache> tüm iş akışı hizmeti ana bir uzantısı olarak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-127">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="cdc6a-128">Bu, tüm iş akışı hizmeti ana bilgisayarlar arasında önbellek paylaşımı ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-128">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="cdc6a-129">Bu adımları gerçekleştirmek için aşağıdaki kod örnekleri göster.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-129">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="cdc6a-130">Öncelikle, türünün bir örneği bildirin <xref:System.ServiceModel.Activities.SendMessageChannelCache> sınıf düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-130">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="cdc6a-131">Ardından, statik önbellek uzantısı, her iş akışı hizmeti ana bilgisayarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-131">Next, add the static cache extension to each workflow service host.</span></span>  
  
```  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="cdc6a-132">Barındırılan iş akışı hizmeti örneği düzeyine paylaşımı önbelleği ayarlamak için ekleme bir `Func<SendMessageChannelCache>` temsilci iş akışı hizmeti ana bilgisayarı için bir uzantısı olarak ve yeni bir örneğini başlatır kodu bu temsilci atamak <xref:System.ServiceModel.Activities.SendMessageChannelCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-132">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="cdc6a-133">Bu, iş akışı hizmeti ana bilgisayar tüm iş akışı örnekleri tarafından paylaşılan tek bir önbellek yerine her ayrı ayrı iş akışı örneği için farklı bir önbellek sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-133">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="cdc6a-134">Aşağıdaki kod örneğinde, doğrudan tanımlamak için bir lambda ifadesi kullanarak bunu başarmanın gösterilmiştir <xref:System.ServiceModel.Activities.SendMessageChannelCache> temsilci işaret uzantısı.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-134">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
```  
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
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="cdc6a-135">Önbellek Ayarları özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cdc6a-135">Customizing Cache Settings</span></span>  
 <span data-ttu-id="cdc6a-136">Kanal fabrikası önbellek ve kanal önbelleği için önbellek ayarlarını özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-136">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="cdc6a-137">Önbellek ayarları tanımlanan <xref:System.ServiceModel.Activities.ChannelCacheSettings> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-137">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="cdc6a-138"><xref:System.ServiceModel.Activities.SendMessageChannelCache> Sınıfı, varsayılan kurucusunda kanal fabrikası önbellek ve kanal önbellek için varsayılan önbellek ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-138">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its default constructor.</span></span> <span data-ttu-id="cdc6a-139">Aşağıdaki tabloda bu önbellek ayarları önbellek her tür için varsayılan değerler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-139">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="cdc6a-140">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="cdc6a-140">Settings</span></span>|<span data-ttu-id="cdc6a-141">LeaseTimeout (min.)</span><span class="sxs-lookup"><span data-stu-id="cdc6a-141">LeaseTimeout (min)</span></span>|<span data-ttu-id="cdc6a-142">IdleTimeout (min.)</span><span class="sxs-lookup"><span data-stu-id="cdc6a-142">IdleTimeout (min)</span></span>|<span data-ttu-id="cdc6a-143">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="cdc6a-143">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="cdc6a-144">Fabrika önbellek varsayılan</span><span class="sxs-lookup"><span data-stu-id="cdc6a-144">Factory Cache Default</span></span>|<span data-ttu-id="cdc6a-145">TimeSpan.MaxValue</span><span class="sxs-lookup"><span data-stu-id="cdc6a-145">TimeSpan.MaxValue</span></span>|<span data-ttu-id="cdc6a-146">2</span><span class="sxs-lookup"><span data-stu-id="cdc6a-146">2</span></span>|<span data-ttu-id="cdc6a-147">16</span><span class="sxs-lookup"><span data-stu-id="cdc6a-147">16</span></span>|  
|<span data-ttu-id="cdc6a-148">Kanal önbellek varsayılan</span><span class="sxs-lookup"><span data-stu-id="cdc6a-148">Channel Cache Default</span></span>|<span data-ttu-id="cdc6a-149">5</span><span class="sxs-lookup"><span data-stu-id="cdc6a-149">5</span></span>|<span data-ttu-id="cdc6a-150">2</span><span class="sxs-lookup"><span data-stu-id="cdc6a-150">2</span></span>|<span data-ttu-id="cdc6a-151">16</span><span class="sxs-lookup"><span data-stu-id="cdc6a-151">16</span></span>|  
  
 <span data-ttu-id="cdc6a-152">Fabrika önbellek ve kanal önbellek ayarlarını özelleştirmek için örneği <xref:System.ServiceModel.Activities.SendMessageChannelCache> parametreli Oluşturucusu kullanılarak sınıf <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> ve yeni bir örneğini geçirin <xref:System.ServiceModel.Activities.ChannelCacheSettings> her biri için özel değerler ile `factorySettings` ve `channelSettings` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-152">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="cdc6a-153">Ardından, bu sınıfın yeni bir örneğini bir iş akışı hizmeti ana bilgisayarı veya bir iş akışı örneği bir uzantısı olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-153">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="cdc6a-154">Aşağıdaki kod örneği, bir iş akışı örneği için bu adımları uygulamadan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-154">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
```  
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
  
 <span data-ttu-id="cdc6a-155">İş akışı Hizmeti uç noktaları yapılandırmasında tanımlı olduğunda önbelleğe almayı etkinleştirmek için örneği <xref:System.ServiceModel.Activities.SendMessageChannelCache> parametreli Oluşturucusu kullanılarak sınıf <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> ile `allowUnsafeCaching` parametre kümesine `true`.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-155">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="cdc6a-156">Ardından, bu sınıfın yeni bir örneğini bir iş akışı hizmeti ana bilgisayarı veya bir iş akışı örneği bir uzantısı olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-156">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="cdc6a-157">Aşağıdaki kod örneği, bir iş akışı örneği için önbelleğe almayı etkinleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-157">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="cdc6a-158">Kanal fabrikaları ve kanallar için tamamen önbelleği devre dışı bırakmak için kanal fabrikası önbelleği devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-158">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="cdc6a-159">Kanallar, karşılık gelen kanal üreteçleri tarafından sahip olunan gibi Bunun yapılması kanal önbelleği devre dışı de etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-159">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="cdc6a-160">Kanal fabrikası önbelleğini devre dışı bırakmak için geçirdiğiniz `factorySettings` parametresi <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> Oluşturucusu başlatılır bir <xref:System.ServiceModel.Activities.ChannelCacheSettings> örneği bir <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 0 değeri.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-160">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="cdc6a-161">Aşağıdaki kod örneğinde bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-161">The following code example shows this.</span></span>  
  
```  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="cdc6a-162">Yalnızca kanal fabrikası önbelleğinin kullanımı ve geçirerek kanal önbelleğini devre dışı bırakmak seçebileceğiniz `channelSettings` parametresi <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> Oluşturucusu başlatılır bir <xref:System.ServiceModel.Activities.ChannelCacheSettings> örneği bir <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 0 değeri.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-162">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="cdc6a-163">Aşağıdaki kod örneğinde bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-163">The following code example shows this.</span></span>  
  
```  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="cdc6a-164">Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-164">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="cdc6a-165">Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-165">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="cdc6a-166">Aşağıdaki örnek içeren bir yapılandırma dosyası içeriğini gösterir `MyChannelCacheBehavior` hizmet davranışı özel fabrika önbellek ve kanal önbellek ayarlarına.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-166">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="cdc6a-167">Bu hizmet davranışı hizmet aracılığıyla eklenen `behaviorConfiguarion` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="cdc6a-167">This service behavior is added to the service through the `behaviorConfiguarion` attribute.</span></span>  
  
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
