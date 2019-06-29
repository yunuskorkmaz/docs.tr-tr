---
title: Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 079eb037f074155aec3ad5473480bbf5d4d341b2
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425162"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="e6e42-102">Gönderme İşlemleri için Önbellek Paylaşımı Düzeylerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="e6e42-102">Changing the Cache Sharing Levels for Send Activities</span></span>
<span data-ttu-id="e6e42-103"><xref:System.ServiceModel.Activities.SendMessageChannelCache> Uzantısı düzeyleri, kanal üreteci önbellek ayarlarını paylaşımı önbellek özelleştirmenize olanak sağlar ve ileti göndermek için hizmet uç noktaları kullanarak iş akışları için kanal ayarlarıyla önbelleğe <xref:System.ServiceModel.Activities.Send> Mesajlaşma etkinlikleri.</span><span class="sxs-lookup"><span data-stu-id="e6e42-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="e6e42-104">Bu iş akışları genellikle istemci iş akışlarıdır ancak içinde barındırılan iş akışı Hizmetleri ayrıca olabilir bir <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="e6e42-104">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="e6e42-105">Kanal üreteci önbellek içeren önbelleğe alınmış <xref:System.ServiceModel.ChannelFactory%601> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e6e42-105">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="e6e42-106">Kanal önbellek önbelleğe alınmış kanalları içerir.</span><span class="sxs-lookup"><span data-stu-id="e6e42-106">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6e42-107">İş akışları kullanabilirsiniz <xref:System.ServiceModel.Activities.Send> Mesajlaşma iletileri ya da parametreler göndermek için etkinlikleri.</span><span class="sxs-lookup"><span data-stu-id="e6e42-107">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="e6e42-108">İş akışı çalışma zamanı kanal fabrikaları kanal türü oluşturan önbelleğe ekler <xref:System.ServiceModel.Channels.IRequestChannel> kullandığınızda bir <xref:System.ServiceModel.Activities.ReceiveReply> etkinliği ile bir <xref:System.ServiceModel.Activities.Send> etkinliği ve bir <xref:System.ServiceModel.Channels.IOutputChannel> kullanırken yalnızca bir <xref:System.ServiceModel.Activities.Send> etkinlik (hiçbir <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="e6e42-108">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="e6e42-109">Önbellek paylaşımı düzeylerini</span><span class="sxs-lookup"><span data-stu-id="e6e42-109">The Cache Sharing Levels</span></span>  
 <span data-ttu-id="e6e42-110">Varsayılan olarak, bir iş akışı tarafından barındırılan bir <xref:System.ServiceModel.WorkflowServiceHost> tarafından kullanılan önbellek <xref:System.ServiceModel.Activities.Send> Mesajlaşma etkinlikleriyle iş akışı durumlarda arasında paylaşılır <xref:System.ServiceModel.WorkflowServiceHost> (ana bilgisayar önbelleğe alma düzeyi).</span><span class="sxs-lookup"><span data-stu-id="e6e42-110">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="e6e42-111">Tarafından barındırılmadığında bir istemci iş akışı için bir <xref:System.ServiceModel.WorkflowServiceHost>, önbelleğe yalnızca (örnek düzeyi önbelleğe alma) iş akışı örneği için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6e42-111">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="e6e42-112">Önbelleği yalnızca kullanılabilir <xref:System.ServiceModel.Activities.Send> bitiş noktaları yapılandırmasında tanımlandığı, güvenli olmayan önbelleğe almanın etkin olup sürece kullanmayan etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="e6e42-112">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="e6e42-113">Aşağıdakiler için kullanılabilir düzeyleri paylaşımı farklı bir önbellek, <xref:System.ServiceModel.Activities.Send> etkinlikleri iş akışı ve önerilen kullanımları:</span><span class="sxs-lookup"><span data-stu-id="e6e42-113">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
