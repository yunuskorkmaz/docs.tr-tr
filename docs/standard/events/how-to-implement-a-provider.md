---
title: "Nasıl yapılır: Sağlayıcıyı Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observer design pattern [.NET Framework], implementing providers
- providers [.NET Framework], in observer design pattern
- observables [.NET Framework], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0f99a611de4bc344a0fd35130a59d496126e3af5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-implement-a-provider"></a><span data-ttu-id="1c2b4-102">Nasıl yapılır: Sağlayıcıyı Uygulama</span><span class="sxs-lookup"><span data-stu-id="1c2b4-102">How to: Implement a Provider</span></span>
<span data-ttu-id="1c2b4-103">Gözlemci tasarım deseni, verileri izler ve bildirimleri gönderen bir sağlayıcısı ve bildirimleri (geri aramalar) sağlayıcıdan almak, bir veya daha fazla gözlemcilerin arasında bölme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-103">The observer design pattern requires a division between a provider, which monitors data and sends notifications, and one or more observers, which receive notifications (callbacks) from the provider.</span></span> <span data-ttu-id="1c2b4-104">Bu konuda bir sağlayıcı oluşturma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-104">This topic discusses how to create a provider.</span></span> <span data-ttu-id="1c2b4-105">İlgili konu [nasıl yapılır: gözlemci uygulama](../../../docs/standard/events/how-to-implement-an-observer.md), bir gözlemci oluşturulacağını anlatır.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-105">A related topic, [How to: Implement an Observer](../../../docs/standard/events/how-to-implement-an-observer.md), discusses how to create an observer.</span></span>  
  
### <a name="to-create-a-provider"></a><span data-ttu-id="1c2b4-106">Sağlayıcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1c2b4-106">To create a provider</span></span>  
  
