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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139304"
---
# <a name="how-to-implement-an-observer"></a>Nasıl yapılır: Gözlemci Uygulama
Gözlemci tasarım deseninin, bildirimleri kaydeden bir gözlemci arasında bir bölme ve verileri izleyen ve bir veya daha fazla observers 'a bildirim gönderen bir sağlayıcı gerekir. Bu konu, bir gözlemci oluşturmayı açıklar. İlgili konu, [nasıl yapılır: sağlayıcı uygulama](../../../docs/standard/events/how-to-implement-a-provider.md), bir sağlayıcının nasıl oluşturulacağını açıklar.  
  
### <a name="to-create-an-observer"></a>Gözlemci oluşturmak için  
  
1. <xref:System.IObserver%601?displayProperty=nameWithType> arabirimini uygulayan bir tür olan gözlemciyi tanımlayın. Örneğin, aşağıdaki kod, `Temperature`genel tür bağımsız değişkenine sahip oluşturulmuş bir <xref:System.IObserver%601?displayProperty=nameWithType> uygulama olan `TemperatureReporter` adlı bir türü tanımlar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. Gözlemci, sağlayıcı <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> uygulamasını çağırmadan önce bildirim almayı durdurabilir, sağlayıcının <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> yöntemi tarafından döndürülen <xref:System.IDisposable> uygulamasını tutacak özel bir değişken tanımlayın. Ayrıca, sağlayıcının <xref:System.IObservable%601.Subscribe%2A> yöntemini çağıran ve döndürülen <xref:System.IDisposable> nesnesini depolayan bir abonelik yöntemi tanımlamanız gerekir. Örneğin, aşağıdaki kod `unsubscriber` adlı bir özel değişken tanımlar ve sağlayıcının <xref:System.IObservable%601.Subscribe%2A> yöntemini çağıran ve döndürülen nesneyi `unsubscriber` değişkenine atayan bir `Subscribe` yöntemi tanımlar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. Bu özellik gerekliyse, gözlemci, sağlayıcı <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> uygulamasına çağrı yapmadan önce bildirim almayı durdurmasına olanak tanıyan bir yöntem tanımlayın. Aşağıdaki örnek bir `Unsubscribe` yöntemi tanımlar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. <xref:System.IObserver%601> arabirimi tarafından tanımlanan üç yöntemin uygulamalarını sağlayın: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>ve <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. Sağlayıcıya ve uygulamanın ihtiyaçlarına bağlı olarak, <xref:System.IObserver%601.OnError%2A> ve <xref:System.IObserver%601.OnCompleted%2A> yöntemleri saplama uygulamaları olabilir. <xref:System.IObserver%601.OnError%2A> yönteminin, geçirilen <xref:System.Exception> nesnesini özel bir durum olarak işlememesi gerektiğini ve <xref:System.IObserver%601.OnCompleted%2A> yönteminin sağlayıcının <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulamasını çağıracağına yönelik boş olduğunu unutmayın. Aşağıdaki örnek, `TemperatureReporter` sınıfının <xref:System.IObserver%601> uygulamasını gösterir.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sıcaklık izleme uygulaması için <xref:System.IObserver%601> uygulaması sağlayan `TemperatureReporter` sınıfı için tüm kaynak kodunu içerir.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IObserver%601>
- [Gözlemci Tasarım Deseni](../../../docs/standard/events/observer-design-pattern.md)
- [Nasıl yapılır: Sağlayıcıyı Uygulama](../../../docs/standard/events/how-to-implement-a-provider.md)
- [Gözlemci Tasarım Deseni En İyi Yöntemleri](../../../docs/standard/events/observer-design-pattern-best-practices.md)
