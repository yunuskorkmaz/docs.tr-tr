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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6426e8bd138d06d3655562de6384e46a12c09279
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46519230"
---
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="47eca-102">Nasıl yapılır: Gözlemci Uygulama</span><span class="sxs-lookup"><span data-stu-id="47eca-102">How to: Implement an Observer</span></span>
<span data-ttu-id="47eca-103">Gözlemci tasarım deseni için bildirimleri kaydeden bir gözlemci veri izler ve bir veya daha fazla gözlemciler için bildirim gönderen bir sağlayıcı arasındaki bölme işleminin gerektirir.</span><span class="sxs-lookup"><span data-stu-id="47eca-103">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="47eca-104">Bu konu, bir gözlemci oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="47eca-104">This topic discusses how to create an observer.</span></span> <span data-ttu-id="47eca-105">İlgili konu başlığında, [nasıl yapılır: sağlayıcıyı uygulama](../../../docs/standard/events/how-to-implement-a-provider.md), bir sağlayıcı oluşturma anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47eca-105">A related topic, [How to: Implement a Provider](../../../docs/standard/events/how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="47eca-106">Gözlemci oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="47eca-106">To create an observer</span></span>  
  
1.  <span data-ttu-id="47eca-107">Gözlemci uygulayan bir tür tanımlamak <xref:System.IObserver%601?displayProperty=nameWithType> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="47eca-107">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="47eca-108">Örneğin, aşağıdaki kod adlı bir tür tanımlar `TemperatureReporter` diğer bir deyişle oluşturulmuş <xref:System.IObserver%601?displayProperty=nameWithType> bir genel tür bağımsız değişkeni uygulamasıyla `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="47eca-108">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  <span data-ttu-id="47eca-109">Gözlemci bildirimleri sağlayıcısı çağrıları önce iptal ederseniz, <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> uygulaması barındıracak özel bir değişken tanımlayın <xref:System.IDisposable> sağlayıcının tarafından döndürülen uygulama <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="47eca-109">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="47eca-110">Ayrıca sağlayıcının çağıran bir abonelik yöntemi tanımlamalıdır <xref:System.IObservable%601.Subscribe%2A> yöntemi ve depoları döndürülen <xref:System.IDisposable> nesne.</span><span class="sxs-lookup"><span data-stu-id="47eca-110">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="47eca-111">Örneğin, aşağıdaki kod adlı özel bir değişken tanımlar `unsubscriber` ve tanımlayan bir `Subscribe` sağlayıcının çağıran yöntemi <xref:System.IObservable%601.Subscribe%2A> yöntemi ve döndürülen nesneyi atar `unsubscriber` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="47eca-111">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  <span data-ttu-id="47eca-112">Gözlemci sağlayıcısı çağrıları önce bildirim almayı durdurmak sağlayan bir yöntem tanımlayın, <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> uygulanması gerekirse bu özellik,.</span><span class="sxs-lookup"><span data-stu-id="47eca-112">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="47eca-113">Aşağıdaki örnekte tanımlayan bir `Unsubscribe` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="47eca-113">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  <span data-ttu-id="47eca-114">Uygulamaları tarafından tanımlanan üç yöntemi sağlamak <xref:System.IObserver%601> arabirimi: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, ve <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="47eca-114">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="47eca-115">Sağlayıcı ve uygulama gereksinimlerine bağlı olarak <xref:System.IObserver%601.OnError%2A> ve <xref:System.IObserver%601.OnCompleted%2A> yöntemleri Koçan uygulamaları olabilir.</span><span class="sxs-lookup"><span data-stu-id="47eca-115">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="47eca-116">Unutmayın <xref:System.IObserver%601.OnError%2A> yöntemi işlememek geçirilen <xref:System.Exception> nesnesi bir özel durum olarak ve <xref:System.IObserver%601.OnCompleted%2A> sağlayıcının çağırmak yöntem ücretsizdir <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="47eca-116">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="47eca-117">Aşağıdaki örnekte gösterildiği <xref:System.IObserver%601> uygulaması `TemperatureReporter` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="47eca-117">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="47eca-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="47eca-118">Example</span></span>  
 <span data-ttu-id="47eca-119">Aşağıdaki örnek, tam kaynak kodunu içerir. `TemperatureReporter` sağlar sınıfını <xref:System.IObserver%601> uygulaması için uygulama izleme bir sıcaklık.</span><span class="sxs-lookup"><span data-stu-id="47eca-119">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="47eca-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47eca-120">See also</span></span>

- <xref:System.IObserver%601>  
- [<span data-ttu-id="47eca-121">Gözlemci Tasarım Deseni</span><span class="sxs-lookup"><span data-stu-id="47eca-121">Observer Design Pattern</span></span>](../../../docs/standard/events/observer-design-pattern.md)  
- [<span data-ttu-id="47eca-122">Nasıl yapılır: Sağlayıcıyı Uygulama</span><span class="sxs-lookup"><span data-stu-id="47eca-122">How to: Implement a Provider</span></span>](../../../docs/standard/events/how-to-implement-a-provider.md)  
- [<span data-ttu-id="47eca-123">Gözlemci Tasarım Deseni En İyi Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="47eca-123">Observer Design Pattern Best Practices</span></span>](../../../docs/standard/events/observer-design-pattern-best-practices.md)
