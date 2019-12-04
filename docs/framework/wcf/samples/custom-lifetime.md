---
title: Özel ömür
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 8625877d9b4d05d5cf06af2c9f8ef10f701e98db
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715472"
---
# <a name="custom-lifetime"></a><span data-ttu-id="420c6-102">Özel ömür</span><span class="sxs-lookup"><span data-stu-id="420c6-102">Custom lifetime</span></span>

<span data-ttu-id="420c6-103">Bu örnek, paylaşılan WCF hizmet örnekleri için özel ömür hizmetleri sağlamak üzere bir Windows Communication Foundation (WCF) uzantısının nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="420c6-103">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>

> [!NOTE]
> <span data-ttu-id="420c6-104">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri Bu makalenin sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="420c6-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>

## <a name="shared-instancing"></a><span data-ttu-id="420c6-105">Paylaşılan örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="420c6-105">Shared instancing</span></span>

<span data-ttu-id="420c6-106">WCF, hizmet örneklerinizin çeşitli örnek oluşturma modlarını sunar.</span><span class="sxs-lookup"><span data-stu-id="420c6-106">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="420c6-107">Bu makalede ele alınan paylaşılan örnek oluşturma modu, bir hizmet örneğini birden çok kanal arasında paylaşmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="420c6-107">The shared instancing mode covered in this article provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="420c6-108">İstemciler, hizmette bir fabrika yöntemiyle iletişim kurabilirler ve iletişim başlatmak için yeni bir kanal oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="420c6-108">Clients can contact a factory method in the service and create a new channel to start communication.</span></span> <span data-ttu-id="420c6-109">Aşağıdaki kod parçacığı, bir istemci uygulamanın var olan bir hizmet örneğine nasıl yeni bir kanal oluşturduğunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="420c6-109">The following code snippet shows how a client application creates a new channel to an existing service instance:</span></span>

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

<span data-ttu-id="420c6-110">Diğer örnek oluşturma modlarının aksine, paylaşılan örnek oluşturma modunun hizmet örneklerini serbest bırakma yöntemine özgü bir yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="420c6-110">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="420c6-111">Varsayılan olarak, tüm kanallar bir <xref:System.ServiceModel.InstanceContext>için kapatıldığında, WCF hizmeti çalışma zamanı, hizmet <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerCall> veya <xref:System.ServiceModel.InstanceContextMode.PerSession>olarak yapılandırılıp yapılandırılmadığını denetler ve bu durumda örneği serbest bırakır ve kaynakları talep eder.</span><span class="sxs-lookup"><span data-stu-id="420c6-111">By default, when all the channels are closed for an <xref:System.ServiceModel.InstanceContext>, the WCF service runtime checks to see if the service <xref:System.ServiceModel.InstanceContextMode> is configured to <xref:System.ServiceModel.InstanceContextMode.PerCall> or <xref:System.ServiceModel.InstanceContextMode.PerSession>, and if so releases the instance and claims the resources.</span></span> <span data-ttu-id="420c6-112">Özel bir <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> kullanılıyorsa, WCF örneği serbest bırakmadan önce sağlayıcı uygulamasının <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="420c6-112">If a custom <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is being used, WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the provider implementation before releasing the instance.</span></span> <span data-ttu-id="420c6-113"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>, örnek `true` döndürürse <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygulama, bir geri çağırma yöntemi kullanarak boşta durumunun `Dispatcher` bildirilmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="420c6-113">If <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> returns `true` the instance is released, otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span> <span data-ttu-id="420c6-114">Bu, sağlayıcının <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> yöntemi çağırarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="420c6-114">This is done by calling the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method of the provider.</span></span>

<span data-ttu-id="420c6-115">Bu örnek, boşta kalma zaman aşımı olan 20 saniyelik <xref:System.ServiceModel.InstanceContext> serbest bırakmayı nasıl erteleyebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="420c6-115">This sample demonstrates how you can delay releasing the <xref:System.ServiceModel.InstanceContext> with an idle timeout of 20 seconds.</span></span>

