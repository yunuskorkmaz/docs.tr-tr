---
title: "Gözlemci Tasarım Deseni"
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
- IObserver(Of T) interface
- IObservable<T> interface
- IObserver<T> interface
- IObservable(Of T) interface
- observer design pattern [.NET Framework]
ms.assetid: 3680171f-f522-453c-aa4a-54f755a78f88
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1650365946797e4c352421d0196b3b0e17913456
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="observer-design-pattern"></a>Gözlemci Tasarım Deseni
Gözlemci tasarım deseni ile kaydetmek ve bir sağlayıcıdan bildirimleri almak abone sağlar. Gönderim tabanlı bildirim gerektiren her senaryo için uygundur. Deseni tanımlayan bir *sağlayıcı* (olarak da bilinen bir *konu* veya bir *observable*) ve sıfır, bir veya daha fazla *gözlemcilerin*. Sağlayıcının gözlemcilerin kaydı ve önceden tanımlı bir koşul olduğunda, olay veya durum değişikliği, sağlayıcı, tüm gözlemcilerin otomatik olarak kendi yöntemlerini çağıran biri tarafından size bildirir. oluşur. Bu yöntem çağrısı sağlayıcı gözlemcilerin için geçerli durum bilgisini de sağlayabilirsiniz. .NET Framework'teki genel uygulayarak gözlemci tasarım deseni uygulanan <xref:System.IObservable%601?displayProperty=nameWithType> ve <xref:System.IObserver%601?displayProperty=nameWithType> arabirimleri. Genel tür parametresi, bildirimi bilgi sağlayan türünü temsil eder.  
  
## <a name="applying-the-pattern"></a>Düzeni uygulama  
 İki farklı bileşenler veya bir veri kaynağı (iş mantığı) katmanı ve bir kullanıcı arabirimi (Görüntüle) katmanı gibi uygulama katmanları arasında temiz bir ayrım desteklediğinden gözlemci tasarım deseni dağıtılmış gönderme temelli bildirimleri için uygundur. Bir sağlayıcı, istemcilere geçerli bilgileri sağlamak için geri çağırmaları kullandığında düzeni uygulanabilir.  
  
 Düzeni uygulama aşağıdakileri sağlamak gerektirir:  
  
-   Bir sağlayıcı veya gözlemcilerin için bildirimleri gönderen nesne konu. Bir sınıf veya uygulayan yapısı sağlayıcısıdır <xref:System.IObservable%601> arabirimi. Sağlayıcı tek bir yöntem uygulamalıdır <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>, bildirimleri sağlayıcıdan almak istediğiniz gözlemcilerin tarafından çağrılır.  
  
-   Bir sağlayıcıdan bildirimleri alan bir nesne olan bir gözlemci. Bir sınıf veya uygulayan yapısı bir gözlemci olduğu <xref:System.IObserver%601> arabirimi. Gözlemci üç yöntem, her biri sağlayıcı tarafından adlı uygulamanız gerekir:  
  
    -   <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, mevcut veya yeni bilgilerle gözlemci sağlar.  
  
    -   <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, bir hata oluştu gözlemci sizi bilgilendirir.  
  
    -   <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, sağlayıcı bildirimleri gönderme tamamladığını gösterir.  
  
-   Gözlemcilerin izlemek sağlayıcı izin mekanizması. Genellikle, sağlayıcı bir kapsayıcı nesne gibi kullanan bir <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> başvuruları tutmak için nesne <xref:System.IObserver%601> bildirimlerine abone olan uygulamalar. Bu amaç için bir depolama kapsayıcısı kullanarak gözlemcilerin sınırsız sayıda sıfıra işlemek sağlayıcıyı etkinleştirir. Gözlemcilerin bildirimleri alma sırasını tanımlı değil; Sağlayıcı sırayı belirlemek için herhangi bir yöntemi kullanabilirsiniz.  
  
-   Bir <xref:System.IDisposable> uygulamasında, bildirim tamamlandığında gözlemcilerin kaldırmak sağlayıcıyı etkinleştirir. Gözlemcilerin almak için bir başvuru <xref:System.IDisposable> uygulamasından <xref:System.IObservable%601.Subscribe%2A> da çağırabilir şekilde yöntemi <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> sağlayıcı bildirimleri gönderme bitmeden aboneliğinizi iptal etmek için yöntem.  
  
