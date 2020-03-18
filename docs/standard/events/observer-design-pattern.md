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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131570"
---
# <a name="observer-design-pattern"></a>Gözlemci Tasarım Deseni

Gözlemci tasarım deseni, abonenin bir sağlayıcıya kaydolmasını ve bildirimlerini almasını sağlar. Anında iletme tabanlı bildirim gerektiren tüm senaryolar için uygundur. Desen bir *sağlayıcı* (nesne *veya* *gözlemlenebilir*olarak da bilinir) ve sıfır, bir veya daha fazla *gözlemci*tanımlar. Gözlemciler sağlayıcıya kaydolur ve önceden tanımlanmış bir koşul, olay veya durum değişikliği olduğunda, sağlayıcı tüm gözlemcileri yöntemlerinden birini arayarak otomatik olarak bilgi edinir. Bu yöntem çağrısında, sağlayıcı gözlemcilere geçerli durum bilgilerini de sağlayabilir. .NET Framework'de, genel <xref:System.IObservable%601?displayProperty=nameWithType> ve <xref:System.IObserver%601?displayProperty=nameWithType> arabirimler uygulanarak gözlemci tasarım deseni uygulanır. Genel tür parametresi, bildirim bilgileri sağlayan türü temsil eder.

## <a name="applying-the-pattern"></a>Deseni Uygulama

Gözlemci tasarım deseni dağıtılmış anında iletme tabanlı bildirimler için uygundur, çünkü veri kaynağı (iş mantığı) katmanı ve kullanıcı arabirimi (ekran) katmanı gibi iki farklı bileşen veya uygulama katmanı arasında temiz bir ayrımı destekler. Desen, bir sağlayıcı müşterilerine geçerli bilgileri sağlamak için geri aramalar kullandığında uygulanabilir.

Deseni uygulamak için aşağıdakileri sağlamanız gerekmektedir:

- Gözlemcilere bildirim gönderen nesne olan sağlayıcı veya özne. Sağlayıcı, <xref:System.IObservable%601> arabirimi uygulayan bir sınıf veya yapıdır. Sağlayıcı, <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>sağlayıcıdan bildirim almak isteyen gözlemciler tarafından çağrılan tek bir yöntem uygulamalıdır.

- Bir sağlayıcıdan bildirim alan bir nesne olan bir gözlemci. Gözlemci, <xref:System.IObserver%601> arabirimi uygulayan bir sınıf veya yapıdır. Gözlemci, hepsi sağlayıcı tarafından çağrılan üç yöntem uygulamalıdır:

  - <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, gözlemciye yeni veya güncel bilgiler sağlar.

  - <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, gözlemciye bir hata oluştuğunu bildirir.

  - <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, sağlayıcının bildirim göndermeyi tamamladığını gösterir.

- Sağlayıcının gözlemcileri takip etmesini sağlayan bir mekanizma. Genellikle, sağlayıcı bildirimlere abone olan <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> <xref:System.IObserver%601> uygulamalara başvuru tutmak için nesne gibi bir kapsayıcı nesnesi kullanır. Bu amaçla bir depolama kapsayıcısı kullanmak, sağlayıcının sıfırile sınırsız sayıda gözlemciyi işlemesini sağlar. Gözlemcilerin bildirim alma sırası tanımlanmaz; sağlayıcı siparişi belirlemek için herhangi bir yöntem kullanmakta serbesttir.

- Bildirim <xref:System.IDisposable> tamamlandığında sağlayıcının gözlemcileri kaldırmasını sağlayan bir uygulama. Gözlemciler <xref:System.IDisposable> <xref:System.IObservable%601.Subscribe%2A> yöntemden uygulamaya bir referans alırlar, böylece sağlayıcı <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> bildirim göndermeyi tamamlamadan önce aboneliği iptal etme yöntemini de arayabilirler.

- Sağlayıcının gözlemcilerine gönderdiği verileri içeren bir nesne. Bu nesnenin türü, <xref:System.IObservable%601> <xref:System.IObserver%601> arabirimlerin genel tür parametresine karşılık gelir. Bu nesne <xref:System.IObservable%601> uygulamayla aynı olabilir, ancak en sık ayrı bir türdür.

