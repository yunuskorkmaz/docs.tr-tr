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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06dbc4b7124aa873fd8471794fa25b0f47f8ce3d
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663571"
---
# <a name="observer-design-pattern"></a>Gözlemci Tasarım Deseni

Gözlemci tasarım deseni ile kaydolun ve bir sağlayıcıdan bildirimleri almak abone sağlar. Anında iletme tabanlı bildirim gerektiren her senaryo için uygundur. Deseni tanımlayan bir *sağlayıcısı* (olarak da bilinen bir *konu* veya *observable*) ve sıfır, bir veya daha fazla *gözlemciler*. Gözlemciler sağlayıcıya Kaydol ve önceden tanımlı bir koşul olduğunda, olayı veya durumu değişikliği, sağlayıcı tüm gözlemciler kendi yöntemlerini çağıran bir tarafından otomatik olarak bildirir. oluşur. Bu yöntem çağrısında sağlayıcı gözlemciler için geçerli durum bilgilerini de sağlayabilirsiniz. .NET Framework'teki genel uygulayarak gözlemci tasarım deseni uygulanan <xref:System.IObservable%601?displayProperty=nameWithType> ve <xref:System.IObserver%601?displayProperty=nameWithType> arabirimleri. Genel tür parametresi bildirimi bilgi sağlayan türünü temsil eder.

## <a name="applying-the-pattern"></a>Desenini uygulama

Gözlemci tasarım deseni iki farklı bileşenler veya bir veri kaynağı (iş mantığı) katmanı ve bir kullanıcı arabirimi (görüntüleme) katmanı gibi uygulama katmanları arasında NET bir ayrım desteklediğinden, dağıtılmış tabanlı anında iletme bildirimleri için uygundur. Sağlayıcı güncel bilgilerle, istemcileri sağlamak için geri çağırmaları kullandığında deseni uygulanabilir.

Desenini uygulama aşağıdakileri sağlamanız gerekir:

- Bir sağlayıcı veya gözlemciler için bildirimler gönderir bir nesne olan konu. Bir sınıf veya yapı uygulayan bir sağlayıcıdır <xref:System.IObservable%601> arabirimi. Sağlayıcı, tek bir yöntem uygulamalıdır <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>, sağlayıcıdan bildirim almak istediğiniz gözlemciler tarafından çağrılır.

- Bir sağlayıcıdan bildirimleri alan bir nesne olan bir gözlemci. Bir sınıf veya yapı uygulayan ise bir gözlemci <xref:System.IObserver%601> arabirimi. Gözlemci, her biri sağlayıcı tarafından çağrılır, üç yöntem uygulaması gerekir:

  - <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, gözlemci yeni veya geçerli bilgileri sağlar.

  - <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, bir hata oluştu gözlemci bildirir.

  - <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, sağlayıcı bildirimleri gönderme işleminin tamamlandığını gösterir.

- Sağlayıcı gözlemciler izlemenize olanak tanıyan bir mekanizma. Genellikle sağlayıcısı gibi bir kapsayıcı nesnesini kullanan bir <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> başvuruları tutmak için nesne <xref:System.IObserver%601> bildirimlerine abone uygulamalar. Bu amaç için bir depolama kapsayıcısı kullanarak sınırsız sayıda gözlemciler sıfıra işlemek sağlayıcı sağlar. Gözlemciler bildirimleri aldıkları sırası tanımlı değildir; Sağlayıcı sırayı belirlemek için herhangi bir yöntem ücretsiz olarak kullanılabilir.

- Bir <xref:System.IDisposable> bildirim tamamlandığında gözlemciler kaldırmak sağlayıcı sağlayan uygulama. Gözlemciler bir başvuru alma <xref:System.IDisposable> uygulamasından <xref:System.IObservable%601.Subscribe%2A> ayrıca çağırabilmek yöntemi <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> sağlayıcısı bildirimleri gönderme bitmeden önce aboneliğinizi iptal etmek için yöntemi.

