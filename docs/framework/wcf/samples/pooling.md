---
title: Biriktirme
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 6554ec9c5eaefaf8c9e39d2a8d92982716cc18c5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809826"
---
# <a name="pooling"></a><span data-ttu-id="a8283-102">Biriktirme</span><span class="sxs-lookup"><span data-stu-id="a8283-102">Pooling</span></span>
<span data-ttu-id="a8283-103">Bu örnek, nesne havuzu desteklemek için Windows Communication Foundation (WCF) genişletmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a8283-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="a8283-104">Örnek sözdizimsel olarak ve anlam olarak benzer bir öznitelik oluşturmak nasıl gösterir `ObjectPoolingAttribute` Kurumsal Hizmetler işlevselliğini özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a8283-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="a8283-105">Nesne havuzu çarpıcı artırma uygulamanın performans sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a8283-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="a8283-106">Ancak, doğru kullanılmıyorsa ters etkisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8283-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="a8283-107">Nesne havuzu kapsamlı başlatma gerektiren sık kullanılan nesnelerini yeniden yükünü azaltmanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a8283-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="a8283-108">Havuza alınmış bir nesne üzerinde bir yöntem çağrısı bir önemli tamamlamak için gereken süre, en büyük havuz boyutu sınırına hemen sonra ancak, nesne havuzu ek istekler kuyruğa atılıyor.</span><span class="sxs-lookup"><span data-stu-id="a8283-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="a8283-109">Bu nedenle bir zaman aşımı özel durum atma tarafından bazı nesne oluşturma isteklere hizmet başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8283-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8283-110">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="a8283-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a8283-111">WCF uzantısı oluşturmanın ilk adımı, genişletilebilirlik noktasını kullanmak üzere karar vermektir.</span><span class="sxs-lookup"><span data-stu-id="a8283-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="a8283-112">WCF'de terimi *dağıtıcısı* sorumlu kullanıcının hizmet üzerinde yöntem çağrılarına gelen iletileri dönüştürme ve Giden iletiye Bu yöntemden dönüş değerleri dönüştürme için bir çalışma zamanı bileşeni başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="a8283-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="a8283-113">Bir WCF hizmeti bir dağıtıcı her bitiş noktasıyla ilgili oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a8283-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="a8283-114">Bu istemciyle ilişkili sözleşme çift yönlü sözleşme ise bir WCF istemcisi bir dağıtıcı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8283-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="a8283-115">Kanal ve uç nokta dağıtıcıları kanal sunar- ve dağıtıcı davranışını denetleyen çeşitli özellikler gösterme tarafından sözleşme genelinde genişletilebilirlik.</span><span class="sxs-lookup"><span data-stu-id="a8283-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="a8283-116"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> Özelliği de inceleme, değiştirme veya dağıtma işlemi özelleştirmek olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8283-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="a8283-117">Bu örnek odaklanır <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> hizmet sınıfının örnekleri sağlayan bir nesneye işaret etmiyor özelliği.</span><span class="sxs-lookup"><span data-stu-id="a8283-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="a8283-118">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="a8283-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="a8283-119">WCF'de, dağıtıcı kullanarak hizmet sınıfı örneği oluşturur. bir <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, hangi uygulayan <xref:System.ServiceModel.Dispatcher.IInstanceProvider> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a8283-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="a8283-120">Bu arabirim üç yöntem vardır:</span><span class="sxs-lookup"><span data-stu-id="a8283-120">This interface has three methods:</span></span>  
  
