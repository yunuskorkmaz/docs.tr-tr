---
title: Hata Ayıklama, İzleme ve Profil Oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
ms.openlocfilehash: 1a43c7fbcb810b22ff9bc409c233d2b1da67370e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217400"
---
# <a name="debugging-tracing-and-profiling"></a>Hata Ayıklama, İzleme ve Profil Oluşturma
.NET Framework bir uygulamada hata ayıklamak için, derleyici ve çalışma zamanı ortamı, bir hata ayıklayıcının uygulamaya iliştirmesine ve mümkünse hem semboller hem de çizgi haritaları (mümkünse, uygulama ve karşılık gelen Microsoft ara Dil (MSIL). Yönetilen bir uygulamanın hatası ayıklandıktan sonra, performansı artırmak için profili oluşturulabilir. Profil oluşturma, en sık yürütülen kodu oluşturan kaynak kodu satırlarını ve bunların yürütülmesi için ne kadar zaman harcanduğunu değerlendirir ve tanımlar.  
  
 .NET Framework uygulamalar, birçok yapılandırma ayrıntılarını işleyen Visual Studio kullanılarak kolayca hata ayıklamalıdır. Visual Studio yüklü değilse, .NET Framework <xref:System.Diagnostics> ad alanındaki hata ayıklama sınıflarını kullanarak .NET Framework uygulamalarının performansını inceleyebilir ve geliştirebilirsiniz. Bu ad alanı, yürütme akışını izlemek için <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>ve <xref:System.Diagnostics.TraceSource> sınıflarını ve profil oluşturma kodu için <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>ve <xref:System.Diagnostics.PerformanceCounter> sınıflarını içerir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [JIT-Ekleme Hata Ayıklamayı Etkinleştirme](enabling-jit-attach-debugging.md)  
 Bir .NET Framework uygulamasına bir hata ayıklama altyapısını JıT olarak eklemek için kayıt defterinin nasıl yapılandırılacağını gösterir.  
  
 [Görüntüde Hata Ayıklamayı Kolaylaştırma](making-an-image-easier-to-debug.md)  
 Derlemeyi hata ayıklamanın daha kolay hale getirmek için JıT izlemenin açık ve en iyi duruma getirme özelliğini nasıl kullanacağınızı gösterir.  
  
 [İzleme ve İşaretleme Uygulamaları](tracing-and-instrumenting-applications.md)  
 Uygulamasının çalışırken nasıl yapıldığını ve ne kadar iyi bir şeyin yanlış geçmiş olduğunu görüntülemek için nasıl ekleneceğini açıklar.  
  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)  
 Çalışma zamanı durumu hakkında bilgi sağlamak için ortak dil çalışma zamanı (CLR) ile birlikte çalışan hata ayıklama yardımlarından oluşan yönetilen hata ayıklama yardımcıları 'nı (MDAs) açıklar.  
  
 [Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme](enhancing-debugging-with-the-debugger-display-attributes.md)  
 Bir tür geliştiricisinin bir hata ayıklayıcıda görüntülendiğinde ne tür görüneceğini nasıl belirtbileceklerini açıklar.  
  
 [Performans Sayaçları](performance-counters.md)  
 Bir uygulamanın performansını izlemek için kullanabileceğiniz sayaçları açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Visual Studio 'da ASP.NET veya ASP.NET Core uygulamalarında hata ayıklama](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)  
 Geliştirme sırasında veya dağıtımdan sonra bir ASP.NET uygulamasında hata ayıklama için önkoşul ve yönergeler sağlar.  
  
 [Geliştirme Kılavuzu](../development-guide.md)  
 Dinamik programlama, birlikte çalışabilirlik, genişletilebilirlik, bellek yönetimi ve iş parçacığı oluşturma hakkında uygulama ve bilgilerinizi oluşturma, yapılandırma, hatasını ayıklama, güvenliğini sağlama ve dağıtma gibi, uygulama geliştirmesine yönelik tüm temel teknoloji alanları ve görevleri için kılavuz sağlar.