- <span data-ttu-id="e6e42-114">**Konak düzeyinde**: Konak paylaşım düzeyi, önbelleğe yalnızca iş akışı hizmeti ana bilgisayarında barındırılan iş akışı örnekleri için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6e42-114">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="e6e42-115">Bir önbellek, ayrıca iş akışı hizmeti konak işlem genelinde önbelleğinde arasında paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="e6e42-115">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
- <span data-ttu-id="e6e42-116">**Örnek düzeyi**: Önbellek paylaşım düzeyi örneğin ömrü boyunca belirli bir iş akışı örneği için kullanılabilir ancak önbelleği için diğer iş akışı örnekleri kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="e6e42-116">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
- <span data-ttu-id="e6e42-117">**Önbelleğin**: Bitiş noktaları yapılandırmasında tanımlandığı kullanan bir iş akışı varsa önbelleği varsayılan olarak kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6e42-117">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="e6e42-118">Ayrıca, açma güvensiz olabilir çünkü bu durumda kapalı önbellek tutmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="e6e42-118">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="e6e42-119">Örneğin, farklı bir kimlik (farklı kimlik bilgileri veya kimliğe bürünme kullanma) her gönderme için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e6e42-119">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="e6e42-120">Bir istemci iş akışı için paylaşım düzeyi önbellek değiştirme</span><span class="sxs-lookup"><span data-stu-id="e6e42-120">Changing the Cache Sharing Level for a Client Workflow</span></span>  
 <span data-ttu-id="e6e42-121">Bir istemci iş akışında paylaşımı önbellek ayarlamak için bir örneğini ekleme <xref:System.ServiceModel.Activities.SendMessageChannelCache> istenen iş akışı örnekleri kümesi için bir genişletme olarak sınıf.</span><span class="sxs-lookup"><span data-stu-id="e6e42-121">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="e6e42-122">Bu, tüm iş akışı örnekleri arasında önbellek paylaşımı ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e6e42-122">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="e6e42-123">Aşağıdaki kod örnekleri, bu adımların nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6e42-123">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="e6e42-124">İlk olarak, türün bir örneğini bildirmeniz <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span><span class="sxs-lookup"><span data-stu-id="e6e42-124">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="e6e42-125">Ardından, her istemci iş akışı örneği için önbellek uzantısı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e6e42-125">Next, add the cache extension to each client workflow instance.</span></span>  
  
