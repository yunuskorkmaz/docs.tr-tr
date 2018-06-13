---
title: '.NET Framework 4.7, 4.6 ve 4.5 Geçiş Kılavuzu '
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8ef6d73aa6cd044cf6808878bf6142a735d015c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391255"
---
# <a name="migration-guide-to-the-net-framework-47-46-and-45"></a>.NET Framework 4.7, 4.6 ve 4.5 Geçiş Kılavuzu 
.NET Framework'ün önceki bir sürümünü kullanarak uygulamanızı oluşturduysanız, genellikle, .NET Framework 4.5 ve kendi noktası sürümleri (4.5.1 ve 4.5.2), .NET Framework 4.6 ve onun noktası sürümleri (4.6.1 ve 4.6.2) veya .NET Framework 4.7 ve kendi noktası için yükseltebilirsiniz (4.7.1 ve 4.7.2) kolayca serbest bırakır. Projenizi Visual Studio'da açın. Projeniz Visual Studio'nun daha önceki bir sürümünde oluşturulduysa **proje Uyumluluk** iletişim kutusu otomatik olarak açılır. Visual Studio Proje yükseltme hakkında daha fazla bilgi için bkz: [bağlantı noktası, geçirme ve yükseltme Visual Studio projeleri](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) ve [Visual Studio 2017 Platform desteği ve Uyumluluk](/visualstudio/productinfo/vs2017-compatibility-vs).  
  
 Ancak, bazı değişiklikler .NET Framework'teki kodunuzdaki değişiklikleri gerektirir. .NET Framework 4.5 ve onun noktası sürümler, .NET Framework 4.6 ve onun noktası sürümleri veya .NET Framework 4.7 yeni işlevsellikten yararlanmak isteyebilirsiniz ve kendi noktası serbest bırakır. Yeni bir .NET Framework sürümünü, tipik olarak adlandırılır için uygulamanızın bu tip değişiklikler yapma *geçiş*. Uygulamanızı geçirilecek yoksa, .NET Framework 4.5 veya sonraki bir sürümünü yeniden derlenmesi olmadan çalıştırabilirsiniz.  
  
## <a name="migration-resources"></a>Geçiş kaynakları  
 Uygulamanızı sürüm 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 veya 4.7.2 .NET Framework'ün önceki sürümlerden geçirmeden önce şu belgeleri gözden geçirin:  
  
-   Bkz: [sürümleri ve bağımlılıkları](../../../docs/framework/migration-guide/versions-and-dependencies.md) her .NET Framework sürümünü temel CLR sürümü anlamak ve uygulamalarınızı başarıyla hedefleme için yönergeleri gözden geçirin.  
  
-   Gözden geçirme [uygulama uyumluluğu](../../../docs/framework/migration-guide/application-compatibility.md) çalışma zamanı ve yeniden hedefleme uygulamanızı ve bunları nasıl ele alınacağını etkileyebilecek değişiklikleri hakkında bilgi almak için.  
  
-   Gözden geçirme [Sınıf Kitaplığı'nda ne kullanılmıyor](../../../docs/framework/whats-new/whats-obsolete.md) türleri veya kullanımdan kaldırmıştır kodunuzu ve önerilen Alternatiflerle üyeleri belirlemek için.  
  
-   Bkz: [yenilikler](../../../docs/framework/whats-new/index.md) uygulamanıza eklemek isteyebilirsiniz yeni özelliklerin açıklamaları için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama Uyumluluğu](../../../docs/framework/migration-guide/application-compatibility.md)  
 [.NET Framework 1.1'den Geçiş](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)  
 [Sürüm Uyumluluğu](../../../docs/framework/migration-guide/version-compatibility.md)  
 [Sürümler ve Bağımlılıklar](../../../docs/framework/migration-guide/versions-and-dependencies.md)  
 [Nasıl yapılır: Bir Uygulamayı .NET Framework 4 veya 4.5'i Destekleyecek Şekilde Yapılandırma](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)  
 [Yenilikler](../../../docs/framework/whats-new/index.md)  
 [Sınıf Kitaplığında Artık Kullanılmayanlar](../../../docs/framework/whats-new/whats-obsolete.md)  
 [.NET framework sürümünü ve derleme bilgileri](http://go.microsoft.com/fwlink/?LinkId=201701)  
 [Microsoft .NET Framework destek yaşam döngüsü ilkesi](http://go.microsoft.com/fwlink/?LinkId=196607) [.NET Framework 4 geçiş sorunları](net-framework-4-migration-issues.md)