## <a name="extending-the-instancecontext"></a><span data-ttu-id="420c6-116">InstanceContext 'i genişletme</span><span class="sxs-lookup"><span data-stu-id="420c6-116">Extending the InstanceContext</span></span>

<span data-ttu-id="420c6-117">WCF 'de, <xref:System.ServiceModel.InstanceContext> hizmet örneği ve `Dispatcher`arasındaki bağlantıdır.</span><span class="sxs-lookup"><span data-stu-id="420c6-117">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="420c6-118">WCF, genişletilebilir nesne düzenlerini kullanarak bu çalışma zamanı bileşenini yeni durum veya davranış ekleyerek genişletmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="420c6-118">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="420c6-119">Genişletilebilir nesne stili, mevcut çalışma zamanı sınıflarını yeni işlevlerle genişletmek ya da bir nesneye yeni durum özellikleri eklemek için WCF 'de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="420c6-119">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="420c6-120">Genişletilebilir nesne deseninin üç arabirimi vardır: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>ve <xref:System.ServiceModel.IExtensionCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="420c6-120">There are three interfaces in the extensible object pattern: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, and <xref:System.ServiceModel.IExtensionCollection%601>.</span></span>

<span data-ttu-id="420c6-121"><xref:System.ServiceModel.IExtensibleObject%601> arabirimi, işlevlerini özelleştiren uzantılara izin vermek için nesneleri tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="420c6-121">The <xref:System.ServiceModel.IExtensibleObject%601> interface is implemented by objects to allow extensions that customize their functionality.</span></span>

<span data-ttu-id="420c6-122"><xref:System.ServiceModel.IExtension%601> arabirimi, `T`türündeki sınıfların uzantıları olabilecek nesneler tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="420c6-122">The <xref:System.ServiceModel.IExtension%601> interface is implemented by objects that can be extensions of classes of type `T`.</span></span>

<span data-ttu-id="420c6-123">Son olarak <xref:System.ServiceModel.IExtensionCollection%601> arabirimi, bir <xref:System.ServiceModel.IExtension%601> uygulamasını türlerine göre almaya izin veren <xref:System.ServiceModel.IExtension%601> uygulamalarının bir koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="420c6-123">And finally, the <xref:System.ServiceModel.IExtensionCollection%601> interface is a collection of <xref:System.ServiceModel.IExtension%601> implementations that allows for retrieving an implementation of <xref:System.ServiceModel.IExtension%601> by their type.</span></span>

<span data-ttu-id="420c6-124">Bu nedenle, <xref:System.ServiceModel.InstanceContext>genişletmek için <xref:System.ServiceModel.IExtension%601> arabirimini uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="420c6-124">Therefore, in order to extend the <xref:System.ServiceModel.InstanceContext>, you must implement the <xref:System.ServiceModel.IExtension%601> interface.</span></span> <span data-ttu-id="420c6-125">Bu örnek projede, `CustomLeaseExtension` sınıfı bu uygulamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="420c6-125">In this sample project, the `CustomLeaseExtension` class contains this implementation.</span></span>

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<span data-ttu-id="420c6-126"><xref:System.ServiceModel.IExtension%601> arabiriminin iki yöntemi vardır <xref:System.ServiceModel.IExtension%601.Attach%2A> ve <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span><span class="sxs-lookup"><span data-stu-id="420c6-126">The <xref:System.ServiceModel.IExtension%601> interface has two methods <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span></span> <span data-ttu-id="420c6-127">Adları da bu iki yöntem, çalışma zamanı tarafından <xref:System.ServiceModel.InstanceContext> sınıfının bir örneğine ekler ve uzantıyı ayırır.</span><span class="sxs-lookup"><span data-stu-id="420c6-127">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="420c6-128">Bu örnekte, uzantısının geçerli örneğine ait olan <xref:System.ServiceModel.InstanceContext> nesnesini izlemek için `Attach` yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="420c6-128">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

