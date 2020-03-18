---
title: 'Nasıl yapılır: Gözlemci Uygulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
ms.openlocfilehash: e6aba4d85e502563291478640927bd0f234736a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139304"
---
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="97f87-102">Nasıl yapılır: Gözlemci Uygulama</span><span class="sxs-lookup"><span data-stu-id="97f87-102">How to: Implement an Observer</span></span>
<span data-ttu-id="97f87-103">Gözlemci tasarım deseni, bildirimler için kayıt yaptıran bir gözlemci ile verileri izleyen ve bir veya daha fazla gözlemciye bildirim gönderen bir sağlayıcı arasında bir bölünme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="97f87-103">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="97f87-104">Bu konu nasıl bir gözlemci oluşturmak için tartışır.</span><span class="sxs-lookup"><span data-stu-id="97f87-104">This topic discusses how to create an observer.</span></span> <span data-ttu-id="97f87-105">İlgili bir konu, [Nasıl: Sağlayıcı uygulama,](../../../docs/standard/events/how-to-implement-a-provider.md)nasıl bir sağlayıcı oluşturmak için tartışır.</span><span class="sxs-lookup"><span data-stu-id="97f87-105">A related topic, [How to: Implement a Provider](../../../docs/standard/events/how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="97f87-106">Gözlemci oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="97f87-106">To create an observer</span></span>  
  
1. <span data-ttu-id="97f87-107">Arabirimi uygulayan bir tür olan gözlemciyi tanımlayın. <xref:System.IObserver%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="97f87-107">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="97f87-108">Örneğin, aşağıdaki kod, genel bir `TemperatureReporter` tür bağımsız <xref:System.IObserver%601?displayProperty=nameWithType> değişkeni `Temperature`olan yapılı bir uygulama olan adlı bir türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97f87-108">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. <span data-ttu-id="97f87-109">Gözlemci, sağlayıcı nın uygulanmasını aramadan <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> önce bildirim almayı durdurabiliyorsa, <xref:System.IDisposable> sağlayıcının <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> yöntemi yle döndürülen uygulamayı tutacak özel bir değişken tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="97f87-109">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="97f87-110">Ayrıca, sağlayıcının <xref:System.IObservable%601.Subscribe%2A> yöntemini çağıran ve döndürülen <xref:System.IDisposable> nesneyi depolayan bir abonelik yöntemi de tanımlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="97f87-110">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="97f87-111">Örneğin, aşağıdaki kod `unsubscriber` adlı özel bir değişkeni `Subscribe` tanımlar ve sağlayıcının <xref:System.IObservable%601.Subscribe%2A> yöntemini çağıran ve döndürülen `unsubscriber` nesneyi değişkene atayan bir yöntem tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97f87-111">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. <span data-ttu-id="97f87-112">Bu özellik gerekiyorsa, sağlayıcı uygulamadan önce gözlemcinin bildirim <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> almayı durdurmasını sağlayan bir yöntem tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="97f87-112">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="97f87-113">Aşağıdaki örnekte bir `Unsubscribe` yöntem tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="97f87-113">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. <span data-ttu-id="97f87-114">Arabirim <xref:System.IObserver%601> tarafından tanımlanan üç yöntemin <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>uygulamalarını <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>sağlayın: , , ve <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="97f87-114">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="97f87-115">Sağlayıcıya ve uygulamanın ihtiyaçlarına bağlı olarak, ve <xref:System.IObserver%601.OnError%2A> <xref:System.IObserver%601.OnCompleted%2A> yöntemler saplama uygulamaları olabilir.</span><span class="sxs-lookup"><span data-stu-id="97f87-115">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="97f87-116">Yöntemin <xref:System.IObserver%601.OnError%2A> geçirilen <xref:System.Exception> nesneyi bir özel durum olarak <xref:System.IObserver%601.OnCompleted%2A> işlememesi gerektiğini ve yöntemin <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> sağlayıcının uygulamasını çağırmakta özgür olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="97f87-116">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="97f87-117">Aşağıdaki örnek, <xref:System.IObserver%601> `TemperatureReporter` sınıfın uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="97f87-117">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="97f87-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="97f87-118">Example</span></span>  
 <span data-ttu-id="97f87-119">Aşağıdaki örnek, bir sıcaklık izleme `TemperatureReporter` uygulaması için <xref:System.IObserver%601> uygulama sağlayan sınıf için tam kaynak kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="97f87-119">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="97f87-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97f87-120">See also</span></span>

- <xref:System.IObserver%601>
- [<span data-ttu-id="97f87-121">Gözlemci Tasarım Deseni</span><span class="sxs-lookup"><span data-stu-id="97f87-121">Observer Design Pattern</span></span>](../../../docs/standard/events/observer-design-pattern.md)
- [<span data-ttu-id="97f87-122">Nasıl yapılır: Sağlayıcıyı Uygulama</span><span class="sxs-lookup"><span data-stu-id="97f87-122">How to: Implement a Provider</span></span>](../../../docs/standard/events/how-to-implement-a-provider.md)
- [<span data-ttu-id="97f87-123">Gözlemci Tasarım Deseni En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="97f87-123">Observer Design Pattern Best Practices</span></span>](../../../docs/standard/events/observer-design-pattern-best-practices.md)
