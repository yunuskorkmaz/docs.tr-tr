---
title: Gözlemci Tasarım Deseni
description: .NET 'teki gözlemci tasarım düzeniyle ilgili bilgi edinin. Bu model, bir abonenin ile kaydolmasına ve bir sağlayıcıdan bildirimler almasına olanak tanır.
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
ms.openlocfilehash: 4edcd2645b28095f4bd18f4918b9afa5c893bd39
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662738"
---
# <a name="observer-design-pattern"></a>Gözlemci Tasarım Deseni

Gözlemci tasarım deseninin bir abone ile kaydolmalarını ve bir sağlayıcıdan gelen bildirimleri almasını sağlar. Gönderim tabanlı bildirim gerektiren tüm senaryolar için uygundur. Bu model, bir *sağlayıcıyı* ( *Konu* veya *observable*olarak da bilinir) ve sıfır, bir veya daha fazla *gözlemcilerin*tanımlar. Gözlemcilerin sağlayıcıya kaydoldu ve önceden tanımlanmış bir koşul, olay veya durum değişikliği gerçekleştiğinde sağlayıcı, yöntemlerinden birini çağırarak tüm gözlemcilerin 'ı otomatik olarak bilgilendirir. Bu yöntem çağrısında sağlayıcı, güncel durum bilgilerini observers 'a de verebilir. .NET Framework, gözlemci tasarım deseninin genel ve arabirimler uygulanarak uygulanması gerekir <xref:System.IObservable%601?displayProperty=nameWithType> <xref:System.IObserver%601?displayProperty=nameWithType> . Genel tür parametresi, bildirim bilgilerini sağlayan türü temsil eder.

## <a name="applying-the-pattern"></a>Desenler uygulanıyor

Bir veri kaynağı (iş mantığı) katmanı ve Kullanıcı arabirimi (görüntü) katmanı gibi iki farklı bileşen veya uygulama katmanı arasında temiz ayrımı desteklediğinden, gözlemci tasarım deseninin dağıtılan gönderim tabanlı bildirimler için uygun olması gerekir. Bir sağlayıcı, istemcilerini geçerli bilgilerle sağlamak için geri çağırmaları kullandığında, bu model uygulanabilir.

Düzenin uygulanması için şunları sağlamanız gerekir:

- Gözlemi sunucularına bildirim gönderen nesnesi olan bir sağlayıcı veya konu. Sağlayıcı, arabirimini uygulayan bir sınıf veya yapıdır <xref:System.IObservable%601> . Sağlayıcı, <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> sağlayıcıdan bildirim almak isteyen gözlemcilerin tarafından çağrılan tek bir yöntemi uygulamalıdır.

- Sağlayıcıdan gelen bildirimleri alan bir nesne olan gözlemci. Gözlemci, arabirimini uygulayan bir sınıf veya yapıdır <xref:System.IObserver%601> . Gözlemci, hepsi sağlayıcı tarafından çağrılan üç yöntemi gerçekleştirmelidir:

  - <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>Yeni veya güncel bilgilerle gözlemci sağlar.

  - <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, gözlemci bir hata oluştuğunu bilgilendirir.

  - <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, sağlayıcının bildirimleri göndermeyi bitirdiğini gösterir.

- Sağlayıcının observers 'ı izlemesine izin veren bir mekanizma. Genellikle, sağlayıcı, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> bildirimlere abone olan uygulamalara başvuruları tutmak için nesnesi gibi bir kapsayıcı nesnesi kullanır <xref:System.IObserver%601> . Bu amaçla bir depolama kapsayıcısı kullanmak, sağlayıcının sınırsız sayıda Observer 'a sıfır işlemesini sağlar. Gözlemcilerin 'ın bildirim alma sırası tanımlı değil; sağlayıcı, siparişi belirlemede herhangi bir yöntemi kullanmak ücretsizdir.

- <xref:System.IDisposable>Sağlayıcının, bildirim tamamlandığında gözlemcilerin 'ı kaldırmasını sağlayan bir uygulama. Observers, yönteminden uygulamaya bir başvuru alır <xref:System.IDisposable> , bu <xref:System.IObservable%601.Subscribe%2A> nedenle <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> sağlayıcının bildirimleri göndermeden önce aboneliğini kaldırmak için yöntemini çağırabilir.

