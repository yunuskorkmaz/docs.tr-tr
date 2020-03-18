---
title: Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
ms.openlocfilehash: 5fca32953af91184fe99d8ef6afe5a2374f325d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67663726"
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme

Olay tabanlı Asynchronous Pattern bir sınıfın asynchronous davranışını ortaya çıkarmak için bir desen sağlar. Bu örüntünün tanıtılmasıyla birlikte,.NET Framework asenkron davranışı ortaya çıkarmak için iki desen <xref:System.IAsyncResult?displayProperty=nameWithType> tanımlar: arabirime dayalı Asynchronous Deseni ve olay tabanlı desen. Bu konu, her iki delekliği uygulamanız için uygun olduğunda açıklanır.

<xref:System.IAsyncResult> Arabirimli eşzamanlı programlama hakkında daha fazla bilgi için, [Bkz. Asynchronous Programming Model (APM).](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)

## <a name="general-principles"></a>Genel İlkeler

Genel olarak, mümkün olduğunda Event tabanlı Asynchronous Deseni'ni kullanarak eşzamanlı özellikleri ortaya çıkarmalısınız. Ancak, olay tabanlı desen karşılayamayacağı bazı gereksinimleri vardır. Bu gibi durumlarda, olay tabanlı <xref:System.IAsyncResult> desen ek olarak desen uygulamak gerekebilir.

> [!NOTE]
> <xref:System.IAsyncResult> Desen de uygulanmadan uygulanacak olay tabanlı desen için nadirdir.

## <a name="guidelines"></a>Yönergeler

Aşağıdaki liste, Olay tabanlı Asynchronous Deseni'ni ne zaman uygulamanız gerektiğine ilişkin yönergeleri açıklar:

- Sınıfınız için eşzamanlı davranışı ortaya çıkarmak için olay tabanlı deseni varsayılan API olarak kullanın.

- Sınıfınız öncelikle <xref:System.IAsyncResult> bir istemci uygulamasında (örneğin Windows Forms) kullanıldığında deseni ortaya çıkarmayın.

- <xref:System.IAsyncResult> Deseni yalnızca gereksinimlerinizi karşılamak için gerekli olduğunda ortaya çıkarın. Örneğin, varolan bir API ile uyumluluk <xref:System.IAsyncResult> deseni ortaya çıkarmanızı gerektirebilir.

- Olay tabanlı <xref:System.IAsyncResult> deseni de ortaya çıkarmadan deseni açığa çıkarmayın.

- <xref:System.IAsyncResult> Deseni ortaya çıkarmanız gerekiyorsa, bunu gelişmiş bir seçenek olarak yapın. Örneğin, bir proxy nesnesi oluşturursanız, <xref:System.IAsyncResult> varsayılan olarak olay tabanlı deseni ve deseni oluşturma seçeneğini oluşturun.

- Desen uygulamanızda olay tabanlı <xref:System.IAsyncResult> desen uygulamanızı oluşturun.

- Hem olay tabanlı deseni hem <xref:System.IAsyncResult> de aynı sınıftaki deseni açığa çıkarmaktan kaçının. "Üst düzey" sınıflardaki olay tabanlı deseni ve "alt düzey" sınıflardaki <xref:System.IAsyncResult> deseni ortaya çıkar. Örneğin, bileşendeki <xref:System.Net.WebClient> olay tabanlı deseni <xref:System.IAsyncResult> <xref:System.Web.HttpRequest> sınıftaki desenle karşılaştırın.

  - Uyumluluk gerektirdiğinde olay tabanlı <xref:System.IAsyncResult> deseni ve deseni aynı sınıfta ortaya çıkar. Örneğin, <xref:System.IAsyncResult> deseni kullanan bir API zaten yayımladıysanız, geriye dönük <xref:System.IAsyncResult> uyumluluk için deseni korumanız gerekir.

  - Ortaya çıkan nesne modeli <xref:System.IAsyncResult> karmaşıklığı uygulamaları ayırma avantajından daha ağır basıyorsa, olay tabanlı deseni ve deseni aynı sınıfta ortaya çıkar. Olay tabanlı deseni açığa çıkarmaktan kaçınmaktansa, her iki deseni tek bir sınıfta ortaya çıkarmak daha iyidir.

  - Tek bir sınıfta hem olay tabanlı <xref:System.IAsyncResult> deseni hem de <xref:System.ComponentModel.EditorBrowsableAttribute> deseni ortaya <xref:System.IAsyncResult> çıkarmanız gerekiyorsa, desen uygulamasını gelişmiş bir özellik olarak işaretlemek için <xref:System.ComponentModel.EditorBrowsableState.Advanced> ayarlı'yı kullanın. Bu, özellikleri ve yöntemleri görüntülemek için değil Visual Studio <xref:System.IAsyncResult> IntelliSense gibi tasarım ortamları, gösterir. Bu özellikler ve yöntemler hala tamamen kullanılabilir, ancak IntelliSense ile çalışan geliştirici API daha net bir görünüme sahiptir.

## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>Olay Tabanlı Desenek IAsyncSonuç Deseni Açığa Kriterleri

Olay tabanlı Asynchronous Desen daha önce belirtilen senaryolar altında birçok faydası olsa da, performans en önemli gereksinimi olup olmadığını farkında olmalıdır bazı dezavantajları vardır.

Olay tabanlı desenin yanı sıra <xref:System.IAsyncResult> desenin ele alınmadığı üç senaryo vardır:

- Bir beklemeyi engelleme<xref:System.IAsyncResult>

- Birçok <xref:System.IAsyncResult> nesnede beklemeyi engelleme

- Tamamlanma kaynıyaç<xref:System.IAsyncResult>

Bu senaryoları olay tabanlı deseni kullanarak ele alabilirsiniz, ancak bunu <xref:System.IAsyncResult> yapmak deseni kullanmaktan daha hantaldır.

Geliştiriciler genellikle <xref:System.IAsyncResult> çok yüksek performans gereksinimleri olan hizmetler için deseni kullanır. Örneğin, tamamlama senaryosu için yoklama yüksek performanslı bir sunucu tekniğidir.

Ayrıca, olay tabanlı desen, özellikle <xref:System.IAsyncResult> <xref:System.EventArgs>daha fazla nesne oluşturduğundan ve iş parçacıkları arasında eşitlediğinden desenden daha az verimlidir.

Aşağıdaki <xref:System.IAsyncResult> liste, deseni kullanmaya karar verirseniz izleyerek bazı öneriler gösterir:

- Deseni <xref:System.IAsyncResult> yalnızca özellikle destek veya <xref:System.Threading.WaitHandle> <xref:System.IAsyncResult> nesneler eihtiyacınız olduğunda ortaya çıkar.

- <xref:System.IAsyncResult> Deseni yalnızca <xref:System.IAsyncResult> deseni kullanan varolan bir API'niz olduğunda ortaya çıkarır.

- <xref:System.IAsyncResult> Desene dayalı varolan bir API'niz varsa, bir sonraki sürümde olay tabanlı deseni de ortaya çıkarmayı düşünün.

- Yalnızca, <xref:System.IAsyncResult> doğruladığınız yüksek performans gereksinimleriniz varsa, olay tabanlı desen tarafından karşılanamıyor, <xref:System.IAsyncResult> ancak desen tarafından karşılanabilirse deseni ortaya çıkarır.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)
- [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
