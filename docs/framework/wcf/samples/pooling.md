---
description: 'Daha fazla bilgi edinin: havuz'
title: Biriktirme
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: cb770b60a3011f95df5a2fdecea6cdc66b64710f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703854"
---
# <a name="pooling"></a><span data-ttu-id="852f3-103">Biriktirme</span><span class="sxs-lookup"><span data-stu-id="852f3-103">Pooling</span></span>

<span data-ttu-id="852f3-104">Bu örnek, nesne havuzlamayı desteklemek için Windows Communication Foundation (WCF) genişletmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="852f3-104">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="852f3-105">Örnek, bir sözdizimi ve anlamsal olarak `ObjectPoolingAttribute` Kurumsal hizmetlerin öznitelik işlevselliğine benzer bir öznitelik oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="852f3-105">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="852f3-106">Nesne havuzu oluşturma, uygulamanın performansına çarpıcı bir artırma sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="852f3-106">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="852f3-107">Ancak, düzgün bir şekilde kullanılmıyorsa, bu, karşı etkiye sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="852f3-107">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="852f3-108">Nesne havuzu oluşturma, kapsamlı başlatma gerektiren sık kullanılan nesneleri yeniden oluşturma yükünü azaltmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="852f3-108">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="852f3-109">Ancak, havuza alınmış bir nesne üzerindeki bir yönteme yapılan çağrının tamamlanmak için önemli miktarda zaman alırsa, en yüksek havuz boyutuna ulaşıldığında nesne havuzu oluşturma ek istekleri sıraya alır.</span><span class="sxs-lookup"><span data-stu-id="852f3-109">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="852f3-110">Bu nedenle, bir zaman aşımı özel durumu oluşturarak bazı nesne oluşturma isteklerine yönelik bir hata verebilir.</span><span class="sxs-lookup"><span data-stu-id="852f3-110">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="852f3-111">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="852f3-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="852f3-112">WCF uzantısı oluşturmanın ilk adımı, genişletilebilirlik noktasının kullanılmasına karar vermaktır.</span><span class="sxs-lookup"><span data-stu-id="852f3-112">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="852f3-113">WCF 'de *dağıtıcı* terimi, gelen iletileri kullanıcının hizmetinde Yöntem etkinleştirmeleri içine dönüştürmeden ve dönüş değerlerini Bu yöntemden giden bir iletiye dönüştürmekten sorumlu bir çalışma zamanı bileşenine başvurur.</span><span class="sxs-lookup"><span data-stu-id="852f3-113">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="852f3-114">WCF hizmeti her uç nokta için bir dağıtıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="852f3-114">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="852f3-115">Bir WCF istemcisinin, bu istemciyle ilişkili sözleşme bir çift yönlü sözleşirse bir dağıtıcı kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="852f3-115">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="852f3-116">Kanal ve uç nokta sevkiyatcılar, Dispatcher 'ın davranışını denetleyen çeşitli özellikleri açığa çıkarmak için kanal ve sözleşme genelinde genişletilebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="852f3-116">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="852f3-117"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A>Özelliği ayrıca, gönderme işlemini incelemenizi, değiştirmenizi veya özelleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="852f3-117">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="852f3-118">Bu örnek, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> hizmet sınıfının örneklerini sağlayan nesnesine işaret eden özelliğine odaklanır.</span><span class="sxs-lookup"><span data-stu-id="852f3-118">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="852f3-119">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="852f3-119">The IInstanceProvider</span></span>  

 <span data-ttu-id="852f3-120">WCF 'de, dağıtıcı, arabirimini uygulayan bir kullanarak hizmet sınıfının örneklerini oluşturur <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> <xref:System.ServiceModel.Dispatcher.IInstanceProvider> .</span><span class="sxs-lookup"><span data-stu-id="852f3-120">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="852f3-121">Bu arabirimin üç yöntemi vardır:</span><span class="sxs-lookup"><span data-stu-id="852f3-121">This interface has three methods:</span></span>  
  
