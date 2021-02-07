---
description: 'Daha fazla bilgi edinin: özel ömür'
title: Özel ömür
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 24845aaa20e60f92e2add568c81ab3d6502ebedf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732481"
---
# <a name="custom-lifetime"></a><span data-ttu-id="b3965-103">Özel ömür</span><span class="sxs-lookup"><span data-stu-id="b3965-103">Custom lifetime</span></span>

<span data-ttu-id="b3965-104">Bu örnek, paylaşılan WCF hizmet örnekleri için özel ömür hizmetleri sağlamak üzere bir Windows Communication Foundation (WCF) uzantısının nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3965-104">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>

> [!NOTE]
> <span data-ttu-id="b3965-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri Bu makalenin sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="b3965-105">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>

## <a name="shared-instancing"></a><span data-ttu-id="b3965-106">Paylaşılan örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="b3965-106">Shared instancing</span></span>

<span data-ttu-id="b3965-107">WCF, hizmet örneklerinizin çeşitli örnek oluşturma modlarını sunar.</span><span class="sxs-lookup"><span data-stu-id="b3965-107">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="b3965-108">Bu makalede ele alınan paylaşılan örnek oluşturma modu, bir hizmet örneğini birden çok kanal arasında paylaşmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3965-108">The shared instancing mode covered in this article provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="b3965-109">İstemciler, hizmette bir fabrika yöntemiyle iletişim kurabilirler ve iletişim başlatmak için yeni bir kanal oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="b3965-109">Clients can contact a factory method in the service and create a new channel to start communication.</span></span> <span data-ttu-id="b3965-110">Aşağıdaki kod parçacığı, bir istemci uygulamanın var olan bir hizmet örneğine nasıl yeni bir kanal oluşturduğunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="b3965-110">The following code snippet shows how a client application creates a new channel to an existing service instance:</span></span>

```csharp
// Create a header for the shared instance id
MessageHeader shareableInstanceContextHeader = MessageHeader.CreateHeader(
        CustomHeader.HeaderName,
        CustomHeader.HeaderNamespace,
        Guid.NewGuid().ToString());

// Create the channel factory
ChannelFactory<IEchoService> channelFactory =
    new ChannelFactory<IEchoService>("echoservice");

// Create the first channel
IEchoService proxy = channelFactory.CreateChannel();

// Call an operation to create shared service instance
using (new OperationContextScope((IClientChannel)proxy))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy.Echo("Apple"));
}

((IChannel)proxy).Close();

// Create the second channel
IEchoService proxy2 = channelFactory.CreateChannel();

// Call an operation using the same header that will reuse the shared service instance
using (new OperationContextScope((IClientChannel)proxy2))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy2.Echo("Apple"));
}
```

<span data-ttu-id="b3965-111">Diğer örnek oluşturma modlarının aksine, paylaşılan örnek oluşturma modunun hizmet örneklerini serbest bırakma yöntemine özgü bir yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="b3965-111">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="b3965-112">Varsayılan olarak, tüm kanallar bir için kapatıldığında <xref:System.ServiceModel.InstanceContext> , WCF hizmeti çalışma zamanı hizmetin veya olarak yapılandırılmış olup olmadığını denetler ve bu <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerCall> <xref:System.ServiceModel.InstanceContextMode.PerSession> durumda örneği serbest bırakır ve kaynakları talep eder.</span><span class="sxs-lookup"><span data-stu-id="b3965-112">By default, when all the channels are closed for an <xref:System.ServiceModel.InstanceContext>, the WCF service runtime checks to see if the service <xref:System.ServiceModel.InstanceContextMode> is configured to <xref:System.ServiceModel.InstanceContextMode.PerCall> or <xref:System.ServiceModel.InstanceContextMode.PerSession>, and if so releases the instance and claims the resources.</span></span> <span data-ttu-id="b3965-113">Bir özel <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> kullanılıyorsa, WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> örneği bırakmadan önce sağlayıcı uygulamasının yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="b3965-113">If a custom <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is being used, WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the provider implementation before releasing the instance.</span></span> <span data-ttu-id="b3965-114"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> `true` Örneği serbest bırakıldığında, <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> `Dispatcher` bir geri çağırma yöntemi kullanarak boşta durumuna bildirimde bulunmak için uygulama sorumludur.</span><span class="sxs-lookup"><span data-stu-id="b3965-114">If <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> returns `true` the instance is released, otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span> <span data-ttu-id="b3965-115">Bu, sağlayıcının yöntemi çağırarak yapılır <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> .</span><span class="sxs-lookup"><span data-stu-id="b3965-115">This is done by calling the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method of the provider.</span></span>

