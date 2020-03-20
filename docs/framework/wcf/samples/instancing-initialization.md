---
title: Başlatmayı Örneklendirme
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 897bb62df0a23073827aeed18b54bf77e8c6d4bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183604"
---
# <a name="instancing-initialization"></a><span data-ttu-id="19753-102">Başlatmayı Örneklendirme</span><span class="sxs-lookup"><span data-stu-id="19753-102">Instancing Initialization</span></span>
<span data-ttu-id="19753-103">Bu örnek, bir arabirim tanımlayarak [Havuzlama](../../../../docs/framework/wcf/samples/pooling.md) örneğini genişletir, `IObjectControl`bu da bir nesnenin başlatılmasını etkinleştirerek ve devre dışı kılarak özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="19753-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="19753-104">İstemci, nesneyi havuza döndüren ve nesneyi havuza döndürmeden yöntemler çağırır.</span><span class="sxs-lookup"><span data-stu-id="19753-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19753-105">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="19753-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="19753-106">Genişletilebilirlik Noktaları</span><span class="sxs-lookup"><span data-stu-id="19753-106">Extensibility Points</span></span>  
 <span data-ttu-id="19753-107">Bir Windows Communication Foundation (WCF) uzantısı oluşturmanın ilk adımı, kullanılacak genişletilebilirlik noktasına karar vermektir.</span><span class="sxs-lookup"><span data-stu-id="19753-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="19753-108">WCF'de *EndpointDispatcher* terimi, gelen iletileri kullanıcının hizmetindeki yöntem çağrılarına dönüştürmekten ve bu yöntemden gelen bir iletiye dönüş değerlerini dönüştürmekten sorumlu bir çalışma zamanı bileşenini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="19753-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="19753-109">WCF hizmeti, her bitiş noktası için bir EndpointDispatcher oluşturur.</span><span class="sxs-lookup"><span data-stu-id="19753-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="19753-110"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher> EndpointDispatcher, sınıfı kullanarak uç nokta kapsamı (hizmet tarafından alınan veya gönderilen tüm iletiler için) genişletilebilirlik sunar.</span><span class="sxs-lookup"><span data-stu-id="19753-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="19753-111">Bu sınıf, EndpointDispatcher davranışını denetleyen çeşitli özellikleri özelleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="19753-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="19753-112">Bu örnek, hizmet <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> sınıfının örneklerini sağlayan nesneyi işaret eden özelliğe odaklanır.</span><span class="sxs-lookup"><span data-stu-id="19753-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="19753-113">ıınstanceprovider</span><span class="sxs-lookup"><span data-stu-id="19753-113">IInstanceProvider</span></span>  
 <span data-ttu-id="19753-114">WCF'de, EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimi uygulayan bir örnek sağlayıcı kullanarak bir hizmet sınıfı örnekleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="19753-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="19753-115">Bu arabirimin yalnızca iki yöntemi vardır:</span><span class="sxs-lookup"><span data-stu-id="19753-115">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="19753-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: İleti geldiğinde, Dispatcher iletiyi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> işlemek için hizmet sınıfının bir örneğini oluşturmak için yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="19753-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="19753-117">Bu yönteme yapılan çağrıların <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> sıklığı özellik tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="19753-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="19753-118">Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özellik , gelen her iletiyi işlemek için yeni bir hizmet <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> sınıfı örneği oluşturulacak şekilde ayarlanmışsa, ileti geldiğinde çağrılır. <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="19753-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="19753-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Hizmet örneği iletiyi işlemeyi bitirdiğinde, EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="19753-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="19753-120"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> Yöntemde olduğu gibi, bu yönteme yapılan çağrıların <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> sıklığı özellik tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="19753-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="19753-121">Nesne Havuzu</span><span class="sxs-lookup"><span data-stu-id="19753-121">The Object Pool</span></span>  
 <span data-ttu-id="19753-122">Sınıf `ObjectPoolInstanceProvider` nesne havuzu için uygulama içerir.</span><span class="sxs-lookup"><span data-stu-id="19753-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="19753-123">Bu sınıf, <xref:System.ServiceModel.Dispatcher.IInstanceProvider> hizmet modeli katmanı ile etkileşim için arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="19753-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="19753-124">EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yöntemi çağırdığında, yeni bir örnek oluşturmak yerine, özel uygulama bellek içi bir havuzda varolan bir nesneyi arar.</span><span class="sxs-lookup"><span data-stu-id="19753-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="19753-125">Varsa, döndürülür.</span><span class="sxs-lookup"><span data-stu-id="19753-125">If one is available, it is returned.</span></span> <span data-ttu-id="19753-126">Aksi `ObjectPoolInstanceProvider` takdirde, `ActiveObjectsCount` özelliğin (havuzdan döndürülen nesne sayısı) maksimum havuz boyutuna ulaşıp ulaşmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="19753-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="19753-127">Değilse, yeni bir örnek oluşturulur ve arayana döndürülür ve `ActiveObjectsCount` daha sonra artımlanır.</span><span class="sxs-lookup"><span data-stu-id="19753-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="19753-128">Aksi takdirde, nesne oluşturma isteği yapılandırılmış bir süre için sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="19753-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="19753-129">`GetObjectFromThePool` Uygulama aşağıdaki örnek kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="19753-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
