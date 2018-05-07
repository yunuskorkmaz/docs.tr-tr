---
title: .NET Yerel ile Başlangıç İyileştirmesini Hesaplama
ms.date: 03/30/2017
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b010307baa8634a4bb62310318d1d718a2525d4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="measuring-startup-improvement-with-net-native"></a>.NET Yerel ile Başlangıç İyileştirmesini Hesaplama
[!INCLUDE[net_native](../../../includes/net-native-md.md)] uygulamaları başlatma süresini önemli ölçüde iyileştirir. Bu geliştirme, taşınabilir, düşük güç cihazlarda ve karmaşık uygulamaları ile özellikle fark edilebilir. Bu konuda bu başlangıç geliştirme ölçmek için gereken temel izleme ile çalışmaya başlamanıza yardımcı olur.  
  
 Performans araştırmalar kolaylaştırmak için olay izleme için Windows (olaylar gerçekleştiğinde tooling bildirmek uygulamanızı sağlayan ETW) adlı bir olay çerçevesi .NET Framework ve Windows kullanın. Ardından PerfView adlı bir aracı kolayca görüntülemek ve ETW olayları çözümlemek için de kullanabilirsiniz. Bu konuda açıklanmaktadır nasıl yapılır:  
  
-   Kullanım <xref:System.Diagnostics.Tracing.EventSource> olayları yaymak üzere sınıfı.  
  
-   Bu olayları toplamak için PerfView kullanın.  
  
-   Bu olayları görüntülemek için PerfView kullanın.  
  
## <a name="using-eventsource-to-emit-events"></a>EventSource olaylarını yaymak üzere kullanma  
 <xref:System.Diagnostics.Tracing.EventSource> özel olay sağlayıcısı oluşturulacağı bir temel sınıf sağlar. Öğesinin bir alt genel olarak, oluşturduğunuz <xref:System.Diagnostics.Tracing.EventSource> ve sarmalayın `Write*` kendi olay yöntemleriyle yöntemleri. Bir singleton deseni genellikle her biri için kullanılan <xref:System.Diagnostics.Tracing.EventSource>.  
  
 Örneğin, aşağıdaki örnekte sınıfında iki performans özellikleri ölçmek için kullanılabilir:  
  
-   Zamana kadar `App` sınıfı oluşturucusu çağrıldı.  
  
-   Zamana kadar `MainPage` Oluşturucusu çağrıldı.  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 Burada dikkat edin gereken birkaç nokta vardır. İlk olarak, tek oluşturulan `AppEventSource.Log`. Bu örnek için tüm günlük kullanılacaktır. İkinci olarak, her olay yöntemi sahip bir <xref:System.Diagnostics.Tracing.EventAttribute>. Bu araç dizinini ilişkilendirmek yardımcı olur <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> üzerinde çağrıldı yöntemiyle yöntemini `AppEventSource`.  
  
 Bu olaylar yalnızca yalnızca tanım olduğuna dikkat edin. Çoğu uygulama kodu bu olayları sonra çalışır. Hangi olayların kodda Kullanıcı etkileşimlerine karşılık gelen, bu ölçmek ve bu kıyaslamaları geliştirmek anlamanız gerekir. Ayrıca, olayları kendilerini yalnızca tek bir örneğini zamanında kaydeder. Genellikle, başlangıç eşleştirilmiş ve her işlem için olayları durdurmak kullanışlıdır. Uygulama başlangıç incelerken başlangıç genellikle işletim sistemini yayar "İşlem/Start" olay etkinliğidir.  
  
 Örneğin, bir RSS Okuyucu oluşturmakta olduğunuz varsayalım. Birkaç bir olay günlüğü için ilginç konumlardır:  
  
-   Ne zaman ana sayfasında önce işlenir.  
  
-   Ne zaman eski RSS hikayeleri yerel depolama biriminden serisi.  
  
-   Ne zaman uygulamanızı yeni hikayeleri eşitlemeye başlar.  
  
-   Uygulamanızı yeni hikayeleri eşitleniyor ne zaman sona ermiştir.  
  
 Uygulama izleme basit: yalnızca türetilmiş sınıf üzerinde uygun yöntemini çağırın. Kullanarak `AppEventSource` önceki örnekten, bir uygulama gibi işaretleyebilir:  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 Uygulama izleme, olayları toplamak hazırsınız.  
  
