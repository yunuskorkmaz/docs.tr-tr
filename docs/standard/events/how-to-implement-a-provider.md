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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141547"
---
# <a name="how-to-implement-a-provider"></a>Nasıl yapılır: Sağlayıcıyı Uygulama
Gözlemci tasarım deseninin, sağlayıcıyı izleyen ve bildirim gönderen bir veya daha fazla observers ve sağlayıcıdan bildirimler alan bir veya daha fazla Observer arasında bir bölüm olması gerekir. Bu konuda, bir sağlayıcının nasıl oluşturulacağı açıklanmaktadır. İlgili konu başlığı, [nasıl yapılır: gözlemci uygulama](../../../docs/standard/events/how-to-implement-an-observer.md), gözlemci oluşturmayı açıklar.  
  
### <a name="to-create-a-provider"></a>Bir sağlayıcı oluşturmak için  
  
1. Sağlayıcının observers 'a göndermekten sorumlu olduğu verileri tanımlayın. Sağlayıcı ve kendisi gözlemcilerin 'a gönderdiği veriler tek bir tür olabilir, ancak bunlar genellikle farklı türlerle temsil edilir. Örneğin, bir sıcaklık izleme uygulamasında `Temperature` yapısı, sağlayıcının (bir sonraki adımda tanımlanan `TemperatureMonitor` sınıfı tarafından temsil edilen) ve gözlemcilerin abone olduğu verileri tanımlar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. <xref:System.IObservable%601?displayProperty=nameWithType> arabirimini uygulayan bir tür olan veri sağlayıcısını tanımlayın. Sağlayıcının genel tür bağımsız değişkeni, sağlayıcının observers 'a gönderdiği türdür. Aşağıdaki örnek, `Temperature`genel tür bağımsız değişkenine sahip oluşturulmuş bir <xref:System.IObservable%601?displayProperty=nameWithType> uygulama olan `TemperatureMonitor` sınıfını tanımlar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. Her gözlemciye uygun olduğunda bildirim gönderilmesini sağlamak için sağlayıcının gözlemciye başvuruları nasıl depolayacağınızı belirleme. En yaygın olarak, genel <xref:System.Collections.Generic.List%601> nesnesi gibi bir koleksiyon nesnesi bu amaçla kullanılır. Aşağıdaki örnek, `TemperatureMonitor` sınıf oluşturucusunda oluşturulan özel bir <xref:System.Collections.Generic.List%601> nesnesini tanımlar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. Sağlayıcının abonelere döndürebilecekleri <xref:System.IDisposable> bir uygulama tanımlayın, böylece herhangi bir zamanda bildirim almayı durdurabilir. Aşağıdaki örnek, bir başvuru oluşturan iç içe `Unsubscriber` sınıfını ve sınıf örneği oluşturulduğunda abonelere abone olan aboneye tanımlar. Bu kod, abonenin kendisini aboneler koleksiyonundan kaldırmak için nesnenin <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulamasını çağırmasını sağlar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> yöntemini uygulayın. Yöntemine <xref:System.IObserver%601?displayProperty=nameWithType> arabirimine bir başvuru geçirilir ve adım 3 ' te bu amaçla tasarlanan nesnede depolanmalıdır. Yöntemi daha sonra 4. adımda geliştirilen <xref:System.IDisposable> uygulamasını döndürmelidir. Aşağıdaki örnek, `TemperatureMonitor` sınıfında <xref:System.IObservable%601.Subscribe%2A> yönteminin uygulamasını gösterir.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>ve <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> uygulamalarını çağırarak gözlemcilerin 'ı uygun şekilde bilgilendirin. Bazı durumlarda, bir hata oluştuğunda sağlayıcı <xref:System.IObserver%601.OnError%2A> yöntemini çağırmayabilir. Örneğin, aşağıdaki `GetTemperature` yöntemi, beş saniyede bir sıcaklık verisini okuyan bir izleyicinin benzetimini yapar ve bu, önceki okumadan bu yana sıcaklığın en az bir olarak değiştirilmişse gözlemi sunucuya bildirir. Cihaz bir sıcaklık bildirmezse (yani değeri null ise), sağlayıcı gözlemi aktarımın tamamlandığını bildirir. Her bir gözlemci <xref:System.IObserver%601.OnCompleted%2A> yöntemini çağırmaya ek olarak, `GetTemperature` yöntemi <xref:System.Collections.Generic.List%601> koleksiyonunu temizler. Bu durumda, sağlayıcı, observers 'ın <xref:System.IObserver%601.OnError%2A> metoduna hiçbir çağrı yapmaz.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sıcaklık izleme uygulaması için <xref:System.IObservable%601> uygulaması tanımlamaya yönelik tüm kaynak kodunu içerir. Bu, observers 'a gönderilen veriler ve <xref:System.IObservable%601> uygulama olan `TemperatureMonitor` sınıfı olan `Temperature` yapısını içerir.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IObservable%601>
- [Gözlemci Tasarım Deseni](../../../docs/standard/events/observer-design-pattern.md)
- [Nasıl yapılır: Gözlemci Uygulama](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Gözlemci Tasarım Deseni En İyi Yöntemleri](../../../docs/standard/events/observer-design-pattern-best-practices.md)
