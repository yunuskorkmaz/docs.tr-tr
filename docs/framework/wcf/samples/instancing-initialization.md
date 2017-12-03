---
title: "Başlatmayı Örneklendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5345816295b9de54426aef3da697b99b4f0ce10e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="instancing-initialization"></a><span data-ttu-id="4b801-102">Başlatmayı Örneklendirme</span><span class="sxs-lookup"><span data-stu-id="4b801-102">Instancing Initialization</span></span>
<span data-ttu-id="4b801-103">Bu örnek genişletir [toplama](../../../../docs/framework/wcf/samples/pooling.md) bir arabirim tanımlayarak örnek `IObjectControl`, etkinleştirme ve devre dışı bırakmadan nesneyi başlatma özelleştirir.</span><span class="sxs-lookup"><span data-stu-id="4b801-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="4b801-104">İstemci, nesne havuza geri dönün ve, nesne havuzuna döndürmeyen yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="4b801-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b801-105">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="4b801-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="4b801-106">Genişletilebilirlik noktaları</span><span class="sxs-lookup"><span data-stu-id="4b801-106">Extensibility Points</span></span>  
 <span data-ttu-id="4b801-107">Oluşturmanın ilk adımı bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uzantısıdır genişletilebilirlik noktasını kullanmak üzere karar vermek için.</span><span class="sxs-lookup"><span data-stu-id="4b801-107">The first step in creating a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="4b801-108">İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], terimi *EndpointDispatcher* sorumlu kullanıcının hizmet üzerinde yöntem çağrılarına gelen iletileri dönüştürme ve o yöntemin dönüş değerleri dönüştürme için bir çalışma zamanı bileşeni başvurduğu bir Giden ileti.</span><span class="sxs-lookup"><span data-stu-id="4b801-108">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="4b801-109">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti her bitiş noktasıyla ilgili bir EndpointDispatcher oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4b801-109">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="4b801-110">Uç nokta genişletilebilirlik kapsamı (alınan veya hizmet tarafından gönderilen tüm iletiler için) kullanarak EndpointDispatcher sunar <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4b801-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="4b801-111">Bu sınıf EndpointDispatcher davranışını denetleyen çeşitli özellikleri özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b801-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="4b801-112">Bu örnek odaklanır <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> hizmet sınıfının örnekleri sağlayan bir nesneye işaret etmiyor özelliği.</span><span class="sxs-lookup"><span data-stu-id="4b801-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="4b801-113">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="4b801-113">IInstanceProvider</span></span>  
 <span data-ttu-id="4b801-114">İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], EndpointDispatcher uygulayan bir örnek sağlayıcısı kullanarak bir hizmet sınıfın örneklerini oluşturur <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4b801-114">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="4b801-115">Bu arabirim, yalnızca iki yöntemi vardır:</span><span class="sxs-lookup"><span data-stu-id="4b801-115">This interface has only two methods:</span></span>  
  