-   <span data-ttu-id="a8283-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Bir ileti geldiğinde dağıtıcısı çağrıları <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> iletiyi işlemek için hizmet sınıfının bir örneğini oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a8283-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="a8283-122">Bu yönteme çağrıları sıklığını tarafından belirlenen <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a8283-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="a8283-123">Örneğin, varsa <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği ayarlanmış <xref:System.ServiceModel.InstanceContextMode.PerCall> hizmet sınıfının yeni bir örneğini, bunu ulaşan her iletiyi işlemek için oluşturulan <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> bir ileti ulaştığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a8283-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
-   <span data-ttu-id="a8283-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: İleti bağımsız değişken olduğunda çağrılır dışında bu önceki yöntemin aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a8283-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
-   <span data-ttu-id="a8283-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Bir hizmet örneğinin ömrü ne zaman geçti, dağıtıcı çağrıları <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a8283-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="a8283-126">İçin olduğu gibi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> yöntemi, bu yönteme çağrıları sıklığını tarafından belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a8283-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="a8283-127">Nesne havuzu</span><span class="sxs-lookup"><span data-stu-id="a8283-127">The Object Pool</span></span>  
 <span data-ttu-id="a8283-128">Özel bir <xref:System.ServiceModel.Dispatcher.IInstanceProvider> uygulamasını bir hizmet için semantiği havuzu gerekli bir nesneyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8283-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="a8283-129">Bu nedenle, bu örnek sahip bir `ObjectPoolingInstanceProvider` özel uyarlamasını sağlayan türü <xref:System.ServiceModel.Dispatcher.IInstanceProvider> havuzu için.</span><span class="sxs-lookup"><span data-stu-id="a8283-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="a8283-130">Zaman `Dispatcher` çağrıları <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> yeni bir örneği oluşturmak yerine yöntemi, özel uygulama bellek içi havuzdaki var olan bir nesne arar.</span><span class="sxs-lookup"><span data-stu-id="a8283-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="a8283-131">Varsa, döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a8283-131">If one is available, it is returned.</span></span> <span data-ttu-id="a8283-132">Aksi takdirde, yeni bir nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a8283-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="a8283-133">Uygulamasını `GetInstance` aşağıdaki örnek kodda gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a8283-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="a8283-134">Özel `ReleaseInstance` uygulama havuzu ve azaltır için örnek yayınlandı ekler `ActiveObjectsCount` değeri.</span><span class="sxs-lookup"><span data-stu-id="a8283-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="a8283-135">`Dispatcher` Bu yöntemleri farklı iş parçacıklarından çağırabilir ve bu nedenle sınıf düzeyinde üyelerine erişimi eşitlenmiş `ObjectPoolingInstanceProvider` sınıfı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a8283-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
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
  
 <span data-ttu-id="a8283-136">`ReleaseInstance` Yöntemi "temizleme başlatma" özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8283-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="a8283-137">Normalde havuzu nesneler en az sayıda havuzu ömrü boyunca tutar.</span><span class="sxs-lookup"><span data-stu-id="a8283-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="a8283-138">Ancak, yapılandırmada belirtilen en üst sınıra ulaşması havuzundaki ek nesneleri oluşturma gerektiren aşırı kullanım dönemlerini olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8283-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="a8283-139">Sonuç olarak, havuzu daha az etkin hale geldiğinde fazlalık nesnelere ek yüke haline gelebilir.</span><span class="sxs-lookup"><span data-stu-id="a8283-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="a8283-140">Bu nedenle, `activeObjectsCount` ulaştığında sıfır, boş bir süreölçer tetikler ve temizleme döngüsü gerçekleştiren başlatılır.</span><span class="sxs-lookup"><span data-stu-id="a8283-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="a8283-141">Davranış ekleme</span><span class="sxs-lookup"><span data-stu-id="a8283-141">Adding the Behavior</span></span>  
 <span data-ttu-id="a8283-142">Dağıtıcı katman uzantıları aşağıdaki davranışları kullanarak sayfaya bağlanır:</span><span class="sxs-lookup"><span data-stu-id="a8283-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
-   <span data-ttu-id="a8283-143">Hizmet davranışları.</span><span class="sxs-lookup"><span data-stu-id="a8283-143">Service Behaviors.</span></span> <span data-ttu-id="a8283-144">Bunlar, tüm hizmet çalışma zamanı özelleştirmesi için izin verir.</span><span class="sxs-lookup"><span data-stu-id="a8283-144">These allow for the customization of the entire service runtime.</span></span>  
  
-   <span data-ttu-id="a8283-145">Uç nokta davranışlar.</span><span class="sxs-lookup"><span data-stu-id="a8283-145">Endpoint Behaviors.</span></span> <span data-ttu-id="a8283-146">Bunlar, hizmet uç noktaları, özellikle bir kanal ve uç nokta dağıtıcısı özelleştirmesi için izin verir.</span><span class="sxs-lookup"><span data-stu-id="a8283-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
-   <span data-ttu-id="a8283-147">Sözleşme davranışlar.</span><span class="sxs-lookup"><span data-stu-id="a8283-147">Contract Behaviors.</span></span> <span data-ttu-id="a8283-148">Bunlar için her ikisini de özelleştirilmesine imkan tanımak <xref:System.ServiceModel.Dispatcher.ClientRuntime> ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime> istemci ve hizmet sırasıyla sınıfları.</span><span class="sxs-lookup"><span data-stu-id="a8283-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="a8283-149">Uzantı havuzu bir nesne amacıyla hizmet davranışı oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8283-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="a8283-150">Hizmet davranışları uygulayarak oluşturulur <xref:System.ServiceModel.Description.IServiceBehavior> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a8283-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="a8283-151">Hizmet modeli özel davranışlar haberdar olmak için birkaç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="a8283-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
-   <span data-ttu-id="a8283-152">Özel bir öznitelik kullanma.</span><span class="sxs-lookup"><span data-stu-id="a8283-152">Using a custom attribute.</span></span>  
  
