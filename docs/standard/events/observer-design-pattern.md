---
title: Gözlemci Tasarım Deseni
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IObserver(Of T) interface
- IObservable<T> interface
- IObserver<T> interface
- IObservable(Of T) interface
- observer design pattern [.NET Framework]
ms.assetid: 3680171f-f522-453c-aa4a-54f755a78f88
ms.openlocfilehash: 817337cec604a431f9f7d4eacb04378ee0d3c227
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131570"
---
# <a name="observer-design-pattern"></a>Gözlemci Tasarım Deseni

Gözlemci tasarım deseninin bir abone ile kaydolmalarını ve bir sağlayıcıdan gelen bildirimleri almasını sağlar. Gönderim tabanlı bildirim gerektiren tüm senaryolar için uygundur. Bu model, bir *sağlayıcıyı* ( *Konu* veya *observable*olarak da bilinir) ve sıfır, bir veya daha fazla *gözlemcilerin*tanımlar. Gözlemcilerin sağlayıcıya kaydoldu ve önceden tanımlanmış bir koşul, olay veya durum değişikliği gerçekleştiğinde sağlayıcı, yöntemlerinden birini çağırarak tüm gözlemcilerin 'ı otomatik olarak bilgilendirir. Bu yöntem çağrısında sağlayıcı, güncel durum bilgilerini observers 'a de verebilir. .NET Framework, gözlemci tasarım deseninin genel <xref:System.IObservable%601?displayProperty=nameWithType> ve <xref:System.IObserver%601?displayProperty=nameWithType> arabirimleri uygulayarak uygulanması gerekir. Genel tür parametresi, bildirim bilgilerini sağlayan türü temsil eder.

## <a name="applying-the-pattern"></a>Desenler uygulanıyor

Bir veri kaynağı (iş mantığı) katmanı ve Kullanıcı arabirimi (görüntü) katmanı gibi iki farklı bileşen veya uygulama katmanı arasında temiz ayrımı desteklediğinden, gözlemci tasarım deseninin dağıtılan gönderim tabanlı bildirimler için uygun olması gerekir. Bir sağlayıcı, istemcilerini geçerli bilgilerle sağlamak için geri çağırmaları kullandığında, bu model uygulanabilir.

Düzenin uygulanması için şunları sağlamanız gerekir:

- Gözlemi sunucularına bildirim gönderen nesnesi olan bir sağlayıcı veya konu. Sağlayıcı, <xref:System.IObservable%601> arabirimini uygulayan bir sınıf veya yapıdır. Sağlayıcı, sağlayıcıdan bildirim almak isteyen gözlemcilerin tarafından çağrılan tek bir yöntem <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>uygulamalıdır.

- Sağlayıcıdan gelen bildirimleri alan bir nesne olan gözlemci. Gözlemci, <xref:System.IObserver%601> arabirimini uygulayan bir sınıf veya yapıdır. Gözlemci, hepsi sağlayıcı tarafından çağrılan üç yöntemi gerçekleştirmelidir:

  - Yeni veya güncel bilgilerle gözlemci sağlayan <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>.

  - <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, gözlemciye bir hata oluştuğunu bildiren.

  - <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, sağlayıcının bildirimleri göndermeyi bitirdiğini gösterir.

- Sağlayıcının observers 'ı izlemesine izin veren bir mekanizma. Genellikle, sağlayıcı, bildirimlere abone olan <xref:System.IObserver%601> uygulamalarına başvuruları tutmak için <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> nesnesi gibi bir kapsayıcı nesnesi kullanır. Bu amaçla bir depolama kapsayıcısı kullanmak, sağlayıcının sınırsız sayıda Observer 'a sıfır işlemesini sağlar. Gözlemcilerin 'ın bildirim alma sırası tanımlı değil; sağlayıcı, siparişi belirlemede herhangi bir yöntemi kullanmak ücretsizdir.

- Sağlayıcının, bildirim tamamlandığında gözlemcilerin 'ı kaldırmasını sağlayan <xref:System.IDisposable> bir uygulama. Observers, <xref:System.IObservable%601.Subscribe%2A> yönteminden <xref:System.IDisposable> uygulamasına bir başvuru alır. bu nedenle, sağlayıcının bildirimleri göndermeden önce aboneliğini kaldırmak için <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metodunu da çağırabilirler.

