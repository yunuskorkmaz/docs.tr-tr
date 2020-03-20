---
title: '.NET Framework 4.8, 4.7, 4.6 ve 4.5 Geçiş Kılavuzu '
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: 2fa992e1c0897d360f322581888c51dca8d8a734
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73974981"
---
# <a name="migration-guide-to-the-net-framework-48-47-46-and-45"></a>.NET Framework 4.8, 4.7, 4.6 ve 4.5 Geçiş Kılavuzu

Uygulamanızı .NET Framework'ün önceki bir sürümünü kullanarak oluşturduysanız, genellikle .NET Framework 4.5 ve puan sürümleri (4.5.1 ve 4.5.2), .NET Framework 4.6 ve puan sürümleri (4.6.1 ve 4.6.2), .NET Framework 4.7 ve puan sürümlerine ( 4.7.1 ve 4.7.2) veya .NET Framework 4.8 kolayca. Görsel Stüdyo'da projenizi açın. Projeniz Visual Studio'nun önceki bir sürümünde oluşturulduysa, **Proje Uyumluluğu** iletişim kutusu otomatik olarak açılır. Visual Studio'da bir projeyi yükseltme hakkında daha fazla bilgi için, [Visual Studio Projeleri ve Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) [2019 Platform Hedefleme ve Uyumluluğu](/visualstudio/releases/2019/compatibility)Geliştirme hakkında bakınız.

 Ancak, .NET Framework'deki bazı değişiklikler için kodunuzda değişiklik gerekir. Ayrıca .NET Framework 4.5 ve onun nokta sürümlerinde,.NET Framework 4.6 ve onun nokta sürümlerinde, .NET Framework 4.7 ve onun puan sürümlerinde veya .NET Framework 4.8'de yeni olan işlevselliklerden yararlanmak isteyebilirsiniz. .NET Framework'ün yeni bir sürümü için uygulamanızda bu tür değişiklikler yapmak genellikle *geçiş*olarak adlandırılır. Uygulamanızın geçirilmeniz gerekiyorsa, uygulamayı yeniden derlemeden .NET Framework 4.5 veya daha sonraki bir sürümde çalıştırabilirsiniz.

## <a name="migration-resources"></a>Geçiş kaynakları

.NET Framework'ün önceki sürümlerinden sürüm 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 veya 4.8 sürümüne geçmeden önce aşağıdaki belgeleri inceleyin:

- .NET Framework'ün her sürümünün altında yatan CLR sürümünü anlamak ve uygulamalarınızı başarıyla hedefleme yönergelerini gözden geçirmek için [Sürümler ve Bağımlılıklar'a](versions-and-dependencies.md) bakın.

- Uygulamanızı etkileyebilecek çalışma zamanı ve yeniden hedefleme değişiklikleri ve bunları nasıl işleyeceğiniöğrenmek için [Uygulama uyumluluğunu](application-compatibility.md) gözden geçirin.

- Kodunuzda geçersiz kılınan türleri veya üyeleri ve önerilen alternatifleri belirlemek için [Sınıf Kitaplığında Eski olanları](../whats-new/whats-obsolete.md) gözden geçirin.

- Uygulamanıza eklemek isteyebileceğiniz yeni özelliklerin açıklamaları için [Yeniliklere](../whats-new/index.md) Bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
- [.NET Framework 1.1'den Geçiş](migrating-from-the-net-framework-1-1.md)
- [Sürüm Uyumluluğu](version-compatibility.md)
- [Sürümler ve Bağımlılıklar](versions-and-dependencies.md)
- [Nasıl yapilir: Bir uygulamayı .NET Framework 4 veya sonraki sürümlerini destekleyecek şekilde yapılandırın](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Yenilikler](../whats-new/index.md)
- [Sınıf Kitaplığı'nda Artık Kullanılmayanlar](../whats-new/whats-obsolete.md)
- [.NET Framework resmi destek politikası](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [.NET Framework 4 geçiş sorunları](net-framework-4-migration-issues.md)