<span data-ttu-id="b3965-116">Bu örnek, <xref:System.ServiceModel.InstanceContext> bir boşta kalma zaman aşımı ile 20 saniye serbest bırakmayı nasıl erteleyebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3965-116">This sample demonstrates how you can delay releasing the <xref:System.ServiceModel.InstanceContext> with an idle timeout of 20 seconds.</span></span>

## <a name="extending-the-instancecontext"></a><span data-ttu-id="b3965-117">InstanceContext 'i genişletme</span><span class="sxs-lookup"><span data-stu-id="b3965-117">Extending the InstanceContext</span></span>

<span data-ttu-id="b3965-118">WCF 'de, <xref:System.ServiceModel.InstanceContext> hizmet örneği ve ile arasındaki bağlantıdır `Dispatcher` .</span><span class="sxs-lookup"><span data-stu-id="b3965-118">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="b3965-119">WCF, genişletilebilir nesne düzenlerini kullanarak bu çalışma zamanı bileşenini yeni durum veya davranış ekleyerek genişletmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3965-119">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="b3965-120">Genişletilebilir nesne stili, mevcut çalışma zamanı sınıflarını yeni işlevlerle genişletmek ya da bir nesneye yeni durum özellikleri eklemek için WCF 'de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b3965-120">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="b3965-121">Genişletilebilir nesne deseninin üç arabirimi vardır: <xref:System.ServiceModel.IExtensibleObject%601> , <xref:System.ServiceModel.IExtension%601> ve <xref:System.ServiceModel.IExtensionCollection%601> .</span><span class="sxs-lookup"><span data-stu-id="b3965-121">There are three interfaces in the extensible object pattern: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, and <xref:System.ServiceModel.IExtensionCollection%601>.</span></span>

<span data-ttu-id="b3965-122"><xref:System.ServiceModel.IExtensibleObject%601>Arabirim, işlevlerini özelleştiren uzantılara izin vermek için nesneleri tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b3965-122">The <xref:System.ServiceModel.IExtensibleObject%601> interface is implemented by objects to allow extensions that customize their functionality.</span></span>

<span data-ttu-id="b3965-123"><xref:System.ServiceModel.IExtension%601>Arabirim, türündeki sınıfların uzantıları olabilecek nesneler tarafından uygulanır `T` .</span><span class="sxs-lookup"><span data-stu-id="b3965-123">The <xref:System.ServiceModel.IExtension%601> interface is implemented by objects that can be extensions of classes of type `T`.</span></span>

<span data-ttu-id="b3965-124">Son olarak, <xref:System.ServiceModel.IExtensionCollection%601> arabirim, <xref:System.ServiceModel.IExtension%601> <xref:System.ServiceModel.IExtension%601> kendi türlerine göre uygulamasının alınmasına izin veren bir uygulamalar koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="b3965-124">And finally, the <xref:System.ServiceModel.IExtensionCollection%601> interface is a collection of <xref:System.ServiceModel.IExtension%601> implementations that allows for retrieving an implementation of <xref:System.ServiceModel.IExtension%601> by their type.</span></span>