- Sağlayıcının observers 'a gönderdiği verileri içeren bir nesne. Bu nesnenin türü, <xref:System.IObservable%601> ve <xref:System.IObserver%601> arabirimlerinin genel tür parametresine karşılık gelir. Bu nesne <xref:System.IObservable%601> uygulamayla aynı olsa da, genellikle ayrı bir tür olur.

> [!NOTE]
> Gözlemci tasarım deseninin yanı sıra, <xref:System.IObservable%601> ve <xref:System.IObserver%601> arabirimleri kullanılarak oluşturulan kitaplıkları keşfetmek isteyebilirsiniz. Örneğin, [.net Için reaktif uzantıları (RX)](https://docs.microsoft.com/previous-versions/dotnet/reactive-extensions/hh242985(v=vs.103)) , zaman uyumsuz programlamayı desteklemek için bir dizi genişletme YÖNTEMINDEN ve LINQ standart dizisi işleçlerinden oluşur.

## <a name="implementing-the-pattern"></a>Kalıbı uygulama

Aşağıdaki örnekte, bir Havaalanı Bagaj talep bilgileri sistemi uygulamak için gözlemci tasarım deseninin kullanımı vardır. `BaggageInfo` bir sınıf, gelen fışıklara ve her bir uçuşdan Bagaj 'nin çekme için kullanılabildiği Carousels hakkında bilgi sağlar. Aşağıdaki örnekte gösterilmiştir.

[!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
[!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]

`BaggageHandler` sınıfı, gelen fışıkları ve Bagaj talebi Carousels hakkında bilgi almaktan sorumludur. Dahili olarak, iki koleksiyon tutar:

- `observers`-güncelleştirilmiş bilgileri alacak istemciler koleksiyonu.

- `flights`-bir fışıkları ve kendilerine atanan Carousels koleksiyonu.

Her iki koleksiyon da `BaggageHandler` sınıf oluşturucusunda oluşturulan genel <xref:System.Collections.Generic.List%601> nesneleri tarafından temsil edilir. `BaggageHandler` sınıfının kaynak kodu aşağıdaki örnekte gösterilmiştir.

[!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
[!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]

Güncelleştirilmiş bilgileri almak isteyen istemciler `BaggageHandler.Subscribe` yöntemini çağırır. İstemci daha önce bildirimlere abone olduysa, `observers` koleksiyonuna istemcinin <xref:System.IObserver%601> uygulamasına yönelik bir başvuru eklenir.

Aşırı yüklenmiş `BaggageHandler.BaggageStatus` yöntemi, bir uçuşdan Bagaj 'nin kaldırılmakta olduğunu veya artık kaldırılamadığını göstermek için çağrılabilir. İlk durumda, yönteme bir uçuş numarası, uçuşın geldiği Havaalanı ve Bagaj 'nin kaldırılmakta olduğu Carusel ' i geçirilmiş olur. İkinci durumda, yönteme yalnızca bir uçuş numarası geçirilir. Kaldırılmakta olan Bagaj için yöntemi, yönteme geçirilen `BaggageInfo` bilgilerinin `flights` koleksiyonunda var olup olmadığını denetler. Değilse, yöntemi bilgileri ekler ve her bir gözlemci `OnNext` yöntemini çağırır. Bagaj 'nin artık kaldırılmayacağı fışıklarda, yöntemi bu uçuşdaki bilgilerin `flights` koleksiyonunda depolanıp saklanmadığını denetler. Eğer ise, yöntemi her bir gözlemci `OnNext` yöntemini çağırır ve `BaggageInfo` nesnesini `flights` koleksiyonundan kaldırır.

Günün son uçuşası ve Bagaj işlendiğinde `BaggageHandler.LastBaggageClaimed` yöntemi çağrılır. Bu yöntem, tüm bildirimlerin tamamlandığını belirtmek için her bir gözlemci `OnCompleted` yöntemini çağırır ve sonra `observers` koleksiyonunu temizler.

Sağlayıcının <xref:System.IObservable%601.Subscribe%2A> yöntemi, gözlemcilerin 'ın <xref:System.IObserver%601.OnCompleted%2A> yöntemi çağrılmadan önce bildirim almayı durdurmasına olanak tanıyan bir <xref:System.IDisposable> uygulamasını döndürür. Bu `Unsubscriber(Of BaggageInfo)` sınıfı için kaynak kodu aşağıdaki örnekte gösterilmiştir. Sınıf `BaggageHandler.Subscribe` yönteminde örneği oluşturulduğunda, `observers` koleksiyonuna bir başvuru ve koleksiyona eklenen gözlemciye bir başvuru geçirilir. Bu başvurular yerel değişkenlere atanır. Nesnenin `Dispose` yöntemi çağrıldığında, gözlemconun `observers` koleksiyonunda var olup olmadığını denetler ve varsa gözlemci 'yi kaldırır.

[!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
[!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]

Aşağıdaki örnek, Bagaj talep bilgilerini görüntüleyen bir temel sınıf olan `ArrivalsMonitor`adlı <xref:System.IObserver%601> bir uygulama sağlar. Bilgiler, kaynak şehir adına göre alfabetik olarak görüntülenir. `ArrivalsMonitor` yöntemleri `overridable` (Visual Basic) veya `virtual` (içinde C#) olarak işaretlenir, bu nedenle tümü türetilmiş bir sınıf tarafından geçersiz kılınabilir.

[!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
[!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]

`ArrivalsMonitor` sınıfı `Subscribe` ve `Unsubscribe` yöntemlerini içerir. `Subscribe` yöntemi, sınıfının bir özel değişkene <xref:System.IObservable%601.Subscribe%2A> çağrısı tarafından döndürülen <xref:System.IDisposable> uygulamasını kaydetmesine olanak sağlar. `Unsubscribe` yöntemi, sağlayıcının <xref:System.IDisposable.Dispose%2A> uygulamasını çağırarak, sınıfın bildirimlerin aboneliklerini kaldırmaya olanak sağlar. `ArrivalsMonitor` Ayrıca <xref:System.IObserver%601.OnNext%2A>, <xref:System.IObserver%601.OnError%2A>ve <xref:System.IObserver%601.OnCompleted%2A> yöntemlerinin uygulamalarını da sağlar. Yalnızca <xref:System.IObserver%601.OnNext%2A> uygulama önemli miktarda kod içerir. Yöntemi, gelen fışıklara ait kaynak havaalanları ve Bagaj 'nin kullanılabildiği Carousels hakkındaki bilgileri tutan özel, sıralanmış, genel <xref:System.Collections.Generic.List%601> bir nesne ile birlikte çalışıyor. `BaggageHandler` sınıfı yeni bir uçuş gelişini bildirirse, <xref:System.IObserver%601.OnNext%2A> yöntemi uygulama bu uçuş hakkında bilgileri listeye ekler. `BaggageHandler` sınıfı, uçuşın bagamı 'nin kaldırılmıştır bildirirse, <xref:System.IObserver%601.OnNext%2A> yöntemi Bu uçuştan kaldırır. Her değişiklik yapıldığında liste sıralanır ve konsola görüntülenir.

Aşağıdaki örnek, `BaggageHandler` sınıfını ve `ArrivalsMonitor` sınıfının iki örneğini örnekleyen uygulama giriş noktasını içerir ve gelen fışıklarla ilgili bilgileri eklemek ve kaldırmak için `BaggageHandler.BaggageStatus` yöntemini kullanır. Her durumda, gözlemcilerin güncelleştirmeleri alır ve Bagaj talep bilgilerini doğru şekilde görüntüler.

[!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
[!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Gözlemci Tasarım Deseni En İyi Yöntemleri](../../../docs/standard/events/observer-design-pattern-best-practices.md)|Gözlemci tasarım modelini uygulayan uygulamalar geliştirirken benimsemek için en iyi uygulamaları açıklar.|
|[Nasıl yapılır: Sağlayıcıyı Uygulama](../../../docs/standard/events/how-to-implement-a-provider.md)|Bir sıcaklık izleme uygulaması için bir sağlayıcının adım adım uygulamasını sağlar.|
|[Nasıl yapılır: Gözlemci Uygulama](../../../docs/standard/events/how-to-implement-an-observer.md)|Bir ısı izleme uygulaması için gözlemci için adım adım bir uygulama sağlar.|
