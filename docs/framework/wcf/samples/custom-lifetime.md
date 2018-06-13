---
title: Özel Yaşam Süresi
ms.date: 03/30/2017
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: e41c970739b8036730fa601433ce7157e01d7e19
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809309"
---
# <a name="custom-lifetime"></a><span data-ttu-id="2094d-102">Özel Yaşam Süresi</span><span class="sxs-lookup"><span data-stu-id="2094d-102">Custom Lifetime</span></span>
<span data-ttu-id="2094d-103">Bu örnek nasıl paylaşılan WCF hizmet örneği için özel yaşam süresi hizmetleri sağlamak için bir Windows Communication Foundation (WCF) uzantısı yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2094d-103">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2094d-104">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="2094d-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="shared-instancing"></a><span data-ttu-id="2094d-105">Paylaşılan örnek oluşturma</span><span class="sxs-lookup"><span data-stu-id="2094d-105">Shared Instancing</span></span>  
 <span data-ttu-id="2094d-106">WCF hizmet örnekleri için birkaç örneklemesini modu sunar.</span><span class="sxs-lookup"><span data-stu-id="2094d-106">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="2094d-107">Bu konuda ele paylaşılan örnek oluşturma modu, bir hizmet örneği birden çok kanaldan arasında paylaşmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="2094d-107">The Shared Instancing mode covered in this topic provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="2094d-108">İstemcileri örneğinin uç noktası adresi yerel olarak gidermek veya hizmet uç noktası adresini çalışan bir örneği elde etmek için Üreteç yöntemi başvurun.</span><span class="sxs-lookup"><span data-stu-id="2094d-108">Clients can either resolve the instance’s endpoint address locally or contact a factory method in the service to obtain the endpoint address of a running instance.</span></span> <span data-ttu-id="2094d-109">Uç nokta adresi olduğunda, bunu yeni bir kanal oluşturmak ve iletişim başlatın.</span><span class="sxs-lookup"><span data-stu-id="2094d-109">Once it has the endpoint address, it can create a new channel and start communication.</span></span> <span data-ttu-id="2094d-110">Aşağıdaki kod parçacığını bir istemci uygulaması var olan bir hizmet örneği için yeni bir kanal nasıl oluşturduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2094d-110">The following code snippet shows how a client application creates a new channel to an existing service instance.</span></span>  
  
```  
// Create the first channel.  
IEchoService proxy = channelFactory.CreateChannel();  
  
// Resolve the instance.  
EndpointAddress epa = ((IClientChannel)proxy).ResolveInstance();  
  
// Create new channel factory with the endpoint address resolved by   
// previous statement.  
ChannelFactory<IEchoService> channelFactory2 =  
                new ChannelFactory<IEchoService>("echoservice",  
                epa);  
  
// Create the second channel to the same instance.  
IEchoService proxy2 = channelFactory2.CreateChannel();  
```  
  
 <span data-ttu-id="2094d-111">Diğer örneklemesini modları, paylaşılan örnekleme modunu hizmet örnekleri yayınlama benzersiz bir şekilde sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2094d-111">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="2094d-112">Tüm kanallar için bir örneği kapatıldığında service WCF çalışma zamanı bir süreölçer başlatır.</span><span class="sxs-lookup"><span data-stu-id="2094d-112">When all the channels are closed for an instance, the service WCF runtime starts a timer.</span></span> <span data-ttu-id="2094d-113">Zaman aşımı süresi dolmadan önce hiç kimsenin bağlantı kurar, WCF örneği serbest bırakır ve kaynak talepleri.</span><span class="sxs-lookup"><span data-stu-id="2094d-113">If nobody makes a connection before the timeout expires, WCF releases the instance and claims the resources.</span></span> <span data-ttu-id="2094d-114">WCF erdirme yordamının parçası olarak çağırır <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi tüm <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> örneği serbest önce uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="2094d-114">As a part of the teardown procedure WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of all <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementations before releasing the instance.</span></span> <span data-ttu-id="2094d-115">Bunların tümünün dönerseniz `true` örneği yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="2094d-115">If all of them return `true` the instance is released.</span></span> <span data-ttu-id="2094d-116">Aksi takdirde <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> uygulamasıdır bilgilendirmek için sorumlu `Dispatcher` bir geri çağırma yöntemi kullanarak boşta durumu.</span><span class="sxs-lookup"><span data-stu-id="2094d-116">Otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span>  
  
 <span data-ttu-id="2094d-117">Varsayılan olarak, boşta kalma zaman aşımı değeri <xref:System.ServiceModel.InstanceContext> bir dakikadır.</span><span class="sxs-lookup"><span data-stu-id="2094d-117">By default, the idle timeout value of <xref:System.ServiceModel.InstanceContext> is one minute.</span></span> <span data-ttu-id="2094d-118">Ancak bu örnek, bu özel bir uzantısı kullanılarak nasıl genişletebilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="2094d-118">However this sample demonstrates how you can extend this using a custom extension.</span></span>  
  