-   Sağlayıcı için kendi gözlemcilerin gönderir verileri içeren bir nesne. Bu nesne türü için genel tür parametresinin karşılık gelen <xref:System.IObservable%601> ve <xref:System.IObserver%601> arabirimleri. Bu nesnenin aynı olsa da <xref:System.IObservable%601> uygulama, en yaygın olarak ayrı bir tür değil.  
  
> [!NOTE]
>  Gözlemci tasarım deseni uygulama yanı sıra, kullanılarak oluşturulan kitaplıkları keşfetme ilgilenebilirsiniz <xref:System.IObservable%601> ve <xref:System.IObserver%601> arabirimleri. Örneğin, [.NET (Rx) için geriye dönük uzantıları](http://go.microsoft.com/fwlink/?LinkId=186345) genişletme yöntemleri ve zaman uyumsuz programlama desteklemek için LINQ standart dizisi işleçleri kümesinden oluşur.  
  
## <a name="implementing-the-pattern"></a>Düzeni uygulama  
 Aşağıdaki örnek, bir havaalanı bagaj talep bilgi sistemi uygulamak için gözlemci tasarım deseni kullanır. A `BaggageInfo` sınıfı, her uçuş gelen bagaj olduğu için alımı kullanılabilir karusel'leri ve gelen uçuşlar hakkında bilgi sağlar. Aşağıdaki örnekte gösterilir.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
 [!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]  
  
 A `BaggageHandler` sınıftır hakkında gelen uçuşlar ve bagaj talep karusel'leri bilgi almak için sorumlu. Dahili olarak, iki koleksiyon tutar:  
  
-   `observers`-Güncelleştirilmiş bilgileri alacak olan istemcileri bir koleksiyonu.  
  
-   `flights`-Uçuşlar ve bunların atanmış karusel'lerin bir koleksiyonu.  
  
 Her iki koleksiyon genel tarafından temsil edilen <xref:System.Collections.Generic.List%601> içinde örneği nesneleri `BaggageHandler` sınıfı oluşturucusu. Kaynak kodu `BaggageHandler` sınıfı, aşağıdaki örnekte gösterilir.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
 [!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]  
  
 Güncelleştirilmiş bilgileri almak istediğiniz istemcileri aramak `BaggageHandler.Subscribe` yöntemi. İstemci daha önce bildirimleri, istemcinin başvuru abone değil, <xref:System.IObserver%601> uygulaması eklenir `observers` koleksiyonu.  
  
 Aşırı yüklenmiş `BaggageHandler.BaggageStatus` yöntemi, bir uçuş gelen bagaj boşaltılıyor veya artık kaldırılıyor göstermek için çağrılabilir. İlk durumda yöntemi uçuş numarası, uçuş kaynaklandığı havaalanı ve Karusel bagaj burada kaldırılıyor geçirilir. İkinci durumda, yöntem yalnızca uçuş numarası geçirilir. Yüklenmekte olan bagaj için kaldırıldığında, yöntemi denetimleri olup `BaggageInfo` yönteme geçirilen bilgileri bulunmaktadır `flights` koleksiyonu. Yoksa, yöntem bilgileri ekler ve her gözlemci 's çağırır `OnNext` yöntemi. Bu uçuş hakkında bilgi depolanan olup olmadığını yöntemi, bagaj artık boşaltılıyor uçuşlar için denetler `flights` koleksiyonu. İse, her gözlemci 's yöntemini çağırır `OnNext` yöntemi ve kaldırır `BaggageInfo` nesnesinin `flights` koleksiyonu.  
  
 Günün son uçuş aldı ve onun bagaj işlendi, `BaggageHandler.LastBaggageClaimed` yöntemi çağrılır. Bu yöntem her gözlemci 's çağırır `OnCompleted` tüm bildirimleri tamamlandığını göstermek için yöntem ve ardından temizler `observers` koleksiyonu.  
  
 Sağlayıcının <xref:System.IObservable%601.Subscribe%2A> yöntemi döndürür bir <xref:System.IDisposable> gözlemcilerin önce bildirimleri almayı durdurmasını sağlayan uygulama <xref:System.IObserver%601.OnCompleted%2A> yöntemi çağrılır. Bu kaynak kodu `Unsubscriber(Of BaggageInfo)` sınıfı, aşağıdaki örnekte gösterilir. Ne zaman sınıfı örneği içinde `BaggageHandler.Subscribe` yöntemi, onu bir başvuru geçirilir `observers` toplama ve koleksiyonuna eklenen gözlemci başvuru. Bu başvurular için yerel değişkenler atanır. Nesnenin `Dispose` yöntemi çağrıldığında, gözlemci hala var olup olmadığını denetler `observers` koleksiyonu ve aşması durumunda gözlemci kaldırır.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
 [!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]  
  
 Aşağıdaki örnek sağlayan bir <xref:System.IObserver%601> adlı uygulama `ArrivalsMonitor`, bagaj talep bilgilerini görüntüleyen bir taban sınıf olduğu. Bilgiler, kaynak Şehir adına göre alfabetik olarak görüntülenir. Yöntemlerinin `ArrivalsMonitor` olarak işaretlenmiş `overridable` (Visual Basic'te) veya `virtual` (C# '), bu nedenle bunlar tüm geçersiz kılınmış türetilmiş sınıf tarafından.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
 [!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]  
  
 `ArrivalsMonitor` Sınıfı içerir `Subscribe` ve `Unsubscribe` yöntemleri. `Subscribe` Yöntemi etkinleştirir kaydetmek için sınıf <xref:System.IDisposable> çağrısı tarafından döndürülen uygulama <xref:System.IObservable%601.Subscribe%2A> özel bir değişken için. `Unsubscribe` Yöntemi etkinleştirir sağlayıcının çağırarak bildirim aboneliği için sınıf <xref:System.IDisposable.Dispose%2A> uygulaması. `ArrivalsMonitor`Ayrıca uygulamaları sağlar <xref:System.IObserver%601.OnNext%2A>, <xref:System.IObserver%601.OnError%2A>, ve <xref:System.IObserver%601.OnCompleted%2A> yöntemleri. Yalnızca <xref:System.IObserver%601.OnNext%2A> uygulama kodu önemli miktarda içerir. Yöntem ile özel, sıralanmış, genel çalışır <xref:System.Collections.Generic.List%601> gelen uçuşlar başlangıcı havaalanları hakkında bilgileri tutan nesne ve bunların bagaj olduğu kullanılabilir karusel'lerin. Varsa `BaggageHandler` sınıfı raporlar yeni uçuş varış <xref:System.IObserver%601.OnNext%2A> yöntem uygulaması, uçuş bilgilerini listesine ekler. Varsa `BaggageHandler` sınıfı raporlar uçuş 's bagaj kaldırıldı, <xref:System.IObserver%601.OnNext%2A> yöntemi, uçuş listeden kaldırır. Bir değişiklik yapıldığında, listesi sıralanır ve konsolda görüntülenir.  
  
 Aşağıdaki örnek, başlatır uygulama giriş noktası içerir `BaggageHandler` sınıf yanı sıra iki örneğini `ArrivalsMonitor` sınıfı ve kullandığı `BaggageHandler.BaggageStatus` eklemek ve gelen uçuşlar ilgili bilgileri kaldırmak için yöntemi. Her durumda gözlemcilerin güncelleştirmeleri almak ve doğru şekilde bagaj talep bilgilerini görüntüleyin.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
 [!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Gözlemci Tasarım Deseni En İyi Yöntemleri](../../../docs/standard/events/observer-design-pattern-best-practices.md)|Gözlemci tasarım deseni uygulamak uygulamaları geliştirirken benimsemek için en iyi uygulamaları açıklar.|  
|[Nasıl yapılır: Sağlayıcıyı Uygulama](../../../docs/standard/events/how-to-implement-a-provider.md)|Uygulama izleme sıcaklık için bir sağlayıcının adım adım bir uygulama sağlar.|  
|[Nasıl yapılır: Gözlemci Uygulama](../../../docs/standard/events/how-to-implement-an-observer.md)|Bir adım adım uygulamasını bir gözlemci uygulama izleme sıcaklık için sağlar.|
