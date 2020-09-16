---
title: .NET Framework Performansı
description: .NET uygulamalarınızda performansı tasarlayın ve planlayın. Uygulamanızın performansını ölçmek ve geliştirmeler yapmak için Microsoft tarafından sunulan araçları kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- performance [.NET Framework]
- reliability [.NET Framework]
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
ms.openlocfilehash: 50ba2f51ea2fb935c2a5db27ad6249e87cb86dc7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554664"
---
# <a name="net-framework-performance"></a>.NET Framework Performansı
Harika performansa sahip uygulamalar oluşturmak istiyorsanız, uygulamanızın başka bir özelliğini tasarladığınızda olduğu gibi, performansı tasarlamalısınız ve planlamanız gerekir. Uygulamanızın performansını ölçmek için Microsoft tarafından sunulan araçları kullanabilir ve gerekirse, bellek kullanımı, kod işleme ve yanıt verme için geliştirmeler yapabilirsiniz. Bu konu, Microsoft 'un sağladığı performans analizi araçlarını listeler ve uygulama geliştirmenin belirli alanlarının performansını kapsayan diğer konulara bağlantılar sağlar.  
  
## <a name="designing-and-planning-for-performance"></a>Performans için tasarlama ve planlama  
 Harika bir uygulama kullanmak istiyorsanız, herhangi bir özelliği tasarlayacağınızda, uygulamanızın performansını yapmanız gerekir. Uygulamanızda performans açısından kritik senaryoları belirlemelisiniz, performans hedeflerini ayarlayabilir ve bu uygulama senaryolarına yönelik performansı erken ve sık ölçmelisiniz. Her uygulama farklı olduğundan ve performans açısından kritik yürütme yollarına farklı olduğundan, bu yolların erken belirlenmesi ve çabalarınızın odaklanması, üretkenliğinizi en üst düzeye çıkarmanızı sağlar.  
  
 Yüksek performanslı bir uygulama oluşturmak için hedef platformunuza tamamen alışmeniz gerekmez. Bununla birlikte, hedef platformunuzun hangi bölümlerinin performans açısından maliyetli olduğunu anlamak için geliştirme yapmanız gerekir. Geliştirme sürecinizdeki performansı daha erken ölçerek bunu yapabilirsiniz.  
  
 Performans açısından önemli olan ve performans hedeflerinizi oluşturmak için her zaman kullanıcı deneyimini göz önünde bulundurun. Başlangıç zamanı ve yanıt hızı, kullanıcının uygulamanızın kullanımını etkileyecek iki temel alan olur. Uygulamanız çok miktarda bellek kullanıyorsa, Kullanıcı için yavaş görünebilir veya sistemde çalışan diğer uygulamaları etkileyebilir veya bazı durumlarda Windows Mağazası veya Windows Phone Store gönderim sürecinde başarısız olabilir. Ayrıca, kodunuzun hangi bölümlerinin daha sık yürütüleceğini belirlerseniz, kodunuzun bu bölümlerinin iyi iyileştirildiğinden emin olabilirsiniz.  
  
## <a name="analyzing-performance"></a>Performans çözümleme  
 Genel geliştirme planınızın bir parçası olarak, geliştirme sırasında uygulamanızın performansını ölçecek ve sonuçları daha önce ayarladığınız hedeflerle karşılaştıran noktaları belirleyin. Uygulamanızı, kullanıcılarınızın sahip olmasını bekleyen ortamda ve donanımda ölçün. Uygulamanızın performansını erken çözümleyerek ve genellikle geliştirme döngüsünün ilerleyen kısımlarında daha sonra düzeltilmesi gereken mimari kararları değiştirebilirsiniz. Aşağıdaki bölümlerde, uygulamalarınızı çözümlemek ve bu araçlar tarafından kullanılan olay izlemeyi tartışmak için kullanabileceğiniz performans araçları açıklanmaktadır.  
  
### <a name="performance-tools"></a>Performans araçları  
 .NET Framework uygulamalarınızla kullanabileceğiniz bazı performans araçları aşağıda verilmiştir.  
  
