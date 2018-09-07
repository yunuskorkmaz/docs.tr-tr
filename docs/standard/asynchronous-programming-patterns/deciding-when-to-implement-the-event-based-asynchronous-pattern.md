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
ms.openlocfilehash: af30f0d09ce772f20f342ec0936d0ca63f5465d7
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44046145"
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme
Olay tabanlı zaman uyumsuz desen, bir sınıfın zaman uyumsuz davranış açığa çıkarmak için bir desen sağlar. Bu düzen sunulmasıyla birlikte [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] iki deseni için zaman uyumsuz davranış gösterme tanımlar: zaman uyumsuz desen dayalı <xref:System.IAsyncResult?displayProperty=nameWithType> arabirimi ve olay-tabanlı düzeni. Bu konu, her iki desenleri uygulamak, uygun olduğunda açıklar.  
  
 İle zaman uyumsuz programlama hakkında daha fazla bilgi için <xref:System.IAsyncResult> arabirim için bkz: [zaman uyumsuz programlama modeli (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).  
  
## <a name="general-principles"></a>Genel ilkeleri  
 Genel olarak, olay tabanlı zaman uyumsuz desen mümkün olduğunca kullanarak zaman uyumsuz özellikler sunması gerekir. Ancak, olay tabanlı deseni karşılayamayan bazı gereksinimler vardır. Bu gibi durumlarda, uygulamanız gerekebilir <xref:System.IAsyncResult> olay tabanlı deseni yanı sıra deseni.  
  
> [!NOTE]
>  İçin nadir olarak rastlanıyor <xref:System.IAsyncResult> da uygulanan olay-tabanlı deseni uygulanması için desen.  
  
## <a name="guidelines"></a>Kuralları  
 Aşağıdaki liste, olay tabanlı zaman uyumsuz desenin ne zaman uygulamalıdır yönergeleri açıklar:  
  
-   Olay tabanlı düzeni, zaman uyumsuz davranış sınıfınız için kullanıma sunmak için varsayılan API olarak kullanın.  
  
-   Kullanıma <xref:System.IAsyncResult> sınıfınızın bir istemci uygulama, örneğin Windows Forms öncelikli olarak kullanıldığında desen.  
  
-   Yalnızca kullanıma <xref:System.IAsyncResult> desen gereksinimlerinizi Karşılama konusunda gerekli olduğunda. Örneğin, var olan bir API ile uyumluluk kullanıma sunmak gerektirebilecek <xref:System.IAsyncResult> deseni.  
  
-   Kullanıma <xref:System.IAsyncResult> deseni olmadan da olay-tabanlı desenini gösterme.  
  
-   Kullanımına açmanız gerekiyorsa <xref:System.IAsyncResult> desen, Gelişmiş bir seçenek olarak bunu. Bir proxy nesnesi oluşturursanız, örneğin, olay tabanlı deseni varsayılan olarak oluşturmak için bir seçenek ile üretmek <xref:System.IAsyncResult> deseni.  
  
-   Olay tabanlı deseni uygulamanızı oluşturmak, <xref:System.IAsyncResult> deseni uygulaması.  
  
-   Her iki olay tabanlı deseni kullanılmasını önlemek ve <xref:System.IAsyncResult> deseni aynı sınıfta. Olay tabanlı deseni "yüksek düzey" sınıflarda kullanıma sunmak ve <xref:System.IAsyncResult> desen üzerinde "alt düzey" sınıfları. Örneğin, üzerinde olay-tabanlı desenini karşılaştırma <xref:System.Net.WebClient> ile bileşen <xref:System.IAsyncResult> üzerinde desen <xref:System.Web.HttpRequest> sınıfı.  
  
    -   Olay tabanlı deseni kullanıma sunmak ve <xref:System.IAsyncResult> deseni uyumluluk gerektirdiğinde aynı sınıfta. Örneğin, bir API kullanan zaten yayımlandı <xref:System.IAsyncResult> deseni korumak gerekir <xref:System.IAsyncResult> geriye dönük uyumluluk için desen.  
  
    -   Olay tabanlı deseni kullanıma sunmak ve <xref:System.IAsyncResult> uygulamaları ayırma avantajı elde edilen nesne modeli karmaşıklığı ağır varsa aynı sınıf desen. Olay tabanlı desenini gösterme önlemek üzere daha tek bir sınıftaki her iki desenleri göstermek daha iyidir.  
  
    -   Her iki olay tabanlı deseni kullanımına açmanız gerekiyorsa ve <xref:System.IAsyncResult> deseni kullanımı tek bir sınıftaki <xref:System.ComponentModel.EditorBrowsableAttribute> kümesine <xref:System.ComponentModel.EditorBrowsableState.Advanced> işaretlemek için <xref:System.IAsyncResult> Gelişmiş bir özellik olarak deseni uygulaması. Bu gibi değil görüntülemek için Visual Studio IntelliSense, tasarım ortamlara gösterir <xref:System.IAsyncResult> özellikleri ve yöntemleri. Bu özellikler ve yöntemler yine de tam olarak kullanılabilir, ancak API'sinin daha net bir görünüm IntelliSense çalışmayı Geliştirici sahiptir.  
  
## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>Olay tabanlı deseni yanı sıra IAsyncResult desenini gösterme ölçütleri  
 Olay tabanlı zaman uyumsuz desen çok sayıda avantaj yukarıda açıklanan senaryoları altında olsa da performans ise, en önemli gereksinim, bilmeniz gereken bazı dezavantajları vardır.  
  
 Olay tabanlı deseni olmayan adres üç senaryo vardır ve <xref:System.IAsyncResult> Desen:  
  
-   Bir bekleme engelleme <xref:System.IAsyncResult>  
  
-   Çoğu bekleme engelleme <xref:System.IAsyncResult> nesneleri  
  
-   Üzerinde tamamlanması için yoklama <xref:System.IAsyncResult>  
  
 Olay tabanlı deseni kullanılarak bu senaryoları karşılayabilirsiniz. ancak bunun yapılması kullanmaktan daha kullanışsız <xref:System.IAsyncResult> deseni.  
  
 Geliştiriciler sık kullandığınız <xref:System.IAsyncResult> deseni genellikle çok yüksek performans gereksinimlerine sahip hizmetler için. Örneğin, yoklama tamamlama senaryosu için yüksek performanslı server tekniğidir.  
  
 Ayrıca, olay tabanlı deseni daha az verimli <xref:System.IAsyncResult> daha fazla nesne, özellikle oluşturduğundan desen <xref:System.EventArgs>, ve iş parçacıkları arasında eşitler.  
  
 Aşağıdaki liste kullanmaya karar verirseniz izlemek için bazı öneriler gösterir <xref:System.IAsyncResult> Desen:  
  
-   Yalnızca kullanıma <xref:System.IAsyncResult> deseni desteği özellikle gerektirdiğinde <xref:System.Threading.WaitHandle> veya <xref:System.IAsyncResult> nesneleri.  
  
-   Yalnızca kullanıma <xref:System.IAsyncResult> deseni kullanan mevcut bir API'ye sahip olduğunuzda <xref:System.IAsyncResult> deseni.  
  
-   Mevcut bir API'ye göre varsa <xref:System.IAsyncResult> desen, ayrıca olay tabanlı deseni, bir sonraki sürümde kullanıma sunmak isteyebilirsiniz.  
  
-   Yalnızca kullanıma <xref:System.IAsyncResult> doğrulamanız yapıldı, yüksek performans gereksinimleriniz varsa, deseni, olay tabanlı deseni tarafından karşılanamıyor ancak tarafından karşılanması <xref:System.IAsyncResult> deseni.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Olay Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
- [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