- <span data-ttu-id="852f3-122"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: Bir ileti geldiğinde, dağıtıcı <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> iletiyi işlemek için hizmet sınıfının bir örneğini oluşturmak üzere yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="852f3-122"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="852f3-123">Bu yönteme yapılan çağrıların sıklığı, özelliği tarafından belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> .</span><span class="sxs-lookup"><span data-stu-id="852f3-123">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="852f3-124">Örneğin, <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> özelliği, <xref:System.ServiceModel.InstanceContextMode.PerCall> gelen her iletiyi işlemek için yeni bir hizmet sınıfı örneğine ayarlandıysa, her <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> ileti geldiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="852f3-124">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="852f3-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: Bu, bir Ileti bağımsız değişkeni olmadığında çağrılır hariç, önceki yöntemiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="852f3-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
- <span data-ttu-id="852f3-126"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: Bir hizmet örneğinin ömrü geçtiğinde, dağıtıcı <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="852f3-126"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="852f3-127">Yönteminde olduğu gibi <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> , bu yönteme yapılan çağrıların sıklığı özelliği tarafından belirlenir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> .</span><span class="sxs-lookup"><span data-stu-id="852f3-127">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="852f3-128">Nesne havuzu</span><span class="sxs-lookup"><span data-stu-id="852f3-128">The Object Pool</span></span>  

 <span data-ttu-id="852f3-129">Özel bir <xref:System.ServiceModel.Dispatcher.IInstanceProvider> uygulama, bir hizmet için gereken nesne havuzu semantiğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="852f3-129">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="852f3-130">Bu nedenle, bu örnekte `ObjectPoolingInstanceProvider` Havuz için özel uygulama sağlayan bir tür vardır <xref:System.ServiceModel.Dispatcher.IInstanceProvider> .</span><span class="sxs-lookup"><span data-stu-id="852f3-130">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="852f3-131">`Dispatcher`Yöntemi çağırdığında, <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> Yeni bir örnek oluşturmak yerine, özel uygulama bellek içi havuzda var olan bir nesneyi arar.</span><span class="sxs-lookup"><span data-stu-id="852f3-131">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="852f3-132">Kullanılabilir bir tane varsa, döndürülür.</span><span class="sxs-lookup"><span data-stu-id="852f3-132">If one is available, it is returned.</span></span> <span data-ttu-id="852f3-133">Aksi takdirde, yeni bir nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="852f3-133">Otherwise, a new object is created.</span></span> <span data-ttu-id="852f3-134">İçin uygulanması `GetInstance` Aşağıdaki örnek kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="852f3-134">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="852f3-135">Özel `ReleaseInstance` uygulama, yayımlanan örneği havuza geri ekler ve `ActiveObjectsCount` değeri azaltır.</span><span class="sxs-lookup"><span data-stu-id="852f3-135">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="852f3-136">, `Dispatcher` Farklı iş parçacıklarında bu yöntemleri çağırabilir ve bu nedenle, sınıftaki sınıf düzeyi üyelerine eşitlenen erişim `ObjectPoolingInstanceProvider` gerekir.</span><span class="sxs-lookup"><span data-stu-id="852f3-136">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
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
  
 <span data-ttu-id="852f3-137">`ReleaseInstance`Yöntemi "temiz başlatma" özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="852f3-137">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="852f3-138">Normalde havuz, havuzun ömrü boyunca en az sayıda nesne tutar.</span><span class="sxs-lookup"><span data-stu-id="852f3-138">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="852f3-139">Ancak, yapılandırmada belirtilen en yüksek sınıra ulaşmak için havuzda ek nesneler oluşturulmasını gerektiren aşırı kullanım süreleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="852f3-139">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="852f3-140">Sonuç olarak, havuz daha az etkin hale geldiğinde, bu fazlalık nesneler ek bir ek yük haline gelebilir.</span><span class="sxs-lookup"><span data-stu-id="852f3-140">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="852f3-141">Bu nedenle, `activeObjectsCount` sıfıra ulaştığında bir boşta zamanlayıcının tetiklediği ve bir Temizleme döngüsünü gerçekleştirdiği bir boşta kalma süreölçeri başlatılır.</span><span class="sxs-lookup"><span data-stu-id="852f3-141">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="852f3-142">Davranışı ekleme</span><span class="sxs-lookup"><span data-stu-id="852f3-142">Adding the Behavior</span></span>  

 <span data-ttu-id="852f3-143">Dağıtıcı katmanı uzantıları aşağıdaki davranışlar kullanılarak bağlanır:</span><span class="sxs-lookup"><span data-stu-id="852f3-143">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="852f3-144">Hizmet davranışları.</span><span class="sxs-lookup"><span data-stu-id="852f3-144">Service Behaviors.</span></span> <span data-ttu-id="852f3-145">Bu, tüm hizmet çalışma zamanının özelleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="852f3-145">These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="852f3-146">Uç nokta davranışları.</span><span class="sxs-lookup"><span data-stu-id="852f3-146">Endpoint Behaviors.</span></span> <span data-ttu-id="852f3-147">Bu, özellikle bir kanal ve uç nokta dağıtıcısı olan hizmet uç noktalarının özelleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="852f3-147">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
