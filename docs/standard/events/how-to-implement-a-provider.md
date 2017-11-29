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
ms.openlocfilehash: b9d8f96de8cb3d13568e755f1d5e885e0474d891
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-provider"></a>Nasıl yapılır: Sağlayıcıyı Uygulama
Gözlemci tasarım deseni, verileri izler ve bildirimleri gönderen bir sağlayıcısı ve bildirimleri (geri aramalar) sağlayıcıdan almak, bir veya daha fazla gözlemcilerin arasında bölme gerektirir. Bu konuda bir sağlayıcı oluşturma açıklanmaktadır. İlgili konu [nasıl yapılır: gözlemci uygulama](../../../docs/standard/events/how-to-implement-an-observer.md), bir gözlemci oluşturulacağını anlatır.  
  
### <a name="to-create-a-provider"></a>Sağlayıcı oluşturmak için  
  
1.  Sağlayıcı için gözlemcilerin göndermekten sorumludur verileri tanımlamak. Sağlayıcı ve gözlemcilerin için gönderdiği verileri tek bir türü olsa da, bunlar genellikle farklı türleri tarafından gösterilir. Örneğin, bir uygulama, izleme sıcaklık içinde `Temperature` yapısı verileri tanımlar, sağlayıcı (tarafından temsil `TemperatureMonitor` sonraki adımda tanımlanan sınıfı) izler ve hangi gözlemcilerin abone olabilirsiniz.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2.  Arabirimini uygulayan bir tür veri sağlayıcısı tanımlamak <xref:System.IObservable%601?displayProperty=nameWithType> arabirimi. Sağlayıcının genel tür bağımsız değişkeni için gözlemcilerin sağlayıcı gönderdiği türüdür. Aşağıdaki örnek tanımlayan bir `TemperatureMonitor` bir oluşturulmuş olan sınıf <xref:System.IObservable%601?displayProperty=nameWithType> bir uygulama bir genel tür bağımsız değişkeni ile `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3.  Böylece her gözlemci uygun olduğunda bildirim sağlayıcı gözlemcilerin başvurular nasıl depolayacak belirler. En yaygın olarak, bir koleksiyon nesnesi genel gibi <xref:System.Collections.Generic.List%601> nesnesi, bu amaç için kullanılır. Aşağıdaki örnek, bir özel tanımlar <xref:System.Collections.Generic.List%601> içinde örneği nesneyi `TemperatureMonitor` sınıfı oluşturucusu.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4.  Tanımlayan bir <xref:System.IDisposable> sağlayıcı abonelere döndürebilir ve böylece herhangi bir zamanda bildirimleri alma durdurabilirsiniz uygulama. Aşağıdaki örnek, bir iç içe tanımlar `Unsubscriber` sınıfının örneği oluşturulduğunda bir başvuru aboneleri koleksiyonu ve abone geçirilen sınıfı. Bu kod nesnenin çağırmak abone etkinleştirir <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulama kendisini aboneleri Koleksiyondan kaldırılacak.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5.  Uygulama <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> yöntemi. Yöntem başvuru geçirilen <xref:System.IObserver%601?displayProperty=nameWithType> arabirim ve adım 3'te bu amaç için tasarlanmış nesnesindeki depolanması gerekir. Yöntem sonra döndürmelidir <xref:System.IDisposable> uygulama geliştirilen adım 4 '. Aşağıdaki örnek uygulamasını gösterir <xref:System.IObservable%601.Subscribe%2A> yönteminde `TemperatureMonitor` sınıfı.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6.  Çağırarak uygun şekilde gözlemcilerin bildir kendi <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, ve <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> uygulamaları. Bazı durumlarda, bir sağlayıcı değil çağırabilir <xref:System.IObserver%601.OnError%2A> bir hata oluştuğunda yöntemi. Örneğin, aşağıdaki `GetTemperature` yöntemi beş saniyede sıcaklık veri okuyan ve sıcaklık önceki okuma bu yana en az olur.1 derece tarafından değiştiyse gözlemcilerin bildiren bir izleyici benzetimini yapar. Varsa (diğer bir deyişle, kendi değer null ise) aygıtı bir sıcaklık bildirmez, sağlayıcı gözlemcilerin iletim tamamlandığını bildirir. Her gözlemci 's çağırma yanı sıra unutmayın <xref:System.IObserver%601.OnCompleted%2A> yöntemi, `GetTemperature` yöntemini temizler <xref:System.Collections.Generic.List%601> koleksiyonu. Bu durumda, sağlayıcı hiçbir çağrılar <xref:System.IObserver%601.OnError%2A> kendi gözlemcilerin yöntemi.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlamak için tam kaynak kodunu içeren bir <xref:System.IObservable%601> uygulaması için uygulama izleme sıcaklık. İçerdiği `Temperature` gözlemcilerin için gönderilen veri olan yapısı ve `TemperatureMonitor` olan sınıf <xref:System.IObservable%601> uygulaması.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IObservable%601>  
 [Gözlemci tasarım deseni](../../../docs/standard/events/observer-design-pattern.md)  
 [Nasıl yapılır: gözlemci uygulama](../../../docs/standard/events/how-to-implement-an-observer.md)  
 [Gözlemci tasarım deseni en iyi yöntemleri](../../../docs/standard/events/observer-design-pattern-best-practices.md)
