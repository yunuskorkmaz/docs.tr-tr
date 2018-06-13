---
title: .NET Framework Performansı
ms.date: 03/30/2017
helpviewer_keywords:
- performance [.NET Framework]
- reliability [.NET Framework]
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ebfe03ea99f7a9c66fb46f01b37f85daf9e919d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397305"
---
# <a name="net-framework-performance"></a>.NET Framework Performansı
Uygulamaları ile harika performans oluşturmak istiyorsanız, tasarım ve performans için yalnızca planlamanız gerekir, uygulamanızın herhangi bir özellik tasarlarken. Size Microsoft tarafından sağlanan araçları, uygulamanızın performansını ölçmek için kullanıp, gerekirse, bellek kullanımı, kod verimlilik ve yanıt hızını iyileştirmeler sağlar. Bu konu, Microsoft sağlar ve performans için uygulama geliştirme belirli alanlarında kapak diğer konulara bağlantılar sağlanır performans çözümleme araçları listeler.  
  
## <a name="designing-and-planning-for-performance"></a>Tasarlama ve performans için planlama  
 Harika bir gerçekleştirme uygulama istiyorsanız, diğer herhangi bir özelliği Tasarım olarak uygulamanıza performans tasarlamanız gerekir. Erken ve genellikle uygulama, kümesi performans hedeflerini ve bu uygulama senaryolarında ölçü performans performans açısından kritik senaryolarda belirlemeniz gerekir. Her uygulama farklıdır ve farklı performans açısından kritik yürütme yoluna sahip olduğundan, bu yollar erken belirleme ve çabalarınız odaklanan üretkenliğinizi en üst düzeye çıkarmak için etkinleştirin.  
  
 Yüksek performanslı uygulama oluşturmak için hedef platformunuzu tamamen bilgi sahibi olmanız gerekmez. Ancak hedef platformunuzu bölümlerini performans açısından pahalı bir anlama geliştirmelisiniz. Performansı geliştirme sürecini başlarında ölçerek bunu yapabilirsiniz.  
  
 Her zaman performansını önemli alanları belirlemek ve performans hedefleriniz oluşturmak için kullanıcı deneyimini göz önünde bulundurun. Başlangıç zamanı ve yanıtlama hızı uygulamanızı kullanıcının algısı etkileyen iki önemli alanlar şunlardır. Uygulamanız çok miktarda bellek kullanıyorsa, kullanıcıya ağır görünür veya sistem üzerinde çalışan diğer uygulamaları etkiler veya, bazı durumlarda, Windows mağazası veya Windows Phone mağazası gönderme işlemi başarısız olabilir. Ayrıca, hangi kısımlarının kodunuzu daha sık yürütme karar verirseniz, kodunuzu bu kısımları da iyileştirilmiş emin olabilirsiniz.  
  
## <a name="analyzing-performance"></a>Performans çözümleme  
 Parçası olarak genel geliştirme planınız, noktaları geliştirme sırasında nerede ölçecek, uygulamanızın performansını ayarlama ve daha önce ayarlamış hedefleri sonucu karşılaştırın. Kullanıcılarınızı beklediğiniz donanım ve ortamı uygulamanızda ölçün. Erken ve genellikle, uygulamanızın performansı çözümleyerek maliyetli ve daha sonra geliştirme döngüsü çözmek pahalı olabilir mimari kararlar değiştirebilirsiniz. Aşağıdaki bölümlerde, uygulamalarınızı analiz etmek ve bu araçları tarafından kullanılan olay izleme tartışmak için kullanabileceğiniz performans araçları açıklanmaktadır.  
  
### <a name="performance-tools"></a>Performans araçları  
 .NET Framework uygulamalarınızı ile kullanabileceğiniz performans araçları bazıları aşağıda verilmiştir.  
  