-   <span data-ttu-id="4b801-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: Bir ileti geldiğinde, dağıtıcı çağrıları <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> iletiyi işlemek için hizmet sınıfının bir örneğini oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4b801-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="4b801-117">Bu yönteme çağrıları sıklığını tarafından belirlenen <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4b801-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="4b801-118">Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği ayarlanmış <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, hizmet sınıfının yeni bir örneğini, bunu ulaşan her iletiyi işlemek için oluşturulan <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> bir ileti ulaştığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4b801-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
-   <span data-ttu-id="4b801-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: Hizmet örneği iletiyi işlemeyi bitirdikten sonra EndpointDispatcher çağırır <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4b801-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="4b801-120">Olarak <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yöntemi, bu yönteme çağrıları sıklığını tarafından belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4b801-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="4b801-121">Nesne havuzu</span><span class="sxs-lookup"><span data-stu-id="4b801-121">The Object Pool</span></span>  
 <span data-ttu-id="4b801-122">`ObjectPoolInstanceProvider` Sınıf, nesne havuzu uygulamasını içerir.</span><span class="sxs-lookup"><span data-stu-id="4b801-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="4b801-123">Bu sınıf uygulayan <xref:System.ServiceModel.Dispatcher.IInstanceProvider> hizmet modeli katmanını ile etkileşim kurmak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="4b801-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="4b801-124">EndpointDispatcher çağırdığında <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> yeni bir örneği oluşturmak yerine yöntemi, özel uygulama bellek içi havuzdaki var olan bir nesne arar.</span><span class="sxs-lookup"><span data-stu-id="4b801-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="4b801-125">Varsa, döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4b801-125">If one is available, it is returned.</span></span> <span data-ttu-id="4b801-126">Aksi takdirde, `ObjectPoolInstanceProvider` denetler olup olmadığını `ActiveObjectsCount` özelliği (havuzdan döndürülen nesne sayısı), en büyük havuz boyutuna ulaştı.</span><span class="sxs-lookup"><span data-stu-id="4b801-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="4b801-127">Değilse, yeni bir örneği oluşturulur ve yapana varsa ve `ActiveObjectsCount` sonradan artırılır.</span><span class="sxs-lookup"><span data-stu-id="4b801-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="4b801-128">Aksi halde bir nesne oluşturma isteği yapılandırılmış bir süre için sıraya alındı.</span><span class="sxs-lookup"><span data-stu-id="4b801-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="4b801-129">Uygulamasını `GetObjectFromThePool` aşağıdaki örnek kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="4b801-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="4b801-130">Özel `ReleaseInstance` uygulama havuzu ve azaltır için örnek yayınlandı ekler `ActiveObjectsCount` değeri.</span><span class="sxs-lookup"><span data-stu-id="4b801-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="4b801-131">EndpointDispatcher bu yöntemleri farklı iş parçacıklarından çağırabilir ve bu nedenle sınıf düzeyinde üyelerine erişimi eşitlenmiş `ObjectPoolInstanceProvider` sınıfı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4b801-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
