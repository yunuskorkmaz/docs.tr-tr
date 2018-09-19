---
title: .NET Yerel ile Başlangıç İyileştirmesini Hesaplama
ms.date: 03/30/2017
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2603c29fe9108a32f3c3ba86a5aba9fae5042b17
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009548"
---
# <a name="measuring-startup-improvement-with-net-native"></a>.NET Yerel ile Başlangıç İyileştirmesini Hesaplama
[!INCLUDE[net_native](../../../includes/net-native-md.md)] uygulama başlatma süresini önemli ölçüde artırır. Bu geliştirme, taşınabilir, düşük güç tüketimli cihazlar ve karmaşık uygulamaları ile özellikle fark edilebilir. Bu konu, bu başlangıç geliştirme ölçmek için gereken temel araçları ile çalışmaya başlamanıza yardımcı olur.  
  
 Performans araştırmalar kolaylaştırmak için .NET Framework ve Windows için olay izleme Windows (olaylar meydana geldiğinde tooling bildirmek uygulamanızı sağlayan ETW) adlı bir olay çerçevesi kullanın. Ardından, kolayca görüntüleyin ve ETW olayları analiz etmek için PerfView adında bir araç kullanabilirsiniz. Bu konu açıklar nasıl yapılır:  
  
-   Kullanım <xref:System.Diagnostics.Tracing.EventSource> olayları yaymak için sınıf.  
  
-   Bu olayları toplamak için PerfView kullanın.  
  
-   Bu olayları görüntülemek için PerfView kullanın.  
  
## <a name="using-eventsource-to-emit-events"></a>EventSource olaylarını yaymak için kullanma  
 <xref:System.Diagnostics.Tracing.EventSource> bir özel olay sağlayıcısı oluşturulacağı bir temel sınıf sağlar. Öğesinin genel olarak, oluşturduğunuz <xref:System.Diagnostics.Tracing.EventSource> ve kaydırma `Write*` kendi olay yöntemleri ile yöntemleri. Bir singleton deseni genellikle her biri için kullanılan <xref:System.Diagnostics.Tracing.EventSource>.  
  
 Örneğin, aşağıdaki örnekte sınıfı iki performans özelliklerini ölçmek için kullanılabilir:  
  
-   Zamana kadar `App` sınıf oluşturucusu çağrıldı.  
  
-   Zamana kadar `MainPage` Oluşturucusu çağrıldı.  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 Burada gereken birkaç nokta vardır. Bir tekliyi ilk olarak oluşturulduğu `AppEventSource.Log`. Bu örnek için tüm günlük kullanılacaktır. İkinci olarak, her olay yöntemi olan bir <xref:System.Diagnostics.Tracing.EventAttribute>. Bu araçları dizini ilişkilendirmek yardımcı <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> üzerinde çağıran yönteme yöntemiyle `AppEventSource`.  
  
 Bu olaylar yalnızca görsel olduğunu unutmayın. Çoğu uygulama kodu bu olayları sonra çalıştırılır. Kod içinde hangi olayların Kullanıcı etkileşimlerine karşılık gelen, bu ölçün ve bu Kıyaslama geliştirmek anlamanız gerekir. Ayrıca, olaylar yalnızca tek bir örneği kez oturum açmak. Genellikle, başlangıç eşleştirilmiş ve her işlem için olayları durdurmak kullanışlıdır. Uygulama başlatma incelerken, başlangıç olayı genellikle işletim sistemi yayan "İşlem/Start" etkinliğidir.  
  
 Örneğin, bir RSS Okuyucu oluşturduğunuz düşünün. Birkaç günlüğe bir olay yazmak için ilgi çekici konumlar:  
  
-   Ne zaman ana sayfasında önce işlenir.  
  
-   Eski RSS hikayeleri yerel depolama alanından zaman seri.  
  
-   Ne zaman uygulamanızı yeni hikayeleri eşitlemeye başlar.  
  
-   Uygulamanızı yeni hikayeleri eşitleniyor ne zaman sona ermiştir.  
  
 Uygulama izleme basit: yalnızca türetilmiş sınıf üzerinde uygun yöntemi çağırın. Kullanarak `AppEventSource` önceki örnekte, bir uygulama gibi işaretleyebilir:  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 Uygulama izleme eklenmiş, olayları toplamak hazırsınız.  
  