<span data-ttu-id="420c6-129">Ayrıca, genişletilmiş yaşam süresi desteğini sağlamak için gerekli uygulamayı uzantıya eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="420c6-129">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="420c6-130">Bu nedenle `ICustomLease` arabirimi istenen yöntemlerle bildirilmiştir ve `CustomLeaseExtension` sınıfında uygulanır.</span><span class="sxs-lookup"><span data-stu-id="420c6-130">Therefore, the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>

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

<span data-ttu-id="420c6-131">WCF, <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygulamasında <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemini çağırdığında, bu çağrı `CustomLeaseExtension`<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemine yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="420c6-131">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation, this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="420c6-132">Sonra, `CustomLeaseExtension` <xref:System.ServiceModel.InstanceContext> boşta olup olmadığını görmek için kendi özel durumunu denetler.</span><span class="sxs-lookup"><span data-stu-id="420c6-132">Then, the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="420c6-133">Boşta ise `true`döndürür.</span><span class="sxs-lookup"><span data-stu-id="420c6-133">If it is idle, it returns `true`.</span></span> <span data-ttu-id="420c6-134">Aksi halde, belirtilen miktarda genişletilmiş ömür için bir Zamanlayıcı başlatır.</span><span class="sxs-lookup"><span data-stu-id="420c6-134">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>

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

<span data-ttu-id="420c6-135">Zamanlayıcının `Elapsed` olayında, başka bir Temizleme döngüsünü başlatmak için dağıtıcıdaki geri çağırma işlevi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="420c6-135">In the timer’s `Elapsed` event, the callback function in the Dispatcher is called in order to start another clean-up cycle.</span></span>

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

<span data-ttu-id="420c6-136">Boşta durumuna taşınan örnek için yeni bir ileti geldiğinde çalışan süreölçeri yenilemenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="420c6-136">There's no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>

<span data-ttu-id="420c6-137">Örnek, <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemine yapılan çağrıları kesmeye ve bunları `CustomLeaseExtension`yönlendirmeye yönelik <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygular.</span><span class="sxs-lookup"><span data-stu-id="420c6-137">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="420c6-138"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygulama `CustomLifetimeLease` sınıfında bulunur.</span><span class="sxs-lookup"><span data-stu-id="420c6-138">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="420c6-139">WCF hizmet örneğini serbest bırakmak üzere olduğunda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="420c6-139">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="420c6-140">Ancak, bu `ISharedSessionInstance` bir uygulamanın yalnızca bir örneği, ServiceBehavior 'in <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> koleksiyonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="420c6-140">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="420c6-141">Bu, <xref:System.ServiceModel.InstanceContext> WCF 'nin <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemini denetleyip kapatmadığını bilmenin bir yolu olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="420c6-141">This means there's no way of knowing if the <xref:System.ServiceModel.InstanceContext> is closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="420c6-142">Bu nedenle, bu örnek <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> metoduna istekleri seri hale getirmek için iş parçacığı kilitleme kullanır.</span><span class="sxs-lookup"><span data-stu-id="420c6-142">Therefore, this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="420c6-143">Serileştirme uygulamanızın performansını ciddi bir şekilde etkileyebileceğinden, iş parçacığı kilitleme kullanılması önerilen bir yaklaşım değildir.</span><span class="sxs-lookup"><span data-stu-id="420c6-143">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>

<span data-ttu-id="420c6-144">Bir özel üye alanı, Boşta durumunu izlemek için `CustomLifetimeLease` sınıfında kullanılır ve <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="420c6-144">A private member field is used in the `CustomLifetimeLease` class to track the idle state and is returned by the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="420c6-145"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi her çağrıldığında, `isIdle` alanı `false`olarak döndürülür ve sıfırlanır.</span><span class="sxs-lookup"><span data-stu-id="420c6-145">Each time the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is called, the `isIdle` field is returned and reset to `false`.</span></span>  <span data-ttu-id="420c6-146">Dağıtıcıda <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> yöntemini çağırdığından emin olmak için bu değerin `false` ayarlanması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="420c6-146">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>

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

