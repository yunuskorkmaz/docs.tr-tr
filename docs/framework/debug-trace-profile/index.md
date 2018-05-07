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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 481360f731297e1c287c969e6524c68e0c9c0b7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-tracing-and-profiling"></a>Hata Ayıklama, İzleme ve Profil Oluşturma
.NET Framework uygulama hatalarını ayıklamak için derleyici ve çalışma zamanı ortamı uygulamaya eklemek bir hata ayıklayıcısı etkinleştirmek için yapılandırılmış olmalıdır ve hem simge hem de satır üretmek için Mümkünse, uygulama ve onun karşılık gelen Microsoft Ara eşlemeleri dili (MSIL). Yönetilen bir uygulamanın hata ayıklaması sonra performansı artırmak için profili. Profil oluşturma değerlendirir ve en sık yürütülen kod oluşturma kaynak kod satırlarını açıklar ve ne kadar sürer bunları yürütmek için saat.  
  
 .NET framework uygulamaları kolayca birçok yapılandırma ayrıntılarını işler Visual Studio kullanarak ayıklandığını. Visual Studio yüklü değilse, inceleyin ve .NET Framework'te hata ayıklama sınıfları kullanarak .NET Framework uygulamaları performansı <xref:System.Diagnostics> ad alanı. Bu ad alanı içerir <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, ve <xref:System.Diagnostics.TraceSource> yürütme akış, izleme için sınıfları ve <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, ve <xref:System.Diagnostics.PerformanceCounter> kod profili oluşturma için sınıfları.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [JIT-Ekleme Hata Ayıklamayı Etkinleştirme](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 JIT-ekleme kayıt defterine yapılandırmak .NET Framework uygulamasına hata ayıklama altyapısı gösterilmiştir.  
  
 [Görüntüde Hata Ayıklamayı Kolaylaştırma](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 JIT izlemeyi ve en iyi duruma getirme bir derlemeyi debug kolay hale getirmek için devre dışı bırakmak gösterilmiştir.  
  
 [İzleme ve İşaretleme Uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 Çalışırken ve ne kadar iyi görüntülemek için işaretlemesini gittiğini nasıl mı bir şeyler yanlış geçti, uygulamanızın yürütülmesini izlemek açıklar.  
  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 Hangi ortak dil çalışma zamanı (CLR) çalışma zamanı durumu hakkında bilgi sağlamak için birlikte çalışmak yardımları hata ayıklama yönetilen hata ayıklama Yardımcıları (Mda'lar) açıklar.  
  
 [Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 Geliştirici türü ne nasıl belirteceğinizi açıklar türü, bir hata ayıklayıcıda görüntülendiğinde gibi görünür.  
  
 [Performans Sayaçları](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 Bir uygulamanın performansını izlemek için kullanabileceğiniz sayaçları açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ASP.NET ve AJAX uygulamalarında hata ayıklama](http://msdn.microsoft.com/library/9d531913-541b-47b8-864d-138021fca0c6)  
 Önkoşullar ve geliştirme sırasında veya dağıtımdan sonra bir ASP.NET uygulama hata ayıklama hakkında yönergeler sağlar.  
  
 [Geliştirme Kılavuzu](../../../docs/framework/development-guide.md)  
 Dinamik programlama, birlikte çalışabilirlik, genişletilebilirlik, bellek yönetimi ve iş parçacığı oluşturma hakkında uygulama ve bilgilerinizi oluşturma, yapılandırma, hatasını ayıklama, güvenliğini sağlama ve dağıtma gibi, uygulama geliştirmesine yönelik tüm temel teknoloji alanları ve görevleri için kılavuz sağlar.
