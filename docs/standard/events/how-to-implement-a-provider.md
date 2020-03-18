---
title: 'Nasıl yapılır: Sağlayıcıyı Uygulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observer design pattern [.NET Framework], implementing providers
- providers [.NET Framework], in observer design pattern
- observables [.NET Framework], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
ms.openlocfilehash: f5bb3cda0caa39ba3fd094b80e0b769a4bfc1f85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141547"
---
# <a name="how-to-implement-a-provider"></a>Nasıl yapılır: Sağlayıcıyı Uygulama
Gözlemci tasarım deseni, verileri izleyen ve bildirim gönderen sağlayıcı ile sağlayıcıdan bildirim (geri arama) alan bir veya daha fazla gözlemci arasında bir bölünme gerektirir. Bu konu, sağlayıcının nasıl oluşturulabildiğini tartışır. İlgili bir konu, [Nasıl: Bir Gözlemci uygulayın](../../../docs/standard/events/how-to-implement-an-observer.md), nasıl bir gözlemci oluşturmak için tartışır.  
  
### <a name="to-create-a-provider"></a>Sağlayıcı oluşturmak için  
  
1. Sağlayıcının gözlemcilere göndermekten sorumlu olduğu verileri tanımlayın. Sağlayıcı ve gözlemcilere gönderdiği veriler tek bir tür olabilir, ancak genellikle farklı türlerle temsil edilir. Örneğin, bir sıcaklık izleme uygulamasında `Temperature` yapı, sağlayıcının (bir sonraki adımda tanımlanan `TemperatureMonitor` sınıf tarafından temsil edilen) izlediği ve gözlemcilerin abone olduğu verileri tanımlar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. Arabirimi uygulayan bir tür olan veri <xref:System.IObservable%601?displayProperty=nameWithType> sağlayıcısını tanımlayın. Sağlayıcının genel tür bağımsız değişkeni, sağlayıcının gözlemcilere gönderdiği türdür. Aşağıdaki örnek, genel `TemperatureMonitor` bir tür bağımsız <xref:System.IObservable%601?displayProperty=nameWithType> değişkeni `Temperature`ile oluşturulmuş bir uygulama olan bir sınıf tanımlar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. Her gözlemcinin uygun olduğunda bilgilendirilebilmeleri için sağlayıcının gözlemcilere nasıl referanslar depolayacağını belirleyin. En sık, genel <xref:System.Collections.Generic.List%601> bir nesne gibi bir koleksiyon nesnesi bu amaç için kullanılır. Aşağıdaki örnek, <xref:System.Collections.Generic.List%601> `TemperatureMonitor` sınıf oluşturucuda anında bulunan özel bir nesneyi tanımlar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. Sağlayıcının <xref:System.IDisposable> abonelere iade edebileceği bir uygulama tanımlayın, böylece bildirimleri istedikleri zaman durdurabilecekler. Aşağıdaki örnek, sınıf anında `Unsubscriber` yapıldığında abone koleksiyonuna ve aboneye başvuruda bulunulan iç içe geçmiş bir sınıf tanımlar. Bu kod, abonenin kendisini abone koleksiyonundan kaldırmak için nesnenin <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulamasını aramasını sağlar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. Yöntemi <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> uygulayın. Yöntem <xref:System.IObserver%601?displayProperty=nameWithType> arabirime bir başvuru geçirilir ve adım 3'te bu amaç için tasarlanmış nesnede depolanmalıdır. Yöntem daha sonra <xref:System.IDisposable> adım 4 geliştirilen uygulama döndürmeniz gerekir. Aşağıdaki örnek, <xref:System.IObservable%601.Subscribe%2A> `TemperatureMonitor` yöntemin sınıftaki uygulamasını gösterir.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. Gözlemcileri uygun şekilde, <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>uygulamalarını <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> ve uygulamalarını arayarak bildirin. Bazı durumlarda, bir hata oluştuğunda bir sağlayıcı <xref:System.IObserver%601.OnError%2A> yöntemi aramayabilir. Örneğin, aşağıdaki `GetTemperature` yöntem, sıcaklık verilerini her beş saniyede bir okuyan bir monitörü simüle eder ve sıcaklık önceki okumadan bu yana en az 0,1 derece değişip değişmediğini gözlemcilere haber vetir. Cihaz bir sıcaklık bildirmezse (yani değeri null ise), sağlayıcı gözlemcilere iletimin tamamladığını bildirir. Her gözlemcinin <xref:System.IObserver%601.OnCompleted%2A> yöntemini çağırmanın yanı sıra, yöntemin <xref:System.Collections.Generic.List%601> `GetTemperature` koleksiyonu temize temizler. Bu durumda, sağlayıcı gözlemcilerinyöntemini <xref:System.IObserver%601.OnError%2A> hiçbir çağrı yapar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sıcaklık izleme uygulaması <xref:System.IObservable%601> için bir uygulama tanımlamak için tam kaynak kodunu içerir. Gözlemcilere `Temperature` gönderilen veri olan yapıyı ve uygulama `TemperatureMonitor` olan <xref:System.IObservable%601> sınıfı içerir.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IObservable%601>
- [Gözlemci Tasarım Deseni](../../../docs/standard/events/observer-design-pattern.md)
- [Nasıl yapılır: Gözlemci Uygulama](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Gözlemci Tasarım Deseni En İyi Yöntemleri](../../../docs/standard/events/observer-design-pattern-best-practices.md)