## <a name="gathering-events-with-perfview"></a>PerfView toplama olayları  
 PerfView ETW olayları performans araştırmalar uygulamanızdan her türlü yapmanıza yardımcı olmak için kullanır. Ayrıca olanak sağlayan GUI farklı türde olaylar için günlüğe kaydetmeyi açmak veya kapatmak bir yapılandırmayı içerir. PerfView ücretsiz bir araçtır ve yüklenebilir [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=28567). Daha fazla bilgi için izleme [PerfView öğretici videolar](http://channel9.msdn.com/Series/PerfView-Tutorial).  
  
> [!NOTE]
>  PerfView ARM sistemleri üzerinde olaylarını toplamak için kullanılamaz. ARM sistemleri üzerinde olaylarını toplamak için Windows Performans Kaydedicisi (WBT) kullanın. Daha fazla bilgi için bkz: [Vance Morrison'ın blog gönderisi](http://blogs.msdn.com/b/vancem/archive/2012/12/19/collecting-etw-perfview-data-on-an-windows-rt-winrt-arm-surface-device.aspx).  
  
 Komut satırından PerfView de çalıştırabilirsiniz. Sağlayıcınızdan yalnızca olayları günlüğe kaydetmek için komut istemi penceresi açın ve aşağıdaki komutu girin:  
  
```  
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile   
```  
  
 burada:  
  
 `-KernelEvents:Process`  
 Ne zaman işlemi başlatır ve durdurur bilmek istediğiniz gösterir. Diğer olay sürelerinden çıkarılır için uygulamanız için işlem/başlangıç olayı olması gerekir.  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 PerfView varsayılan olarak açar ve Şirketim Uygulamam sağlayıcısında kapatır diğer sağlayıcılar devre dışı bırakır.  (Yıldız işareti, olduğunu gösteren bir <xref:System.Diagnostics.Tracing.EventSource>.)  
  
 `collect outputFile`  
 Toplama başlatmak ve outputFile.etl.zip için verileri kaydetmek istediğinizi belirtir.  
  
 PerfView başlattıktan sonra uygulamanızı çalıştırın. Uygulamanızı çalıştırırken unutmayın gereken birkaç şey vardır:  
  
-   Bir yayın derlemesinde hata ayıklama derlemesi kullanın. Hata ayıklama yapıları genellikle ek hata denetimi ve hata işleme uygulamanızı beklenenden daha yavaş çalışmasına neden olabilir kodunu içerir.  
  
-   Bir hata ayıklayıcısı ekli uygulamanızı çalıştıran, uygulamanızın performansını etkiler.  
  
-   Windows, uygulama başlatma işlemlerini hızlandırmak için birden çok önbelleğe alma stratejilerine kullanır. Uygulamanız şu anda bellekte önbelleğe alınmış ve diskten yüklü olması gerekmez, hızlı başlayacaktır. Tutarlılık sağlamak için başlatın ve uygulamanızı birkaç kez ölçme önce kapatın.  
  
 Böylece PerfView verilmiş olayları toplayabilir uygulamanızı çalıştırdıktan seçin **koleksiyonunu Durdur** düğmesi. Genellikle, gereksiz olayları alma için uygulamanızı kapatmadan önce koleksiyonu durdurmanız gerekir. Ancak, kapatma veya askıya performans ölçümleri gerçekleştiriyoruz, koleksiyon devam etmek istersiniz.  
  
## <a name="displaying-the-events"></a>Olayları görüntüleme  
 Zaten toplanan olayları görüntülemek için .etl açmak üzere PerfView kullanın veya. etl.zip dosya oluşturduğunuz ve seçin **olayları**. ETW toplanan olaylar, diğer işlemlerden olaylar dahil olmak üzere çok sayıda hakkında bilgiler. Araştırmanızı odaklanmak için aşağıdaki olaylar görünümü metin kutularına tamamlayın:  
  
-   İçinde **işlem filtre** kutusunda, uygulama adınızı (olmadan ".exe") belirtin.  
  
-   İçinde **olay türleri filtresi** kutusunda, belirtin `Process/Start | MyCompany-MyApp`. Bu olaylar için bir filtre Şirketim Uygulamam ve Windows çekirdek/işlem/başlangıç olayı ayarlar.  
  
 Sol bölmede listelenen tüm olayları seçin (Ctrl-A) ve **Enter** anahtarı. Şimdi, zaman damgaları her olaydan görüyor olmalısınız. Bu zaman damgaları izleme başlangıç göreli olduğundan, başlangıçtan itibaren geçen zamanı tanımlamak için işleminin başlangıç zamanından itibaren her olay sırada çıkartılacak sahip. İki zaman damgaları seçmek için Ctrl + Click kullanırsanız, sayfanın sonundaki durum çubuğunda görüntülenen aralarındaki fark görürsünüz. Bu, (işlem başlangıç dahil) görüntüsündeki herhangi iki olay arasında geçen süre görmeyi kolaylaştırır. Görünüm için kısayol menüsünü açın ve CSV dosyasına dışarı aktarma veya kaydetmek veya verileri işlemek için Microsoft Excel açılırken gibi yararlı seçenekleri sayısını seçin.  
  
 Özgün uygulamanızı ve sürüm için yordamı tekrarlayarak kullanılarak oluşturulan [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri, performans farkı karşılaştırabilirsiniz.   [!INCLUDE[net_native](../../../includes/net-native-md.md)] uygulamalar genellikle Başlat olmayan daha hızlı[!INCLUDE[net_native](../../../includes/net-native-md.md)] uygulamalar. Sorunda daha derin düşünüyorsanız PerfView en zaman ayırdığınız kodunuzu bölümlerini de tanımlayabilirsiniz. Daha fazla bilgi için izleme [PerfView öğreticileri](http://channel9.msdn.com/Series/PerfView-Tutorial) veya okuma [Vance Morrison'ın blog girdisi](http://blogs.msdn.com/b/vancem/archive/2011/12/28/publication-of-the-perfview-performance-analysis-tool.aspx).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.Tracing.EventSource>
