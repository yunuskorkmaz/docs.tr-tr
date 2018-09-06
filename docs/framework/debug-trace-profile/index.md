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
ms.openlocfilehash: ff2be73b2cea563066f70ea2fe6d53840f718e75
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855289"
---
# <a name="debugging-tracing-and-profiling"></a>Hata Ayıklama, İzleme ve Profil Oluşturma
Bir .NET Framework uygulamasında hata ayıklamak için derleyici ve çalışma zamanı ortamı uygulamaya eklemek bir hata ayıklayıcı etkinleştirmek için yapılandırılması gerekir ve hem simge hem de satır üretmek için mümkün olduğunda, uygulama ve onun ilişkili Microsoft Ara eşler Dil (MSIL). Yönetilen bir uygulama hata ayıklama sonra performansını artırmak üzere profili. Profil oluşturma değerlendirir ve en sık yürütülen kodu kaynak kodu satırlarını açıklar ve ne kadar bunları yürütmek için alır.  
  
 .NET framework uygulamaları, kolayca configuration ayrıntıların birçoğu işleme Visual Studio kullanarak hata ayıklama. Visual Studio yüklü değilse, inceleyin ve .NET Framework'te hata ayıklama sınıfları kullanarak .NET Framework uygulamalarının performansını <xref:System.Diagnostics> ad alanı. Bu ad alanı içerir <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, ve <xref:System.Diagnostics.TraceSource> yürütme akışı izleme için sınıfları ve <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, ve <xref:System.Diagnostics.PerformanceCounter> kod profil oluşturma için sınıflar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [JIT-Ekleme Hata Ayıklamayı Etkinleştirme](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 JIT-ekleme için kayıt defterini yapılandırmak bir .NET Framework uygulamasına bir hata ayıklama altyapısı gösterilmektedir.  
  
 [Görüntüde Hata Ayıklamayı Kolaylaştırma](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 Bir derlemeyi hata ayıklama daha kolay hale getirmek üzere üzerinde JIT izleme ve iyileştirme kapatmak gösterilmektedir.  
  
 [İzleme ve İşaretleme Uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 Çalışır durumdayken ve ne kadar iyi görüntülemek için araç haline getirmek için onu gerçekleştiriyor nasıl mı bir sorun oluştu, uygulamanın yürütülmesini izlemek açıklar.  
  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 Ortak dil çalışma zamanı (CLR) çalışma zamanı durum bilgilerini sağlamak için birlikte çalışan yardımlarda hata ayıklar, yönetilen hata ayıklama Yardımcıları (Mda'lar) açıklar.  
  
 [Hata Ayıklayıcı Görüntü Öznitelikleriyle Hata Ayıklamayı Geliştirme](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 Geliştirici bir türün ne nasıl belirteceğinizi açıklar türü bir hata ayıklayıcıda zaman görüntülendiği gibi görünecektir.  
  
 [Performans Sayaçları](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 Uygulama performansını izlemek için kullanabileceğiniz sayaçlar açıklanmaktadır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ASP.NET ve AJAX Uygulamalarında Hata Ayıklama](https://msdn.microsoft.com/library/9d531913-541b-47b8-864d-138021fca0c6)  
 Önkoşullar ve nasıl bir ASP.NET uygulama geliştirme süresince veya dağıtım sonrasında hata ayıklama için yönergeler sağlar.  
  
 [Geliştirme Kılavuzu](../../../docs/framework/development-guide.md)  
 Dinamik programlama, birlikte çalışabilirlik, genişletilebilirlik, bellek yönetimi ve iş parçacığı oluşturma hakkında uygulama ve bilgilerinizi oluşturma, yapılandırma, hatasını ayıklama, güvenliğini sağlama ve dağıtma gibi, uygulama geliştirmesine yönelik tüm temel teknoloji alanları ve görevleri için kılavuz sağlar.