- Sağlayıcının observers 'a gönderdiği verileri içeren bir nesne. Bu nesnenin türü, ve arabirimlerinin genel tür parametresine karşılık gelir <xref:System.IObservable%601> <xref:System.IObserver%601> . Bu nesne uygulamayla aynı olsa da <xref:System.IObservable%601> , genellikle ayrı bir tür olur.

> [!NOTE]
> Gözlemci tasarım deseninin yanı sıra, ve arabirimleri kullanılarak oluşturulan kitaplıkları keşfetmek isteyebilirsiniz <xref:System.IObservable%601> <xref:System.IObserver%601> . Örneğin, [.net Için reaktif uzantıları (RX)](https://docs.microsoft.com/previous-versions/dotnet/reactive-extensions/hh242985(v=vs.103)) , zaman uyumsuz programlamayı desteklemek için bir dizi genişletme YÖNTEMINDEN ve LINQ standart dizisi işleçlerinden oluşur.

## <a name="implementing-the-pattern"></a>Kalıbı uygulama

Aşağıdaki örnekte, bir Havaalanı Bagaj talep bilgileri sistemi uygulamak için gözlemci tasarım deseninin kullanımı vardır. Bir `BaggageInfo` sınıf, gelen fışıklara ve her bir uçuşdan Bagaj 'nin çekme için kullanılabildiği Carousels hakkında bilgi sağlar. Aşağıdaki örnekte gösterilmiştir.

[!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
[!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]

Bir `BaggageHandler` sınıf, gelen fışıkları ve Bagaj talebi Carousels hakkında bilgi almaktan sorumludur. Dahili olarak, iki koleksiyon tutar:

- `observers`-Güncelleştirilmiş bilgileri alacak istemciler koleksiyonu.

- `flights`-Bir fışıkları ve atanan Carousels koleksiyonu.

Her iki koleksiyon <xref:System.Collections.Generic.List%601> da sınıf oluşturucusunda oluşturulan genel nesneler tarafından temsil edilir `BaggageHandler` . Sınıfının kaynak kodu `BaggageHandler` Aşağıdaki örnekte gösterilmiştir.

[!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
[!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]

Güncelleştirilmiş bilgileri almak isteyen istemciler `BaggageHandler.Subscribe` yöntemini çağırır. İstemci daha önce bildirimlere abone olduysa, koleksiyona istemci uygulamasına bir başvuru <xref:System.IObserver%601> eklenir `observers` .

Aşırı yüklenmiş `BaggageHandler.BaggageStatus` Yöntem, bir uçuşdan Bagaj 'nin kaldırılmakta olduğunu veya artık kaldırılamadığını göstermek için çağrılabilir. İlk durumda, yönteme bir uçuş numarası, uçuşın geldiği Havaalanı ve Bagaj 'nin kaldırılmakta olduğu Carusel ' i geçirilmiş olur. İkinci durumda, yönteme yalnızca bir uçuş numarası geçirilir. Kaldırılmakta olan Bagaj için yöntemi, `BaggageInfo` yönteme geçirilen bilgilerin koleksiyonda mevcut olup olmadığını denetler `flights` . Değilse, yöntemi bilgileri ekler ve her bir gözlemci `OnNext` yöntemini çağırır. Bagaj 'nin artık kaldırılmayacağı fışıklarda, yöntemi bu uçuşdaki bilgilerin koleksiyonda depolanıp saklanmadığını denetler `flights` . Eğer ise, yöntemi her bir gözlemci yöntemini çağırır `OnNext` ve `BaggageInfo` nesneyi `flights` koleksiyondan kaldırır.

Günün son uçuşası ve Bagaj işlendiğinde, `BaggageHandler.LastBaggageClaimed` yöntemi çağrılır. Bu yöntem `OnCompleted` , tüm bildirimlerin tamamlandığını göstermek için her bir gözlemci yöntemini çağırır ve sonra `observers` koleksiyonu temizler.

Sağlayıcının <xref:System.IObservable%601.Subscribe%2A> yöntemi <xref:System.IDisposable> , gözlemcilerin 'ın Yöntem çağrılmadan önce bildirim almayı durdurmasına olanak tanıyan bir uygulama döndürür <xref:System.IObserver%601.OnCompleted%2A> . Bu sınıfın kaynak kodu `Unsubscriber(Of BaggageInfo)` Aşağıdaki örnekte gösterilmiştir. Sınıfında sınıf örneği oluşturulduğunda `BaggageHandler.Subscribe` , koleksiyona bir başvuru `observers` ve koleksiyona eklenen gözlemci başvurusu geçirilir. Bu başvurular yerel değişkenlere atanır. Nesnenin `Dispose` yöntemi çağrıldığında, gözlemciye hala koleksiyonda mevcut olup olmadığını denetler `observers` ve varsa, gözlemci 'yi kaldırır.

[!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
[!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]

Aşağıdaki örnek <xref:System.IObserver%601> adlı `ArrivalsMonitor` , Bagaj talep bilgilerini görüntüleyen bir temel sınıf olan adlı bir uygulama sağlar. Bilgiler, kaynak şehir adına göre alfabetik olarak görüntülenir. Yöntemleri, `ArrivalsMonitor` `overridable` (Visual Basic) veya `virtual` (C# ' de) olarak işaretlenir, bu nedenle tümü türetilmiş bir sınıf tarafından geçersiz kılınabilir.

[!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
[!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]

`ArrivalsMonitor`Sınıfı `Subscribe` ve `Unsubscribe` yöntemlerini içerir. `Subscribe`Yöntemi, sınıfının <xref:System.IDisposable> çağrısı tarafından döndürülen uygulamayı <xref:System.IObservable%601.Subscribe%2A> özel bir değişkene kaydetmesine olanak sağlar. `Unsubscribe`Yöntemi, sağlayıcının uygulamasını çağırarak, sınıfının bildirimlerden aboneliklerini kaldırma yapmasına olanak sağlar <xref:System.IDisposable.Dispose%2A> . `ArrivalsMonitor`,, ve yöntemlerinin uygulamalarını da sağlar <xref:System.IObserver%601.OnNext%2A> <xref:System.IObserver%601.OnError%2A> <xref:System.IObserver%601.OnCompleted%2A> . Yalnızca <xref:System.IObserver%601.OnNext%2A> uygulama önemli miktarda kod içerir. Yöntemi, <xref:System.Collections.Generic.List%601> gelen fışıklara ait kaynak havaalanları ve Bagaj 'nin kullanılabildiği Carousels hakkındaki bilgileri tutan özel, sıralanmış, genel bir nesne ile birlikte çalışıyor. `BaggageHandler`Sınıf yeni bir uçuş gelişini bildirirse, <xref:System.IObserver%601.OnNext%2A> Yöntem uygulama bu uçuş hakkındaki bilgileri listeye ekler. Sınıf, `BaggageHandler` uçuşın Bagaj 'nin kaldırılmış olduğunu bildirirse, <xref:System.IObserver%601.OnNext%2A> yöntemi listeden bu uçuşı kaldırır. Her değişiklik yapıldığında liste sıralanır ve konsola görüntülenir.

Aşağıdaki örnek, sınıfının ve sınıfının iki örneğinin örneğini oluşturan uygulama giriş noktasını içerir `BaggageHandler` `ArrivalsMonitor` ve `BaggageHandler.BaggageStatus` gelen fışıklarla ilgili bilgileri eklemek ve kaldırmak için yöntemini kullanır. Her durumda, gözlemcilerin güncelleştirmeleri alır ve Bagaj talep bilgilerini doğru şekilde görüntüler.

[!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
[!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Gözlemci Tasarım Deseni En İyi Yöntemleri](observer-design-pattern-best-practices.md)|Gözlemci tasarım modelini uygulayan uygulamalar geliştirirken benimsemek için en iyi uygulamaları açıklar.|
|[Nasıl yapılır: sağlayıcı uygulama](how-to-implement-a-provider.md)|Bir sıcaklık izleme uygulaması için bir sağlayıcının adım adım uygulamasını sağlar.|
|[Nasıl yapılır: gözlemci uygulama](how-to-implement-an-observer.md)|Bir ısı izleme uygulaması için gözlemci için adım adım bir uygulama sağlar.|
