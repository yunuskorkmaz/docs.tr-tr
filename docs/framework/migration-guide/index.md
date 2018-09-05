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
ms.openlocfilehash: fc3796e3e79112b14d45bb410e63656a81d474c8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526726"
---
# <a name="migration-guide-to-the-net-framework-47-46-and-45"></a>.NET Framework 4.7, 4.6 ve 4.5 Geçiş Kılavuzu 
Uygulamanızı .NET Framework'ün önceki bir sürümünü kullanarak oluşturduysanız, genellikle, .NET Framework 4.5 ve nokta sürümleri (4.5.1 ve 4.5.2'yi), .NET Framework 4.6 ve onun nokta sürümleri (4.6.1 ve 4.6.2), veya .NET Framework 4.7 ve kendi noktasını yükseltebilirsiniz (4.7.1 ve 4.7.2) kolayca serbest bırakır. Projenizi Visual Studio'da açın. Projenizi Visual Studio'nun önceki bir sürümde oluşturulmuşsa **proje uygunluğu** iletişim kutusu otomatik olarak açılır. Visual Studio'da bir proje yükseltme hakkında daha fazla bilgi için bkz. [bağlantı noktası, geçirme ve yükseltme Visual Studio projeleri](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) ve [Visual Studio 2017 Platform desteği ve Uyumluluk](/visualstudio/productinfo/vs2017-compatibility-vs).  
  
 Ancak, .NET Framework'teki bazı değişiklikler kodunuzda değişiklikler gerektirir. .NET Framework 4.5 ve nokta sürümleri, .NET Framework 4.6 ve onun nokta sürümleri veya .NET Framework 4.7 yeni olan işlevsellikten yararlanmak isteyebilirsiniz ve nokta sürümlerini. .NET Framework'ün yeni bir sürümü, tipik olarak adlandırılır için uygulamanızda bu tür değişiklikleri yapmaya *geçiş*. Uygulamanızı geçişi sahip değilse, bu .NET Framework 4.5 veya sonraki bir sürümünü yeniden derlemeden çalıştırabilirsiniz.  
  
## <a name="migration-resources"></a>Geçiş kaynakları  
 Uygulamanızı .NET Framework'ün önceki sürümlerinden 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 veya 4.7.2 sürümüne geçirmeden önce aşağıdaki belgeleri gözden geçirin:  
  
-   Bkz: [sürümler ve bağımlılıklar](../../../docs/framework/migration-guide/versions-and-dependencies.md) .NET Framework'ün her sürümü temelinde CLR sürümünü anlamak ve uygulamalarınızı başarıyla hedeflemekle yönergeleri gözden geçirin.  
  
-   Gözden geçirme [uygulama uyumluluğu](../../../docs/framework/migration-guide/application-compatibility.md) çalışma zamanı ve yeniden hedefleme değişiklikleri uygulamanız ve bunları nasıl ele alınacağını etkileyebilecek öğrenin.  
  
-   Gözden geçirme [Sınıf Kitaplığı'nda ne kullanılmıyor](../../../docs/framework/whats-new/whats-obsolete.md) herhangi bir tür veya üyeleri geçersiz yapılan kodunuzu ve önerilen alternatifleri belirlemek için.  
  
-   Bkz: [yenilikler](../../../docs/framework/whats-new/index.md) uygulamanıza eklemek isteyebileceğiniz yeni özelliklerin açıklamaları için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama Uyumluluğu](../../../docs/framework/migration-guide/application-compatibility.md)  
 [.NET Framework 1.1'den Geçiş](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)  
 [Sürüm Uyumluluğu](../../../docs/framework/migration-guide/version-compatibility.md)  
 [Sürümler ve Bağımlılıklar](../../../docs/framework/migration-guide/versions-and-dependencies.md)  
 [Nasıl yapılır: Bir Uygulamayı .NET Framework 4 veya 4.5'i Destekleyecek Şekilde Yapılandırma](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)  
 [Yenilikler](../../../docs/framework/whats-new/index.md)  
 [Sınıf Kitaplığında Artık Kullanılmayanlar](../../../docs/framework/whats-new/whats-obsolete.md)  
 [.NET framework sürüm ve derleme bilgileri](https://go.microsoft.com/fwlink/?LinkId=201701)  
 [Microsoft .NET Framework Destek Ömrü İlkesi](https://go.microsoft.com/fwlink/?LinkId=196607) [.NET Framework 4 geçiş sorunları](net-framework-4-migration-issues.md)
