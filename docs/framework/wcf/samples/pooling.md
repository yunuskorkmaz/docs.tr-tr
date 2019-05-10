---
title: Biriktirme
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: d9f48f6bfade9dc2e28fd5495c8e450e43c36a9c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664757"
---
# <a name="pooling"></a><span data-ttu-id="c2b5b-102">Biriktirme</span><span class="sxs-lookup"><span data-stu-id="c2b5b-102">Pooling</span></span>
<span data-ttu-id="c2b5b-103">Bu örnek nasıl genişleteceğinizi nesne havuzu desteklemek için Windows Communication Foundation (WCF) gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="c2b5b-104">Örnek sözdizimi ve anlamsal olarak benzer bir öznitelik oluşturmak nasıl gösterir `ObjectPoolingAttribute` Enterprise Hizmetleri işlevselliğinin özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="c2b5b-105">Nesne havuzu bir uygulamanın performansı çarpıcı bir boost sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="c2b5b-106">Ancak, düzgün bir şekilde kullanılmıyorsa karşı etkili sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="c2b5b-107">Nesne havuzu kapsamlı başlatma gerektiren sık kullanılan nesnelerin yeniden yükünü azaltmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="c2b5b-108">Havuza alınmış bir nesne üzerinde bir yönteme bir çağrı önemli miktarda zaman alıyorsa, maksimum havuz boyutuna ulaştı hemen sonra ancak nesne havuzu ek istekler kuyruğa alır.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="c2b5b-109">Bu nedenle bazı nesne oluşturma isteklerinin bir zaman aşımı özel durum tarafından hizmet başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2b5b-110">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c2b5b-111">WCF uzantısı oluşturmanın ilk adımı, kullanılacak genişletilebilirlik noktası karar vermektir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="c2b5b-112">Wcf'de terimi *dağıtıcı* sorumlu kullanıcının hizmeti yöntem çağrılarına gelen iletileri dönüştürme ve dönüş değerleri Bu yöntemden giden bir iletiye dönüştürmek için bir çalışma zamanı bileşeni ifade eder.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="c2b5b-113">Bir WCF hizmeti bir dağıtıcı için her uç nokta oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="c2b5b-114">Bu istemciyle ilişkili sözleşme çift yönlü sözleşme ise bir WCF istemcisi bir dağıtıcı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="c2b5b-115">Kanal ve uç nokta dağıtıcıları kanal teklif- ve dağıtıcı davranışını denetleyen çeşitli özellikleri kullanıma sunan tarafından sözleşme kapsamında genişletilebilirlik.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="c2b5b-116"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> Özelliği de incelemek, değiştirme veya özelleştirme dağıtma işlemi olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="c2b5b-117">Bu örnek odaklanır <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> hizmet sınıfının örnekleri sağlayan bir nesneye işaret etmiyor özelliği.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="c2b5b-118">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="c2b5b-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="c2b5b-119">WCF'de, dağıtıcı hizmeti kullanarak sınıf örneği oluşturur. bir <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, uygulayan <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="c2b5b-120">Bu arabirim üç yöntem vardır:</span><span class="sxs-lookup"><span data-stu-id="c2b5b-120">This interface has three methods:</span></span>  
  
