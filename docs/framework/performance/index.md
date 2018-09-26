---
title: .NET Framework Performansı
ms.date: 03/30/2017
helpviewer_keywords:
- performance [.NET Framework]
- reliability [.NET Framework]
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59f8ceaf7981aebf3ae64e10d253004780f47e50
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47199456"
---
# <a name="net-framework-performance"></a>.NET Framework Performansı
Mükemmel performans gösteren uygulamalar oluşturmak istiyorsanız, tasarım ve performans planlamanız başka bir uygulama özelliğini tasarladığınız gibi. Microsoft tarafından sağlanan araçları uygulamalarınızın performansını ölçmek için vb., gerekirse, bellek kullanımı, kod veriminde ve yanıt hızını iyileştirme yapın. Bu konu, Microsoft sağlar ve uygulama geliştirmenin belirli alanları için performansı kapsayan diğer konulara bağlantılar sağlar Performans analiz araçlarını listeler.  
  
## <a name="designing-and-planning-for-performance"></a>Performans için planlama ve tasarlama  
 Mükemmel performanslı bir uygulama istiyorsanız, yalnızca diğer herhangi bir özelliği tasarlarken olduğu gibi performans uygulamanızda tasarlamanız gerekir. Performans açısından kritik senaryolar, uygulama, performans hedeflerini ayarlamalı ve bu uygulama senaryolarının performansını erken ve sıkça belirlemeniz gerekir. Her uygulama farklıdır ve farklı bir performans açısından kritik yürütme yollarına sahip olduğundan bu yolların erken belirlenmesi ve çabalarınıza odaklanmak verimliliğinizi en üst düzeye çıkarmak için etkinleştirin.  
  
 Yüksek performanslı uygulama oluşturmak için hedef platform hakkında tamamen bilgi sahibi olmanız gerekmez. Ancak hedef platformunuzu bölümlerini maliyetli performans terimleri olduğuna ilişkin bir anlayış geliştirmelisiniz. Geliştirme sürecinin başlarında performansı ölçerek bunu yapabilirsiniz.  
  
 Performans için önemli olan alanları belirlemek ve başarım hedeflerinizi belirlemek için her zaman kullanıcı deneyimini düşünün. Başlangıç saati ve yanıt hızı, uygulamanızın bir kullanıcının algılamasını etkileyecek iki önemli alandır var. Uygulamanız çok miktarda bellek kullanıyorsa, kullanıcıya ağır görünüyor veya sistemde çalışan diğer uygulamaları etkileyebilir veya bazı durumlarda, Windows Store veya Windows Phone Store gönderme işlemi başarısız olabilir. Ayrıca kodunuzun hangi parçalarının daha sık yürütüleceğini belirler, bu bölümlerinin iyileştirilmiş olduğundan da emin yapabilirsiniz.  
  
## <a name="analyzing-performance"></a>Performans çözümleme  
 Genel Geliştirme planınızın bir parçası olarak noktalarını geliştirme sırasında burada ölçersiniz uygulamanızın performansını ayarlamak ve önceden ayarlanan hedefleri sonuçlarını karşılaştırın. Uygulamanızı kullanıcılarınızın sahip olmasını beklediğiniz donanım ve ortam içinde ölçün. Uygulamanızın performansını erken ve sıkça çözümleyerek, daha sonra gelişim döngüsünde düzeltmek pahalı olur mimari kararları değiştirebilirsiniz. Aşağıdaki bölümlerde, uygulamalarınızı çözümlemek ve bu araçlar tarafından kullanılan olay izlemeyi tartışmak için kullanabileceğiniz performans araçları açıklanmaktadır.  
  
### <a name="performance-tools"></a>Performans araçları  
 .NET Framework uygulamalarınızı ile kullanabileceğiniz performans araçları bazıları aşağıda verilmiştir.  
  
