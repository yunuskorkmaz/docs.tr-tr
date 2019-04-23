---
title: '4.8, 4.7, 4.6 ve 4.5 .NET Framework Geçiş Kılavuzu '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb51a0be57992d65a88e958d76a5e371dc028a00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974967"
---
# <a name="migration-guide-to-the-net-framework-48-47-46-and-45"></a>4.8, 4.7, 4.6 ve 4.5 .NET Framework Geçiş Kılavuzu

Uygulamanızı .NET Framework'ün önceki bir sürümü kullanılarak oluşturuldu, bunu genellikle .NET Framework 4.5 için yükseltebilirsiniz ve nokta (4.5.1 ve 4.5.2'yi) sürümlerini .NET Framework 4.6 ve onun nokta sürümleri (4.6.1 ve 4.6.2), .NET Framework 4.7 ve onun nokta sürümleri) 4.7.1 ve 4.7.2) veya .NET Framework 4.8 kolayca. Projenizi Visual Studio'da açın. Projenizi Visual Studio'nun önceki bir sürümde oluşturulmuşsa **proje uygunluğu** iletişim kutusu otomatik olarak açılır. Visual Studio'da bir proje yükseltme hakkında daha fazla bilgi için bkz. [bağlantı noktası, geçirme ve yükseltme Visual Studio projeleri](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) ve [Visual Studio 2019 Platform hedefleme ve Uyumluluk](/visualstudio/releases/2019/compatibility).

 Ancak, .NET Framework'teki bazı değişiklikler kodunuzda değişiklikler gerektirir. .NET Framework 4.5 ve nokta sürümleri, .NET Framework 4.6 ve onun nokta sürümleri, .NET Framework 4.7 ve onun nokta sürümleri veya .NET Framework 4.8 yeni olan işlevsellikten yararlanmak isteyebilirsiniz. .NET Framework'ün yeni bir sürümü, tipik olarak adlandırılır için uygulamanızda bu tür değişiklikleri yapmaya *geçiş*. Uygulamanızı geçişi sahip değilse, bu .NET Framework 4.5 veya sonraki bir sürümünü yeniden derlemeden çalıştırabilirsiniz.

## <a name="migration-resources"></a>Geçiş kaynakları

Uygulamanızı .NET Framework'ün önceki sürümlerinden 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 veya 4.8 sürümüne geçirmeden önce aşağıdaki belgeleri gözden geçirin:

- Bkz: [sürümler ve bağımlılıklar](versions-and-dependencies.md) .NET Framework'ün her sürümü temelinde CLR sürümünü anlamak ve uygulamalarınızı başarıyla hedeflemekle yönergeleri gözden geçirin.

- Gözden geçirme [uygulama uyumluluğu](application-compatibility.md) çalışma zamanı ve yeniden hedefleme değişiklikleri uygulamanız ve bunları nasıl ele alınacağını etkileyebilecek öğrenin.

- Gözden geçirme [Sınıf Kitaplığı'nda ne kullanılmıyor](../whats-new/whats-obsolete.md) herhangi bir tür veya üyeleri geçersiz yapılan kodunuzu ve önerilen alternatifleri belirlemek için.

- Bkz: [yenilikler](../whats-new/index.md) uygulamanıza eklemek isteyebileceğiniz yeni özelliklerin açıklamaları için.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Uyumluluğu](application-compatibility.md)
- [.NET Framework 1.1'den Geçiş](migrating-from-the-net-framework-1-1.md)
- [Sürüm Uyumluluğu](version-compatibility.md)
- [Sürümler ve Bağımlılıklar](versions-and-dependencies.md)
- [Nasıl yapılır: Bir uygulamayı .NET Framework 4 veya sonraki sürümler destekleyecek şekilde yapılandırma](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Yenilikler](../whats-new/index.md)
- [Sınıf Kitaplığında Artık Kullanılmayanlar](../whats-new/whats-obsolete.md)
- [.NET framework sürüm ve derleme bilgileri](https://go.microsoft.com/fwlink/?LinkId=201701)
- [Microsoft .NET Framework Destek Ömrü İlkesi](https://go.microsoft.com/fwlink/?LinkId=196607)
- [.NET Framework 4 geçiş sorunları](net-framework-4-migration-issues.md)