- <span data-ttu-id="852f3-148">Sözleşme davranışları.</span><span class="sxs-lookup"><span data-stu-id="852f3-148">Contract Behaviors.</span></span> <span data-ttu-id="852f3-149">Bunlar, hem hem de <xref:System.ServiceModel.Dispatcher.ClientRuntime> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> istemci üzerindeki ve hizmet üzerindeki sınıfların özelleştirilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="852f3-149">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="852f3-150">Bir nesne havuzu uzantısının amacı için bir hizmet davranışı oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="852f3-150">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="852f3-151">Hizmet davranışları arabirimi uygulayarak oluşturulur <xref:System.ServiceModel.Description.IServiceBehavior> .</span><span class="sxs-lookup"><span data-stu-id="852f3-151">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="852f3-152">Hizmet modelinin özel davranışlardan haberdar olması için çeşitli yollar vardır:</span><span class="sxs-lookup"><span data-stu-id="852f3-152">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="852f3-153">Özel bir öznitelik kullanma.</span><span class="sxs-lookup"><span data-stu-id="852f3-153">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="852f3-154">Imperatively, hizmet açıklamasının davranış koleksiyonuna ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="852f3-154">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="852f3-155">Yapılandırma dosyası genişletiliyor.</span><span class="sxs-lookup"><span data-stu-id="852f3-155">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="852f3-156">Bu örnek özel bir özniteliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="852f3-156">This sample uses a custom attribute.</span></span> <span data-ttu-id="852f3-157">Oluşturulduğunda, <xref:System.ServiceModel.ServiceHost> hizmetin tür tanımında kullanılan öznitelikleri inceler ve kullanılabilir davranışları hizmet açıklamasının davranış koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="852f3-157">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="852f3-158">Arabirimin <xref:System.ServiceModel.Description.IServiceBehavior> içinde üç yöntemi vardır-- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> , <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> , ve <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> .</span><span class="sxs-lookup"><span data-stu-id="852f3-158">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="852f3-159"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>Yöntemi, davranışın hizmete uygulanabileceğini sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="852f3-159">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="852f3-160">Bu örnekte, uygulama hizmetin ile yapılandırılmamasını sağlar <xref:System.ServiceModel.InstanceContextMode.Single> .</span><span class="sxs-lookup"><span data-stu-id="852f3-160">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="852f3-161"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>Yöntemi, hizmetin bağlamalarını yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="852f3-161">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="852f3-162">Bu senaryoda gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="852f3-162">It is not required in this scenario.</span></span> <span data-ttu-id="852f3-163">, <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> Hizmetin sevkiyatlarını yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="852f3-163">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="852f3-164">Bu yöntem, başlatıldığında WCF tarafından çağırılır <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="852f3-164">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="852f3-165">Aşağıdaki parametreler bu yönteme geçirilir:</span><span class="sxs-lookup"><span data-stu-id="852f3-165">The following parameters are passed into this method:</span></span>  
  