|Aracı|Açıklama|  
|----------|-----------------|  
|Visual Studio Performans Analizi|Windows işletim sistemi çalıştıran bilgisayarlara dağıtılan .NET Framework uygulamalarınızı CPU kullanımı çözümlemek için kullanın.<br /><br /> Bu araç kullanılabilir **hata ayıklama** Visual Studio'da bir proje açtıktan sonra menü. Daha fazla bilgi için [performans Gezgini](/visualstudio/profiling/performance-explorer). **Not:** kullanım Windows Phone Uygulama analizi (sonraki satıra bakın) Windows Phone hedeflenirken.|  
|Windows Phone Uygulama analizi|CPU ve bellek, ağ veri aktarım hızını, uygulama yanıt verme hızını ve Windows Phone uygulamalarınızda pil tüketimini çözümlemek için kullanın.<br /><br /> Bu araç kullanılabilir **hata ayıklama** yükledikten sonra Visual Studio'da bir Windows Phone projesi için menü [Windows Phone SDK'sı](https://go.microsoft.com/fwlink/?LinkId=265773). Daha fazla bilgi için [uygulamasını Windows Phone için profil oluşturma](https://msdn.microsoft.com/library/windowsphone/develop/jj215908\(v=vs.105\).aspx).|  
|[PerfView](https://www.microsoft.com/download/details.aspx?id=28567)|CPU ve bellekle ilgili performans sorunlarını tanımlamak için kullanın. Bu araç atık toplama ve JIT derlemesi hakkında bilgilerin yanı sıra gelişmiş bellek ve CPU araştırmaları sağlamak için Windows (ETW) ve CLR Profil oluşturma API'leri için olay izleme kullanır. PerfView kullanma hakkında daha fazla bilgi için bkz uygulama ile birlikte gelen eğitim ve Yardım dosyaları [kanal 9 video eğitimleri](http://channel9.msdn.com/Series/PerfView-Tutorial), ve [blog gönderilerini](https://blogs.msdn.com/b/vancem/archive/tags/perfview/).<br /><br /> Belleğe özgü sorunlar için bkz: [kullanarak bellek incelemeleri için PerfView](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots).|  
|[Windows Performans Çözümleyicisi](https://www.microsoft.com/download/details.aspx?id=30652)|Aynı bilgisayarda çoklu uygulamaları çalıştırırken, uygulamanızın bellek ve depolama kullanmak gibi genel sistem başarımını belirlemek için kullanın. Bu araç İndirme Merkezi'nden Windows değerlendirme ve dağıtım Seti'nin (ADK) parçası olarak kullanılabilir [!INCLUDE[win8](../../../includes/win8-md.md)]. Daha fazla bilgi için [Windows Performans Çözümleyicisi](https://msdn.microsoft.com/library/windows/desktop/hh448170.aspx).|  
  
### <a name="event-tracing-for-windows-etw"></a>Olay izleme için Windows (ETW)  
 ETW, çalışma kodu hakkındaki tanı bilgisini elde sağlar ve önceden bahsedilen performans araçlarından birçoğunu önemlidir bir tekniktir. ETW, .NET Framework uygulamaları ve Windows tarafından belirli olaylar oluştuğunda günlükler üretir. ETW ile etkinleştirebilir ve böylece uygulamanızı yeniden başlatmadan üretim ortamında ayrıntılı izleme gerçekleştirebilir, günlüğü dinamik olarak devre dışı bırakın. .NET Framework ETW olayları için destek sağlar ve ETW, performans verileri oluşturmak için birçok profil oluşturma ve performans araçları tarafından kullanılır. Bu araçlar genellikle etkinleştirin ve bunların bilinmesi yararlı olacak şekilde ETW olaylarını devre dışı bırakın. Uygulamanızın belirli bileşenleri hakkında performans bilgileri toplamak için özel ETW olaylarını kullanabilirsiniz. .NET Framework içindeki ETW desteği hakkında daha fazla bilgi için bkz. [ortak dil çalışma zamanı modülünde ETW olayları](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md) ve [görev paralel kitaplığı ve PLINQ'da ETW olayları](../../../docs/framework/performance/etw-events-in-task-parallel-library-and-plinq.md).  
  
## <a name="performance-by-app-type"></a>Uygulama türüne göre performans  
 .NET Framework uygulamasının her türü kendi en iyi yöntemler, konuları ve performans değerlendirme araçları vardır. Aşağıdaki tablo performans konularının bağlantılarını belirli .NET Framework uygulama türleri için.  
  
|Uygulama türü|Bkz. |  
|--------------|---------|  
|Tüm platformlar için .NET framework uygulamaları|[Atık Toplama ve Performans](../../../docs/standard/garbage-collection/performance.md)<br /><br /> [Performans İpuçları](../../../docs/framework/performance/performance-tips.md)|  
|[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] C++, C# ve Visual Basic içinde yazılan uygulamalar|[C++, C# ve Visual Basic kullanan Windows Store uygulamaları için en iyi performans](https://msdn.microsoft.com/library/windows/apps/hh750313.aspx)|  
|Windows Phone|[Windows Phone için uygulama performans değerlendirmeleri](https://msdn.microsoft.com/library/windowsphone/develop/ff967560\(v=vs.105\).aspx)<br /><br /> [Windows Phone Uygulama analizi](https://msdn.microsoft.com/library/windowsphone/develop/hh202934\(v=vs.105\).aspx)<br /><br /> [Windows Phone uygulamalarınızı daha hızlı Market'te Al](https://msdn.microsoft.com/magazine/hh781024.aspx)|  
|Windows Presentation Foundation (WPF)|[WPF Performans paketi](https://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e)|  
|Silverlight|[Performans İpuçları](https://msdn.microsoft.com/library/cc189071\(v=vs.95\).aspx)|  
|ASP.NET|[ASP.NET performansa genel bakış](https://msdn.microsoft.com/library/f882bf1b-a009-4312-ac06-74370ffabc0b)|  
|Windows Forms|[Windows Forms uygulamalarının performansını artırmak için pratik ipuçları](https://msdn.microsoft.com/magazine/cc163630.aspx)|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[.NET Framework Uygulamalarında Önbelleğe Alma](../../../docs/framework/performance/caching-in-net-framework-applications.md)|Uygulamanızın performansını artırmak için verileri önbelleğe alma tekniklerini açıklar.|  
|[Geç Başlatma](../../../docs/framework/performance/lazy-initialization.md)|Özellikle uygulamanın başlangıcında performansı artırmak için gerektiğinde nesnelerinin nasıl başlatılacağını açıklar.|  
|[Güvenilirlik](../../../docs/framework/performance/reliability.md)|Bir sunucu ortamında zaman uyumsuz özel durumları önleme hakkında bilgi sağlar.|  
|[Büyük, Yanıt Veren .NET Framework Uygulamaları Yazma](../../../docs/framework/performance/writing-large-responsive-apps.md)|Performans İpuçları C# ve Visual Basic derleyicileri, yönetilen kodda yeniden yazma toplanan ve birkaç gerçek örnekler C# derleyicisi içerir sağlar.|