```  
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
  
 <span data-ttu-id="4b801-132">`ReleaseInstance` Yöntemi sağlayan bir *başlatma Temizleme* özelliği.</span><span class="sxs-lookup"><span data-stu-id="4b801-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="4b801-133">Normalde havuzu nesneler en az sayıda havuzu ömrü boyunca tutar.</span><span class="sxs-lookup"><span data-stu-id="4b801-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="4b801-134">Ancak, yapılandırmada belirtilen en üst sınıra ulaşması havuzundaki ek nesneleri oluşturma gerektiren aşırı kullanım dönemlerini olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b801-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="4b801-135">Sonunda havuzu daha az etkin olduğunda fazlalık nesnelere ek yüke haline gelebilir.</span><span class="sxs-lookup"><span data-stu-id="4b801-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="4b801-136">Bu nedenle, `activeObjectsCount` tetikler ve temizleme döngüsü gerçekleştiren bir boşta süreölçeri başlatılır sıfır ulaşır.</span><span class="sxs-lookup"><span data-stu-id="4b801-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 <span data-ttu-id="4b801-137">ServiceModel katman uzantıları aşağıdaki davranışları kullanarak sayfaya bağlanır:</span><span class="sxs-lookup"><span data-stu-id="4b801-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
-   <span data-ttu-id="4b801-138">Hizmet davranışları: Bunlar tüm hizmet çalışma zamanı özelleştirmesi için izin verir.</span><span class="sxs-lookup"><span data-stu-id="4b801-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
-   <span data-ttu-id="4b801-139">Uç nokta davranışları: Bunlar EndpointDispatcher dahil olmak üzere belirli hizmet uç noktası, özelleştirme için izin verir.</span><span class="sxs-lookup"><span data-stu-id="4b801-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
-   <span data-ttu-id="4b801-140">Sözleşme davranışları: Bunlar için ya da özelleştirilmesine imkan tanımak <xref:System.ServiceModel.Dispatcher.ClientRuntime> veya <xref:System.ServiceModel.Dispatcher.DispatchRuntime> istemci veya hizmet sırasıyla sınıfları.</span><span class="sxs-lookup"><span data-stu-id="4b801-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
-   <span data-ttu-id="4b801-141">İşlemi davranışları: Bunlar için ya da özelleştirilmesine imkan tanımak <xref:System.ServiceModel.Dispatcher.ClientOperation> veya <xref:System.ServiceModel.Dispatcher.DispatchOperation> istemci veya hizmet sırasıyla sınıfları.</span><span class="sxs-lookup"><span data-stu-id="4b801-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="4b801-142">Uzantı havuzu nesneyi amacıyla bir uç noktası davranışı ya da hizmet davranışı oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="4b801-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="4b801-143">Bu örnekte, tüm uç hizmetinin yeteneğini havuzu nesne geçerli bir hizmet davranışı kullanırız.</span><span class="sxs-lookup"><span data-stu-id="4b801-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="4b801-144">Hizmet davranışları uygulayarak oluşturulur <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4b801-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="4b801-145">ServiceModel özel davranışlar haberdar olmak için birkaç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="4b801-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
-   <span data-ttu-id="4b801-146">Özel bir öznitelik kullanma.</span><span class="sxs-lookup"><span data-stu-id="4b801-146">Using a custom attribute.</span></span>  
  
-   <span data-ttu-id="4b801-147">İmperatively hizmet açıklaması 's davranışları koleksiyona ekleme.</span><span class="sxs-lookup"><span data-stu-id="4b801-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
-   <span data-ttu-id="4b801-148">Yapılandırma dosyası genişletme.</span><span class="sxs-lookup"><span data-stu-id="4b801-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="4b801-149">Bu örnek özel bir öznitelik kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b801-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="4b801-150">Zaman <xref:System.ServiceModel.ServiceHost> olan oluşturulan, hizmetin tür tanımında kullanılan öznitelikler inceler ve kullanılabilir davranışları hizmet açıklaması 's davranışları koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="4b801-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="4b801-151"><xref:System.ServiceModel.Description.IServiceBehavior> Arabirim üç yöntem vardır: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,` ve <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="4b801-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="4b801-152">Bu yöntemleri tarafından çağrılır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zaman <xref:System.ServiceModel.ServiceHost> başlatıldığını.</span><span class="sxs-lookup"><span data-stu-id="4b801-152">These methods are called by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="4b801-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>ilk olarak adlandırılır; tutarsızlıkları denetlenecek hizmeti sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b801-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="4b801-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>sonraki çağrılır; Bu yöntem yalnızca çok Gelişmiş senaryolarda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4b801-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="4b801-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>Son olarak adlandırılır ve çalışma zamanı yapılandırmak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="4b801-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="4b801-156">Aşağıdaki parametreleri içine geçirilir <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="4b801-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
-   <span data-ttu-id="4b801-157">`Description`: Bu parametre, tüm hizmet hizmet açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b801-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="4b801-158">Bu hizmetin uç noktaları, sözleşmeler, bağlamaları ve hizmeti ile ilişkili diğer veri hakkında açıklama verilerini incelemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4b801-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
-   <span data-ttu-id="4b801-159">`ServiceHostBase`: Bu parametre sağlar <xref:System.ServiceModel.ServiceHostBase> , şu anda başlatılır.</span><span class="sxs-lookup"><span data-stu-id="4b801-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="4b801-160">Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulaması, yeni bir örneğini `ObjectPoolInstanceProvider` örneği ve atanan <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> her bir özellik <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> için bağlı <xref:System.ServiceModel.ServiceHostBase>.</span><span class="sxs-lookup"><span data-stu-id="4b801-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
```  
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
  
 <span data-ttu-id="4b801-161">Ek olarak bir <xref:System.ServiceModel.Description.IServiceBehavior> uygulama `ObjectPoolingAttribute` sınıfı öznitelik bağımsız değişkenleri kullanarak nesne havuzu özelleştirmek için birkaç üye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4b801-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="4b801-162">Bu üyeleri dahil `MaxSize`, `MinSize`, `Enabled` ve `CreationTimeout`, .NET Enterprise Hizmetleri tarafından sağlanan özellik kümesi havuzu nesne eşleşecek şekilde.</span><span class="sxs-lookup"><span data-stu-id="4b801-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="4b801-163">Davranış havuzu nesne artık eklenebilir bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yeni oluşturulan özel hizmet uygulamasıyla yorumlama tarafından hizmet `ObjectPooling` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4b801-163">The object pooling behavior can now be added to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="4b801-164">Takma etkinleştirme ve devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="4b801-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="4b801-165">Nesne havuzu oluşturma, birincil amacı, kısa süreli nesneler görece pahalı oluşturma ve başlatma ile en iyi duruma getirme sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="4b801-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="4b801-166">Bu nedenle önemli ölçüde performans artışı düzgün kullandıysanız uygulamaya verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b801-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="4b801-167">Nesne havuzdan döndürdüğünden Oluşturucusu yalnızca bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4b801-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="4b801-168">Ancak, böylece bunlar başlatmak ve tek bir bağlam sırasında kullanılan kaynakları temizleme bazı uygulamalar belirli bir düzeyde denetimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4b801-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="4b801-169">Örneğin, bir hesaplama kümesi için kullanılan bir nesne, sonraki hesaplama işlemeden önce özel alanları sıfırlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b801-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="4b801-170">Kurumsal Hizmetler geçersiz kılma nesne Geliştirici izin vererek bu tür bir bağlama özgü başlatma etkin `Activate` ve `Deactivate` yöntemleri <xref:System.EnterpriseServices.ServicedComponent> temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4b801-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="4b801-171">Nesne havuzu çağrılarını `Activate` havuzdan nesnesi döndüren hemen önce yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4b801-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="4b801-172">`Deactivate`Nesne havuza geri döndüğünde adı verilir.</span><span class="sxs-lookup"><span data-stu-id="4b801-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="4b801-173"><xref:System.EnterpriseServices.ServicedComponent> Temel sınıfı da sahip bir `boolean` adlı özellik `CanBePooled`, havuzu nesne daha fazla havuza olup olmadığını bildirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4b801-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="4b801-174">Bu işlev taklit etmek üzere ortak bir arabirim örnek bildirir (`IObjectControl`), daha önce bahsedilen üyeler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="4b801-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="4b801-175">Bu arabirim, ardından sınıfları bağlam belirli başlatma sağlamaya yönelik hizmeti tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4b801-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="4b801-176"><xref:System.ServiceModel.Dispatcher.IInstanceProvider> Uygulaması bu gereksinimleri karşılamak için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4b801-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="4b801-177">Şimdi, her zaman size bir nesne çağırarak `GetInstance` yöntemi, kontrol gerekir nesne uygulayan olup olmadığını `IObjectControl.` aşması durumunda çağırmalısınız `Activate` yöntemi uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="4b801-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="4b801-178">Bir nesne havuza geri döndürülürken bir onay için gereken `CanBePooled` nesne eklemeden önce özelliğini yeniden havuzuna.</span><span class="sxs-lookup"><span data-stu-id="4b801-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
```  
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
  
 <span data-ttu-id="4b801-179">Hizmet Geliştirici nesneyi havuza olup olmadığını karar verebilirsiniz çünkü nesne sayısı belirli bir zamanda havuzunda en az boyutun altında gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b801-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="4b801-180">Bu nedenle nesne sayısı en düşük düzeyin altına indi ve gerekli başlatma temizleme yordamı işaretlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4b801-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
```  
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
  
 <span data-ttu-id="4b801-181">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4b801-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="4b801-182">Her konsol penceresinde hizmet ve istemci kapatmak için Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4b801-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4b801-183">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="4b801-183">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4b801-184">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b801-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4b801-185">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b801-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4b801-186">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4b801-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4b801-187">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="4b801-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4b801-188">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4b801-188">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4b801-189">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4b801-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4b801-190">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4b801-190">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
  
## <a name="see-also"></a><span data-ttu-id="4b801-191">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b801-191">See Also</span></span>
