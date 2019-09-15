---
title: Başlatmayı Örneklendirme
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: ca135aca8f84ddf79ec7447e7fa7814f61984419
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989839"
---
# <a name="instancing-initialization"></a><span data-ttu-id="d6e87-102">Başlatmayı Örneklendirme</span><span class="sxs-lookup"><span data-stu-id="d6e87-102">Instancing Initialization</span></span>
<span data-ttu-id="d6e87-103">Bu örnek, bir arabirimini etkinleştirerek ve devre dışı bırakarak bir `IObjectControl`nesnenin başlatılmasını özelleştiren bir arabirim tanımlayarak [Havuz oluşturma](../../../../docs/framework/wcf/samples/pooling.md) örneğini genişletir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="d6e87-104">İstemci, nesneyi havuza döndüren ve havuza nesne döndüren yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d6e87-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="d6e87-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="d6e87-106">Genişletilebilirlik noktaları</span><span class="sxs-lookup"><span data-stu-id="d6e87-106">Extensibility Points</span></span>  
 <span data-ttu-id="d6e87-107">Windows Communication Foundation (WCF) uzantısı oluşturmanın ilk adımı, genişletilebilirlik noktasının kullanılmasına karar vermaktır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="d6e87-108">WCF 'de, *EndpointDispatcher* terimi, gelen iletileri kullanıcının hizmetinde Yöntem etkinleştirmeleri içine dönüştürmeden ve dönüş değerlerini Bu yöntemden giden bir iletiye dönüştürmekten sorumlu bir çalışma zamanı bileşenine başvurur.</span><span class="sxs-lookup"><span data-stu-id="d6e87-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="d6e87-109">WCF hizmeti her uç nokta için bir EndpointDispatcher oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6e87-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="d6e87-110">EndpointDispatcher, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> sınıfını kullanarak uç nokta kapsamı (hizmet tarafından alınan veya gönderilen tüm iletiler için) sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6e87-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="d6e87-111">Bu sınıf, EndpointDispatcher davranışını denetleyen çeşitli özellikleri özelleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6e87-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="d6e87-112">Bu örnek, hizmet sınıfının <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> örneklerini sağlayan nesnesine işaret eden özelliğine odaklanır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="d6e87-113">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="d6e87-113">IInstanceProvider</span></span>  
 <span data-ttu-id="d6e87-114">WCF 'de, EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimini uygulayan bir örnek sağlayıcı kullanarak bir hizmet sınıfının örneklerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6e87-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="d6e87-115">Bu arabirimin yalnızca iki yöntemi vardır:</span><span class="sxs-lookup"><span data-stu-id="d6e87-115">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="d6e87-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Bir ileti geldiğinde, dağıtıcı iletiyi işlemek için hizmet <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> sınıfının bir örneğini oluşturmak üzere yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="d6e87-117">Bu yönteme yapılan çağrıların sıklığı, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="d6e87-118">Örneğin <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> , özelliği olarak <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>ayarlandıysa, gelen her iletiyi işlemek için yeni bir hizmet sınıfı örneği oluşturulur, bu nedenle <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> ileti her geldiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="d6e87-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Hizmet örneği iletiyi işlemeyi tamamladığında, EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="d6e87-120">Yönteminde olduğu gibi, bu yönteme yapılan çağrıların sıklığı <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği tarafından belirlenir. <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A></span><span class="sxs-lookup"><span data-stu-id="d6e87-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="d6e87-121">Nesne havuzu</span><span class="sxs-lookup"><span data-stu-id="d6e87-121">The Object Pool</span></span>  
 <span data-ttu-id="d6e87-122">`ObjectPoolInstanceProvider` Sınıfı, nesne havuzu için uygulamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="d6e87-123">Bu sınıf, <xref:System.ServiceModel.Dispatcher.IInstanceProvider> hizmet modeli katmanıyla etkileşimde bulunmak için arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="d6e87-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="d6e87-124">EndpointDispatcher <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yöntemi çağırdığında, yeni bir örnek oluşturmak yerine, özel uygulama bellek içi havuzda var olan bir nesneyi arar.</span><span class="sxs-lookup"><span data-stu-id="d6e87-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="d6e87-125">Kullanılabilir bir tane varsa, döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d6e87-125">If one is available, it is returned.</span></span> <span data-ttu-id="d6e87-126">Aksi takdirde `ObjectPoolInstanceProvider` , `ActiveObjectsCount` özelliğinin (havuzdan döndürülen nesne sayısı) en yüksek havuz boyutuna ulaştığından, bu özelliği denetler.</span><span class="sxs-lookup"><span data-stu-id="d6e87-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="d6e87-127">Aksi takdirde, yeni bir örnek oluşturulup çağırana döndürülür ve `ActiveObjectsCount` daha sonra artırılır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="d6e87-128">Aksi takdirde, bir nesne oluşturma isteği yapılandırılmış bir süre için sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="d6e87-129">İçin `GetObjectFromThePool` uygulanması aşağıdaki örnek kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="d6e87-130">Özel `ReleaseInstance` uygulama, yayımlanan örneği havuza geri ekler ve `ActiveObjectsCount` değeri azaltır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="d6e87-131">EndpointDispatcher Bu yöntemleri farklı iş parçacıklarından çağırabilir ve bu nedenle, `ObjectPoolInstanceProvider` sınıftaki sınıf düzeyi üyelerine eşitlenen erişim gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
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
  
 <span data-ttu-id="d6e87-132">Yöntemi bir temizleme başlatma özelliği sağlar. `ReleaseInstance`</span><span class="sxs-lookup"><span data-stu-id="d6e87-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="d6e87-133">Normalde havuz, havuzun ömrü boyunca en az sayıda nesne tutar.</span><span class="sxs-lookup"><span data-stu-id="d6e87-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="d6e87-134">Ancak, yapılandırmada belirtilen en yüksek sınıra ulaşmak için havuzda ek nesneler oluşturulmasını gerektiren aşırı kullanım süreleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="d6e87-135">Sonuç olarak, havuz daha az etkin hale geldiğinde, bu fazlalık nesneler ek bir ek yük haline gelebilir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="d6e87-136">Bu nedenle, `activeObjectsCount` bir boşta kalma süreölçeri sıfıra ulaştığında harekete geçiren ve Temizleme döngüsünü gerçekleştiren bir Zamanlayıcı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 <span data-ttu-id="d6e87-137">ServiceModel katman uzantıları aşağıdaki davranışlar kullanılarak kullanıma alınır:</span><span class="sxs-lookup"><span data-stu-id="d6e87-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="d6e87-138">Hizmet davranışları: Bu, tüm hizmet çalışma zamanının özelleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="d6e87-139">Uç nokta davranışları: Bu, EndpointDispatcher dahil olmak üzere belirli bir hizmet uç noktasının özelleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="d6e87-140">Sözleşme davranışları: Bunlar, sırasıyla istemci veya hizmette bulunan <xref:System.ServiceModel.Dispatcher.ClientRuntime> ya <xref:System.ServiceModel.Dispatcher.DispatchRuntime> da sınıfların özelleştirilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6e87-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="d6e87-141">İşlem davranışları: Bunlar, sırasıyla istemci veya hizmette bulunan <xref:System.ServiceModel.Dispatcher.ClientOperation> ya <xref:System.ServiceModel.Dispatcher.DispatchOperation> da sınıfların özelleştirilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6e87-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="d6e87-142">Bir nesne havuzu uzantısının amacı için bir uç nokta davranışı veya bir hizmet davranışı oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="d6e87-143">Bu örnekte, hizmetin her uç noktasına nesne havuzu oluşturma özelliğini uygulayan bir hizmet davranışı kullanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="d6e87-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="d6e87-144">Hizmet davranışları <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi uygulayarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d6e87-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="d6e87-145">Özel davranışları ServiceModel olarak algılayan çeşitli yollar vardır:</span><span class="sxs-lookup"><span data-stu-id="d6e87-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="d6e87-146">Özel bir öznitelik kullanma.</span><span class="sxs-lookup"><span data-stu-id="d6e87-146">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="d6e87-147">Imperatively, hizmet açıklamasının davranış koleksiyonuna ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="d6e87-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="d6e87-148">Yapılandırma dosyası genişletiliyor.</span><span class="sxs-lookup"><span data-stu-id="d6e87-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="d6e87-149">Bu örnek özel bir özniteliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="d6e87-150"><xref:System.ServiceModel.ServiceHost> Oluşturulduğunda, hizmetin tür tanımında kullanılan öznitelikleri inceler ve kullanılabilir davranışları hizmet açıklamasının davranış koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="d6e87-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="d6e87-151">`,` Arabiriminüç`,` yöntemi vardır: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>ve. <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> <xref:System.ServiceModel.Description.IServiceBehavior> <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A></span><span class="sxs-lookup"><span data-stu-id="d6e87-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="d6e87-152">Bu yöntemler, <xref:System.ServiceModel.ServiceHost> başlatıldığında WCF tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="d6e87-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>İlk olarak çağrılır; hizmetin tutarsızlıklar için inceleneme izin verir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="d6e87-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>sonraki çağırılır; Bu yöntem yalnızca Gelişmiş senaryolarda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="d6e87-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>son olarak adlandırılır ve çalışma zamanının yapılandırılmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="d6e87-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="d6e87-156">Aşağıdaki parametreler içine <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>geçirilir:</span><span class="sxs-lookup"><span data-stu-id="d6e87-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="d6e87-157">`Description`: Bu parametre tüm hizmet için hizmet açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6e87-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="d6e87-158">Bu, hizmetin uç noktaları, sözleşmeleri, bağlamaları ve hizmetle ilişkili diğer verilerle ilgili açıklama verilerini denetlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="d6e87-159">`ServiceHostBase`: Bu parametre, <xref:System.ServiceModel.ServiceHostBase> Şu anda başlatılmış olan öğesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6e87-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="d6e87-160">Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulamada, öğesinin `ObjectPoolInstanceProvider` yeni bir örneği örneği oluşturulur ve ' a iliştirilmiş her <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> bir <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> <xref:System.ServiceModel.ServiceHostBase>özelliğine atanır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
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
  
 <span data-ttu-id="d6e87-161">Bir <xref:System.ServiceModel.Description.IServiceBehavior> uygulamaya ek olarak, `ObjectPoolingAttribute` sınıfı öznitelik bağımsız değişkenlerini kullanarak nesne havuzunu özelleştirmek için çeşitli üyelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="d6e87-162">Bu Üyeler, `MaxSize`.NET Enterprise `Enabled` Services tarafından sunulan nesne havuzu özellik kümesini eşleştirmek için, ve `CreationTimeout`içerir `MinSize`.</span><span class="sxs-lookup"><span data-stu-id="d6e87-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="d6e87-163">Nesne havuzu oluşturma davranışı artık yeni oluşturulan özel `ObjectPooling` öznitelikle hizmet uygulamasına ek olarak bir WCF hizmetine eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="d6e87-164">Etkinleştirme ve devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="d6e87-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="d6e87-165">Nesne havuzunun birincil amacı, kısa süreli nesneleri görece maliyetli oluşturma ve başlatma ile optimize etmek.</span><span class="sxs-lookup"><span data-stu-id="d6e87-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="d6e87-166">Bu nedenle, düzgün şekilde kullanılırsa uygulamaya çarpıcı bir performans artışı verebilir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="d6e87-167">Nesne havuzdan döndürüldüğünden, Oluşturucu yalnızca bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="d6e87-168">Ancak bazı uygulamalar, tek bir bağlam sırasında kullanılan kaynakları başlatıp temizleyebilecekleri bir denetim düzeyi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="d6e87-169">Örneğin, bir hesaplamalar kümesi için kullanılan bir nesne, bir sonraki hesaplamayı işlemeden önce özel alanlarını sıfırlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="d6e87-170">Kurumsal Hizmetler, nesne geliştiricisi geçersiz kılınmasına `Activate` ve `Deactivate` <xref:System.EnterpriseServices.ServicedComponent> temel sınıftan yöntemlere izin vererek bu tür içeriğe özgü başlatma işlemini etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="d6e87-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="d6e87-171">Nesne havuzu, nesneyi havuzdan `Activate` döndürmeden hemen önce yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="d6e87-172">`Deactivate`, nesne havuza geri dönzaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="d6e87-173">Temel sınıf ayrıca adlı `boolean` `CanBePooled`bir özelliğe sahiptir ve bu, havuzun daha fazla havuza kaydedilip edilmeyeceğini bildirmek için kullanılabilir. <xref:System.EnterpriseServices.ServicedComponent></span><span class="sxs-lookup"><span data-stu-id="d6e87-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="d6e87-174">Bu işlevselliği taklit etmek için örnek, belirtilen üyelere sahip ortak bir`IObjectControl`Arabirim () bildirir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="d6e87-175">Bu arabirim daha sonra içeriğe özgü başlatma sağlamak üzere amaçlanan hizmet sınıfları tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d6e87-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="d6e87-176"><xref:System.ServiceModel.Dispatcher.IInstanceProvider> Uygulamanın bu gereksinimleri karşılayacak şekilde değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="d6e87-177">Şimdi, `GetInstance` yöntemini çağırarak bir nesne aldığınızda, nesnenin ne zaman uygulayıp uygulamadığını `IObjectControl.` denetlemeniz gerekir `Activate` , yöntemi uygun şekilde çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="d6e87-178">Havuza bir nesne döndürürken, nesne havuza geri eklenmeden önce `CanBePooled` özelliği için bir denetim gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
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
  
 <span data-ttu-id="d6e87-179">Hizmet geliştiricisi bir nesnenin havuza kaydedilip edilmeyeceğini belirleyebildiğinden, havuzdaki belirli bir zamanda bulunan nesne sayısı en düşük boyutun altına gidebilir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="d6e87-180">Bu nedenle, nesne sayısının en düşük düzeyin altında olup olmadığını ve Temizleme yordamında gerekli başlatmayı gerçekleştirip gerçekleştirmediğini denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
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
  
 <span data-ttu-id="d6e87-181">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="d6e87-182">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d6e87-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d6e87-183">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d6e87-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d6e87-184">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d6e87-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d6e87-185">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d6e87-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d6e87-186">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d6e87-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d6e87-187">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6e87-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d6e87-188">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d6e87-188">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="d6e87-189">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="d6e87-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d6e87-190">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d6e87-190">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
