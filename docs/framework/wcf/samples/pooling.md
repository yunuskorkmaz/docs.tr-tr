---
title: Biriktirme
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 46abc2c9c667ea7614581d7fafaa8e174db7f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183399"
---
# <a name="pooling"></a><span data-ttu-id="c7148-102">Biriktirme</span><span class="sxs-lookup"><span data-stu-id="c7148-102">Pooling</span></span>
<span data-ttu-id="c7148-103">Bu örnek, windows communication foundation'ın (WCF) nesne havuzuna nasıl genişletileni gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7148-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="c7148-104">Örnek, Kurumsal Hizmetler'in öznitelik işlevine `ObjectPoolingAttribute` sözdizimsel ve anlamsal olarak benzeyen bir öznitelik nasıl oluşturulacak larını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7148-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="c7148-105">Nesne birleştirme, uygulamanın performansına önemli bir destek sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c7148-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="c7148-106">Ancak, düzgün kullanılmaz ise ters etkiye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7148-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="c7148-107">Nesne birleştirme, yaygın başlatma gerektiren sık kullanılan nesneleri yeniden oluşturma ek yükü azaltmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c7148-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="c7148-108">Ancak, birleştirilmiş nesne üzerindeki bir yönteme yapılan çağrının tamamlanması önemli miktarda zaman alıyorsa, nesne biriktirme kuyruğa en kısa sürede en kısa sürede en kısa sürede ek istekler bir araya getirmek.</span><span class="sxs-lookup"><span data-stu-id="c7148-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="c7148-109">Bu nedenle, zaman adabı atarak bazı nesne oluşturma isteklerine hizmet etmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="c7148-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7148-110">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="c7148-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c7148-111">WCF uzantısı oluşturmanın ilk adımı, kullanılacak genişletilebilirlik noktasına karar vermektir.</span><span class="sxs-lookup"><span data-stu-id="c7148-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="c7148-112">WCF'de *sevkiyat* terimi, gelen iletileri kullanıcının hizmetindeki yöntem çağrılarına dönüştürmekten ve bu yöntemden giden iletiye dönüş değerlerini dönüştürmekten sorumlu bir çalışma zamanı bileşenianlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c7148-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="c7148-113">WCF hizmeti, her bitiş noktası için bir sevk irsaliyesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7148-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="c7148-114">Bir WCF istemcisi, söz konusu istemciyle ilişkili sözleşme çift yönlü bir sözleşmeyse, bir gönderici kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7148-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="c7148-115">Kanal ve uç nokta dağıtıcıları, gönderenin davranışını kontrol eden çeşitli özellikleri açığa çıkararak kanal ve sözleşme genelinde genişletilebilirlik sunar.</span><span class="sxs-lookup"><span data-stu-id="c7148-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="c7148-116">Özellik <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> ayrıca gönderme işlemini incelemenize, değiştirmenize veya özelleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c7148-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="c7148-117">Bu örnek, hizmet <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> sınıfının örneklerini sağlayan nesneyi işaret eden özelliğe odaklanır.</span><span class="sxs-lookup"><span data-stu-id="c7148-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="c7148-118">IInstanceSağlayıcı</span><span class="sxs-lookup"><span data-stu-id="c7148-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="c7148-119">WCF'de, gönderici <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimi uygulayan bir , kullanarak hizmet sınıfının örneklerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c7148-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="c7148-120">Bu arabirimin üç yöntemi vardır:</span><span class="sxs-lookup"><span data-stu-id="c7148-120">This interface has three methods:</span></span>  
  
