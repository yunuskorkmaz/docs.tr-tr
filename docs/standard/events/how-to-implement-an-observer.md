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
# <a name="how-to-implement-an-observer"></a>Nasıl yapılır: Gözlemci Uygulama
Gözlemci tasarım deseni, bildirimler için kayıt yaptıran bir gözlemci ile verileri izleyen ve bir veya daha fazla gözlemciye bildirim gönderen bir sağlayıcı arasında bir bölünme gerektirir. Bu konu nasıl bir gözlemci oluşturmak için tartışır. İlgili bir konu, [Nasıl: Sağlayıcı uygulama,](../../../docs/standard/events/how-to-implement-a-provider.md)nasıl bir sağlayıcı oluşturmak için tartışır.  
  
### <a name="to-create-an-observer"></a>Gözlemci oluşturmak için  
  
1. Arabirimi uygulayan bir tür olan gözlemciyi tanımlayın. <xref:System.IObserver%601?displayProperty=nameWithType> Örneğin, aşağıdaki kod, genel bir `TemperatureReporter` tür bağımsız <xref:System.IObserver%601?displayProperty=nameWithType> değişkeni `Temperature`olan yapılı bir uygulama olan adlı bir türü tanımlar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. Gözlemci, sağlayıcı nın uygulanmasını aramadan <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> önce bildirim almayı durdurabiliyorsa, <xref:System.IDisposable> sağlayıcının <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> yöntemi yle döndürülen uygulamayı tutacak özel bir değişken tanımlayın. Ayrıca, sağlayıcının <xref:System.IObservable%601.Subscribe%2A> yöntemini çağıran ve döndürülen <xref:System.IDisposable> nesneyi depolayan bir abonelik yöntemi de tanımlamalısınız. Örneğin, aşağıdaki kod `unsubscriber` adlı özel bir değişkeni `Subscribe` tanımlar ve sağlayıcının <xref:System.IObservable%601.Subscribe%2A> yöntemini çağıran ve döndürülen `unsubscriber` nesneyi değişkene atayan bir yöntem tanımlar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. Bu özellik gerekiyorsa, sağlayıcı uygulamadan önce gözlemcinin bildirim <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> almayı durdurmasını sağlayan bir yöntem tanımlayın. Aşağıdaki örnekte bir `Unsubscribe` yöntem tanımlanır.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. Arabirim <xref:System.IObserver%601> tarafından tanımlanan üç yöntemin <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>uygulamalarını <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>sağlayın: , , ve <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. Sağlayıcıya ve uygulamanın ihtiyaçlarına bağlı olarak, ve <xref:System.IObserver%601.OnError%2A> <xref:System.IObserver%601.OnCompleted%2A> yöntemler saplama uygulamaları olabilir. Yöntemin <xref:System.IObserver%601.OnError%2A> geçirilen <xref:System.Exception> nesneyi bir özel durum olarak <xref:System.IObserver%601.OnCompleted%2A> işlememesi gerektiğini ve yöntemin <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> sağlayıcının uygulamasını çağırmakta özgür olduğunu unutmayın. Aşağıdaki örnek, <xref:System.IObserver%601> `TemperatureReporter` sınıfın uygulamasını gösterir.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sıcaklık izleme `TemperatureReporter` uygulaması için <xref:System.IObserver%601> uygulama sağlayan sınıf için tam kaynak kodunu içerir.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IObserver%601>
- [Gözlemci Tasarım Deseni](../../../docs/standard/events/observer-design-pattern.md)
- [Nasıl yapılır: Sağlayıcıyı Uygulama](../../../docs/standard/events/how-to-implement-a-provider.md)
- [Gözlemci Tasarım Deseni En İyi Yöntemleri](../../../docs/standard/events/observer-design-pattern-best-practices.md)