- <span data-ttu-id="852f3-166">`Description`: Bu bağımsız değişken hizmetin tamamı için hizmet açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="852f3-166">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="852f3-167">Bu, hizmetin uç noktaları, sözleşmeleri, bağlamaları ve diğer veriler hakkındaki açıklama verilerini denetlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="852f3-167">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
- <span data-ttu-id="852f3-168">`ServiceHostBase`: Bu bağımsız değişken, <xref:System.ServiceModel.ServiceHostBase> Şu anda başlatılmış olan ' i sağlar.</span><span class="sxs-lookup"><span data-stu-id="852f3-168">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="852f3-169">Özel uygulamada, <xref:System.ServiceModel.Description.IServiceBehavior> öğesinin yeni bir örneği örneği `ObjectPoolingInstanceProvider` oluşturulur ve her Ikisi de <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> ServiceHostBase içindeki özelliğe atanır.</span><span class="sxs-lookup"><span data-stu-id="852f3-169">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
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
  
 <span data-ttu-id="852f3-170">Bir uygulamaya ek olarak <xref:System.ServiceModel.Description.IServiceBehavior> , <xref:System.EnterpriseServices.ObjectPoolingAttribute> sınıfı öznitelik bağımsız değişkenlerini kullanarak nesne havuzunu özelleştirmek için çeşitli üyelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="852f3-170">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="852f3-171">Bu Üyeler, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A> <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A> <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A> .NET Enterprise Services tarafından sunulan nesne havuzu özellik kümesini eşleştirmek için, ve içerir.</span><span class="sxs-lookup"><span data-stu-id="852f3-171">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="852f3-172">Nesne havuzu oluşturma davranışı artık yeni oluşturulan özel öznitelikle hizmet uygulamasına ek olarak bir WCF hizmetine eklenebilir `ObjectPooling` .</span><span class="sxs-lookup"><span data-stu-id="852f3-172">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="852f3-173">Örnek çalıştırma</span><span class="sxs-lookup"><span data-stu-id="852f3-173">Running the Sample</span></span>  

 <span data-ttu-id="852f3-174">Örnek, belirli senaryolarda nesne havuzu kullanarak kazanılabilir performans avantajlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="852f3-174">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="852f3-175">Hizmet uygulaması iki hizmet uygular-- `WorkService` ve `ObjectPooledWorkService` .</span><span class="sxs-lookup"><span data-stu-id="852f3-175">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="852f3-176">Her iki hizmet de aynı uygulamayı paylaşır; her ikisi de pahalı başlatma gerektirir ve görece bir `DoWork()` yöntemi ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="852f3-176">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="852f3-177">Tek fark, `ObjectPooledWorkService` içinde nesne havuzlama yapılandırması olan ' dir:</span><span class="sxs-lookup"><span data-stu-id="852f3-177">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
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
  
 <span data-ttu-id="852f3-178">İstemcisini çalıştırdığınızda bu zaman `WorkService` 5 kez çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="852f3-178">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="852f3-179">Böylece 5 kez çağrı yapılır `ObjectPooledWorkService` .</span><span class="sxs-lookup"><span data-stu-id="852f3-179">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="852f3-180">Zaman içindeki fark daha sonra görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="852f3-180">The difference in time is then displayed:</span></span>  
  
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
> <span data-ttu-id="852f3-181">İstemci her iki hizmet de ilk kez çalıştırıldığında aynı süre içinde olacak şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="852f3-181">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="852f3-182">Örneği yeniden çalıştırırsanız, `ObjectPooledWorkService` Bu nesnenin bir örneği zaten havuzda bulunduğundan, bunun çok daha hızlı döndürdüğünden emin olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="852f3-182">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="852f3-183">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="852f3-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="852f3-184">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="852f3-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="852f3-185">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="852f3-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="852f3-186">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="852f3-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="852f3-187">Bu örneğe yönelik yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="852f3-187">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="852f3-188">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="852f3-188">The samples may already be installed on your machine.</span></span> <span data-ttu-id="852f3-189">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="852f3-189">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="852f3-190">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="852f3-190">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="852f3-191">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="852f3-191">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