-   <span data-ttu-id="a8283-153">İmperatively hizmet açıklaması 's davranışları koleksiyona ekleme.</span><span class="sxs-lookup"><span data-stu-id="a8283-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
-   <span data-ttu-id="a8283-154">Yapılandırma dosyası genişletme.</span><span class="sxs-lookup"><span data-stu-id="a8283-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="a8283-155">Bu örnek özel bir öznitelik kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8283-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="a8283-156">Zaman <xref:System.ServiceModel.ServiceHost> oluşturulan hizmetin tür tanımında kullanılan öznitelikler inceler ve kullanılabilir davranışları hizmet açıklaması 's davranışları koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="a8283-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="a8283-157">Arabirim <xref:System.ServiceModel.Description.IServiceBehavior> üç yöntem--içerdiği <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, ve <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8283-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="a8283-158"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> Yöntemi davranışı hizmete uygulanabilir emin olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8283-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="a8283-159">Bu örnekte, uygulama hizmeti ile yapılandırılmamış sağlar <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="a8283-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="a8283-160"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> Yöntemi hizmetin bağlamalar yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8283-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="a8283-161">Bu senaryoda gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a8283-161">It is not required in this scenario.</span></span> <span data-ttu-id="a8283-162"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Hizmetin dağıtıcıları yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8283-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="a8283-163">Bu yöntem WCF tarafından çağrılır zaman <xref:System.ServiceModel.ServiceHost> başlatıldığını.</span><span class="sxs-lookup"><span data-stu-id="a8283-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="a8283-164">Aşağıdaki parametreleri, bu yönteme geçirilen:</span><span class="sxs-lookup"><span data-stu-id="a8283-164">The following parameters are passed into this method:</span></span>  
  
-   <span data-ttu-id="a8283-165">`Description`: Bu bağımsız değişken tüm hizmet hizmet açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8283-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="a8283-166">Bu hizmetin uç noktaları, sözleşmeler, bağlamaları ve diğer verileri hakkında açıklama verilerini incelemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8283-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
-   <span data-ttu-id="a8283-167">`ServiceHostBase`: Bu bağımsız değişken sağlar <xref:System.ServiceModel.ServiceHostBase> , şu anda başlatılır.</span><span class="sxs-lookup"><span data-stu-id="a8283-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="a8283-168">Özel <xref:System.ServiceModel.Description.IServiceBehavior> uygulama yeni bir örnek, `ObjectPoolingInstanceProvider` örneği ve atanan <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> her bir özellik <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ServiceHostBase içinde.</span><span class="sxs-lookup"><span data-stu-id="a8283-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
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
  
 <span data-ttu-id="a8283-169">Ek olarak bir <xref:System.ServiceModel.Description.IServiceBehavior> uygulama <xref:System.EnterpriseServices.ObjectPoolingAttribute> sınıfı öznitelik bağımsız değişkenleri kullanarak nesne havuzu özelleştirmek için birkaç üye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a8283-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="a8283-170">Bu üyeleri dahil <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, ve <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, .NET Enterprise Hizmetleri tarafından sağlanan özellik kümesi havuzu nesne eşleşecek şekilde.</span><span class="sxs-lookup"><span data-stu-id="a8283-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="a8283-171">Davranış havuzu nesne artık bir WCF hizmetine yeni oluşturulan özel hizmet uygulamasıyla yorumlama tarafından eklenebilir `ObjectPooling` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a8283-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="a8283-172">Örnek çalışıyor</span><span class="sxs-lookup"><span data-stu-id="a8283-172">Running the Sample</span></span>  
 <span data-ttu-id="a8283-173">Örnek, belirli senaryolarda nesne havuzu kullanarak kazanılan performans avantajı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8283-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="a8283-174">Hizmet uygulaması iki hizmet--uygulayan `WorkService` ve `ObjectPooledWorkService`.</span><span class="sxs-lookup"><span data-stu-id="a8283-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="a8283-175">Hem Hizmetleri aynı uygulama paylaşımı--Bunlar hem pahalı başlatma gerektirir ve sonra kullanıma bir `DoWork()` görece ucuz yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a8283-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="a8283-176">Tek fark `ObjectPooledWorkService` sahip yapılandırılmış nesne havuzu:</span><span class="sxs-lookup"><span data-stu-id="a8283-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
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
  
 <span data-ttu-id="a8283-177">İstemci çalıştırdığınızda, arama zaman `WorkService` 5 kez.</span><span class="sxs-lookup"><span data-stu-id="a8283-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="a8283-178">Daha sonra arama zaman `ObjectPooledWorkService` 5 kez.</span><span class="sxs-lookup"><span data-stu-id="a8283-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="a8283-179">Saat farkı sonra görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="a8283-179">The difference in time is then displayed:</span></span>  
  
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
>  <span data-ttu-id="a8283-180">İstemci bir ilk çalıştırıldığında, aynı miktarda süre hakkında olabilmesi için her iki hizmet görünür.</span><span class="sxs-lookup"><span data-stu-id="a8283-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="a8283-181">Örneği yeniden çalıştırırsanız, görebilirsiniz `ObjectPooledWorkService` söz konusu nesne örneği havuzunda zaten mevcut olduğundan çok daha hızlı döndürür.</span><span class="sxs-lookup"><span data-stu-id="a8283-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a8283-182">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="a8283-182">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a8283-183">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8283-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a8283-184">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8283-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a8283-185">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8283-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8283-186">Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanırsanız, istemci kodu eşleşecek şekilde istemci yapılandırmasında uç nokta adı değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a8283-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a8283-187">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8283-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a8283-188">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a8283-188">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a8283-189">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a8283-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a8283-190">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a8283-190">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
  
## <a name="see-also"></a><span data-ttu-id="a8283-191">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8283-191">See Also</span></span>