1.  <span data-ttu-id="1c2b4-107">Sağlayıcı için gözlemcilerin göndermekten sorumludur verileri tanımlamak.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-107">Define the data that the provider is responsible for sending to observers.</span></span> <span data-ttu-id="1c2b4-108">Sağlayıcı ve gözlemcilerin için gönderdiği verileri tek bir türü olsa da, bunlar genellikle farklı türleri tarafından gösterilir.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-108">Although the provider and the data that it sends to observers can be a single type, they are generally represented by different types.</span></span> <span data-ttu-id="1c2b4-109">Örneğin, bir uygulama, izleme sıcaklık içinde `Temperature` yapısı verileri tanımlar, sağlayıcı (tarafından temsil `TemperatureMonitor` sonraki adımda tanımlanan sınıfı) izler ve hangi gözlemcilerin abone olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-109">For example, in a temperature monitoring application, the `Temperature` structure defines the data that the provider (which is represented by the `TemperatureMonitor` class defined in the next step) monitors and to which observers subscribe.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2.  <span data-ttu-id="1c2b4-110">Arabirimini uygulayan bir tür veri sağlayıcısı tanımlamak <xref:System.IObservable%601?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-110">Define the data provider, which is a type that implements the <xref:System.IObservable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="1c2b4-111">Sağlayıcının genel tür bağımsız değişkeni için gözlemcilerin sağlayıcı gönderdiği türüdür.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-111">The provider's generic type argument is the type that the provider sends to observers.</span></span> <span data-ttu-id="1c2b4-112">Aşağıdaki örnek tanımlayan bir `TemperatureMonitor` bir oluşturulmuş olan sınıf <xref:System.IObservable%601?displayProperty=nameWithType> bir uygulama bir genel tür bağımsız değişkeni ile `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-112">The following example defines a `TemperatureMonitor` class, which is a constructed <xref:System.IObservable%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3.  <span data-ttu-id="1c2b4-113">Böylece her gözlemci uygun olduğunda bildirim sağlayıcı gözlemcilerin başvurular nasıl depolayacak belirler.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-113">Determine how the provider will store references to observers so that each observer can be notified when appropriate.</span></span> <span data-ttu-id="1c2b4-114">En yaygın olarak, bir koleksiyon nesnesi genel gibi <xref:System.Collections.Generic.List%601> nesnesi, bu amaç için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-114">Most commonly, a collection object such as a generic <xref:System.Collections.Generic.List%601> object is used for this purpose.</span></span> <span data-ttu-id="1c2b4-115">Aşağıdaki örnek, bir özel tanımlar <xref:System.Collections.Generic.List%601> içinde örneği nesneyi `TemperatureMonitor` sınıfı oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-115">The following example defines a private <xref:System.Collections.Generic.List%601> object that is instantiated in the `TemperatureMonitor` class constructor.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4.  <span data-ttu-id="1c2b4-116">Tanımlayan bir <xref:System.IDisposable> sağlayıcı abonelere döndürebilir ve böylece herhangi bir zamanda bildirimleri alma durdurabilirsiniz uygulama.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-116">Define an <xref:System.IDisposable> implementation that the provider can return to subscribers so that they can stop receiving notifications at any time.</span></span> <span data-ttu-id="1c2b4-117">Aşağıdaki örnek, bir iç içe tanımlar `Unsubscriber` sınıfının örneği oluşturulduğunda bir başvuru aboneleri koleksiyonu ve abone geçirilen sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-117">The following example defines a nested `Unsubscriber` class that is passed a reference to the subscribers collection and to the subscriber when the class is instantiated.</span></span> <span data-ttu-id="1c2b4-118">Bu kod nesnenin çağırmak abone etkinleştirir <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulama kendisini aboneleri Koleksiyondan kaldırılacak.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-118">This code enables the subscriber to call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation to remove itself from the subscribers collection.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5.  <span data-ttu-id="1c2b4-119">Uygulama <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-119">Implement the <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="1c2b4-120">Yöntem başvuru geçirilen <xref:System.IObserver%601?displayProperty=nameWithType> arabirim ve adım 3'te bu amaç için tasarlanmış nesnesindeki depolanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-120">The method is passed a reference to the <xref:System.IObserver%601?displayProperty=nameWithType> interface and should be stored in the object designed for that purpose in step 3.</span></span> <span data-ttu-id="1c2b4-121">Yöntem sonra döndürmelidir <xref:System.IDisposable> uygulama geliştirilen adım 4 '.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-121">The method should then return the <xref:System.IDisposable> implementation developed in step 4.</span></span> <span data-ttu-id="1c2b4-122">Aşağıdaki örnek uygulamasını gösterir <xref:System.IObservable%601.Subscribe%2A> yönteminde `TemperatureMonitor` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-122">The following example shows the implementation of the <xref:System.IObservable%601.Subscribe%2A> method in the `TemperatureMonitor` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6.  <span data-ttu-id="1c2b4-123">Çağırarak uygun şekilde gözlemcilerin bildir kendi <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, ve <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-123">Notify observers as appropriate by calling their <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementations.</span></span> <span data-ttu-id="1c2b4-124">Bazı durumlarda, bir sağlayıcı değil çağırabilir <xref:System.IObserver%601.OnError%2A> bir hata oluştuğunda yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-124">In some cases, a provider may not call the <xref:System.IObserver%601.OnError%2A> method when an error occurs.</span></span> <span data-ttu-id="1c2b4-125">Örneğin, aşağıdaki `GetTemperature` yöntemi beş saniyede sıcaklık veri okuyan ve sıcaklık önceki okuma bu yana en az olur.1 derece tarafından değiştiyse gözlemcilerin bildiren bir izleyici benzetimini yapar.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-125">For example, the following `GetTemperature` method simulates a monitor that reads temperature data every five seconds and notifies observers if the temperature has changed by at least .1 degree since the previous reading.</span></span> <span data-ttu-id="1c2b4-126">Varsa (diğer bir deyişle, kendi değer null ise) aygıtı bir sıcaklık bildirmez, sağlayıcı gözlemcilerin iletim tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-126">If the device does not report a temperature (that is, if its value is null), the provider notifies observers that the transmission is complete.</span></span> <span data-ttu-id="1c2b4-127">Her gözlemci 's çağırma yanı sıra unutmayın <xref:System.IObserver%601.OnCompleted%2A> yöntemi, `GetTemperature` yöntemini temizler <xref:System.Collections.Generic.List%601> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-127">Note that, in addition to calling each observer's <xref:System.IObserver%601.OnCompleted%2A> method, the `GetTemperature` method clears the <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="1c2b4-128">Bu durumda, sağlayıcı hiçbir çağrılar <xref:System.IObserver%601.OnError%2A> kendi gözlemcilerin yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-128">In this case, the provider makes no calls to the <xref:System.IObserver%601.OnError%2A> method of its observers.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="1c2b4-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c2b4-129">Example</span></span>  
 <span data-ttu-id="1c2b4-130">Aşağıdaki örnek tanımlamak için tam kaynak kodunu içeren bir <xref:System.IObservable%601> uygulaması için uygulama izleme sıcaklık.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-130">The following example contains the complete source code for defining an <xref:System.IObservable%601> implementation for a temperature monitoring application.</span></span> <span data-ttu-id="1c2b4-131">İçerdiği `Temperature` gözlemcilerin için gönderilen veri olan yapısı ve `TemperatureMonitor` olan sınıf <xref:System.IObservable%601> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-131">It includes the `Temperature` structure, which is the data sent to observers, and the `TemperatureMonitor` class, which is the <xref:System.IObservable%601> implementation.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="1c2b4-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c2b4-132">See Also</span></span>  
 <xref:System.IObservable%601>  
 [<span data-ttu-id="1c2b4-133">Gözlemci Tasarım Deseni</span><span class="sxs-lookup"><span data-stu-id="1c2b4-133">Observer Design Pattern</span></span>](../../../docs/standard/events/observer-design-pattern.md)  
 [<span data-ttu-id="1c2b4-134">Nasıl yapılır: Gözlemci Uygulama</span><span class="sxs-lookup"><span data-stu-id="1c2b4-134">How to: Implement an Observer</span></span>](../../../docs/standard/events/how-to-implement-an-observer.md)  
 [<span data-ttu-id="1c2b4-135">Gözlemci Tasarım Deseni En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="1c2b4-135">Observer Design Pattern Best Practices</span></span>](../../../docs/standard/events/observer-design-pattern-best-practices.md)
