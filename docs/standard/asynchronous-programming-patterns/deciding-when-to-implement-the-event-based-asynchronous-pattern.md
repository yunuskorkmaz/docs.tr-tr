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
ms.openlocfilehash: c235a838504889a105ef98df47f7373a145503da
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289453"
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme

Olay tabanlı zaman uyumsuz model, bir sınıfın zaman uyumsuz davranışını açığa çıkarmak için bir model sağlar. Bu düzenin tanıtılmasıyla .NET Framework, zaman uyumsuz davranışı ortaya çıkarmak için iki desen tanımlar: arabirime dayalı zaman uyumsuz desen <xref:System.IAsyncResult?displayProperty=nameWithType> ve olay tabanlı Düzen. Bu konu başlığı altında, her iki deseni de uygulamanız için uygun olduğunda açıklanır.

Arabirim ile zaman uyumsuz programlama hakkında daha fazla bilgi için <xref:System.IAsyncResult> bkz. [zaman uyumsuz programlama MODELI (APM)](asynchronous-programming-model-apm.md).

## <a name="general-principles"></a>Genel Ilkeler

Genel olarak, mümkün olduğunda olay tabanlı zaman uyumsuz model kullanarak zaman uyumsuz özellikleri kullanıma sunmalısınız. Ancak, olay tabanlı düzenin karşılayamayacak bazı gereksinimler vardır. Bu durumlarda, <xref:System.IAsyncResult> olay tabanlı düzene ek olarak, model uygulamanız gerekebilir.

> [!NOTE]
> <xref:System.IAsyncResult>Düzenin, olay tabanlı model de uygulanmadan uygulanması çok nadir bir durumdur.

## <a name="guidelines"></a>Yönergeler

Aşağıdaki listede olay tabanlı zaman uyumsuz model uygulamanız gereken yönergeler açıklanmaktadır:

- Sınıfınız için zaman uyumsuz davranışı göstermek üzere varsayılan API olarak olay tabanlı bir model kullanın.

- <xref:System.IAsyncResult>Sınıfınız öncelikle bir istemci uygulamasında kullanılıyorsa, örneğin Windows Forms.

- Yalnızca gereksinimlerinizi karşılamak <xref:System.IAsyncResult> için gerekli olduğunda bu kalıbı sunun. Örneğin, var olan bir API ile uyumluluk, bu kalıbı göstermek için gerekli olabilir <xref:System.IAsyncResult> .

- <xref:System.IAsyncResult>Ayrıca, olay tabanlı bir model de görüntülenmeden stili açığa çıkarmayın.

- Kalıbı kullanıma sunmalısınız <xref:System.IAsyncResult> , bunu gelişmiş bir seçenek olarak yapın. Örneğin, bir ara sunucu nesnesi oluşturursanız, model oluşturma seçeneği ile varsayılan olarak olay tabanlı desenler oluşturun <xref:System.IAsyncResult> .

- Kendi örüntüsünün uygulamanızda olay tabanlı model uygulamanızı oluşturun <xref:System.IAsyncResult> .