- <span data-ttu-id="c2b5b-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Bir ileti dağıtıcısı çağrıları geldiğinde <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> iletiyi işlemek için hizmet sınıfının bir örneğini oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="c2b5b-122">Bu yöntem çağrıları sıklığını belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="c2b5b-123">Örneğin, varsa <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği <xref:System.ServiceModel.InstanceContextMode.PerCall> ulaşan, bunu her iletiyi işlemek için hizmet sınıfının yeni bir örneğini oluşturan <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> bir ileti geldiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="c2b5b-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Hiçbir ileti bağımsız değişken olduğunda çağrılır ancak bu önceki yöntemin aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
- <span data-ttu-id="c2b5b-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Bir hizmet örneğinin ömrünü zaman geçti, dağıtıcı çağrıları <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="c2b5b-126">İçin olduğu gibi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> yöntemi, bu yöntem çağrıları sıklığına göre belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="c2b5b-127">Nesne havuzu</span><span class="sxs-lookup"><span data-stu-id="c2b5b-127">The Object Pool</span></span>  
 <span data-ttu-id="c2b5b-128">Özel bir <xref:System.ServiceModel.Dispatcher.IInstanceProvider> uygulamasını bir hizmet için semantiği havuzu gerekli bir nesneyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="c2b5b-129">Bu nedenle, bu örnek sahip bir `ObjectPoolingInstanceProvider` özel uygulanışı sağlayan tür <xref:System.ServiceModel.Dispatcher.IInstanceProvider> havuzu için.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="c2b5b-130">Zaman `Dispatcher` çağrıları <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> yöntemi, yeni bir örneğini oluşturmak yerine, özel uygulama var olan bir nesne, bellek havuzunda arar.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="c2b5b-131">Varsa, döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-131">If one is available, it is returned.</span></span> <span data-ttu-id="c2b5b-132">Aksi takdirde, yeni bir nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="c2b5b-133">Uygulamasını `GetInstance` aşağıdaki örnek kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="c2b5b-134">Özel `ReleaseInstance` uygulama havuzu ve azaltır için yayımlanan örneği ekler `ActiveObjectsCount` değeri.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="c2b5b-135">`Dispatcher` Farklı iş parçacıklarından bu yöntemleri çağırabilir ve bu nedenle sınıf düzeyinde üyelerine erişim eşitlenmiş `ObjectPoolingInstanceProvider` sınıfı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