|Araç|Açıklama|  
|----------|-----------------|  
|Visual Studio performans analizi|Windows işletim sistemi çalıştıran bilgisayarlara dağıtılacak .NET Framework uygulamalarınızın CPU kullanımını çözümlemek için kullanın.<br /><br /> Bu araç, bir projeyi açtıktan sonra Visual Studio 'daki **hata ayıklama** menüsünden kullanılabilir. Daha fazla bilgi için bkz. [Performans Gezgini](/visualstudio/profiling/performance-explorer). **Note:**  Windows Phone hedeflerken uygulama analizini Windows Phone (sonraki satıra bakın) kullanın.|  
|Uygulama analizini Windows Phone|Windows Phone uygulamalarınızda CPU ve bellek, ağ veri aktarım hızı, uygulama yanıt hızı ve pil tüketimini çözümlemek için kullanın.<br /><br /> Bu araç, [Windows Phone SDK 'sını](https://go.microsoft.com/fwlink/?LinkId=265773)yükledikten sonra Visual Studio 'da bir Windows Phone projesi Için **hata ayıklama** menüsünden kullanılabilir. Daha fazla bilgi için bkz. [Windows Phone 8 Için uygulama profili oluşturma](/previous-versions/windows/apps/jj215908(v=vs.105)).|  
|[PerfView](https://www.microsoft.com/download/details.aspx?id=28567)|CPU ve bellekle ilgili performans sorunlarını belirlemek için kullanın. Bu araç, gelişmiş bellek ve CPU araştırmaları ve çöp toplama ve JıT derleme hakkında bilgi sağlamak için Windows için olay izleme (ETW) ve CLR profil oluşturma API 'Lerini kullanır. PerfView kullanma hakkında daha fazla bilgi için, uygulamanın, [Channel 9 video öğreticilerinin](https://channel9.msdn.com/Series/PerfView-Tutorial)ve [Blog gönderilerinin](/archive/blogs/vancem/)içerdiği öğretici ve yardım dosyalarına bakın.<br /><br /> Belleğe özgü sorunlar için bkz. [bellek araştırmaları Için PerfView kullanma](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots).|  
|[Windows Performans Çözümleyicisi](https://www.microsoft.com/download/details.aspx?id=30652)|Aynı bilgisayarda birden çok uygulama çalışırken uygulamanızın belleği ve depolama alanı kullanımı gibi genel sistem performansının belirlenmesi için kullanın. Bu araç, Windows 8 için Windows değerlendirme ve dağıtım seti 'nin (ADK) bir parçası olarak indirme merkezinden edinilebilir. Daha fazla bilgi için bkz. [Windows Performans Çözümleyici](/windows-hardware/test/wpt/windows-performance-analyzer).|
  
### <a name="event-tracing-for-windows-etw"></a>Windows için olay izleme (ETW)  
 ETW, çalışan kod hakkında tanılama bilgileri elde etmenizi sağlayan ve daha önce bahsedilen birçok performans aracı için gerekli olan bir tekniktir. ETW, belirli olaylar .NET Framework uygulamalar ve Windows tarafından başlatıldığında Günlükler oluşturur. ETW ile günlüğü dinamik olarak etkinleştirebilir ve devre dışı bırakabilir. böylece, uygulamanızı yeniden başlatmadan bir üretim ortamında ayrıntılı izleme yapabilirsiniz. .NET Framework ETW olayları için destek sağlar ve ETW, performans verileri oluşturmak için birçok profil oluşturma ve performans aracı tarafından kullanılır. Bu araçlar, ETW olaylarını etkinleştirir ve devre dışı bırakır. bu nedenle, bunlarla benzerlik yararlı olur. Uygulamanızın belirli bileşenleriyle ilgili performans bilgilerini toplamak için belirli ETW olayları kullanabilirsiniz. .NET Framework ETW desteği hakkında daha fazla bilgi için, [görev paralel kitaplığı ve PLıNQ 'Da](etw-events-in-task-parallel-library-and-plinq.md) [ortak dil çalışma zamanı](etw-events-in-the-common-language-runtime.md) ve ETW olayları ' nda ETW olayları ' na bakın.  
  
## <a name="performance-by-app-type"></a>Uygulama türüne göre performans  
 .NET Framework uygulamasının her türü, performansı değerlendirmek için kendi en iyi uygulamalarına, noktalara ve araçlarına sahiptir. Aşağıdaki tablo, belirli .NET Framework uygulama türleri için performans konularına bağlantı sağlar.  
  
|Uygulama türü|Bkz.|  
|--------------|---------|  
|Tüm platformlar için .NET Framework uygulamalar|[Çöp toplama ve performans](../../standard/garbage-collection/performance.md)<br /><br /> [Performans Ipuçları](performance-tips.md)|  
|C++, C# ve Visual Basic yazılan Windows 8. x Mağazası uygulamaları|[C++, C# ve Visual Basic kullanarak Windows Mağazası uygulamaları için en iyi performans uygulamaları](/previous-versions/windows/apps/hh750313(v=win.10))|  
|Windows Presentation Foundation (WPF)|[WPF performans paketi](/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))|  
|ASP.NET|[ASP.NET performansına genel bakış](/previous-versions/aspnet/cc668225(v=vs.100))|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[.NET Framework Uygulamalarında Önbelleğe Alma](caching-in-net-framework-applications.md)|Uygulamanızdaki performansı artırmak için verileri önbelleğe alma tekniklerini açıklar.|  
|[Yavaş Başlatma](lazy-initialization.md)|Özellikle uygulama başlangıcında, performansı artırmak için nesnelerin gerekli olduğu gibi nasıl başlatılacağını açıklar.|  
|[Güvenilirlik](reliability.md)|Bir sunucu ortamında zaman uyumsuz özel durumların önlenmesi hakkında bilgi sağlar.|  
|[Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma](writing-large-responsive-apps.md)|Yönetilen koddaki C# ve Visual Basic derleyicileri yeniden yazarken toplanan performans ipuçları sağlar ve C# derleyicisinden birçok gerçek örnek içerir.|