## <a name="extending-the-instancecontext"></a><span data-ttu-id="2094d-119">InstanceContext genişletme</span><span class="sxs-lookup"><span data-stu-id="2094d-119">Extending the InstanceContext</span></span>  
 <span data-ttu-id="2094d-120">Wcf'de, <xref:System.ServiceModel.InstanceContext> hizmet örneği arasında bağlantı ve `Dispatcher`.</span><span class="sxs-lookup"><span data-stu-id="2094d-120">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="2094d-121">WCF yeni durumu veya davranışı, Genişletilebilir nesne desenine kullanarak ekleyerek bu çalışma zamanı bileşeni genişletmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2094d-121">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="2094d-122">Genişletilebilir object deseni WCF'de ya da mevcut çalışma zamanı sınıflarını yeni işlevselliği ile genişletmek veya yeni durumu özellik için bir nesne eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2094d-122">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="2094d-123">Genişletilebilir nesne modelinde üç arabirimi vardır: `IExtensibleObject<T>`, `IExtension<T>`, ve `IExtensionCollection<T>`.</span><span class="sxs-lookup"><span data-stu-id="2094d-123">There are three interfaces in the extensible object pattern: `IExtensibleObject<T>`, `IExtension<T>`, and `IExtensionCollection<T>`.</span></span>  
  
 <span data-ttu-id="2094d-124">`IExtensibleObject<T>` Arabirimi işlevleriyle özelleştirme uzantılarına izin vermek için nesneler tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2094d-124">The `IExtensibleObject<T>` interface is implemented by objects to allow extensions which customize their functionality.</span></span>  
  
 <span data-ttu-id="2094d-125">`IExtension<T>` Arabirimi türü sınıfların uzantıları olabilir nesneleri tarafından uygulanan `T`.</span><span class="sxs-lookup"><span data-stu-id="2094d-125">The `IExtension<T>` interface is implemented by objects that can be extensions of classes of type `T`.</span></span>  
  
 <span data-ttu-id="2094d-126">Ve son olarak, `IExtensionCollection<T>` arabirimidir koleksiyonu `IExtensions` izin veren almak için `IExtensions` türlerine göre.</span><span class="sxs-lookup"><span data-stu-id="2094d-126">And finally, the `IExtensionCollection<T>` interface is a collection of `IExtensions` that allows for retrieving `IExtensions` by their type.</span></span>  
  
 <span data-ttu-id="2094d-127">Bu nedenle genişletmek için <xref:System.ServiceModel.InstanceContext> uygulamanız gereken `IExtension` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="2094d-127">Therefore in order to extend the <xref:System.ServiceModel.InstanceContext> you must implement the `IExtension` interface.</span></span> <span data-ttu-id="2094d-128">Bu örnek projesinde `CustomLeaseExtension` sınıfı, bu uygulama içerir.</span><span class="sxs-lookup"><span data-stu-id="2094d-128">In this sample project the `CustomLeaseExtension` class contains this implementation.</span></span>  
  
```  
class CustomLeaseExtension : IExtension<InstanceContext>  
{  
}  
```  
  
 <span data-ttu-id="2094d-129">`IExtension` Arabirimi sahip iki yöntem `Attach` ve `Detach`.</span><span class="sxs-lookup"><span data-stu-id="2094d-129">The `IExtension` interface has two methods `Attach` and `Detach`.</span></span> <span data-ttu-id="2094d-130">Çalışma zamanı ekler ve uzantı örneği ayırır adlarını kapsıyor gibi bu iki yöntem denir <xref:System.ServiceModel.InstanceContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2094d-130">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="2094d-131">Bu örnekte `Attach` yöntemi izlemek için kullanılan <xref:System.ServiceModel.InstanceContext> geçerli uzantısı örneğine ait olduğu nesne.</span><span class="sxs-lookup"><span data-stu-id="2094d-131">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>  
  
```  
InstanceContext owner;  
  
public void Attach(InstanceContext owner)  
{  
  this.owner = owner;   
}  
```  
  
 <span data-ttu-id="2094d-132">Ayrıca, gerekli uygulama genişletilmiş ömrü desteği sağlamak için uzantı eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2094d-132">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="2094d-133">Bu nedenle `ICustomLease` arabirimi istenen yöntemleriyle bildirilir ve uygulanan `CustomLeaseExtension` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2094d-133">Therefore the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>  
  
