---
title: 'Nasıl yapılır: Sağlayıcı Uygulama'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12c229b3a1436f9794258fec13905cce0fb767aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026342"
---
# <a name="how-to-implement-a-provider"></a>Nasıl yapılır: Sağlayıcı Uygulama
Gözlemci tasarım deseni veri izler ve bildirimleri gönderen bir sağlayıcı bildirimi (geri aramalar) sağlayıcıdan almak, bir veya daha fazla gözlemciler arasındaki bölme işleminin gerektirir. Bu konuda, bir sağlayıcı oluşturmak nasıl ele alınmaktadır. İlgili konu başlığında, [nasıl yapılır: Gözlemci uygulama](../../../docs/standard/events/how-to-implement-an-observer.md), bir gözlemci oluşturma anlatılmaktadır.  
  
### <a name="to-create-a-provider"></a>Bir sağlayıcı oluşturmak için  
  
1. Sağlayıcı için gözlemciler göndermekten sorumludur verileri tanımlar. Sağlayıcı ve gözlemciler için gönderdiği veriler tek bir tür olabilir, ancak genellikle farklı türler tarafından temsil edilir. Örneğin, bir uygulama, izleme sıcaklık `Temperature` yapısını tanımlayan veriler, sağlayıcı (ile temsil edilir `TemperatureMonitor` sonraki adımda tanımlanan sınıfı) izler ve hangi gözlemciler için abone olun.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. Uygulayan bir tür veri sağlayıcısı tanımlamak <xref:System.IObservable%601?displayProperty=nameWithType> arabirimi. Sağlayıcının genel tür bağımsız değişkeni için gözlemciler sağlayıcı gönderen türüdür. Aşağıdaki örnekte tanımlayan bir `TemperatureMonitor` bir oluşturulmuş olan sınıf <xref:System.IObservable%601?displayProperty=nameWithType> bir genel tür bağımsız değişkeni uygulamasıyla `Temperature`.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. Böylece her gözlemci uygun olduğunda bildirim sağlayıcı gözlemciler başvuruları nasıl depolayacak belirleyin. En yaygın olarak, bir koleksiyon nesnesi gibi genel <xref:System.Collections.Generic.List%601> nesnesi, bu amaçla kullanılır. Aşağıdaki örnek bir özel tanımlar <xref:System.Collections.Generic.List%601> içinde oluşturulan bir nesnenin `TemperatureMonitor` sınıf oluşturucusu.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. Tanımlayan bir <xref:System.IDisposable> sağlayıcı abonelere döndürebilir ve böylece bildirimleri almayı durdurmak uygulaması. Aşağıdaki örnek, bir iç içe tanımlar `Unsubscriber` sınıfının örneği oluşturulduğunda aboneleri koleksiyonu ve abone için bir başvuru sınıfı. Bu kod nesnenin çağırmak abone etkinleştirir <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulama kendisini aboneleri Koleksiyondan kaldırılacak.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. Uygulama <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> yöntemi. Başvuru için bir yönteme <xref:System.IObserver%601?displayProperty=nameWithType> arabirim ve adım 3'te bu amaç için tasarlanan nesne depolanması gerekir. Yöntemi ardından döndürmelidir <xref:System.IDisposable> adım 4'te uygulama geliştirdi. Aşağıdaki örnek uygulamasını gösterir <xref:System.IObservable%601.Subscribe%2A> yönteminde `TemperatureMonitor` sınıfı.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. Gözlemciler uygun şekilde çağırarak bildir kendi <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, ve <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> uygulamaları. Bazı durumlarda, bir sağlayıcı değil çağırabilir <xref:System.IObserver%601.OnError%2A> bir hata oluştuğunda yöntemi. Örneğin, aşağıdaki `GetTemperature` yöntemi her beş saniyede sıcaklık verileri okur ve sıcaklık olur.1 dereceye göre en az önceki okuma bu yana değişmişse gözlemciler bildiren bir izleyici benzetimini yapar. Cihaz bir sıcaklık raporlamaz (diğer bir deyişle, değer null ise), sağlayıcı gözlemciler iletim tamamlandığını bildirir. Her gözlemci 's çağırma yanı sıra Not <xref:System.IObserver%601.OnCompleted%2A> yöntemi `GetTemperature` yöntemi temizler <xref:System.Collections.Generic.List%601> koleksiyonu. Bu durumda, sağlayıcı hiçbir çağrılar <xref:System.IObserver%601.OnError%2A> kendi gözlemci yöntemi.  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlamak için tam kaynak kodunu içeren bir <xref:System.IObservable%601> uygulama için uygulama izleme bir sıcaklık. İçerdiği `Temperature` gözlemciler için gönderilen verilerin olan yapısı ve `TemperatureMonitor` sınıfının <xref:System.IObservable%601> uygulaması.  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IObservable%601>
- [Gözlemci Tasarım Deseni](../../../docs/standard/events/observer-design-pattern.md)
- [Nasıl yapılır: Gözlemci uygulama](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Gözlemci Tasarım Deseni En İyi Yöntemleri](../../../docs/standard/events/observer-design-pattern-best-practices.md)