- <span data-ttu-id="c7148-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Bir ileti geldiğinde, Dispatcher, iletiyi işlemek için hizmet sınıfının bir örneğini oluşturmak için <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="c7148-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="c7148-122">Bu yönteme yapılan çağrıların <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> sıklığı özellik tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="c7148-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="c7148-123">Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özellik gelen her <xref:System.ServiceModel.InstanceContextMode.PerCall> iletiyi işlemek için yeni bir hizmet sınıfı <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> örneği olarak ayarlanmışsa, ileti geldiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c7148-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="c7148-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: İleti bağımsız değişkeni olmadığında bu çağrılan dışında, bu önceki yöntemle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c7148-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
- <span data-ttu-id="c7148-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Bir hizmet örneğinin ömrü geçtiğinde, Sevk irsaliyesi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="c7148-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="c7148-126">Yöntemde <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> olduğu gibi, bu yönteme yapılan çağrıların <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> sıklığı özellik tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="c7148-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="c7148-127">Nesne Havuzu</span><span class="sxs-lookup"><span data-stu-id="c7148-127">The Object Pool</span></span>  
 <span data-ttu-id="c7148-128">Özel <xref:System.ServiceModel.Dispatcher.IInstanceProvider> bir uygulama, bir hizmet için gerekli nesne birleştirme semantik sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7148-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="c7148-129">Bu nedenle, bu `ObjectPoolingInstanceProvider` örnek havuzlama <xref:System.ServiceModel.Dispatcher.IInstanceProvider> için özel uygulama sağlayan bir türü vardır.</span><span class="sxs-lookup"><span data-stu-id="c7148-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="c7148-130"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> Yöntem `Dispatcher` çağırDığında, yeni bir örnek oluşturmak yerine, özel uygulama bellek içi bir havuzda varolan bir nesneyi arar.</span><span class="sxs-lookup"><span data-stu-id="c7148-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="c7148-131">Varsa, döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c7148-131">If one is available, it is returned.</span></span> <span data-ttu-id="c7148-132">Aksi takdirde, yeni bir nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c7148-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="c7148-133">`GetInstance` Uygulama aşağıdaki örnek kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="c7148-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
```csharp  
object IInstanceProvider.GetInstance(InstanceContext instanceContext, Message message)  
{  
    object obj = null;  
  
    lock (poolLock)  
    {  
        if (pool.Count > 0)  
        {  
            obj = pool.Pop();  
        }  
        else  
        {  
            obj = CreateNewPoolObject();  
        }  
        activeObjectsCount++;  
    }  
  
    WritePoolMessage(ResourceHelper.GetString("MsgNewObject"));  
  
    idleTimer.Stop();  
  
    return obj;
}  
```  
  
 <span data-ttu-id="c7148-134">Özel `ReleaseInstance` uygulama, serbest bırakılan örneği havuza geri ekler `ActiveObjectsCount` ve değeri eriter.</span><span class="sxs-lookup"><span data-stu-id="c7148-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="c7148-135">Bu `Dispatcher` yöntemleri farklı iş parçacıklarından arayabilirsiniz ve bu nedenle `ObjectPoolingInstanceProvider` sınıftaki sınıf düzeyi üyelerine eşitlenmiş erişim gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c7148-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
```csharp  
void IInstanceProvider.ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        pool.Push(instance);  
        activeObjectsCount--;  
  
        WritePoolMessage(  
        ResourceHelper.GetString("MsgObjectPooled"));  
  
        // When the service goes completely idle (no requests
        // are being processed), the idle timer is started  
        if (activeObjectsCount == 0)  
            idleTimer.Start();
    }  
}  
```  
  
 <span data-ttu-id="c7148-136">Yöntem `ReleaseInstance` bir "önbaşlatma temizleme" özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7148-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="c7148-137">Normalde havuz, havuzun ömrü boyunca en az sayıda nesne tutar.</span><span class="sxs-lookup"><span data-stu-id="c7148-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="c7148-138">Ancak, yapılandırmada belirtilen maksimum sınıra ulaşmak için havuzda ek nesneler oluşturmayı gerektiren aşırı kullanım dönemleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7148-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="c7148-139">Sonunda, havuz daha az etkin hale geldiğinde, bu artı nesneler ek bir ek yükü haline gelebilir.</span><span class="sxs-lookup"><span data-stu-id="c7148-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="c7148-140">Bu nedenle, `activeObjectsCount` sıfıra ulaştığında, bir temizleme döngüsünü tetikleyen ve gerçekleştiren bir boşta zamanlayıcı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="c7148-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="c7148-141">Davranışı Ekleme</span><span class="sxs-lookup"><span data-stu-id="c7148-141">Adding the Behavior</span></span>  
 <span data-ttu-id="c7148-142">Dispatcher katmanı uzantıları aşağıdaki davranışları kullanarak bağlanır:</span><span class="sxs-lookup"><span data-stu-id="c7148-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="c7148-143">Hizmet Davranışları.</span><span class="sxs-lookup"><span data-stu-id="c7148-143">Service Behaviors.</span></span> <span data-ttu-id="c7148-144">Bunlar, tüm hizmet çalışma zamanının özelleştirilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7148-144">These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="c7148-145">Bitiş Noktası Davranışları.</span><span class="sxs-lookup"><span data-stu-id="c7148-145">Endpoint Behaviors.</span></span> <span data-ttu-id="c7148-146">Bunlar, hizmet bitiş noktalarının, özellikle bir Kanal ve Bitiş Noktası Göndericinin özelleştirilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7148-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
