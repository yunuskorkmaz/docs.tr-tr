---
title: .NET Framework Performansı
ms.date: 03/30/2017
helpviewer_keywords:
- performance [.NET Framework]
- reliability [.NET Framework]
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3f3d035ebf6472788e2c7d6e11cb1a39708367b
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800335"
---
# <a name="net-framework-performance"></a>.NET Framework Performansı
Mükemmel performans gösteren uygulamalar oluşturmak isterseniz, herhangi bir uygulama özelliğini tasarladığınız gibi tasarlama yapmanız ve performans planlamanız gerekir. Microsoft tarafından sağlanan araçları uygulamalarınızın performansını ölçmek için kullanabilir, gerekirse de bellek kullanımında, kod veriminde ve yanıt vermesinde geliştirmeler yapabilirsiniz. Bu konu Microsoft'un sağladığı performans analiz araçlarını listeler ve uygulama geliştirmenin belirli alanları için performansı kapsayan diğer konulara bağlantılar sağlar.  
  
## <a name="designing-and-planning-for-performance"></a>Performans için tasarlama ve planlama  
 Mükemmel performanslı bir uygulama istiyorsanız, herhangi bir özelliği tasarlarken olduğu gibi, uygulama performansını uygulamanızda tasarlamanız gerekir. Uygulamanızda performans açısından kritik olan senaryoları belirlemeli, performans hedeflerini ayarlamalı ve bu uygulama senaryolarının performansını erken bir aşamada ve sıklıkla ölçmelisiniz. Her uygulama farklı olduğundan ve performans açısından farklı kritik yürütme yollarına sahip olduğundan bu yolların erken belirlenmesi ve çabalarınıza odaklanmak verimliliğinizi en üst düzeye çıkarmanızı sağlar.  
  
 Yüksek performanslı uygulama oluşturmak için hedef platform hakkında tamamen bilgi sahibi olmanız gerekmez. Ancak hedef platformunuzun hangi parçalarının maliyetli performans terimleri olduğuna ilişkin bir anlayış geliştirmelisiniz. Geliştirme sürecinin başlarında performansı ölçerek bunu yapabilirsiniz.  
  
 Performans için önemli olan alanları belirlemek ve başarım hedeflerinizi belirlemek için, her zaman kullanıcı deneyimini düşünün. Başlangıç saati ve yanıt verme hızı, uygulamanızın bir kullanıcının algılamasını etkileyecek iki önemli alandır. Uygulamanız çok miktarda bellek kullanıyorsa, kullanıcıya ağır görünüyor olabilir veya sistemde çalışan diğer uygulamaları etkileyebilir veya bazı durumlarda, Windows Mağazası'nı veya Windows Phone Mağazası gönderme işlemini başarısız kılabilir. Ayrıca kodunuzun hangi parçalarının daha sık yürütüleceğini belirler, kodlarınızın bu bölümlerinin iyileştirilmiş olduğundan emin olabilirsiniz.  
  
## <a name="analyzing-performance"></a>Performans çözümleme  
 Genel geliştirme planınızın bir parçası olarak, geliştirme sırasında uygulamanızın performansını ölçebileceğiniz ve sonuçları, daha önce belirlediğiniz hedeflerle karşılaştırabileceğiniz puanlar belirleyin. Uygulamanızı kullanıcılarınızın sahip olduğunu beklediğiniz donanım ve ortam içinde ölçün. Uygulamanızın performansını erken ve sıkça çözümleyerek, geliştirme döngüsünü daha sonra düzeltmenin pahalı olacağı mimari kararları değiştirebilirsiniz. Aşağıdaki bölümlerde, uygulamalarınızı çözümlemek ve bu araçlar tarafından kullanılan olay izlemeyi tartışmak için kullanabileceğiniz performans araçları açıklanmaktadır.  
  
### <a name="performance-tools"></a>Performans araçları  
 NET Framework uygulamaları ile kullanabileceğiniz bazı performans araçları şunlardır.  
  