## <a name="gathering-events-with-perfview"></a>PerfView ile olayları toplama  
 PerfView ETW olayları performans araştırmalar uygulamanızdan her türlü bunu yapmanıza yardımcı olmak için kullanır. Ayrıca, bir yapılandırma sağlayan GUI açıp farklı türde olaylar için günlüğe kaydetmeyi etkinleştirmek içerir. PerfView ücretsiz bir araçtır ve indirilebileceğini [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=28567). Daha fazla bilgi için izleme [PerfView öğretici videolar](http://channel9.msdn.com/Series/PerfView-Tutorial).  
  
> [!NOTE]
>  PerfView ARM sistemlerinde olayları toplamak için kullanılamaz. ARM sistemlerinde olayları toplamak için Windows Performans kaydedici (WPR) kullanın. Daha fazla bilgi için [Vance Morrison'ın blog gönderisi](https://blogs.msdn.com/b/vancem/archive/2012/12/19/collecting-etw-perfview-data-on-an-windows-rt-winrt-arm-surface-device.aspx).  
  
 Ayrıca, PerfView komut satırından çalıştırabilirsiniz. Sağlayıcınızdan yalnızca olayları günlüğe kaydetmek için komut istemi penceresi açın ve komutu girin:  
  
```  
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile   
```  
  
 burada:  
  
 `-KernelEvents:Process`  
 Ne zaman işlemi başlatır ve durdurur bilmek istediğiniz gösterir. Diğer olay sürelerinden çıkarılabilir, böylece uygulamanız için işlem/başlangıç olayı gerekir.  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 PerfView varsayılan olarak etkinleştirir ve Şirketim MyApp sağlayıcısında kapatır diğer sağlayıcılar devre dışı bırakır.  (Yıldız işareti olduğunu gösterir. bir <xref:System.Diagnostics.Tracing.EventSource>.)  
  
 `collect outputFile`  
 Koleksiyonu Başlat ve outputFile.etl.zip için verileri kaydetmek istediğinizi belirtir.  
  
 PerfView başlattıktan sonra uygulamanızı çalıştırın. Unutmayın, uygulamanızı çalıştıran gereken birkaç nokta vardır:  
  
-   Yayın derleme, hata ayıklama derlemesi kullanın. Hata ayıklama yapılarında, genellikle ek hata denetimi ve hata işleme uygulama beklenenden daha yavaş çalışmasına neden olabilecek kodunu içerir.  
  
-   Bir hata ayıklayıcısı ekli, uygulamanızı çalıştıran uygulamanızın performansını etkiler.  
  
-   Windows uygulama başlatma sürelerini hızlandırmak için birden çok önbelleğe alma stratejilerine kullanır. Uygulamanız şu anda bellekte önbelleğe alınmış ve diskten yüklü olması gerekmez, daha hızlı bir şekilde başlar. Tutarlılık sağlamak için başlatın ve uygulamanızı birkaç kez ölçme önce kapatın.  
  
 PerfView yayılan olayları toplayabilir, böylece, uygulamanızı çalıştırdığınızda seçin **toplamasını Durdur** düğmesi. Genellikle, gereksiz olayları elde uygulamanızı kapatmadan önce koleksiyonu durdurmanız gerekir. Ancak, kapatma ya da ertelenmesi performans ölçüm yaptığınız, koleksiyon devam isteyebilirsiniz.  
  
## <a name="displaying-the-events"></a>Olaylarını görüntüleme  
 Zaten toplanan olayları görüntülemek için .etl açmak için PerfView kullanın veya. etl.zip dosyası oluşturulur ve seçin **olayları**. ETW olayları, diğer işlemlerin olaylarını dahil olmak üzere çok sayıda ilgili bilgileri topladıktan. Araştırmanızı odaklanmak için aşağıdaki olaylar görünümü metin kutularına tamamlayın:  
  
-   İçinde **filtresi** kutusunda, uygulama adınız (olmadan ".exe") belirtin.  
  
-   İçinde **olay türleri filtresi** kutusunda, belirtin `Process/Start | MyCompany-MyApp`. Bu olaylar için bir filtre Şirketim MyApp ve Windows çekirdek/işlem/başlangıç olayı ayarlar.  
  
 Tüm olaylar, sol bölmede listelenen seçin (Ctrl-A) ve **Enter** anahtarı. Artık, her olay zaman damgası görmeye olmalıdır. Bu zaman damgaları izleme başlangıcını göreli olduğundan başlangıcından bu yana geçen süreyi belirlemek için işlemin başlangıç zamanından itibaren her olayın zaman çıkarılacak sahip. İki zaman damgaları seçmek için CTRL tuşuna basıp tıklayarak kullanıyorsanız, bunları sayfanın alt kısmındaki durum çubuğunda görüntülenen arasındaki fark görürsünüz. Bu, herhangi iki olay görüntüdeki (işlem başlangıç dahil) arasında geçen süreyi görmek kolaylaştırır. Görünüm için kısayol menüsünü açın ve CSV dosyalarına dışarı aktarma veya kaydetmek veya verileri işlemek için Microsoft Excel'i açıp gibi kullanışlı seçenekler, bir dizi seçin.  
  
 Yordam hem özgün uygulamanızı hem de sürümü için yinelenen, kullanılarak oluşturulan [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri, performans farkı karşılaştırabilirsiniz.   [!INCLUDE[net_native](../../../includes/net-native-md.md)] uygulamalar genellikle başlangıç olmayan daha hızlı[!INCLUDE[net_native](../../../includes/net-native-md.md)] uygulamalar. Daha ayrıntılı araştırmaya ilgileniyorsanız, PerfView ayrıca en çok zaman alan, kodunuzun parçalarını belirleyebilir. Daha fazla bilgi için izleme [PerfView öğreticiler](http://channel9.msdn.com/Series/PerfView-Tutorial) veya okuma [Vance Morrison'ın blog girişine](https://blogs.msdn.com/b/vancem/archive/2011/12/28/publication-of-the-perfview-performance-analysis-tool.aspx).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.Tracing.EventSource>