<span data-ttu-id="b3965-125">Bu nedenle, öğesini genişletmek için <xref:System.ServiceModel.InstanceContext> arabirimini uygulamanız gerekir <xref:System.ServiceModel.IExtension%601> .</span><span class="sxs-lookup"><span data-stu-id="b3965-125">Therefore, in order to extend the <xref:System.ServiceModel.InstanceContext>, you must implement the <xref:System.ServiceModel.IExtension%601> interface.</span></span> <span data-ttu-id="b3965-126">Bu örnek projede, `CustomLeaseExtension` sınıfı bu uygulamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="b3965-126">In this sample project, the `CustomLeaseExtension` class contains this implementation.</span></span>

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<span data-ttu-id="b3965-127"><xref:System.ServiceModel.IExtension%601>Arabirimin iki yöntemi vardır <xref:System.ServiceModel.IExtension%601.Attach%2A> <xref:System.ServiceModel.IExtension%601.Detach%2A> .</span><span class="sxs-lookup"><span data-stu-id="b3965-127">The <xref:System.ServiceModel.IExtension%601> interface has two methods <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span></span> <span data-ttu-id="b3965-128">Adları da bu iki yöntem, çalışma zamanı, uzantıyı bir sınıfın örneğine iliştirir ve ayrıldığında çağrılır <xref:System.ServiceModel.InstanceContext> .</span><span class="sxs-lookup"><span data-stu-id="b3965-128">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="b3965-129">Bu örnekte, `Attach` yöntemi <xref:System.ServiceModel.InstanceContext> uzantının geçerli örneğine ait olan nesneyi izlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b3965-129">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

<span data-ttu-id="b3965-130">Ayrıca, genişletilmiş yaşam süresi desteğini sağlamak için gerekli uygulamayı uzantıya eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3965-130">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="b3965-131">Bu nedenle, `ICustomLease` arabirim istenen yöntemlerle bildirilmiştir ve `CustomLeaseExtension` sınıfında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b3965-131">Therefore, the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>

```csharp
interface ICustomLease
{
    bool IsIdle { get; }
    InstanceContextIdleCallback Callback { get; set; }
}

class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease
{
}
```

<span data-ttu-id="b3965-132">WCF <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> uygulamada yöntemi çağırdığında <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> , bu çağrı <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> öğesinin metoduna yönlendirilir `CustomLeaseExtension` .</span><span class="sxs-lookup"><span data-stu-id="b3965-132">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation, this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="b3965-133">Sonra, `CustomLeaseExtension` öğesinin boşta olup olmadığını görmek için özel durumunu denetler <xref:System.ServiceModel.InstanceContext> .</span><span class="sxs-lookup"><span data-stu-id="b3965-133">Then, the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="b3965-134">Boşta kalırsa, döndürür `true` .</span><span class="sxs-lookup"><span data-stu-id="b3965-134">If it is idle, it returns `true`.</span></span> <span data-ttu-id="b3965-135">Aksi halde, belirtilen miktarda genişletilmiş ömür için bir Zamanlayıcı başlatır.</span><span class="sxs-lookup"><span data-stu-id="b3965-135">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>

```csharp
public bool IsIdle
{
  get
  {
    lock (thisLock)
    {
      if (isIdle)
      {
        return true;
      }
      else
      {
        StartTimer();
        return false;
      }
    }
  }
}
```

<span data-ttu-id="b3965-136">Zamanlayıcının `Elapsed` olayında, başka bir Temizleme döngüsünü başlatmak Için dağıtıcıdaki geri çağırma işlevi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="b3965-136">In the timer’s `Elapsed` event, the callback function in the Dispatcher is called in order to start another clean-up cycle.</span></span>

```csharp
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)
{
    lock (thisLock)
    {
        StopTimer();
        isIdle = true;
        Utility.WriteMessageToConsole(
            ResourceHelper.GetString("MsgLeaseExpired"));
        callback(owner);
    }
}
```

<span data-ttu-id="b3965-137">Boşta durumuna taşınan örnek için yeni bir ileti geldiğinde çalışan süreölçeri yenilemenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="b3965-137">There's no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>