```csharp 
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="e6e42-126">Paylaşım düzeyi barındırılan iş akışı hizmeti için önbellek değiştirme</span><span class="sxs-lookup"><span data-stu-id="e6e42-126">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  
 <span data-ttu-id="e6e42-127">Bir barındırılan iş akışı hizmetinde paylaşımı önbellek ayarlamak için bir örneğini ekleme <xref:System.ServiceModel.Activities.SendMessageChannelCache> tüm iş akışı hizmet konakları için bir genişletme olarak sınıf.</span><span class="sxs-lookup"><span data-stu-id="e6e42-127">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="e6e42-128">Bu, tüm iş akışı hizmeti konak arasında önbellek paylaşımı ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e6e42-128">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="e6e42-129">Bu adımları gerçekleştirmek için aşağıdaki kod örnekleri göster.</span><span class="sxs-lookup"><span data-stu-id="e6e42-129">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="e6e42-130">İlk olarak, türün bir örneğini bildirmeniz <xref:System.ServiceModel.Activities.SendMessageChannelCache> sınıf düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="e6e42-130">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="e6e42-131">Ardından, her iş akışı hizmeti konağı için statik önbellek uzantısı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e6e42-131">Next, add the static cache extension to each workflow service host.</span></span>  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="e6e42-132">Örnek düzeyi bir barındırılan iş akışı hizmetinde paylaşımı önbellek için ekleyin bir `Func<SendMessageChannelCache>` temsilci iş akışı hizmeti konağı için bir genişletme olarak ve yeni bir örneğini başlatan kodu bu temsilci atama <xref:System.ServiceModel.Activities.SendMessageChannelCache> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e6e42-132">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="e6e42-133">İş akışı hizmeti konak tüm iş akışı örnekleri tarafından paylaşılan tek bir önbellek yerine her bir ayrı ayrı iş akışı örneği için farklı bir önbellek sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e6e42-133">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="e6e42-134">Aşağıdaki kod örneği, doğrudan tanımlamak için bir lambda ifadesi kullanarak bunu başarmanın gösterilmektedir <xref:System.ServiceModel.Activities.SendMessageChannelCache> temsilci işaret uzantısı.</span><span class="sxs-lookup"><span data-stu-id="e6e42-134">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
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
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="e6e42-135">Önbellek ayarlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e6e42-135">Customizing Cache Settings</span></span>  
 <span data-ttu-id="e6e42-136">Kanal üreteci önbellek ve kanal önbellek için önbellek ayarlarını özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6e42-136">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="e6e42-137">Önbellek ayarları tanımlanan <xref:System.ServiceModel.Activities.ChannelCacheSettings> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e6e42-137">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="e6e42-138"><xref:System.ServiceModel.Activities.SendMessageChannelCache> Sınıf varsayılan oluşturucusuna varsayılan kanal üreteci önbellek ve kanal önbellek için önbellek ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e6e42-138">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its default constructor.</span></span> <span data-ttu-id="e6e42-139">Aşağıdaki tabloda, bu önbelleğin her türü için önbellek ayarları için varsayılan değerleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e6e42-139">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="e6e42-140">Ayarlar</span><span class="sxs-lookup"><span data-stu-id="e6e42-140">Settings</span></span>|<span data-ttu-id="e6e42-141">LeaseTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="e6e42-141">LeaseTimeout (min)</span></span>|<span data-ttu-id="e6e42-142">IdleTimeout (min)</span><span class="sxs-lookup"><span data-stu-id="e6e42-142">IdleTimeout (min)</span></span>|<span data-ttu-id="e6e42-143">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="e6e42-143">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="e6e42-144">Önbellek varsayılan fabrika</span><span class="sxs-lookup"><span data-stu-id="e6e42-144">Factory Cache Default</span></span>|<span data-ttu-id="e6e42-145">TimeSpan.MaxValue</span><span class="sxs-lookup"><span data-stu-id="e6e42-145">TimeSpan.MaxValue</span></span>|<span data-ttu-id="e6e42-146">2</span><span class="sxs-lookup"><span data-stu-id="e6e42-146">2</span></span>|<span data-ttu-id="e6e42-147">16</span><span class="sxs-lookup"><span data-stu-id="e6e42-147">16</span></span>|  
|<span data-ttu-id="e6e42-148">Kanal önbellek varsayılan</span><span class="sxs-lookup"><span data-stu-id="e6e42-148">Channel Cache Default</span></span>|<span data-ttu-id="e6e42-149">5</span><span class="sxs-lookup"><span data-stu-id="e6e42-149">5</span></span>|<span data-ttu-id="e6e42-150">2</span><span class="sxs-lookup"><span data-stu-id="e6e42-150">2</span></span>|<span data-ttu-id="e6e42-151">16</span><span class="sxs-lookup"><span data-stu-id="e6e42-151">16</span></span>|  
  
 <span data-ttu-id="e6e42-152">Üreteci önbellek ve kanal önbellek ayarlarını özelleştirmek için örneği <xref:System.ServiceModel.Activities.SendMessageChannelCache> parametreli bir kurucu kullanarak <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> ve yeni bir örneğini geçirin <xref:System.ServiceModel.Activities.ChannelCacheSettings> her biri için özel değerlerle `factorySettings` ve `channelSettings` Parametreler.</span><span class="sxs-lookup"><span data-stu-id="e6e42-152">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="e6e42-153">Ardından, bu sınıfın yeni bir örneğini bir iş akışı hizmeti konak ya da bir iş akışı örneği bir uzantısı olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e6e42-153">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="e6e42-154">Aşağıdaki kod örneği, bir iş akışı örneği için bu adımları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e6e42-154">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
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
  
 <span data-ttu-id="e6e42-155">İş akışı hizmetinizi bitiş noktaları yapılandırmasında tanımlandığı sahip olduğunda önbelleğe almayı etkinleştirmek için örneği <xref:System.ServiceModel.Activities.SendMessageChannelCache> parametreli bir kurucu kullanarak <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> ile `allowUnsafeCaching` parametresini `true`.</span><span class="sxs-lookup"><span data-stu-id="e6e42-155">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="e6e42-156">Ardından, bu sınıfın yeni bir örneğini bir iş akışı hizmeti konak ya da bir iş akışı örneği bir uzantısı olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e6e42-156">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="e6e42-157">Aşağıdaki kod örneği, bir iş akışı örneği için önbelleğe almayı etkinleştirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e6e42-157">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="e6e42-158">Kanal fabrikaları ve kanallar için tamamen önbelleğini devre dışı bırakmak için kanal üreteci önbellek devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="e6e42-158">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="e6e42-159">Kanal tarafından karşılık gelen, kanal fabrikaları sahip olduğu gibi Bunun yapılması kanal önbellek de etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="e6e42-159">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="e6e42-160">Kanal üreteci önbellek devre dışı bırakmak için geçirmek `factorySettings` parametresi <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> oluşturucusu için başlatılan bir <xref:System.ServiceModel.Activities.ChannelCacheSettings> ile örnek bir <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 0 değeri.</span><span class="sxs-lookup"><span data-stu-id="e6e42-160">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="e6e42-161">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6e42-161">The following code example shows this.</span></span>  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="e6e42-162">Yalnızca kanal üreteci önbellek ve kanal önbellek geçirerek devre dışı seçebilirsiniz `channelSettings` parametresi <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> oluşturucusu için başlatılan bir <xref:System.ServiceModel.Activities.ChannelCacheSettings> ile örnek bir <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 0 değeri.</span><span class="sxs-lookup"><span data-stu-id="e6e42-162">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="e6e42-163">Aşağıdaki kod örneği bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6e42-163">The following code example shows this.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="e6e42-164">Barındırılan iş akışı hizmetinde, uygulama yapılandırma dosyasında üreteci önbellek ve kanal önbellek ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6e42-164">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="e6e42-165">Bunu yapmak için üretecini ve kanal önbellek için önbellek ayarlarını içeren bir hizmet davranışını ekleyin ve bu hizmet davranışını hizmetinize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e6e42-165">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="e6e42-166">Aşağıdaki örnek, içeren bir yapılandırma dosyası içeriğini gösterir `MyChannelCacheBehavior` özel üreteci önbellek ve kanal önbellek ayarları ile hizmet davranışı.</span><span class="sxs-lookup"><span data-stu-id="e6e42-166">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="e6e42-167">Bu hizmet davranışını hizmet aracılığıyla eklenen `behaviorConfiguration` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e6e42-167">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