|Aracı|Açıklama|  
|----------|-----------------|  
|Visual Studio Performans Analizi|.NET Framework uygulamalarınızın Windows işletim sistemi çalıştıran bilgisayarlara dağıtılacak CPU kullanımı çözümlemek için kullanın.<br /><br /> Bu aracı kullanılabilir **hata ayıklama** bir projeyi açtığınızda Visual Studio menüsünde. Daha fazla bilgi için bkz: [performans Gezgini](/visualstudio/profiling/performance-explorer). **Not:** kullanım Windows Phone Uygulama analizi (sonraki satıra bakın) Windows Phone hedeflerken.|  
|Windows Phone Uygulama analizi|CPU ve bellek, ağ veri aktarım hızı, uygulama yanıt hızını ve Windows Phone uygulamalarınızı pil tüketimini çözümlemek için kullanın.<br /><br /> Bu aracı kullanılabilir **hata ayıklama** yüklendikten sonra Visual Studio içinde Windows Phone projesi için menü [Windows Phone SDK'sı](http://go.microsoft.com/fwlink/?LinkId=265773). Daha fazla bilgi için bkz: [Windows Phone için uygulama profil](http://msdn.microsoft.com/library/windowsphone/develop/jj215908\(v=vs.105\).aspx).|  
|[PerfView](http://www.microsoft.com/download/details.aspx?id=28567)|CPU ve bellekle ilgili performans sorunlarını tanımlamak için kullanın. Olay izleme, bu aracı çöp toplama ve JIT derleme hakkında bilgi yanı sıra gelişmiş bellek ve CPU araştırmalar sağlamak için Windows (ETW) ve CLR API'leri profil için kullanır. Uygulamayla birlikte öğretici ve Yardım dosyaları PerfView kullanma hakkında daha fazla bilgi için bkz: [Channel 9 video öğreticilerinin](http://channel9.msdn.com/Series/PerfView-Tutorial), ve [blog gönderileri](http://blogs.msdn.com/b/vancem/archive/tags/perfview/).<br /><br /> Bellek özgü sorunları için bkz: [kullanarak PerfView bellek araştırmalar için](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots).|  
|[Windows Performans Çözümleyicisi](http://www.microsoft.com/download/details.aspx?id=30652)|Aynı bilgisayara birden fazla uygulama çalışırken, uygulamanızın bellek ve depolama alanı kullanmak gibi genel sistem performansını belirlemek için kullanın. Bu aracı Yükleme Merkezi'nden Windows değerlendirme ve dağıtım Seti'nin (ADK) bir parçası olarak kullanılabilir [!INCLUDE[win8](../../../includes/win8-md.md)]. Daha fazla bilgi için bkz: [Windows Performans Çözümleyicisi](http://msdn.microsoft.com/library/windows/desktop/hh448170.aspx).|  
  
### <a name="event-tracing-for-windows-etw"></a>Olay izleme için Windows (ETW)  
 ETW kodu çalıştırma hakkında tanılama bilgilerini elde etmek olanak tanır ve çok daha önce bahsedilen performans araçları için gerekli olan bir tekniktir. .NET Framework uygulamalarını ve Windows tarafından belirli olaylar ortaya çıktığında ETW günlükleri oluşturur. ETW ile etkinleştirin ve dinamik günlüğü, ayrıntılı izleme bir üretim ortamında, uygulamanızın yeniden başlatmanıza gerek kalmadan gerçekleştirebilmeleri için devre dışı. .NET Framework ETW olayları için destek sağlar ve ETW performans verileri oluşturmak için birçok profil oluşturma ve performans araçları tarafından kullanılır. Bu araçlar genellikle etkinleştirmek ve bunları aşina yararlı olacak şekilde ETW olayları devre dışı. Belirli ETW olayları, uygulamanızın belirli bileşenler hakkında performans bilgileri toplamak için kullanabilirsiniz. .NET Framework ETW desteği hakkında daha fazla bilgi için bkz: [ortak dil çalışma zamanında ETW olayları](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md) ve [görev paralel kitaplığı ve PLINQ'da ETW olayları](../../../docs/framework/performance/etw-events-in-task-parallel-library-and-plinq.md).  
  
## <a name="performance-by-app-type"></a>Uygulama türüne göre performans  
 .NET Framework uygulama her türünü kendi en iyi yöntemler, ilgili önemli noktalar ve performans değerlendirme araçları vardır. Aşağıdaki tabloda performansı konulara bağlantılar belirli .NET Framework uygulama türleri için.  
  
|Uygulama türü|Bkz. |  
|--------------|---------|  
|Tüm platformlar için .NET framework uygulamaları|[Atık Toplama ve Performans](../../../docs/standard/garbage-collection/performance.md)<br /><br /> [Performans İpuçları](../../../docs/framework/performance/performance-tips.md)|  
|[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] C++, C# ve Visual Basic içinde yazılmış uygulamalar|[C++, C# ve Visual Basic kullanarak Windows mağazası uygulamaları için performansı en iyi yöntemler](http://msdn.microsoft.com/library/windows/apps/hh750313.aspx)|  
|Windows Phone|[Windows Phone için uygulama başarım düşünceleri](http://msdn.microsoft.com/library/windowsphone/develop/ff967560\(v=vs.105\).aspx)<br /><br /> [Windows Phone Uygulama analizi](http://msdn.microsoft.com/library/windowsphone/develop/hh202934\(v=vs.105\).aspx)<br /><br /> [Windows Phone uygulamalarınızı daha hızlı Market Al](http://msdn.microsoft.com/magazine/hh781024.aspx)|  
|Windows Presentation Foundation (WPF)|[WPF Performans paketi](http://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e)|  
|Silverlight|[Performans İpuçları](http://msdn.microsoft.com/library/cc189071\(v=vs.95\).aspx)|  
|ASP.NET|[ASP.NET Performans genel bakış](http://msdn.microsoft.com/library/f882bf1b-a009-4312-ac06-74370ffabc0b)|  
|Windows Forms|[Windows Forms uygulamaları performansını artırma pratik ipuçları](http://msdn.microsoft.com/magazine/cc163630.aspx)|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[.NET Framework Uygulamalarında Önbelleğe Alma](../../../docs/framework/performance/caching-in-net-framework-applications.md)|Uygulamanızın performansını artırmak için verileri önbelleğe alma için teknikleri açıklar.|  
|[Geç Başlatma](../../../docs/framework/performance/lazy-initialization.md)|Nesneleri özellikle uygulama başlatma sırasında performansı artırmak için gerektiği başlatmak açıklar.|  
|[Güvenilirlik](../../../docs/framework/performance/reliability.md)|Bir sunucu ortamında zaman uyumsuz özel durumları önleme hakkında bilgi sağlar.|  
|[Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma](../../../docs/framework/performance/writing-large-responsive-apps.md)|Performans İpuçları C# ve Visual Basic derleyicileri yönetilen kod yeniden yazma toplanır ve C# Derleyici birkaç gerçek örneklerinden içerir sağlar.|
