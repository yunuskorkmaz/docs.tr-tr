---
title: 'Nasıl yapılır: Gözlemci Uygulama'
description: .NET ' te bir gözlemci uygulayın. Gözlemci tasarım deseninin bir gözlemci arasında, bildirimler için kayıt ve sağlayıcı için bir bölüm gerekir.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
ms.openlocfilehash: 43236ead15be0777f4284ba553a2f2f5e09d0a73
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769001"
---
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="84c93-104">Nasıl yapılır: Gözlemci Uygulama</span><span class="sxs-lookup"><span data-stu-id="84c93-104">How to: Implement an Observer</span></span>
<span data-ttu-id="84c93-105">Gözlemci tasarım deseninin, bildirimleri kaydeden bir gözlemci arasında bir bölme ve verileri izleyen ve bir veya daha fazla observers 'a bildirim gönderen bir sağlayıcı gerekir.</span><span class="sxs-lookup"><span data-stu-id="84c93-105">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="84c93-106">Bu konu, bir gözlemci oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="84c93-106">This topic discusses how to create an observer.</span></span> <span data-ttu-id="84c93-107">İlgili konu, [nasıl yapılır: sağlayıcı uygulama](how-to-implement-a-provider.md), bir sağlayıcının nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="84c93-107">A related topic, [How to: Implement a Provider](how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="84c93-108">Gözlemci oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="84c93-108">To create an observer</span></span>  
  
1. <span data-ttu-id="84c93-109">Arabirimini uygulayan bir tür olan gözlemciyi tanımlayın <xref:System.IObserver%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="84c93-109">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="84c93-110">Örneğin, aşağıdaki kod, `TemperatureReporter` <xref:System.IObserver%601?displayProperty=nameWithType> genel tür bağımsız değişkenine sahip oluşturulmuş bir uygulama olan adlı bir türü tanımlar `Temperature` .</span><span class="sxs-lookup"><span data-stu-id="84c93-110">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. <span data-ttu-id="84c93-111">Gözlemci, sağlayıcı uygulamasını çağırmadan önce bildirim almayı durdurabilir <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> , <xref:System.IDisposable> sağlayıcının yöntemi tarafından döndürülen uygulamayı tutacak özel bir değişken tanımlayın <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="84c93-111">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="84c93-112">Ayrıca, sağlayıcının <xref:System.IObservable%601.Subscribe%2A> yöntemini çağıran ve döndürülen nesneyi depolayan bir abonelik yöntemi tanımlamanız gerekir <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="84c93-112">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="84c93-113">Örneğin, aşağıdaki kod adlı bir özel değişkeni tanımlar `unsubscriber` ve `Subscribe` sağlayıcının yöntemini çağıran ve <xref:System.IObservable%601.Subscribe%2A> döndürülen nesneyi değişkenine atayan bir yöntemi tanımlar `unsubscriber` .</span><span class="sxs-lookup"><span data-stu-id="84c93-113">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. <span data-ttu-id="84c93-114">Bu özellik gerekliyse, gözlemciye, sağlayıcı uygulama çağrılmadan önce bildirim almayı durdurmasını sağlayan bir yöntem tanımlayın <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="84c93-114">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="84c93-115">Aşağıdaki örnek bir yöntemi tanımlar `Unsubscribe` .</span><span class="sxs-lookup"><span data-stu-id="84c93-115">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. <span data-ttu-id="84c93-116">Arabirimi tarafından tanımlanan üç yöntemin uygulamalarını sağlayın <xref:System.IObserver%601> : <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> , <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> , ve <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="84c93-116">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="84c93-117">Sağlayıcıya ve uygulamanın ihtiyaçlarına bağlı olarak, <xref:System.IObserver%601.OnError%2A> ve <xref:System.IObserver%601.OnCompleted%2A> yöntemleri saplama uygulamaları olabilir.</span><span class="sxs-lookup"><span data-stu-id="84c93-117">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="84c93-118"><xref:System.IObserver%601.OnError%2A>Yöntemin geçirilen <xref:System.Exception> nesneyi özel durum olarak işlememesi gerektiğini ve <xref:System.IObserver%601.OnCompleted%2A> yöntemin, sağlayıcının uygulamasını çağırmak için boş olduğunu unutmayın <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="84c93-118">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="84c93-119">Aşağıdaki örnek, <xref:System.IObserver%601> sınıfının uygulamasını gösterir `TemperatureReporter` .</span><span class="sxs-lookup"><span data-stu-id="84c93-119">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="84c93-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="84c93-120">Example</span></span>  
 <span data-ttu-id="84c93-121">Aşağıdaki örnek `TemperatureReporter` , <xref:System.IObserver%601> bir sıcaklık izleme uygulaması için uygulama sağlayan, sınıfının tüm kaynak kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="84c93-121">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="84c93-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84c93-122">See also</span></span>

- <xref:System.IObserver%601>
- [<span data-ttu-id="84c93-123">Gözlemci tasarım kalıbı</span><span class="sxs-lookup"><span data-stu-id="84c93-123">Observer Design Pattern</span></span>](observer-design-pattern.md)
- [<span data-ttu-id="84c93-124">Nasıl yapılır: sağlayıcı uygulama</span><span class="sxs-lookup"><span data-stu-id="84c93-124">How to: Implement a Provider</span></span>](how-to-implement-a-provider.md)
- [<span data-ttu-id="84c93-125">Gözlemci Tasarım Deseni En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="84c93-125">Observer Design Pattern Best Practices</span></span>](observer-design-pattern-best-practices.md)