```csharp
private object GetObjectFromThePool()  
{  
    bool didNotTimeout =
       availableCount.WaitOne(creationTimeout, true);  
    if(didNotTimeout)  
    {  
         object obj = null;  
         lock (poolLock)  
        {  
             if (pool.Count != 0)  
             {  
                   obj = pool.Pop();  
                   activeObjectsCount++;  
             }  
             else if (pool.Count == 0)  
             {  
                   if (activeObjectsCount < maxPoolSize)  
                   {  
                        obj = CreateNewPoolObject();  
                        activeObjectsCount++;  
  
                        #if (DEBUG)  
                        WritePoolMessage(  
                             ResourceHelper.GetString("MsgNewObject"));  
                       #endif  
                   }
            }  
           idleTimer.Stop();  
      }  
     // Call the Activate method if possible.  
    if (obj is IObjectControl)  
   {  
         ((IObjectControl)obj).Activate();  
   }  
   return obj;  
}  
throw new TimeoutException(  
ResourceHelper.GetString("ExObjectCreationTimeout"));  
}  
```  
  
 <span data-ttu-id="19753-130">Özel `ReleaseInstance` uygulama, serbest bırakılan örneği havuza geri ekler `ActiveObjectsCount` ve değeri eriter.</span><span class="sxs-lookup"><span data-stu-id="19753-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="19753-131">EndpointDispatcher bu yöntemleri farklı iş iş parçacıklarından çağırabilir ve bu nedenle `ObjectPoolInstanceProvider` sınıftaki sınıf düzeyi üyelerine eşitlenmiş erişim gereklidir.</span><span class="sxs-lookup"><span data-stu-id="19753-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
