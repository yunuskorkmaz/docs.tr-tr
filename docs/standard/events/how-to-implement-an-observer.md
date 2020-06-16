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
# <a name="how-to-implement-an-observer"></a>Nasıl yapılır: Gözlemci Uygulama
Gözlemci tasarım deseninin, bildirimleri kaydeden bir gözlemci arasında bir bölme ve verileri izleyen ve bir veya daha fazla observers 'a bildirim gönderen bir sağlayıcı gerekir. Bu konu, bir gözlemci oluşturmayı açıklar. İlgili konu, [nasıl yapılır: sağlayıcı uygulama](how-to-implement-a-provider.md), bir sağlayıcının nasıl oluşturulacağını açıklar.  
  
### <a name="to-create-an-observer"></a>Gözlemci oluşturmak için  
  
1. Arabirimini uygulayan bir tür olan gözlemciyi tanımlayın <xref:System.IObserver%601?displayProperty=nameWithType> . Örneğin, aşağıdaki kod, `TemperatureReporter` <xref:System.IObserver%601?displayProperty=nameWithType> genel tür bağımsız değişkenine sahip oluşturulmuş bir uygulama olan adlı bir türü tanımlar `Temperature` .  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2. Gözlemci, sağlayıcı uygulamasını çağırmadan önce bildirim almayı durdurabilir <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> , <xref:System.IDisposable> sağlayıcının yöntemi tarafından döndürülen uygulamayı tutacak özel bir değişken tanımlayın <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> . Ayrıca, sağlayıcının <xref:System.IObservable%601.Subscribe%2A> yöntemini çağıran ve döndürülen nesneyi depolayan bir abonelik yöntemi tanımlamanız gerekir <xref:System.IDisposable> . Örneğin, aşağıdaki kod adlı bir özel değişkeni tanımlar `unsubscriber` ve `Subscribe` sağlayıcının yöntemini çağıran ve <xref:System.IObservable%601.Subscribe%2A> döndürülen nesneyi değişkenine atayan bir yöntemi tanımlar `unsubscriber` .  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3. Bu özellik gerekliyse, gözlemciye, sağlayıcı uygulama çağrılmadan önce bildirim almayı durdurmasını sağlayan bir yöntem tanımlayın <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> . Aşağıdaki örnek bir yöntemi tanımlar `Unsubscribe` .  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4. Arabirimi tarafından tanımlanan üç yöntemin uygulamalarını sağlayın <xref:System.IObserver%601> : <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> , <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> , ve <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> . Sağlayıcıya ve uygulamanın ihtiyaçlarına bağlı olarak, <xref:System.IObserver%601.OnError%2A> ve <xref:System.IObserver%601.OnCompleted%2A> yöntemleri saplama uygulamaları olabilir. <xref:System.IObserver%601.OnError%2A>Yöntemin geçirilen <xref:System.Exception> nesneyi özel durum olarak işlememesi gerektiğini ve <xref:System.IObserver%601.OnCompleted%2A> yöntemin, sağlayıcının uygulamasını çağırmak için boş olduğunu unutmayın <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> . Aşağıdaki örnek, <xref:System.IObserver%601> sınıfının uygulamasını gösterir `TemperatureReporter` .  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek `TemperatureReporter` , <xref:System.IObserver%601> bir sıcaklık izleme uygulaması için uygulama sağlayan, sınıfının tüm kaynak kodunu içerir.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IObserver%601>
- [Gözlemci tasarım kalıbı](observer-design-pattern.md)
- [Nasıl yapılır: sağlayıcı uygulama](how-to-implement-a-provider.md)
- [Gözlemci Tasarım Deseni En İyi Yöntemleri](observer-design-pattern-best-practices.md)