- Sağlayıcı için kendi gözlemciler gönderdiği veriler içeren bir nesne. Bu nesne türü genel tür parametresine karşılık geldiği <xref:System.IObservable%601> ve <xref:System.IObserver%601> arabirimleri. Bu nesne ile aynı olsa da <xref:System.IObservable%601> uygulama, ayrı bir tür olduğu en yaygın olarak.

> [!NOTE]
> Gözlemci tasarım deseni uygulama yanı sıra, kullanılarak oluşturulan kitaplıkları keşfetmeye de ilginizi çekebilir <xref:System.IObservable%601> ve <xref:System.IObserver%601> arabirimleri. Örneğin, [.NET (Rx) için reaktif Uzantılar](https://docs.microsoft.com/previous-versions/dotnet/reactive-extensions/hh242985(v=vs.103)) uzantı yöntemleri ve zaman uyumsuz programlamayı desteklemek için LINQ standart dizisi işleçleri kümesinden oluşur.

## <a name="implementing-the-pattern"></a>Desenini uygulama

Aşağıdaki örnek, bir Havalimanı bagaj talep bilgi sistemi uygulamak için gözlemci tasarım deseni kullanır. A `BaggageInfo` sınıfı ve her uçuş gelen bagaj kullanılabildiği için alımı görüntülendiği döngüler yer gelen uçuşlar hakkında bilgi sağlar. Aşağıdaki örnekte gösterilmektedir.

[!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
[!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]

A `BaggageHandler` sınıfı hakkında gelen uçuşlar ve bagaj talep görüntülendiği döngüler yer bilgi almak için sorumlu. Dahili olarak, iki koleksiyon tutar:

- `observers` -Bir koleksiyonu alacak olan istemcileri bilgiler güncelleştirilmiştir.

- `flights` -Uçuş ve otelden kendi atanan görüntülendiği döngüler yer bir koleksiyonu.

Her iki koleksiyon genel tarafından temsil edilen <xref:System.Collections.Generic.List%601> içinde örneklenen nesneleri `BaggageHandler` sınıf oluşturucusu. Kaynak kodu `BaggageHandler` sınıfı, aşağıdaki örnekte gösterilmiştir.

[!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
[!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]

Güncelleştirilmiş bilgileri almak istiyorsanız istemciler çağrı `BaggageHandler.Subscribe` yöntemi. İstemci daha önce bildirimleri, istemcinin bir başvuru abone değil, <xref:System.IObserver%601> uygulaması eklenir `observers` koleksiyonu.

Aşırı yüklenen `BaggageHandler.BaggageStatus` yöntemi, bir uçuştaki gelen bagaj boşaltılıyor veya artık boşaltılıyor göstermek için çağrılabilir. Bu durumda, yöntem uçuş numarası, uçuş kaynaklandığı havaalanı ve döngüsü bagaj burada boşaltılıyor geçirilir. İkinci durumda, yalnızca uçuş birkaç yöntemi geçirilir. Yüklenmekte olan bagaj için kaldırıldığında, yöntemi denetimleri olup `BaggageInfo` yönteme bilgi bulunmaktadır `flights` koleksiyonu. Kullanmıyorsa, yöntem bilgileri ekler ve her gözlemci'nın çağıran `OnNext` yöntemi. Bu uçuş hakkında bilgi içinde mi depolanacağını yöntemi olan bagaj artık boşaltılıyor uçuşlar için denetler `flights` koleksiyonu. İse, her bir gözlemci 's yöntemi çağıran `OnNext` yöntemi ve kaldırır `BaggageInfo` nesnesinden `flights` koleksiyonu.

Günün son uçuş aldı ve kendi bagaj işlendiğinde `BaggageHandler.LastBaggageClaimed` yöntemi çağrılır. Bu yöntem her gözlemci 's çağırır `OnCompleted` tüm bildirimler tamamlandığını göstermek için yöntem ve sonra temizler `observers` koleksiyonu.

Sağlayıcının <xref:System.IObservable%601.Subscribe%2A> yöntemi döndürür bir <xref:System.IDisposable> önce bildirim almayı durdurmak gözlemciler sağlayan uygulama <xref:System.IObserver%601.OnCompleted%2A> yöntemi çağrılır. Bu kaynak kodu `Unsubscriber(Of BaggageInfo)` sınıfı, aşağıdaki örnekte gösterilmiştir. Sınıfı oluşturulduğunda `BaggageHandler.Subscribe` yöntemi, bir başvuru geçirilir `observers` toplama ve koleksiyona eklendiğinde gözlemci başvuru. Bu başvurular, yerel değişkenlere atanır. Zaman nesnenin `Dispose` yöntemi çağrıldığında, gözlemci hala var olup olmadığını denetler `observers` koleksiyonu ve aşması durumunda gözlemci kaldırır.

[!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
[!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]

Aşağıdaki örnek sağlayan bir <xref:System.IObserver%601> adlı uygulama `ArrivalsMonitor`, bagaj talep bilgilerini görüntüleyen bir temel sınıf. Bilgiler, kaynak şehri adına göre alfabetik olarak görüntülenir. Yöntemlerinin `ArrivalsMonitor` olarak işaretlenmiş `overridable` (Visual Basic'te) veya `virtual` (içinde C#), bunlar tüm türetilmiş sınıf tarafından geçersiz kılınabilir.

[!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
[!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]

`ArrivalsMonitor` Sınıfı içeren `Subscribe` ve `Unsubscribe` yöntemleri. `Subscribe` Yöntemi sağlar sınıfını kaydetmek <xref:System.IDisposable> çağrısı tarafından döndürülen uygulama <xref:System.IObservable%601.Subscribe%2A> özel bir değişken için. `Unsubscribe` Sınıfı sağlayıcının çağırarak bildirim aboneliği için yöntemi etkinleştirir <xref:System.IDisposable.Dispose%2A> uygulaması. `ArrivalsMonitor` Ayrıca uygulamaları sağlar <xref:System.IObserver%601.OnNext%2A>, <xref:System.IObserver%601.OnError%2A>, ve <xref:System.IObserver%601.OnCompleted%2A> yöntemleri. Yalnızca <xref:System.IObserver%601.OnNext%2A> uygulaması, önemli miktarda kod içerir. Yöntem ile özel, sıralanmış, genel çalışır <xref:System.Collections.Generic.List%601> gelen uçuşlar için kaynak havaalanları hakkında bilgileri tutan nesne ve bunların bagaj olduğu kullanılabilir görüntülendiği döngüler yer. Varsa `BaggageHandler` sınıfı raporlar yeni bir uçuş varış <xref:System.IObserver%601.OnNext%2A> yöntem uygulaması, uçuş bilgilerini listesine ekler. Varsa `BaggageHandler` sınıfı raporlar flight'ın bagaj kaldırıldı, olduğunu <xref:System.IObserver%601.OnNext%2A> yöntemi, uçuş listeden kaldırır. Bir değişiklik yapıldığında, listesi sıralanır ve konsola görüntülenir.

Aşağıdaki örnek başlatan uygulamanın giriş noktasını içeren `BaggageHandler` sınıfı iki örneğini yanı sıra `ArrivalsMonitor` sınıfı ve kullandığı `BaggageHandler.BaggageStatus` ekleme ve kaldırma gelen uçuşlar hakkında bilgi için yöntemi. Her durumda, gözlemciler güncelleştirmeleri almak ve doğru şekilde bagaj talep bilgilerini görüntüler.

[!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
[!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Gözlemci Tasarım Deseni En İyi Yöntemleri](../../../docs/standard/events/observer-design-pattern-best-practices.md)|Gözlemci tasarım deseni kullanan uygulamalar geliştirirken benimsemek için en iyi uygulamaları açıklar.|
|[Nasıl yapılır: Sağlayıcıyı uygulama](../../../docs/standard/events/how-to-implement-a-provider.md)|Uygulama izleme bir sıcaklık için Sağlayıcı'nın adım adım bir uygulamasını sağlar.|
|[Nasıl yapılır: Gözlemci uygulama](../../../docs/standard/events/how-to-implement-an-observer.md)|Bir adım adım bir gözlemci uygulama izleme bir sıcaklık için sağlar.|