<span data-ttu-id="b3965-138">Örnek, <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> yöntemine yapılan çağrıları kesmeye <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> ve bunlara yönlendirmelerini uygular `CustomLeaseExtension` .</span><span class="sxs-lookup"><span data-stu-id="b3965-138">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="b3965-139"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>Uygulama `CustomLifetimeLease` sınıfında bulunur.</span><span class="sxs-lookup"><span data-stu-id="b3965-139">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="b3965-140"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>WCF hizmet örneğini serbest bırakmak üzere olduğunda yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b3965-140">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="b3965-141">Ancak, bu, bir uygulamanın yalnızca bir örneği olan bir tek örnek olarak, `ISharedSessionInstance` ServiceBehavior <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> koleksiyonunun koleksiyonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="b3965-141">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="b3965-142">Bu, <xref:System.ServiceModel.InstanceContext> WCF 'nin yöntemi denetleyip kapatılmadığını bilmenin bir yolu olmadığı anlamına gelir <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> .</span><span class="sxs-lookup"><span data-stu-id="b3965-142">This means there's no way of knowing if the <xref:System.ServiceModel.InstanceContext> is closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="b3965-143">Bu nedenle, bu örnek metoduna istekleri seri hale getirmek için iş parçacığı kilitleme kullanır <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> .</span><span class="sxs-lookup"><span data-stu-id="b3965-143">Therefore, this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b3965-144">Serileştirme uygulamanızın performansını ciddi bir şekilde etkileyebileceğinden, iş parçacığı kilitleme kullanılması önerilen bir yaklaşım değildir.</span><span class="sxs-lookup"><span data-stu-id="b3965-144">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>

<span data-ttu-id="b3965-145">Bir özel üye alanı, `CustomLifetimeLease` Boşta durumunu izlemek için sınıfında kullanılır ve yöntemi tarafından döndürülür <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> .</span><span class="sxs-lookup"><span data-stu-id="b3965-145">A private member field is used in the `CustomLifetimeLease` class to track the idle state and is returned by the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="b3965-146"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>Yöntemi her çağrıldığında, `isIdle` alan olarak döndürülür ve sıfırlanır `false` .</span><span class="sxs-lookup"><span data-stu-id="b3965-146">Each time the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is called, the `isIdle` field is returned and reset to `false`.</span></span>  <span data-ttu-id="b3965-147">`false`Dağıtıcıda yöntemi çağırdığından emin olmak için bu değerin olarak ayarlanması gereklidir <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> .</span><span class="sxs-lookup"><span data-stu-id="b3965-147">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>

```csharp
public bool IsIdle(InstanceContext instanceContext)
{
    get
    {
        lock (thisLock)
        {
            //...
            bool idleCopy = isIdle;
            isIdle = false;
            return idleCopy;
        }
    }
}
```

<span data-ttu-id="b3965-148"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>Yöntemi döndürürse `false` , dağıtıcı yöntemini kullanarak bir geri çağırma işlevi kaydeder <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> .</span><span class="sxs-lookup"><span data-stu-id="b3965-148">If the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> method returns `false`, the Dispatcher registers a callback function by using the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span> <span data-ttu-id="b3965-149">Bu yöntem, <xref:System.ServiceModel.InstanceContext> serbest bırakılmakta olan öğesine bir başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="b3965-149">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="b3965-150">Bu nedenle, örnek kod `ICustomLease` tür uzantısını sorgulayabilir ve `ICustomLease.IsIdle` genişletilmiş durumdaki özelliği kontrol edebilir.</span><span class="sxs-lookup"><span data-stu-id="b3965-150">Therefore, the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>

```csharp
public void NotifyIdle(InstanceContextIdleCallback callback,
            InstanceContext instanceContext)
{
    lock (thisLock)
    {
       ICustomLease customLease =
           instanceContext.Extensions.Find<ICustomLease>();
       customLease.Callback = callback;
       isIdle = customLease.IsIdle;
       if (isIdle)
       {
             callback(instanceContext);
       }
    }
}
```