<span data-ttu-id="420c6-147"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> yöntemi `false`döndürürse, dağıtıcı <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> yöntemini kullanarak bir geri çağırma işlevi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="420c6-147">If the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> method returns `false`, the Dispatcher registers a callback function by using the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span> <span data-ttu-id="420c6-148">Bu yöntem, serbest bırakılmakta olan <xref:System.ServiceModel.InstanceContext> bir başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="420c6-148">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="420c6-149">Bu nedenle, örnek kod `ICustomLease` türü uzantısını sorgulayabilir ve genişletilmiş durumdaki `ICustomLease.IsIdle` özelliğini denetleyebilir.</span><span class="sxs-lookup"><span data-stu-id="420c6-149">Therefore, the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>

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

<span data-ttu-id="420c6-150">`ICustomLease.IsIdle` özelliği denetlenmadan önce, `CustomLeaseExtension` bir süre boşta kaldığında dağıtıcıya bildirmesini sağlamak için gerekli olduğu için geri çağırma özelliğinin ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="420c6-150">Before the `ICustomLease.IsIdle` property is checked, the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="420c6-151">`ICustomLease.IsIdle` `true`döndürürse `isIdle` özel üye `CustomLifetimeLease` yalnızca `true` olarak ayarlanır ve geri çağırma yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="420c6-151">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="420c6-152">Kod bir kilit içerdiğinden, diğer iş parçacıkları bu özel üyenin değerini değiştiremezler.</span><span class="sxs-lookup"><span data-stu-id="420c6-152">Because the code holds a lock, other threads can't change the value of this private member.</span></span> <span data-ttu-id="420c6-153">Dağıtıcı <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>bir sonraki sefer çağırdığında, `true` döndürür ve dağıtıcıda örneği serbest bırakmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="420c6-153">And the next time Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, it returns `true` and lets Dispatcher release the instance.</span></span>

<span data-ttu-id="420c6-154">Artık özel uzantı için groundçalışmadığına göre, hizmet modeline bağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="420c6-154">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="420c6-155">`CustomLeaseExtension` uygulamasını <xref:System.ServiceModel.InstanceContext>bağlamak için WCF, <xref:System.ServiceModel.InstanceContext>önkurulumunu gerçekleştirmek için <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="420c6-155">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="420c6-156">Örnekte, `CustomLeaseInitializer` sınıfı bu arabirimi uygular ve tek yöntem başlatmasıyla <xref:System.ServiceModel.InstanceContext.Extensions%2A> koleksiyonuna bir `CustomLeaseExtension` örneği ekler.</span><span class="sxs-lookup"><span data-stu-id="420c6-156">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="420c6-157">Bu yöntem, <xref:System.ServiceModel.InstanceContext>başlatılırken dağıtıcı tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="420c6-157">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 <span data-ttu-id="420c6-158">Son olarak <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygulama, <xref:System.ServiceModel.Description.IServiceBehavior> uygulamasını kullanarak hizmet modeline bağlanır.</span><span class="sxs-lookup"><span data-stu-id="420c6-158">Finally the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="420c6-159">Bu uygulama `CustomLeaseTimeAttribute` sınıfına yerleştirilir ve ayrıca bu davranışı bir öznitelik olarak göstermek için <xref:System.Attribute> temel sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="420c6-159">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the <xref:System.Attribute> base class to expose this behavior as an attribute.</span></span>

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

<span data-ttu-id="420c6-160">Bu davranış örnek bir hizmet sınıfına, `CustomLeaseTime` özniteliğiyle birlikte ek olarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="420c6-160">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

<span data-ttu-id="420c6-161">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="420c6-161">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="420c6-162">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="420c6-162">Press ENTER in each console window to shut down the service and client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="420c6-163">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="420c6-163">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="420c6-164">[Windows Communication Foundation Örnekleri Için bir kerelik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="420c6-164">Ensure that you've performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="420c6-165">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="420c6-165">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="420c6-166">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="420c6-166">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="420c6-167">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="420c6-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="420c6-168">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="420c6-168">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="420c6-169">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="420c6-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="420c6-170">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="420c6-170">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
