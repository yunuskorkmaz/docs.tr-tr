---
title: "Nasıl yapılır: Gözlemci Uygulama"
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
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a964bd031f6f8a7fc029b2b209b9693b72e688af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="d1655-102">Nasıl yapılır: Gözlemci Uygulama</span><span class="sxs-lookup"><span data-stu-id="d1655-102">How to: Implement an Observer</span></span>
<span data-ttu-id="d1655-103">Gözlemci tasarım deseni bildirimleri için kaydeder, bir gözlemci, verileri izler ve bir veya daha fazla gözlemcilerin bildirimleri gönderen bir sağlayıcısı arasındaki bölme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d1655-103">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="d1655-104">Bu konu bir gözlemci oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d1655-104">This topic discusses how to create an observer.</span></span> <span data-ttu-id="d1655-105">İlgili konu [nasıl yapılır: sağlayıcıyı uygulama](../../../docs/standard/events/how-to-implement-a-provider.md), bir sağlayıcı oluşturulacağını anlatır.</span><span class="sxs-lookup"><span data-stu-id="d1655-105">A related topic, [How to: Implement a Provider](../../../docs/standard/events/how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="d1655-106">Bir gözlemci oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d1655-106">To create an observer</span></span>  
  
1.  <span data-ttu-id="d1655-107">Arabirimini uygulayan bir tür gözlemci tanımlamak <xref:System.IObserver%601?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d1655-107">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="d1655-108">Örneğin, aşağıdaki kod adlı tür tanımlar `TemperatureReporter` diğer bir deyişle oluşturulan <xref:System.IObserver%601?displayProperty=nameWithType> bir uygulama bir genel tür bağımsız değişkeni ile `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="d1655-108">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  <span data-ttu-id="d1655-109">Gözlemci bildirimleri sağlayıcısı çağrıları önce alma durdurursanız, kendi <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> uygulaması, tutacak özel bir değişkeni tanımlamak <xref:System.IDisposable> sağlayıcının tarafından döndürülen uygulama <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d1655-109">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d1655-110">Sağlayıcının çağıran bir abonelik yöntemi tanımlamanız gerekir <xref:System.IObservable%601.Subscribe%2A> yöntemi ve depoları döndürülen <xref:System.IDisposable> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d1655-110">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="d1655-111">Örneğin, aşağıdaki kod adlı özel bir değişken tanımlar `unsubscriber` ve tanımlayan bir `Subscribe` sağlayıcının çağıran yöntemi <xref:System.IObservable%601.Subscribe%2A> yöntemi ve döndürülen nesneyi atar `unsubscriber` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="d1655-111">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  <span data-ttu-id="d1655-112">Gözlemci bildirimleri sağlayıcısı çağrıları önce almayı durdurmasını sağlayan bir yöntemi tanımlamak, <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> bu özelliği gerekliyse, uygulama.</span><span class="sxs-lookup"><span data-stu-id="d1655-112">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="d1655-113">Aşağıdaki örnek tanımlayan bir `Unsubscribe` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d1655-113">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  <span data-ttu-id="d1655-114">Tarafından tanımlanan üç yöntem uygulamalarını <xref:System.IObserver%601> arabirimi: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, ve <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d1655-114">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d1655-115">Sağlayıcı ve uygulamanızın gereksinimlerine bağlı olarak <xref:System.IObserver%601.OnError%2A> ve <xref:System.IObserver%601.OnCompleted%2A> yöntemleri, saplama uygulamaları olabilir.</span><span class="sxs-lookup"><span data-stu-id="d1655-115">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="d1655-116">Unutmayın <xref:System.IObserver%601.OnError%2A> yöntemi değil ele geçirilen <xref:System.Exception> nesnesi bir özel durum olarak ve <xref:System.IObserver%601.OnCompleted%2A> yöntemdir sağlayıcının çağırmak ücretsiz <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="d1655-116">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="d1655-117">Aşağıdaki örnekte gösterildiği <xref:System.IObserver%601> uyarlamasını `TemperatureReporter` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d1655-117">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="d1655-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1655-118">Example</span></span>  
 <span data-ttu-id="d1655-119">Aşağıdaki örnek, tam kaynak kodunu içerir `TemperatureReporter` sağlayan sınıf <xref:System.IObserver%601> uygulama izleme sıcaklık için uygulama.</span><span class="sxs-lookup"><span data-stu-id="d1655-119">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="d1655-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d1655-120">See Also</span></span>  
 <xref:System.IObserver%601>  
 [<span data-ttu-id="d1655-121">Gözlemci tasarım deseni</span><span class="sxs-lookup"><span data-stu-id="d1655-121">Observer Design Pattern</span></span>](../../../docs/standard/events/observer-design-pattern.md)  
 [<span data-ttu-id="d1655-122">Nasıl yapılır: sağlayıcıyı uygulama</span><span class="sxs-lookup"><span data-stu-id="d1655-122">How to: Implement a Provider</span></span>](../../../docs/standard/events/how-to-implement-a-provider.md)  
 [<span data-ttu-id="d1655-123">Gözlemci tasarım deseni en iyi yöntemleri</span><span class="sxs-lookup"><span data-stu-id="d1655-123">Observer Design Pattern Best Practices</span></span>](../../../docs/standard/events/observer-design-pattern-best-practices.md)