<span data-ttu-id="b3965-151">`ICustomLease.IsIdle`Özellik denetlenmadan önce, bu, dağıtıcıya boşta kaldığında bildirimde bulunması için gerekli olduğundan geri çağırma özelliği ayarlanmalıdır `CustomLeaseExtension` .</span><span class="sxs-lookup"><span data-stu-id="b3965-151">Before the `ICustomLease.IsIdle` property is checked, the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="b3965-152">`ICustomLease.IsIdle`Öğesini döndürürse `true` , `isIdle` özel üye ' ın `CustomLifetimeLease` öğesine ayarlanır `true` ve geri çağırma yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="b3965-152">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="b3965-153">Kod bir kilit içerdiğinden, diğer iş parçacıkları bu özel üyenin değerini değiştiremezler.</span><span class="sxs-lookup"><span data-stu-id="b3965-153">Because the code holds a lock, other threads can't change the value of this private member.</span></span> <span data-ttu-id="b3965-154">Dağıtıcısı bir sonraki sefer aradığında,, <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> `true` Dispatcher örneğini serbest bırakmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="b3965-154">And the next time Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, it returns `true` and lets Dispatcher release the instance.</span></span>

<span data-ttu-id="b3965-155">Artık özel uzantı için groundçalışmadığına göre, hizmet modeline bağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3965-155">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="b3965-156">`CustomLeaseExtension`Uygulamanızı öğesine bağlamak için <xref:System.ServiceModel.InstanceContext> WCF, ' nin önkurulumunu <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> gerçekleştirme arabirimini sağlar <xref:System.ServiceModel.InstanceContext> .</span><span class="sxs-lookup"><span data-stu-id="b3965-156">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="b3965-157">Örnekte, `CustomLeaseInitializer` sınıfı bu arabirimi uygular ve `CustomLeaseExtension` <xref:System.ServiceModel.InstanceContext.Extensions%2A> tek yöntem başlatmasıyla koleksiyona bir örneği ekler.</span><span class="sxs-lookup"><span data-stu-id="b3965-157">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="b3965-158">Bu yöntem, başlatılırken dağıtıcı tarafından çağırılır <xref:System.ServiceModel.InstanceContext> .</span><span class="sxs-lookup"><span data-stu-id="b3965-158">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 <span data-ttu-id="b3965-159">Son olarak, uygulama, <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygulamayı kullanarak hizmet modeline bağlanır <xref:System.ServiceModel.Description.IServiceBehavior> .</span><span class="sxs-lookup"><span data-stu-id="b3965-159">Finally the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="b3965-160">Bu uygulama `CustomLeaseTimeAttribute` sınıfına yerleştirilir ve ayrıca <xref:System.Attribute> Bu davranışı bir öznitelik olarak göstermek için temel sınıftan türetilir.</span><span class="sxs-lookup"><span data-stu-id="b3965-160">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the <xref:System.Attribute> base class to expose this behavior as an attribute.</span></span>

```csharp
public void ApplyDispatchBehavior(ServiceDescription description,
           ServiceHostBase serviceHostBase)
{
    CustomLifetimeLease customLease = new CustomLifetimeLease(timeout);

    foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
    {
        ChannelDispatcher cd = cdb as ChannelDispatcher;

        if (cd != null)
        {
            foreach (EndpointDispatcher ed in cd.Endpoints)
            {
                ed.DispatchRuntime.InstanceContextProvider = customLease;
            }
        }
    }
}
```

<span data-ttu-id="b3965-161">Bu davranış, özniteliğe ek olarak eklenerek örnek bir hizmet sınıfına eklenebilir `CustomLeaseTime` .</span><span class="sxs-lookup"><span data-stu-id="b3965-161">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

<span data-ttu-id="b3965-162">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b3965-162">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="b3965-163">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b3965-163">Press ENTER in each console window to shut down the service and client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b3965-164">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b3965-164">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="b3965-165">[Windows Communication Foundation Örnekleri Için bir kerelik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b3965-165">Ensure that you've performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="b3965-166">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="b3965-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="b3965-167">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="b3965-167">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b3965-168">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b3965-168">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b3965-169">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b3965-169">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b3965-170">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b3965-170">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b3965-171">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b3965-171">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