- Hem olay tabanlı hem de <xref:System.IAsyncResult> aynı sınıfta bulunan kalıbı açığa çıkarmaktan kaçının. "Daha yüksek düzey" sınıflarda olay tabanlı düzende ve <xref:System.IAsyncResult> "alt düzey" sınıflarda düzende kullanıma sunun. Örneğin, bileşen üzerindeki olay tabanlı kalıbı, <xref:System.Net.WebClient> <xref:System.IAsyncResult> sınıfındaki düzeniyle karşılaştırın <xref:System.Web.HttpRequest> .

  - Uyumluluk gerektirdiğinde, olay tabanlı bir model ve <xref:System.IAsyncResult> aynı sınıf üzerindeki kalıbı kullanıma sunun. Örneğin, modelini kullanan bir API zaten çıkardıysanız <xref:System.IAsyncResult> , <xref:System.IAsyncResult> geriye dönük uyumluluk için kalıbı saklamanız gerekir.

  - <xref:System.IAsyncResult>Ortaya çıkan nesne modeli karmaşıklığı, uygulamaları ayırmanın avantajını aşarsa, olay tabanlı modeli ve modeli aynı sınıf üzerinde kullanıma sunun. Olay tabanlı deseni açığa çıkarmaktan kaçınmak için, her iki deseni tek bir sınıfta göstermek daha iyidir.

  - Hem olay tabanlı hem de <xref:System.IAsyncResult> tek bir sınıfta bir model kullanıma sunmalı, <xref:System.ComponentModel.EditorBrowsableAttribute> <xref:System.ComponentModel.EditorBrowsableState.Advanced> <xref:System.IAsyncResult> model uygulamasını gelişmiş bir özellik olarak işaretlemek için olarak ayarla ' yı kullanın. Bu, özellikleri ve yöntemleri görüntülememe gibi, Visual Studio IntelliSense gibi ortam ortamlarının tasarlanacağını belirtir <xref:System.IAsyncResult> . Bu özellikler ve yöntemler hala tamamen kullanılabilir, ancak IntelliSense aracılığıyla çalışan geliştirici, API 'nin daha net bir görünümüne sahiptir.

## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>Olay tabanlı düzene ek olarak IAsyncResult deseninin açığa çıkarılması ölçütü

Olay tabanlı zaman uyumsuz düzende daha önce bahsedilen senaryolar altında birçok avantaj olsa da, bu, performansın en önemli gereksiniminiz olup olmadığını bilmeniz gereken bazı dezavantajlara sahiptir.

Olay tabanlı düzenin, ve deseninin yanı sıra, bu üç senaryo da ele alınmaz <xref:System.IAsyncResult> :

- Engelleme, bir tane üzerinde bekle<xref:System.IAsyncResult>

- Birçok nesne için engelleme bekleme <xref:System.IAsyncResult>

- Tamamlanma için yoklama<xref:System.IAsyncResult>

Bu senaryolara olay tabanlı bir model kullanarak adresleyerek, ancak bunu yapmak, deseninin kullanılmasıyla daha kısaberdir <xref:System.IAsyncResult> .

Geliştiriciler genellikle <xref:System.IAsyncResult> çok yüksek performans gereksinimlerine sahip olan hizmetler için olan kalıbı kullanır. Örneğin, tamamlama senaryosu için yoklama, yüksek performanslı bir sunucu tekniğidir.

Ayrıca, <xref:System.IAsyncResult> özellikle <xref:System.EventArgs> ve iş parçacıkları arasında eşitlendiği için daha fazla nesne oluşturduğundan, olay tabanlı bir model, düzeninden daha etkilidir.

Aşağıdaki listede, deseninin kullanılmasına karar verirseniz izlenecek bazı öneriler gösterilmektedir <xref:System.IAsyncResult> :

- Yalnızca <xref:System.IAsyncResult> veya nesneleri için destek istediğinizde, sadece stili ortaya <xref:System.Threading.WaitHandle> çıkarın <xref:System.IAsyncResult> .

- Yalnızca <xref:System.IAsyncResult> , kalıbı kullanan mevcut BIR API 'ye sahip olduğunuzda bu kalıbı ortaya çıkarın <xref:System.IAsyncResult> .

- Modele dayalı mevcut bir API 'niz varsa, bir <xref:System.IAsyncResult> sonraki sürümdeki olay tabanlı bir model de kullanıma sunma seçeneğini de göz önünde bulundurun.

- Yalnızca, <xref:System.IAsyncResult> doğrulamış olduğunuz yüksek performanslı gereksinimleriniz varsa, olay tabanlı bir model tarafından karşılanamadıysanız ancak bu model tarafından karşılanamadığında, stili ortaya çıkarın <xref:System.IAsyncResult> .

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](component-that-supports-the-event-based-asynchronous-pattern.md)
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Deseni Uygulama](implementing-the-event-based-asynchronous-pattern.md)
- [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](event-based-asynchronous-pattern-overview.md)
