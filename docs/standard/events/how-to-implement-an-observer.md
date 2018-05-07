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
ms.openlocfilehash: f291bc91575ccde346f16552636d44951a0e6eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-an-observer"></a>Nasıl yapılır: Gözlemci Uygulama
Gözlemci tasarım deseni bildirimleri için kaydeder, bir gözlemci, verileri izler ve bir veya daha fazla gözlemcilerin bildirimleri gönderen bir sağlayıcısı arasındaki bölme gerektirir. Bu konu bir gözlemci oluşturulacağını açıklar. İlgili konu [nasıl yapılır: sağlayıcıyı uygulama](../../../docs/standard/events/how-to-implement-a-provider.md), bir sağlayıcı oluşturulacağını anlatır.  
  
### <a name="to-create-an-observer"></a>Bir gözlemci oluşturmak için  
  
1.  Arabirimini uygulayan bir tür gözlemci tanımlamak <xref:System.IObserver%601?displayProperty=nameWithType> arabirimi. Örneğin, aşağıdaki kod adlı tür tanımlar `TemperatureReporter` diğer bir deyişle oluşturulan <xref:System.IObserver%601?displayProperty=nameWithType> bir uygulama bir genel tür bağımsız değişkeni ile `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  Gözlemci bildirimleri sağlayıcısı çağrıları önce alma durdurursanız, kendi <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> uygulaması, tutacak özel bir değişkeni tanımlamak <xref:System.IDisposable> sağlayıcının tarafından döndürülen uygulama <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> yöntemi. Sağlayıcının çağıran bir abonelik yöntemi tanımlamanız gerekir <xref:System.IObservable%601.Subscribe%2A> yöntemi ve depoları döndürülen <xref:System.IDisposable> nesnesi. Örneğin, aşağıdaki kod adlı özel bir değişken tanımlar `unsubscriber` ve tanımlayan bir `Subscribe` sağlayıcının çağıran yöntemi <xref:System.IObservable%601.Subscribe%2A> yöntemi ve döndürülen nesneyi atar `unsubscriber` değişkeni.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  Gözlemci bildirimleri sağlayıcısı çağrıları önce almayı durdurmasını sağlayan bir yöntemi tanımlamak, <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> bu özelliği gerekliyse, uygulama. Aşağıdaki örnek tanımlayan bir `Unsubscribe` yöntemi.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  Tarafından tanımlanan üç yöntem uygulamalarını <xref:System.IObserver%601> arabirimi: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, ve <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. Sağlayıcı ve uygulamanızın gereksinimlerine bağlı olarak <xref:System.IObserver%601.OnError%2A> ve <xref:System.IObserver%601.OnCompleted%2A> yöntemleri, saplama uygulamaları olabilir. Unutmayın <xref:System.IObserver%601.OnError%2A> yöntemi değil ele geçirilen <xref:System.Exception> nesnesi bir özel durum olarak ve <xref:System.IObserver%601.OnCompleted%2A> yöntemdir sağlayıcının çağırmak ücretsiz <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulaması. Aşağıdaki örnekte gösterildiği <xref:System.IObserver%601> uyarlamasını `TemperatureReporter` sınıfı.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tam kaynak kodunu içerir `TemperatureReporter` sağlayan sınıf <xref:System.IObserver%601> uygulama izleme sıcaklık için uygulama.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IObserver%601>  
 [Gözlemci Tasarım Deseni](../../../docs/standard/events/observer-design-pattern.md)  
 [Nasıl yapılır: Sağlayıcıyı Uygulama](../../../docs/standard/events/how-to-implement-a-provider.md)  
 [Gözlemci Tasarım Deseni En İyi Yöntemleri](../../../docs/standard/events/observer-design-pattern-best-practices.md)