|Aracı|Açıklama|  
|----------|-----------------|  
|Visual Studio Performans Analizi|Windows işletim sistemi çalıştıran bilgisayarlara dağıtılan .NET Framework uygulamalarınızı CPU kullanımı çözümlemek için kullanın.<br /><br /> Bu araç, bir projeyi açtıktan sonra Visual Studio 'daki **hata ayıklama** menüsünden kullanılabilir. Daha fazla bilgi için bkz. [Performans Gezgini](/visualstudio/profiling/performance-explorer). **Note:**  Windows Phone hedeflerken uygulama analizini Windows Phone (sonraki satıra bakın) kullanın.|  
|Windows Telefon Uygulama Çözümlemesi|CPU ve belleği, ağ veri aktarım hızını, uygulama yanıt verme becerisini ve Windows Phone uygulamalarınızda pil tüketimini çözümlemek için kullanın.<br /><br /> Bu araç, [Windows Phone SDK 'sını](https://go.microsoft.com/fwlink/?LinkId=265773)yükledikten sonra Visual Studio 'da bir Windows Phone projesi Için **hata ayıklama** menüsünden kullanılabilir. Daha fazla bilgi için bkz. [Windows Phone 8 Için uygulama profili oluşturma](https://docs.microsoft.com/previous-versions/windows/apps/jj215908(v=vs.105)).|  
|[PerfView](https://www.microsoft.com/download/details.aspx?id=28567)|CPU ve bellekle ilgili performans sorunlarını tanımlamak için kullanın. Bu araç atık toplama ve JIT derlemesi hakkında bilgilerin yanı sıra gelişmiş bellek ve CPU araştırmaları sağlamak için Windows (ETW) ve CLR Profil Oluşturma API'leri için olay izlemeyi kullanır. PerfView kullanma hakkında daha fazla bilgi için, uygulamanın, [Channel 9 video öğreticilerinin](https://channel9.msdn.com/Series/PerfView-Tutorial)ve [Blog gönderilerinin](https://blogs.msdn.microsoft.com/vancem/tag/perfview/)içerdiği öğretici ve yardım dosyalarına bakın.<br /><br /> Belleğe özgü sorunlar için bkz. [bellek araştırmaları Için PerfView kullanma](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots).|  
|[Windows Performans Çözümleyicisi](https://www.microsoft.com/download/details.aspx?id=30652)|Aynı bilgisayarda çoklu uygulamaları çalıştırırken, uygulamanın bellek ve depolama kullanmak gibi genel sistem başarımını belirlemek için kullanın. Bu araç, Windows 8 için Windows değerlendirme ve dağıtım seti 'nin (ADK) bir parçası olarak indirme merkezinden edinilebilir. Daha fazla bilgi için bkz. [Windows Performans Çözümleyici](/windows-hardware/test/wpt/windows-performance-analyzer).|  
  
### <a name="event-tracing-for-windows-etw"></a>Windows için olay izleme (ETW)  
 ETW, çalışma kodu hakkındaki tanı bilgisini elde etmenizi sağlayan bir tekniktir ve önceden bahsedilen performans araçlarından bir çoğu için gereklidir. ETW, .NET Framework uygulaması ve Windows nedeniyle özel olaylar oluştuğunda günlükler üretir. ETW ile, günlüğü dinamik olarak etkinleştirebilir ve devre dışı bırakabilirsiniz; böylelikle uygulamanızı yeniden başlatmadan üretim ortamında ayrıntılı izleme yapabilirsiniz. .NET Framework ETW olayları için destek sağlar ve ETW, performans verileri oluşturmak için çok sayıda profil oluşturma ve performans araçları tarafından kullanılır. Bu araçlar genellikle ETW olaylarını etkinleştirir ve devre dışı bırakır, dolayısıyla bunların bilinmesi yararlı olacaktır. Uygulamanızın belirli bileşenleri hakkında performans bilgileri toplamak için özel ETW olaylarını kullanabilirsiniz. .NET Framework ETW desteği hakkında daha fazla bilgi için, [görev paralel kitaplığı ve PLıNQ 'Da](etw-events-in-task-parallel-library-and-plinq.md) [ortak dil çalışma zamanı](etw-events-in-the-common-language-runtime.md) ve ETW olayları ' nda ETW olayları ' na bakın.  
  
## <a name="performance-by-app-type"></a>Uygulama türüne göre performans  
 .NET Framework uygulamasının her bir türünün, performans değerlendirmesi için kendi en iyi uygulamaları, düşünceleri ve araçları vardır. Aşağıdaki tablo, belirli .NET Framework uygulama türleriyle ilgili performans konularının bağlantılarını içermektedir.  
  
|Uygulama türü|Bkz.|  
|--------------|---------|  
|Tüm platformlar için .NET Framework uygulamalar|[Atık Toplama ve Performans](../../standard/garbage-collection/performance.md)<br /><br /> [Performans İpuçları](performance-tips.md)|  
|C++, C#Ve Visual Basic yazılan Windows 8. x Mağazası uygulamaları|[, C++ C#Ve Visual Basic kullanarak Windows Mağazası uygulamaları için en iyi performans uygulamaları](https://docs.microsoft.com/previous-versions/windows/apps/hh750313%28v=win.10%29)|  
|Windows Presentation Foundation (WPF)|[WPF performans paketi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa969767(v=vs.100))|  
|ASP.NET|[ASP.NET performansına genel bakış](https://docs.microsoft.com/previous-versions/aspnet/cc668225(v=vs.100))|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[.NET Framework Uygulamalarında Önbelleğe Alma](caching-in-net-framework-applications.md)|Uygulamanızda performansı yükseltmek için verileri önbelleğe alma tekniklerini açıklar.|  
|[Geç Başlatma](lazy-initialization.md)|Özellikle uygulamanın başlangıcında performansı artırmak için gerektiği şekilde nesnelerin nasıl başlatılacağını açıklar.|  
|[Güvenilirlik](reliability.md)|Bir sunucu ortamında zaman uyumsuz özel durumları engellemek hakkında bilgi sağlar.|  
|[Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma](writing-large-responsive-apps.md)|Yönetilen koddaki C# ve Visual Basic derleyicilerini yeniden yazmadan toplanan performans ipuçları sağlar ve C# derleyicisinden birkaç gerçek örnek içerir.|