```  
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
  
 <span data-ttu-id="c2b5b-136">`ReleaseInstance` Yöntemi "temizleme başlatma" özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="c2b5b-137">Normalde havuza havuz ömrü boyunca nesnelerin en az sayıda tutar.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="c2b5b-138">Bununla birlikte, yapılandırmada belirtilen üst sınırına ulaşmadığınız havuzunda ek nesneleri oluşturma gerektiren aşırı kullanım dönemlerini olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="c2b5b-139">Sonuç olarak, havuzu daha az etkin hale geldiğinde, fazlalık nesneleri bir ek yükü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="c2b5b-140">Bu nedenle, `activeObjectsCount` sıfıra indiğinde, tetikler ve bir temizleme döngüsü gerçekleştiren boş bir süreölçer başlatılır.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="c2b5b-141">Davranış ekleme</span><span class="sxs-lookup"><span data-stu-id="c2b5b-141">Adding the Behavior</span></span>  
 <span data-ttu-id="c2b5b-142">Dağıtıcı katman uzantıları aşağıdaki davranışları kullanarak sayfaya bağlanır:</span><span class="sxs-lookup"><span data-stu-id="c2b5b-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="c2b5b-143">Hizmet davranışları.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-143">Service Behaviors.</span></span> <span data-ttu-id="c2b5b-144">Bunlar, tüm hizmet çalışma zamanı özelleştirme için izin verir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-144">These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="c2b5b-145">Uç nokta davranışları.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-145">Endpoint Behaviors.</span></span> <span data-ttu-id="c2b5b-146">Bu hizmet uç noktaları, özellikle bir kanal ve uç nokta dağıtıcı özelleştirme yapma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
- <span data-ttu-id="c2b5b-147">Sözleşme davranışlar.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-147">Contract Behaviors.</span></span> <span data-ttu-id="c2b5b-148">Bu ikisinin özelleştirme için izin <xref:System.ServiceModel.Dispatcher.ClientRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime> istemciyi ve hizmeti üzerinde sırasıyla sınıfları.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="c2b5b-149">Uzantı havuzu bir nesne için bir hizmet davranışını oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="c2b5b-150">Hizmet davranışları uygulayarak oluşturulur <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="c2b5b-151">Hizmet modeli özel davranışlar haberdar olmak için birkaç yol vardır:</span><span class="sxs-lookup"><span data-stu-id="c2b5b-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="c2b5b-152">Özel bir öznitelik kullanma.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-152">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="c2b5b-153">Kesin hizmet açıklaması'nın davranışları koleksiyonunuza ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="c2b5b-154">Yapılandırma dosyası genişletme.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="c2b5b-155">Bu örnek bir özel öznitelik kullanır.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="c2b5b-156">Zaman <xref:System.ServiceModel.ServiceHost> oluşturulur bu hizmetin türü tanımında kullanılan öznitelikler inceler ve kullanılabilir davranışlar hizmet açıklaması'nın davranışları koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="c2b5b-157">Arabirim <xref:System.ServiceModel.Description.IServiceBehavior> üç yöntem--içerdiğinden <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, ve <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="c2b5b-158"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> Yöntemi davranış hizmetine uygulanabilir emin olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="c2b5b-159">Bu örnekte, uygulama hizmeti ile yapılandırılmamış sağlar <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="c2b5b-160"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> Yöntemi, hizmet bağlamalarını yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="c2b5b-161">Bu senaryoda gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-161">It is not required in this scenario.</span></span> <span data-ttu-id="c2b5b-162"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Hizmetin dağıtıcıları yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="c2b5b-163">Bu yöntem, WCF tarafından çağrılır, <xref:System.ServiceModel.ServiceHost> Başlatılmakta olan.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="c2b5b-164">Aşağıdaki parametreleri, bu yönteme geçirilir:</span><span class="sxs-lookup"><span data-stu-id="c2b5b-164">The following parameters are passed into this method:</span></span>  
  
- <span data-ttu-id="c2b5b-165">`Description`: Bu bağımsız değişken tüm hizmet hizmet açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="c2b5b-166">Bu hizmet uç noktaları, sözleşmeler, bağlamalar ve diğer verileri hakkında açıklama verilerini incelemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
- <span data-ttu-id="c2b5b-167">`ServiceHostBase`: Bu bağımsız değişken sağlar <xref:System.ServiceModel.ServiceHostBase> başlatılan şu anda.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="c2b5b-168">Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulama yeni bir örneği, `ObjectPoolingInstanceProvider` örneği ve atanan <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> her bir özellik <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ServiceHostBase içinde.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
```  
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
                if (throttle == null)  
                {  
                    throttle = cd.ServiceThrottle;  
                }  
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
  
 <span data-ttu-id="c2b5b-169">Ek olarak bir <xref:System.ServiceModel.Description.IServiceBehavior> uygulama <xref:System.EnterpriseServices.ObjectPoolingAttribute> sınıfı özniteliği bağımsız değişkenleri kullanarak nesne havuzu özelleştirmek için birkaç üyelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="c2b5b-170">Bu üyeleri içeren <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, ve <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, .NET Enterprise Hizmetleri tarafından sağlanan havuzu nesne eşleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="c2b5b-171">Davranış havuzu nesnesi artık bir WCF hizmeti için yeni oluşturulan özel hizmet uygulamasıyla açıklamalar eklenebilir `ObjectPooling` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="c2b5b-172">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c2b5b-172">Running the Sample</span></span>  
 <span data-ttu-id="c2b5b-173">Örnek, belirli senaryolarda nesne havuzu kullanarak kazanılan performans avantajlarının gösterir.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="c2b5b-174">İki Hizmetleri hizmet uygulamasının uygulayan `WorkService` ve `ObjectPooledWorkService`.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="c2b5b-175">Hem Hizmetleri aynı uygulama paylaşımı--Bunlar hem pahalı başlatma gerektirir ve sunarsınız bir `DoWork()` oldukça fazla alan kaplamıyor yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="c2b5b-176">Tek fark `ObjectPooledWorkService` sahip yapılandırılmış nesne havuzu:</span><span class="sxs-lookup"><span data-stu-id="c2b5b-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
```  
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
  
 <span data-ttu-id="c2b5b-177">İstemci çalıştırdığınızda, arama zaman `WorkService` 5 kez.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="c2b5b-178">Ardından arama zaman `ObjectPooledWorkService` 5 kez.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="c2b5b-179">Saat farkı ardından görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="c2b5b-179">The difference in time is then displayed:</span></span>  
  
```  
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
>  <span data-ttu-id="c2b5b-180">İstemci ilk çalıştırıldığında her iki hizmet de aynı süre hakkında yararlanmak için görünür.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="c2b5b-181">Örnek yeniden çalıştırırsanız, gördüğünüz gibi `ObjectPooledWorkService` havuzunda o nesnenin bir örneği zaten varolduğundan çok daha hızlı döndürür.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c2b5b-182">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c2b5b-182">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c2b5b-183">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2b5b-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c2b5b-184">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2b5b-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c2b5b-185">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2b5b-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2b5b-186">Bu örnek için yapılandırmayı yeniden üretmek için Svcutil.exe kullanma, istemci kodu eşleştirilecek istemci yapılandırmasında uç noktası adını değiştirmek emin olun.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c2b5b-187">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c2b5b-188">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-188">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c2b5b-189">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c2b5b-190">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c2b5b-190">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