- <span data-ttu-id="c7148-147">Sözleşme Davranışları.</span><span class="sxs-lookup"><span data-stu-id="c7148-147">Contract Behaviors.</span></span> <span data-ttu-id="c7148-148">Bunlar, istemci ve <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> hizmet sırasıyla hem de sınıfların özelleştirilmesiiçin izin verir.</span><span class="sxs-lookup"><span data-stu-id="c7148-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="c7148-149">Bir nesne birleştirme uzantısı amacıyla bir hizmet davranışı oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7148-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="c7148-150">Hizmet davranışları <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi uygulanarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c7148-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="c7148-151">Hizmet modelini özel davranışlardan haberdar etmenin birkaç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="c7148-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="c7148-152">Özel bir öznitelik kullanma.</span><span class="sxs-lookup"><span data-stu-id="c7148-152">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="c7148-153">Zorunlu olarak hizmet açıklamasının davranış koleksiyonuna ekleme.</span><span class="sxs-lookup"><span data-stu-id="c7148-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="c7148-154">Yapılandırma dosyasını genişletme.</span><span class="sxs-lookup"><span data-stu-id="c7148-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="c7148-155">Bu örnek özel bir öznitelik kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7148-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="c7148-156"><xref:System.ServiceModel.ServiceHost> Oluşturulduğunda, hizmetin tür tanımında kullanılan öznitelikleri inceler ve hizmet açıklamasının davranış koleksiyonuna kullanılabilir davranışları ekler.</span><span class="sxs-lookup"><span data-stu-id="c7148-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="c7148-157">Arayüzün <xref:System.ServiceModel.Description.IServiceBehavior> içinde üç yöntem <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>var <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>-- , , ve.</span><span class="sxs-lookup"><span data-stu-id="c7148-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="c7148-158">Yöntem, <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> davranışın hizmete uygulanabilmesini sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7148-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="c7148-159">Bu örnekte, uygulama hizmetin <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="c7148-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="c7148-160">Yöntem, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> hizmetin bağlaçlarını yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7148-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="c7148-161">Bu senaryoda gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c7148-161">It is not required in this scenario.</span></span> <span data-ttu-id="c7148-162">Bu, <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> hizmetin sevk gönderimlerini yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c7148-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="c7148-163">Bu yöntem, başharflere <xref:System.ServiceModel.ServiceHost> para verilirken WCF tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c7148-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="c7148-164">Aşağıdaki parametreler bu yönteme aktarılır:</span><span class="sxs-lookup"><span data-stu-id="c7148-164">The following parameters are passed into this method:</span></span>  
  