> [!NOTE]
> Gözlemci tasarım deseni uygulamanın yanı sıra, ve <xref:System.IObservable%601> <xref:System.IObserver%601> arayüzler kullanılarak oluşturulmuş kitaplıkları keşfetmek ilginizi çekebilir. Örneğin, [.NET (Rx) için Reaktif Uzantılar,](https://docs.microsoft.com/previous-versions/dotnet/reactive-extensions/hh242985(v=vs.103)) eşzamanlı programlamayı desteklemek için bir dizi uzantı yöntemi ve LINQ standart sıra işleçlerinden oluşur.

## <a name="implementing-the-pattern"></a>Desenin Uygulanması

Aşağıdaki örnek, bir havaalanı bagaj talep bilgi sistemini uygulamak için gözlemci tasarım modelini kullanır. Bir `BaggageInfo` sınıf, gelen uçuşlar ve her uçuştan bagaj almak için kullanılabilir olan atlıkarıncalar hakkında bilgi sağlar. Aşağıdaki örnekte gösterilmiştir.

[!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
[!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]

Bir `BaggageHandler` sınıf gelen uçuşlar ve bagaj talep atlıkarıncaları hakkında bilgi almaktan sorumludur. Dahili olarak, iki koleksiyon tutar:

- `observers`- Güncel bilgiler alacak istemciler topluluğu.

- `flights`- Uçuşlar ve atanan atlıkarıncalar koleksiyonu.

Her iki koleksiyon da <xref:System.Collections.Generic.List%601> `BaggageHandler` sınıf oluşturucusunda anında bulunan genel nesnelerle temsil edilir. `BaggageHandler` Sınıfın kaynak kodu aşağıdaki örnekte gösterilmiştir.

[!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
[!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]

Güncelleştirilmiş bilgi almak isteyen `BaggageHandler.Subscribe` istemciler yöntemi arar. İstemci bildirimlere daha önce abone olmadıysa, istemcinin <xref:System.IObserver%601> uygulamasına bir `observers` başvuru koleksiyona eklenir.

Aşırı yükleme `BaggageHandler.BaggageStatus` yöntemi, bir uçuştaki bagajın boşaltıldığını veya artık boşaltılmamadığını belirtmek için çağrılabilir. İlk durumda, yöntem bir uçuş numarası, uçuşun geldiği havaalanı ve bagajın boşaltıldığı atlıkarınca dan geçirilir. İkinci durumda, yöntem yalnızca bir uçuş numarası geçirilir. Boşaltılan bagajlar için yöntem, yönteme `BaggageInfo` aktarılan bilgilerin koleksiyonda `flights` bulunup bulunmadığını kontrol eder. Değilse, yöntem bilgileri ekler ve her gözlemcinin `OnNext` yöntemini çağırır. Bagajı artık boşaltılamayan uçuşlarda yöntem, o uçuşla ilgili bilgilerin `flights` koleksiyonda depolanıp saklanmadığını kontrol eder. Bu ysa, yöntem her gözlemcinin `OnNext` yöntemini çağırır `BaggageInfo` ve `flights` nesneyi koleksiyondan kaldırır.

Günün son uçuşu indiğinde ve bagajı işlendiğinde, `BaggageHandler.LastBaggageClaimed` yönteme denir. Bu yöntem, tüm `OnCompleted` bildirimlerin tamamlandığını belirtmek için her gözlemcinin `observers` yöntemini çağırır ve sonra koleksiyonu temizler.

Sağlayıcının <xref:System.IObservable%601.Subscribe%2A> yöntemi, gözlemcilerin <xref:System.IDisposable> <xref:System.IObserver%601.OnCompleted%2A> yöntem çağrılmadan önce bildirim almayı durdurmasını sağlayan bir uygulama döndürür. Bu `Unsubscriber(Of BaggageInfo)` sınıfın kaynak kodu aşağıdaki örnekte gösterilmiştir. Sınıf `BaggageHandler.Subscribe` yöntemde anında olduğunda, `observers` koleksiyona bir başvuru ve koleksiyona eklenen gözlemciye bir başvuru aktarılır. Bu başvurular yerel değişkenlere atanır. Nesnenin `Dispose` yöntemi çağrıldığında, gözlemcinin `observers` koleksiyonda hala var olup olmadığını denetler ve varsa gözlemciyi kaldırır.

[!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
[!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]

Aşağıdaki örnek, <xref:System.IObserver%601> bagaj `ArrivalsMonitor`talep bilgilerini görüntüleyen bir taban sınıf olan "adlı" bir uygulama sağlar. Bilgiler alfabetik olarak, kaynak şehir adı ile görüntülenir. Yöntemleri (Visual Basic' veya `ArrivalsMonitor` `overridable` `virtual` (C#'da) olarak işaretlenir, böylece bunların tümü türemiş bir sınıf tarafından geçersiz kılınabilir.

[!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
[!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]

Sınıf `ArrivalsMonitor` `Subscribe` ve `Unsubscribe` yöntemleri içerir. Yöntem, `Subscribe` sınıfın çağrıyla özel <xref:System.IDisposable> bir değişkene <xref:System.IObservable%601.Subscribe%2A> döndürülen uygulamayı kaydetmesini sağlar. Yöntem, `Unsubscribe` sağlayıcının <xref:System.IDisposable.Dispose%2A> uygulamasını arayarak sınıfın bildirimlerden aboneliğini iptal etmesini sağlar. `ArrivalsMonitor`ayrıca , <xref:System.IObserver%601.OnNext%2A>, <xref:System.IObserver%601.OnError%2A>ve <xref:System.IObserver%601.OnCompleted%2A> yöntemlerinin uygulamalarını sağlar. Yalnızca <xref:System.IObserver%601.OnNext%2A> uygulama önemli miktarda kod içerir. Bu yöntem, gelen uçuşlar ve <xref:System.Collections.Generic.List%601> bagajlarının bulunduğu atlıkarıncalar için menşe havaalanları hakkında bilgi tutan özel, sıralanmış, genel bir nesneyle çalışır. `BaggageHandler` Sınıf yeni bir uçuş gelişi <xref:System.IObserver%601.OnNext%2A> rapor ederse, yöntem uygulaması listeye bu uçuş hakkında bilgi ekler. `BaggageHandler` Sınıf, uçuşun bagajının boşaltıldığını bildirirse, <xref:System.IObserver%601.OnNext%2A> yöntem bu uçuşu listeden kaldırır. Değişiklik yapıldığında, liste sıralanır ve konsola görüntülenir.

Aşağıdaki örnek, `BaggageHandler` sınıfın iki örneğinin `ArrivalsMonitor` yanı sıra sınıfı anlık olarak anlabilen ve `BaggageHandler.BaggageStatus` gelen uçuşlar la ilgili bilgileri eklemek ve kaldırmak için yöntemi kullanan uygulama giriş noktasını içerir. Her durumda, gözlemciler güncellemeleri alır ve bagaj talep bilgilerini doğru bir şekilde görüntüler.

[!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
[!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Gözlemci Tasarım Deseni En İyi Yöntemleri](../../../docs/standard/events/observer-design-pattern-best-practices.md)|Gözlemci tasarım deseni uygulayan uygulamalar geliştirirken benimsenmesi gereken en iyi uygulamaları açıklar.|
|[Nasıl yapılır: Sağlayıcıyı Uygulama](../../../docs/standard/events/how-to-implement-a-provider.md)|Sıcaklık izleme uygulaması için bir sağlayıcının adım adım uygulanmasını sağlar.|
|[Nasıl yapılır: Gözlemci Uygulama](../../../docs/standard/events/how-to-implement-an-observer.md)|Sıcaklık izleme uygulaması için bir gözlemcinin adım adım uygulanmasını sağlar.|