```csharp
public void ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        // Check whether the object can be pooled.
        // Call the Deactivate method if possible.  
        if (instance is IObjectControl)  
        {  
            IObjectControl objectControl = (IObjectControl)instance;  
            objectControl.Deactivate();  
  
            if (objectControl.CanBePooled)  
            {  
                pool.Push(instance);  
  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectPooled"));  
                #endif
            }  
            else  
            {  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectWasNotPooled"));  
                #endif  
            }  
        }  
        else  
        {  
            pool.Push(instance);  
  
            #if(DEBUG)  
            WritePoolMessage(  
                ResourceHelper.GetString("MsgObjectPooled"));  
            #endif
        }  
  
        activeObjectsCount--;  
  
        if (activeObjectsCount == 0)  
        {  
            idleTimer.Start();
        }  
    }  
  
    availableCount.Release(1);  
}  
```  
  
 <span data-ttu-id="19753-132">Yöntem, `ReleaseInstance` bir *temizleme başlatma* özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="19753-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="19753-133">Normalde havuz, havuzun ömrü boyunca en az sayıda nesne tutar.</span><span class="sxs-lookup"><span data-stu-id="19753-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="19753-134">Ancak, yapılandırmada belirtilen maksimum sınıra ulaşmak için havuzda ek nesneler oluşturmayı gerektiren aşırı kullanım dönemleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="19753-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="19753-135">Sonunda havuz daha az aktif hale geldiğinde bu artı nesneler ekstra bir ek yükü haline gelebilir.</span><span class="sxs-lookup"><span data-stu-id="19753-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="19753-136">Bu nedenle `activeObjectsCount` sıfıra ulaştığında bir temizleme döngüsü tetikler ve gerçekleştirir bir boşta zamanlayıcı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="19753-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();
}  
```  
  
 <span data-ttu-id="19753-137">ServiceModel katman uzantıları aşağıdaki davranışları kullanarak bağlanır:</span><span class="sxs-lookup"><span data-stu-id="19753-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="19753-138">Hizmet Davranışları: Bunlar, tüm hizmet çalışma zamanının özelleştirilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="19753-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="19753-139">Bitiş Noktası Davranışları: Bunlar, EndpointDispatcher da dahil olmak üzere belirli bir hizmet bitiş noktasının özelleştirilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="19753-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="19753-140">Sözleşme Davranışları: Bunlar, istemci veya <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> hizmetteki sınıfların sırasıyla özelleştirilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="19753-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="19753-141">İşlem Davranışları: Bunlar, istemci <xref:System.ServiceModel.Dispatcher.ClientOperation> veya <xref:System.ServiceModel.Dispatcher.DispatchOperation> hizmetteki sınıfların sırasıyla özelleştirilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="19753-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="19753-142">Nesne birleştirme uzantısı amacıyla, bitiş noktası davranışı veya hizmet davranışı oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="19753-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="19753-143">Bu örnekte, nesne birleştirme yeteneğini hizmetin her bitiş noktasına uygulayan bir hizmet davranışı kullanırız.</span><span class="sxs-lookup"><span data-stu-id="19753-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="19753-144">Hizmet davranışları <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi uygulanarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="19753-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="19753-145">ServiceModel'i özel davranışlardan haberdar etmenin birkaç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="19753-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="19753-146">Özel bir öznitelik kullanma.</span><span class="sxs-lookup"><span data-stu-id="19753-146">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="19753-147">Zorunlu olarak hizmet açıklamasının davranış koleksiyonuna ekleme.</span><span class="sxs-lookup"><span data-stu-id="19753-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="19753-148">Yapılandırma dosyasını genişletme.</span><span class="sxs-lookup"><span data-stu-id="19753-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="19753-149">Bu örnek özel bir öznitelik kullanır.</span><span class="sxs-lookup"><span data-stu-id="19753-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="19753-150"><xref:System.ServiceModel.ServiceHost> Oluşturulduğunda, hizmetin tür tanımında kullanılan öznitelikleri inceler ve hizmet açıklamasının davranış koleksiyonuna kullanılabilir davranışları ekler.</span><span class="sxs-lookup"><span data-stu-id="19753-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="19753-151"><xref:System.ServiceModel.Description.IServiceBehavior> Arabirimin üç yöntemi <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>vardır: ve .</span><span class="sxs-lookup"><span data-stu-id="19753-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="19753-152">Bu yöntemler, başharflere <xref:System.ServiceModel.ServiceHost> alınırken WCF tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="19753-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="19753-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>ilk denir; tutarsızlıklar için hizmetin denetlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="19753-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="19753-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>sonraki denir; bu yöntem yalnızca çok gelişmiş senaryolarda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="19753-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="19753-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>sonuncu olarak adlandırılır ve çalışma süresini yapılandırmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="19753-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="19753-156">Aşağıdaki parametreler e <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>aktarılır:</span><span class="sxs-lookup"><span data-stu-id="19753-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="19753-157">`Description`: Bu parametre, tüm hizmet için hizmet açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="19753-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="19753-158">Bu, hizmetin bitiş noktaları, sözleşmeleri, bağlamaları ve hizmetle ilişkili diğer verilerle ilgili açıklama verilerini incelemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19753-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="19753-159">`ServiceHostBase`: Bu parametre, şu anda başharflere getirilmekte olan parametreyi <xref:System.ServiceModel.ServiceHostBase> sağlar.</span><span class="sxs-lookup"><span data-stu-id="19753-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="19753-160">Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulamada, yeni bir `ObjectPoolInstanceProvider` örnek anında ve bağlı her <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> bir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> özellik <xref:System.ServiceModel.ServiceHostBase>atanır.</span><span class="sxs-lookup"><span data-stu-id="19753-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
```csharp
public void ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    if (enabled)  
    {  
        // Create an instance of the ObjectPoolInstanceProvider.  
        instanceProvider = new ObjectPoolInstanceProvider(description.ServiceType,  
        maxPoolSize, minPoolSize, creationTimeout);  
  
        // Assign our instance provider to Dispatch behavior in each
        // endpoint.  
        foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
        {  
             ChannelDispatcher cd = cdb as ChannelDispatcher;  
             if (cd != null)  
             {  
                 foreach (EndpointDispatcher ed in cd.Endpoints)  
                 {  
                        ed.DispatchRuntime.InstanceProvider = instanceProvider;  
                 }  
             }  
         }  
     }  
}
```  
  
 <span data-ttu-id="19753-161">Bir <xref:System.ServiceModel.Description.IServiceBehavior> uygulamaya ek `ObjectPoolingAttribute` olarak sınıf öznitelik bağımsız değişkenleri kullanarak nesne havuzu özelleştirmek için birkaç üye vardır.</span><span class="sxs-lookup"><span data-stu-id="19753-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="19753-162">Bu `MaxSize`üyeler, `MinSize` `Enabled` .NET Enterprise Services tarafından sağlanan nesne birleştirme özelliğini eşleştirmek için , ve `CreationTimeout`, içerir.</span><span class="sxs-lookup"><span data-stu-id="19753-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="19753-163">Nesne birleştirme davranışı artık yeni oluşturulan özel `ObjectPooling` öznitelik ile hizmet uygulaması açıklama yaparak bir WCF hizmetine eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="19753-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="19753-164">Hooking Aktivasyon ve Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="19753-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="19753-165">Nesne birleştirmenin birincil amacı, göreceli olarak pahalı oluşturma ve başlatma ile kısa ömürlü nesneleri en iyi duruma getirmektir.</span><span class="sxs-lookup"><span data-stu-id="19753-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="19753-166">Bu nedenle, düzgün kullanıldığında bir uygulamaya önemli bir performans artışı sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="19753-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="19753-167">Nesne havuzdan döndürüldinandığından, oluşturucu yalnızca bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="19753-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="19753-168">Ancak, bazı uygulamalar, tek bir bağlam sırasında kullanılan kaynakları başlatma ve temizleme yapabilmeleri için bir miktar denetim gerektirir.</span><span class="sxs-lookup"><span data-stu-id="19753-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="19753-169">Örneğin, bir hesaplama kümesi için kullanılan bir nesne, sonraki hesaplamayı işlemeden önce özel alanlarını sıfırlayabilir.</span><span class="sxs-lookup"><span data-stu-id="19753-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="19753-170">Kurumsal Hizmetler, nesne geliştiricisinin ve `Activate` `Deactivate` yöntemleri <xref:System.EnterpriseServices.ServicedComponent> temel sınıftan geçersiz kılmasına izin vererek bu tür içeriğe özgü bir başlatma olanağı sağladı.</span><span class="sxs-lookup"><span data-stu-id="19753-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="19753-171">Nesne havuzu, `Activate` nesneyi havuzdan döndürmeden hemen önce yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="19753-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="19753-172">`Deactivate`nesne havuza geri döndüğünde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="19753-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="19753-173">Taban sınıfın, nesnenin `CanBePooled`daha fazla havuza alınıp alınamayacağını havuza bildirmek için kullanılabilecek , adlı bir `boolean` özelliği de vardır. <xref:System.EnterpriseServices.ServicedComponent></span><span class="sxs-lookup"><span data-stu-id="19753-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="19753-174">Bu işlevselliği taklit etmek için, örnek`IObjectControl`yukarıda belirtilen üyeleri olan bir ortak arabirim ( ) bildirir.</span><span class="sxs-lookup"><span data-stu-id="19753-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="19753-175">Bu arabirim daha sonra bağlam belirli bir başlangıç sağlamak amacıyla hizmet sınıfları tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="19753-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="19753-176">Uygulama, <xref:System.ServiceModel.Dispatcher.IInstanceProvider> bu gereksinimleri karşılamak için değiştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="19753-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="19753-177">Şimdi, `GetInstance` yöntemi çağırarak bir nesne almak her zaman, nesne `IObjectControl.` uygular eğer olup olmadığını `Activate` kontrol etmelisiniz, uygun şekilde yöntemi aramanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="19753-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="19753-178">Bir nesneyi havuza döndürdükten sonra, `CanBePooled` nesneyi havuza geri eklemeden önce özellik için bir denetim gerekir.</span><span class="sxs-lookup"><span data-stu-id="19753-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
```csharp  
if (instance is IObjectControl)  
{  
    IObjectControl objectControl = (IObjectControl)instance;  
    objectControl.Deactivate();  
    if (objectControl.CanBePooled)  
    {  
       pool.Push(instance);  
    }  
}  
```  
  
 <span data-ttu-id="19753-179">Hizmet geliştiricisi bir nesnenin bir araya gelip gelemeyeceğine karar verebildiği için, belirli bir zamanda havuzdaki nesne sayısı minimum boyutun altına inebilir.</span><span class="sxs-lookup"><span data-stu-id="19753-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="19753-180">Bu nedenle, nesne sayısının minimum düzeyin altına inip gitmediğini kontrol etmeli ve temizleme yordamında gerekli başlatmaişlemini gerçekleştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="19753-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
```csharp  
// Remove the surplus objects.  
if (pool.Count > minPoolSize)  
{  
  // Clean the surplus objects.  
}
else if (pool.Count < minPoolSize)  
{  
  // Reinitialize the missing objects.  
  while(pool.Count != minPoolSize)  
  {  
    pool.Push(CreateNewPoolObject());  
  }  
}  
```  
  
 <span data-ttu-id="19753-181">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="19753-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="19753-182">Hizmeti ve istemciyi kapatmak için her konsol penceresinde Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="19753-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="19753-183">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="19753-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="19753-184">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="19753-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="19753-185">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="19753-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="19753-186">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="19753-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="19753-187">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="19753-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="19753-188">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="19753-188">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="19753-189">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="19753-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="19753-190">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="19753-190">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