- <span data-ttu-id="c7148-165">`Description`: Bu bağımsız değişken, tüm hizmet için hizmet açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7148-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="c7148-166">Bu, hizmetin uç noktaları, sözleşmeleri, ciltleri ve diğer verilerle ilgili açıklama verilerini incelemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7148-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
- <span data-ttu-id="c7148-167">`ServiceHostBase`: Bu bağımsız <xref:System.ServiceModel.ServiceHostBase> değişken, şu anda başharflere getirilmekte olan şeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7148-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="c7148-168">Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulamada yeni bir `ObjectPoolingInstanceProvider` örnek anında ve ServiceHostBase <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> her <xref:System.ServiceModel.Dispatcher.DispatchRuntime> özelliğine atanır.</span><span class="sxs-lookup"><span data-stu-id="c7148-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
```csharp  
void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    // Create an instance of the ObjectPoolInstanceProvider.  
    ObjectPoolingInstanceProvider instanceProvider = new  
           ObjectPoolingInstanceProvider(description.ServiceType,
                                                    minPoolSize);  
  
    // Forward the call if we created a ServiceThrottlingBehavior.  
    if (this.throttlingBehavior != null)  
    {  
        ((IServiceBehavior)this.throttlingBehavior).ApplyDispatchBehavior(description, serviceHostBase);  
    }  
  
    // In case there was already a ServiceThrottlingBehavior
    // (this.throttlingBehavior==null), it should have initialized
    // a single ServiceThrottle on all ChannelDispatchers.
    // As we loop through the ChannelDispatchers, we verify that
    // and modify the ServiceThrottle to guard MaxPoolSize.  
    ServiceThrottle throttle = null;  
  
    foreach (ChannelDispatcherBase cdb in
            serviceHostBase.ChannelDispatchers)  
    {  
        ChannelDispatcher cd = cdb as ChannelDispatcher;  
        if (cd != null)  
        {  
            // Make sure there is exactly one throttle used by all
            // endpoints. If there were others, we could not enforce
            // MaxPoolSize.  
            if ((this.throttlingBehavior == null) &&
                        (this.maxPoolSize != Int32.MaxValue))  
            {  
                throttle ??= cd.ServiceThrottle;
                if (cd.ServiceThrottle == null)  
                {  
                    throw new
InvalidOperationException(ResourceHelper.GetString("ExNullThrottle"));  
                }  
                if (throttle != cd.ServiceThrottle)  
                {  
                    throw new InvalidOperationException(ResourceHelper.GetString("ExDifferentThrottle"));  
                }  
             }  
  
             foreach (EndpointDispatcher ed in cd.Endpoints)  
             {  
                 // Assign it to DispatchBehavior in each endpoint.  
                 ed.DispatchRuntime.InstanceProvider =
                                      instanceProvider;  
             }  
         }  
     }  
  
     // Set the MaxConcurrentInstances to limit the number of items
     // that will ever be requested from the pool.  
     if ((throttle != null) && (throttle.MaxConcurrentInstances >
                                      this.maxPoolSize))  
     {  
         throttle.MaxConcurrentInstances = this.maxPoolSize;  
     }  
}  
```  
  
 <span data-ttu-id="c7148-169">Bir <xref:System.ServiceModel.Description.IServiceBehavior> uygulamaya ek <xref:System.EnterpriseServices.ObjectPoolingAttribute> olarak sınıf öznitelik bağımsız değişkenleri kullanarak nesne havuzu özelleştirmek için birkaç üye vardır.</span><span class="sxs-lookup"><span data-stu-id="c7148-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="c7148-170">Bu <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>üyeler, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>.NET Enterprise Services tarafından sağlanan nesne birleştirme özelliğini eşleştirmek için , ve <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, içerir.</span><span class="sxs-lookup"><span data-stu-id="c7148-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="c7148-171">Nesne birleştirme davranışı artık yeni oluşturulan özel `ObjectPooling` öznitelik ile hizmet uygulaması açıklama yaparak bir WCF hizmetine eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c7148-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="c7148-172">Örneği Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c7148-172">Running the Sample</span></span>  
 <span data-ttu-id="c7148-173">Örnek, belirli senaryolarda nesne havuzu kullanılarak elde edilebilen performans avantajlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7148-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="c7148-174">Hizmet uygulaması iki hizmet `WorkService` uygular `ObjectPooledWorkService`-- ve .</span><span class="sxs-lookup"><span data-stu-id="c7148-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="c7148-175">Her iki hizmet de aynı uygulamayı paylaşıyor - her `DoWork()` ikisi de pahalı bir başlangıç gerektiriyor ve sonra nispeten ucuz bir yöntemi ortaya çıkarıyor.</span><span class="sxs-lookup"><span data-stu-id="c7148-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="c7148-176">Tek fark, yapılandırılan nesne havuzu `ObjectPooledWorkService` olmasıdır:</span><span class="sxs-lookup"><span data-stu-id="c7148-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
```csharp  
[ObjectPooling(MinPoolSize = 0, MaxPoolSize = 5)]  
public class ObjectPooledWorkService : IDoWork  
{  
    public ObjectPooledWorkService()  
    {  
        Thread.Sleep(5000);  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService instance created.");  
    }  
  
    public void DoWork()  
    {  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService.GetData() completed.");  
    }
}  
```  
  
 <span data-ttu-id="c7148-177">İstemciyi çalıştırdığınızda, `WorkService` 5 kez arama zaman.</span><span class="sxs-lookup"><span data-stu-id="c7148-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="c7148-178">Daha sonra kez `ObjectPooledWorkService` 5 kez arama.</span><span class="sxs-lookup"><span data-stu-id="c7148-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="c7148-179">Zaman farkı daha sonra görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="c7148-179">The difference in time is then displayed:</span></span>  
  
```console
Press <ENTER> to start the client.  
  
Calling WorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling WorkService took: 26722 ms.  
Calling ObjectPooledWorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling ObjectPooledWorkService took: 5323 ms.  
Press <ENTER> to exit.  
```  
  
> [!NOTE]
> <span data-ttu-id="c7148-180">İstemci ilk kez çalıştırıldığı zaman, her iki hizmet de yaklaşık olarak aynı süreyi alır gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="c7148-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="c7148-181">Örneği yeniden çalıştıran bu nesnenin bir `ObjectPooledWorkService` örneği havuzda zaten var olduğundan, çok daha hızlı döndürür görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7148-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c7148-182">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="c7148-182">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c7148-183">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="c7148-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c7148-184">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c7148-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c7148-185">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="c7148-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7148-186">Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c7148-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c7148-187">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7148-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c7148-188">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c7148-188">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c7148-189">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="c7148-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c7148-190">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7148-190">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
