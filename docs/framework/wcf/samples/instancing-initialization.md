---
title: Başlatmayı Örneklendirme
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: ee7d470cb80e913707ae6e92039061efde8fcb7f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715796"
---
# <a name="instancing-initialization"></a><span data-ttu-id="1cd5c-102">Başlatmayı Örneklendirme</span><span class="sxs-lookup"><span data-stu-id="1cd5c-102">Instancing Initialization</span></span>
<span data-ttu-id="1cd5c-103">Bu örnek, bir arabirimini etkinleştirerek ve devre dışı bırakarak bir nesnenin başlatılmasını özelleştiren `IObjectControl`bir arabirim tanımlayarak [Havuz](../../../../docs/framework/wcf/samples/pooling.md) örneğini genişletir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="1cd5c-104">İstemci, nesneyi havuza döndüren ve havuza nesne döndüren yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1cd5c-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="1cd5c-106">Genişletilebilirlik noktaları</span><span class="sxs-lookup"><span data-stu-id="1cd5c-106">Extensibility Points</span></span>  
 <span data-ttu-id="1cd5c-107">Windows Communication Foundation (WCF) uzantısı oluşturmanın ilk adımı, genişletilebilirlik noktasının kullanılmasına karar vermaktır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="1cd5c-108">WCF 'de, *EndpointDispatcher* terimi, gelen iletileri kullanıcının hizmetinde Yöntem etkinleştirmeleri içine dönüştürmeden ve dönüş değerlerini Bu yöntemden giden bir iletiye dönüştürmekten sorumlu bir çalışma zamanı bileşenine başvurur.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="1cd5c-109">WCF hizmeti her uç nokta için bir EndpointDispatcher oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="1cd5c-110">EndpointDispatcher, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> sınıfını kullanarak uç nokta kapsamı (hizmetin aldığı veya hizmet tarafından gönderilen tüm iletiler için) sağlar.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="1cd5c-111">Bu sınıf, EndpointDispatcher davranışını denetleyen çeşitli özellikleri özelleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="1cd5c-112">Bu örnek, hizmet sınıfının örneklerini sağlayan nesnesine işaret eden <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> özelliğine odaklanır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="1cd5c-113">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="1cd5c-113">IInstanceProvider</span></span>  
 <span data-ttu-id="1cd5c-114">WCF 'de, EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimini uygulayan bir örnek sağlayıcısı kullanarak bir hizmet sınıfının örneklerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="1cd5c-115">Bu arabirimin yalnızca iki yöntemi vardır:</span><span class="sxs-lookup"><span data-stu-id="1cd5c-115">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="1cd5c-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: bir ileti geldiğinde dağıtıcı, iletiyi işlemek üzere hizmet sınıfının bir örneğini oluşturmak için <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="1cd5c-117">Bu yönteme yapılan çağrıların sıklığı <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="1cd5c-118">Örneğin <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>olarak ayarlanırsa, gelen her iletiyi işlemek için yeni bir hizmet sınıfı örneği oluşturulur, bu nedenle <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> ileti geldiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="1cd5c-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: hizmet örneği iletiyi işlemeyi tamamladığında, EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="1cd5c-120"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yönteminde olduğu gibi, bu yönteme yapılan çağrıların sıklığı <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="1cd5c-121">Nesne havuzu</span><span class="sxs-lookup"><span data-stu-id="1cd5c-121">The Object Pool</span></span>  
 <span data-ttu-id="1cd5c-122">`ObjectPoolInstanceProvider` sınıfı, nesne havuzunun uygulamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="1cd5c-123">Bu sınıf, hizmet modeli katmanıyla etkileşimde bulunmak için <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="1cd5c-124">EndpointDispatcher, yeni bir örnek oluşturmak yerine <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yöntemini çağırdığında, özel uygulama bellek içi havuzda var olan bir nesneyi arar.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="1cd5c-125">Kullanılabilir bir tane varsa, döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-125">If one is available, it is returned.</span></span> <span data-ttu-id="1cd5c-126">Aksi takdirde, `ActiveObjectsCount` özelliğinin (havuzdan döndürülen nesne sayısı) en yüksek havuz boyutuna ulaştığından `ObjectPoolInstanceProvider` denetler.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="1cd5c-127">Aksi takdirde, yeni bir örnek oluşturulur ve çağırana döndürülür ve `ActiveObjectsCount` daha sonra artırılır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="1cd5c-128">Aksi takdirde, bir nesne oluşturma isteği yapılandırılmış bir süre için sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="1cd5c-129">`GetObjectFromThePool` uygulanması aşağıdaki örnek kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="1cd5c-130">Özel `ReleaseInstance` uygulama, yayımlanan örneği havuza geri ekler ve `ActiveObjectsCount` değerini azaltır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="1cd5c-131">EndpointDispatcher Bu yöntemleri farklı iş parçacıklarından çağırabilir ve bu nedenle `ObjectPoolInstanceProvider` sınıfındaki sınıf düzeyi üyelerine eşitlenen erişim gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
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
  
 <span data-ttu-id="1cd5c-132">`ReleaseInstance` yöntemi bir *Temizleme başlatma* özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="1cd5c-133">Normalde havuz, havuzun ömrü boyunca en az sayıda nesne tutar.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="1cd5c-134">Ancak, yapılandırmada belirtilen en yüksek sınıra ulaşmak için havuzda ek nesneler oluşturulmasını gerektiren aşırı kullanım süreleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="1cd5c-135">Sonuç olarak, havuz daha az etkin hale geldiğinde, bu fazlalık nesneler ek bir ek yük haline gelebilir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="1cd5c-136">Bu nedenle `activeObjectsCount` sıfırdan ulaştığında bir boşta kalma süreölçeri tetiklenir ve Temizleme döngüsünü gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 <span data-ttu-id="1cd5c-137">ServiceModel katman uzantıları aşağıdaki davranışlar kullanılarak kullanıma alınır:</span><span class="sxs-lookup"><span data-stu-id="1cd5c-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="1cd5c-138">Hizmet davranışları: Bu, tüm hizmet çalışma zamanının özelleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="1cd5c-139">Uç nokta davranışları: Bu, EndpointDispatcher dahil olmak üzere belirli bir hizmet uç noktasının özelleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="1cd5c-140">Sözleşme davranışları: Bu, sırasıyla istemci veya hizmette <xref:System.ServiceModel.Dispatcher.ClientRuntime> ya da <xref:System.ServiceModel.Dispatcher.DispatchRuntime> sınıfların özelleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="1cd5c-141">İşlem davranışları: Bu, sırasıyla istemci veya hizmette <xref:System.ServiceModel.Dispatcher.ClientOperation> ya da <xref:System.ServiceModel.Dispatcher.DispatchOperation> sınıfların özelleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="1cd5c-142">Bir nesne havuzu uzantısının amacı için bir uç nokta davranışı veya bir hizmet davranışı oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="1cd5c-143">Bu örnekte, hizmetin her uç noktasına nesne havuzu oluşturma özelliğini uygulayan bir hizmet davranışı kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="1cd5c-144">Hizmet davranışları <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi uygulayarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="1cd5c-145">Özel davranışları ServiceModel olarak algılayan çeşitli yollar vardır:</span><span class="sxs-lookup"><span data-stu-id="1cd5c-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="1cd5c-146">Özel bir öznitelik kullanma.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-146">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="1cd5c-147">Imperatively, hizmet açıklamasının davranış koleksiyonuna ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="1cd5c-148">Yapılandırma dosyası genişletiliyor.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="1cd5c-149">Bu örnek özel bir özniteliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="1cd5c-150"><xref:System.ServiceModel.ServiceHost> oluşturulduğunda, hizmetin tür tanımında kullanılan öznitelikleri inceler ve kullanılabilir davranışları hizmet açıklamasının davranış koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="1cd5c-151"><xref:System.ServiceModel.Description.IServiceBehavior> arabirimi üç yönteme sahiptir: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` ve <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="1cd5c-152"><xref:System.ServiceModel.ServiceHost> başlatıldığında bu yöntemler WCF tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="1cd5c-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> ilk olarak çağrılır; hizmetin tutarsızlıklar için inceleneme izin verir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="1cd5c-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> daha sonra çağrılır; Bu yöntem yalnızca Gelişmiş senaryolarda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="1cd5c-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> son olarak adlandırılır ve çalışma zamanının yapılandırılmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="1cd5c-156">Aşağıdaki parametreler <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>geçirilir:</span><span class="sxs-lookup"><span data-stu-id="1cd5c-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="1cd5c-157">`Description`: Bu parametre hizmetin tamamı için hizmet açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="1cd5c-158">Bu, hizmetin uç noktaları, sözleşmeleri, bağlamaları ve hizmetle ilişkili diğer verilerle ilgili açıklama verilerini denetlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="1cd5c-159">`ServiceHostBase`: Bu parametre, şu anda başlatılmış olan <xref:System.ServiceModel.ServiceHostBase> sağlar.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="1cd5c-160">Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulamasında, yeni bir `ObjectPoolInstanceProvider` örneği oluşturulur ve <xref:System.ServiceModel.ServiceHostBase>eklenen her <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> özelliğine atanır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
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
  
 <span data-ttu-id="1cd5c-161"><xref:System.ServiceModel.Description.IServiceBehavior> uygulamasına ek olarak, `ObjectPoolingAttribute` sınıfı, nesne havuzunu öznitelik bağımsız değişkenlerini kullanarak özelleştirmek için çeşitli üyelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="1cd5c-162">Bu Üyeler, .NET Enterprise Services tarafından sunulan nesne havuzu özellik kümesiyle eşleşecek `MaxSize`, `MinSize`, `Enabled` ve `CreationTimeout`içerir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="1cd5c-163">Nesne havuzu oluşturma davranışı artık yeni oluşturulan özel `ObjectPooling` özniteliğiyle hizmet uygulamasına ek olarak bir WCF hizmetine eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="1cd5c-164">Etkinleştirme ve devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="1cd5c-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="1cd5c-165">Nesne havuzunun birincil amacı, kısa süreli nesneleri görece maliyetli oluşturma ve başlatma ile optimize etmek.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="1cd5c-166">Bu nedenle, düzgün şekilde kullanılırsa uygulamaya çarpıcı bir performans artışı verebilir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="1cd5c-167">Nesne havuzdan döndürüldüğünden, Oluşturucu yalnızca bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="1cd5c-168">Ancak bazı uygulamalar, tek bir bağlam sırasında kullanılan kaynakları başlatıp temizleyebilecekleri bir denetim düzeyi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="1cd5c-169">Örneğin, bir hesaplamalar kümesi için kullanılan bir nesne, bir sonraki hesaplamayı işlemeden önce özel alanlarını sıfırlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="1cd5c-170">Kurumsal Hizmetler, nesne geliştiricisinin <xref:System.EnterpriseServices.ServicedComponent> taban sınıfından `Activate` ve `Deactivate` yöntemleri geçersiz kılmasına izin vererek bu tür içeriğe özgü başlatma işlemini etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="1cd5c-171">Nesne havuzu, nesneyi havuzdan döndürmeden hemen önce `Activate` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="1cd5c-172">`Deactivate`, nesne havuza geri dönzaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="1cd5c-173"><xref:System.EnterpriseServices.ServicedComponent> temel sınıfı `CanBePooled`adlı bir `boolean` özelliğine sahiptir ve bu, havuzun daha fazla havuza eklenip eklenmeyeceğini bildirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="1cd5c-174">Bu işlevselliği taklit etmek için örnek, belirtilen üyelere sahip ortak bir arabirim (`IObjectControl`) bildirir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="1cd5c-175">Bu arabirim daha sonra içeriğe özgü başlatma sağlamak üzere amaçlanan hizmet sınıfları tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="1cd5c-176"><xref:System.ServiceModel.Dispatcher.IInstanceProvider> uygulamasının bu gereksinimleri karşılayacak şekilde değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="1cd5c-177">Artık `GetInstance` yöntemini çağırarak bir nesne aldığınızda, nesnenin `IObjectControl.` uygulayıp uygulamadığını denetlemeniz gerekir, `Activate` yöntemini uygun şekilde çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="1cd5c-178">Havuza bir nesne döndürürken, nesne havuza geri eklenmeden önce `CanBePooled` özelliği için bir denetim gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
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
  
 <span data-ttu-id="1cd5c-179">Hizmet geliştiricisi bir nesnenin havuza kaydedilip edilmeyeceğini belirleyebildiğinden, havuzdaki belirli bir zamanda bulunan nesne sayısı en düşük boyutun altına gidebilir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="1cd5c-180">Bu nedenle, nesne sayısının en düşük düzeyin altında olup olmadığını ve Temizleme yordamında gerekli başlatmayı gerçekleştirip gerçekleştirmediğini denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
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
  
 <span data-ttu-id="1cd5c-181">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="1cd5c-182">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1cd5c-183">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="1cd5c-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1cd5c-184">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1cd5c-185">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1cd5c-186">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1cd5c-187">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1cd5c-188">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-188">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="1cd5c-189">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1cd5c-190">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1cd5c-190">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
