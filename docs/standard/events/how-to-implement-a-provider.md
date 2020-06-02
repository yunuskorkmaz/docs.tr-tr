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
ms.openlocfilehash: 4f8a213c0df3ef3c633106b7249a4947fe77c0d2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280029"
---
# <a name="how-to-implement-a-provider"></a>Nasıl yapılır: Sağlayıcıyı Uygulama
Gözlemci tasarım deseninin, sağlayıcıyı izleyen ve bildirim gönderen bir veya daha fazla observers ve sağlayıcıdan bildirimler alan bir veya daha fazla Observer arasında bir bölüm olması gerekir. Bu konuda, bir sağlayıcının nasıl oluşturulacağı açıklanmaktadır. İlgili konu başlığı, [nasıl yapılır: gözlemci uygulama](how-to-implement-an-observer.md), gözlemci oluşturmayı açıklar.  
  
### <a name="to-create-a-provider"></a>Bir sağlayıcı oluşturmak için  
  
1. Sağlayıcının observers 'a göndermekten sorumlu olduğu verileri tanımlayın. Sağlayıcı ve kendisi gözlemcilerin 'a gönderdiği veriler tek bir tür olabilir, ancak bunlar genellikle farklı türlerle temsil edilir. Örneğin, bir sıcaklık izleme uygulamasında `Temperature` Yapı, sağlayıcının (bir `TemperatureMonitor` sonraki adımda tanımlanan sınıf tarafından temsil edilen) izleyicilerin ve hangi gözlemcilerin 'in abone olduğu verileri tanımlar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. Arabirimini uygulayan bir tür olan veri sağlayıcısını tanımlayın <xref:System.IObservable%601?displayProperty=nameWithType> . Sağlayıcının genel tür bağımsız değişkeni, sağlayıcının observers 'a gönderdiği türdür. Aşağıdaki örnek `TemperatureMonitor` , <xref:System.IObservable%601?displayProperty=nameWithType> genel tür bağımsız değişkeni ile oluşturulmuş bir uygulama olan bir sınıfı tanımlar `Temperature` .  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. Her gözlemciye uygun olduğunda bildirim gönderilmesini sağlamak için sağlayıcının gözlemciye başvuruları nasıl depolayacağınızı belirleme. En yaygın olarak, genel nesne gibi bir koleksiyon nesnesi <xref:System.Collections.Generic.List%601> Bu amaçla kullanılır. Aşağıdaki örnek, <xref:System.Collections.Generic.List%601> sınıf oluşturucusunda örneği oluşturulan özel bir nesneyi tanımlar `TemperatureMonitor` .  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. <xref:System.IDisposable>Sağlayıcının abonelere döndürebilecekleri bir uygulama tanımlayın, böylece herhangi bir zamanda bildirim almayı durdurabilir. Aşağıdaki örnek, `Unsubscriber` abone koleksiyonuna ve sınıf örneği oluşturulduğunda aboneye bir başvuru aktarılan iç içe bir sınıfı tanımlar. Bu kod, abonenin <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> kendisini aboneler koleksiyonundan kaldırmak için nesnenin uygulamasını çağırmasını sağlar.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. Yöntemini uygulayın <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> . Yöntemine bir başvuru geçirilir <xref:System.IObserver%601?displayProperty=nameWithType> ve adım 3 ' te bu amaçla tasarlanan nesnede depolanmalıdır. Yöntemi daha sonra <xref:System.IDisposable> Adım 4 ' te geliştirilen uygulamayı döndürmelidir. Aşağıdaki örnek, <xref:System.IObservable%601.Subscribe%2A> sınıfındaki yönteminin uygulamasını gösterir `TemperatureMonitor` .  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, Ve uygulamalarını çağırarak, gözlemcilerin 'ı uygun şekilde bilgilendirin <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> . Bazı durumlarda, bir hata oluştuğunda sağlayıcı yöntemi çağırmayabilir <xref:System.IObserver%601.OnError%2A> . Örneğin, aşağıdaki yöntem, `GetTemperature` beş saniyede bir sıcaklık verisini okuyan bir izleyiciyi taklit eder ve önceki okumadan bu yana sıcaklığın en az 1 olarak değişmesi durumunda gözlemcilerin 'a bildirimde bulunur. Cihaz bir sıcaklık bildirmezse (yani değeri null ise), sağlayıcı gözlemi aktarımın tamamlandığını bildirir. Her gözlemci yöntemini çağırmanın yanı sıra, <xref:System.IObserver%601.OnCompleted%2A> `GetTemperature` yöntemi <xref:System.Collections.Generic.List%601> koleksiyonu temizler. Bu durumda, sağlayıcı <xref:System.IObserver%601.OnError%2A> observers yöntemine hiçbir çağrı yapmaz.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.IObservable%601> bir sıcaklık izleme uygulaması için uygulama tanımlamaya yönelik tüm kaynak kodunu içerir. Bu, `Temperature` observers 'a gönderilen veriler ve `TemperatureMonitor` uygulama olan sınıf olan yapıyı içerir <xref:System.IObservable%601> .  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IObservable%601>
- [Gözlemci tasarım kalıbı](observer-design-pattern.md)
- [Nasıl yapılır: gözlemci uygulama](how-to-implement-an-observer.md)
- [Gözlemci Tasarım Deseni En İyi Yöntemleri](observer-design-pattern-best-practices.md)