```  
interface ICustomLease  
{  
    bool IsIdle { get; }          
    InstanceContextIdleCallback Callback { get; set; }  
}  
  
class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease  
{  
}  
```  
  
 <span data-ttu-id="2094d-134">WCF zaman çağırır <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yönteminde <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> bu çağrı için yönlendirilir uygulama <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="2094d-134">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="2094d-135">Ardından `CustomLeaseExtension` özel durumu görmek için denetler olup olmadığını <xref:System.ServiceModel.InstanceContext> boştadır.</span><span class="sxs-lookup"><span data-stu-id="2094d-135">Then the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="2094d-136">Döndürür boşta ise `true`.</span><span class="sxs-lookup"><span data-stu-id="2094d-136">If it is idle it returns `true`.</span></span> <span data-ttu-id="2094d-137">Aksi halde, belirtilen bir genişletilmiş ömrü miktarı için bir süreölçer başlatır.</span><span class="sxs-lookup"><span data-stu-id="2094d-137">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>  
  
```  
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
  
 <span data-ttu-id="2094d-138">Zamanlayıcı'nın içinde `Elapsed` olay dağıtıcı geri çağırma işlevi başka temizleme döngüsü başlatmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2094d-138">In the timer’s `Elapsed` event the callback function in the Dispatcher is called in order to start another clean up cycle.</span></span>  
  
```  
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)  
{  
    idleTimer.Stop();  
    isIdle = true;    
    callback(owner);  
}  
```  
  
 <span data-ttu-id="2094d-139">Çalışan Zamanlayıcı boşta durumuna taşınan örneği için yeni bir ileti geldiğinde yenilemeye yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="2094d-139">There is no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>  
  
 <span data-ttu-id="2094d-140">Örnek uygulayan <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> çağrıları kesmeye <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi ve rota onları `CustomLeaseExtension`.</span><span class="sxs-lookup"><span data-stu-id="2094d-140">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="2094d-141"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> Uygulama bulunduğu `CustomLifetimeLease` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2094d-141">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="2094d-142"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> Yöntemi WCF hizmet örneği hakkında yayımlamayı olduğunda çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2094d-142">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="2094d-143">Ancak, belirli bir yalnızca bir örneği var. `ISharedSessionInstance` ServiceBehavior'ın uygulamasında <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2094d-143">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="2094d-144">Bu bilmesinin yolu yoktur anlamına gelir <xref:System.ServiceModel.InstanceContext> WCF denetler aynı anda kapatılan <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2094d-144">This means there is no way of knowing the <xref:System.ServiceModel.InstanceContext> being closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="2094d-145">Bu nedenle bu örnek isteklerine serileştirmek için kilitleme iş parçacığı kullanan <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2094d-145">Therefore this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2094d-146">Seri hale getirme, uygulamanızın performansını önemli ölçüde etkileyebileceğinden iş parçacığı kilitleme kullanılarak önerilen yaklaşım değildir.</span><span class="sxs-lookup"><span data-stu-id="2094d-146">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>  
  
 <span data-ttu-id="2094d-147">Özel üye değişkeni kullanılır `CustomLeaseExtension` izlemek için sınıf `IsIdle` değeri.</span><span class="sxs-lookup"><span data-stu-id="2094d-147">A private member variable is used in the `CustomLeaseExtension` class to track the `IsIdle` value.</span></span> <span data-ttu-id="2094d-148">Her zaman değerini <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> alınır `IsIdle` özel üye döndürülen ve Sıfırla `false`.</span><span class="sxs-lookup"><span data-stu-id="2094d-148">Each time the value of <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is retrieved the `IsIdle` private member is returned and reset to `false`.</span></span> <span data-ttu-id="2094d-149">Bu değer ayarlamak için gerekli olan `false` dağıtıcısı çağrıları emin olmak için <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2094d-149">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>  
  
```  
public bool IsIdle  
{  
    get   
    {  
       lock (thisLock)  
       {  
           bool idleCopy = isIdle;  
           isIdle = false;  
           return idleCopy;  
       }  
    }  
}  
```  
  
 <span data-ttu-id="2094d-150">Varsa `ISharedSessionLifetime.IsIdle` özelliği döndürür `false` dağıtıcı kullanarak bir geri çağırma işlevini kaydeder `NotifyIdle` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2094d-150">If the `ISharedSessionLifetime.IsIdle` property returns `false` the Dispatcher registers a callback function by using the `NotifyIdle` method.</span></span> <span data-ttu-id="2094d-151">Bu yöntem bir başvuru alır <xref:System.ServiceModel.InstanceContext> yayımlanan.</span><span class="sxs-lookup"><span data-stu-id="2094d-151">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="2094d-152">Bu nedenle örnek kod sorgulayabilirsiniz `ICustomLease` uzantısı yazın ve denetleme `ICustomLease.IsIdle` Genişletilmiş durum özelliğini.</span><span class="sxs-lookup"><span data-stu-id="2094d-152">Therefore the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>  
  
```  
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
  
 <span data-ttu-id="2094d-153">Önce `ICustomLease.IsIdle` özellik geri çağırma özelliği bu için temel olarak ayarlanması gerekiyor işaretli `CustomLeaseExtension` boşta olduğunda göndereni bilgilendirmek için.</span><span class="sxs-lookup"><span data-stu-id="2094d-153">Before the `ICustomLease.IsIdle` property is checked the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="2094d-154">Varsa `ICustomLease.IsIdle` döndürür `true`, `isIdle` özel üye kümesi yalnızca `CustomLifetimeLease` için `true` ve geri çağırma yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="2094d-154">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="2094d-155">Kod bir kilidi tutan olduğundan başka bir iş parçacığı bu özel üyesinin değerini değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2094d-155">Because the code holds a lock, other threads cannot change the value of this private member.</span></span> <span data-ttu-id="2094d-156">Ve dağıtıcı denetlediğinde `ISharedSessionLifetime.IsIdle`, döndürdüğü `true` ve dağıtıcı örneği yayın olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="2094d-156">And the next time Dispatcher checks the `ISharedSessionLifetime.IsIdle`, it returns `true` and lets Dispatcher release the instance.</span></span>  
  
 <span data-ttu-id="2094d-157">Özel uzantı geçişteki tamamladığınıza göre hizmet modeli sayfaya içeriyor.</span><span class="sxs-lookup"><span data-stu-id="2094d-157">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="2094d-158">Takma için `CustomLeaseExtension` uygulamasına <xref:System.ServiceModel.InstanceContext>, WCF sağlar <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> , önyükleme gerçekleştirmek için arabirim <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="2094d-158">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="2094d-159">Örnekte, `CustomLeaseInitializer` sınıfı bu arabirimi uygular ve bir örneğini ekler `CustomLeaseExtension` için <xref:System.ServiceModel.InstanceContext.Extensions%2A> tek yöntem başlatma koleksiyonundan.</span><span class="sxs-lookup"><span data-stu-id="2094d-159">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="2094d-160">Bu yöntem tarafından dağıtıcısı başlatılırken çağrılır <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="2094d-160">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
  IExtension<InstanceContext> customLeaseExtension =  
    new CustomLeaseExtension(timeout);  
  instanceContext.Extensions.Add(customLeaseExtension);  
}  
```  
  
 <span data-ttu-id="2094d-161">Son olarak `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` ve <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> uygulamalarıdır olduğu sayfaya kullanarak hizmet modeli kadar <xref:System.ServiceModel.Description.IServiceBehavior> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="2094d-161">Finally the `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` and <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> implementations are is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="2094d-162">Bu uygulama yerleştirilir `CustomLeaseTimeAttribute` sınıfı ve ayrıca türetilen `Attribute` temel sınıfı bu davranış bir öznitelik olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="2094d-162">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the `Attribute` base class to expose this behavior as an attribute.</span></span> <span data-ttu-id="2094d-163">İçinde `IServiceBehavior.ApplyBehavior` yöntemi, örneklerini <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> ve `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` uygulamaları eklenir `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` ve <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> koleksiyonları <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="2094d-163">In the `IServiceBehavior.ApplyBehavior` method, instances of <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> and `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` implementations are added to the `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` and <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> collections of the <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> respectively.</span></span>  
  
```  
public void ApplyBehavior(ServiceDescription description,   
           ServiceHostBase serviceHostBase,   
           Collection<DispatchBehavior> behaviors,  
           Collection<BindingParameterCollection> parameters)  
{  
    CustomLifetimeLease customLease = new CustomLifetimeLease();  
    CustomLeaseInitializer initializer =   
                new CustomLeaseInitializer(timeout);  
  
    foreach (DispatchBehavior dispatchBehavior in behaviors)  
    {  
        dispatchBehavior.InstanceContextLifetimes.Add(customLease);  
        dispatchBehavior.InstanceContextInitializers.Add(initializer);  
    }  
}  
```  
  
 <span data-ttu-id="2094d-164">Bu davranış ile açıklama ekleyerek bir örnek hizmet sınıfına eklenebilir `CustomLeaseTime` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2094d-164">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Shareable)]  
[CustomLeaseTime(Timeout = 20000)]  
public class EchoService : IEchoService  
{  
  //…  
}  
```  
  
 <span data-ttu-id="2094d-165">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2094d-165">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="2094d-166">Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2094d-166">Press ENTER in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2094d-167">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="2094d-167">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2094d-168">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2094d-168">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="2094d-169">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2094d-169">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="2094d-170">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2094d-170">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2094d-171">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="2094d-171">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2094d-172">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2094d-172">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2094d-173">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="2094d-173">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2094d-174">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2094d-174">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`  
  
## <a name="see-also"></a><span data-ttu-id="2094d-175">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2094d-175">See Also</span></span>
