---
title: 4,8, 4,7, 4,6 ve 4,5 .NET Framework geçiş kılavuzu
description: Yeni özellikler ve uygulama uyumluluğuna yönelik kaynakları içeren daha yeni .NET Framework sürümlere geçirmeye yönelik bir kılavuz.
ms.date: 04/18/2019
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
ms.openlocfilehash: c597f6e7b67e190ffe61a425506a1a34f254942c
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558510"
---
# <a name="migrate-to-net-framework-48-47-46-and-45"></a>.NET Framework 4,8, 4,7, 4,6 ve 4,5 'e geçirin

Uygulamanızı daha önceki bir .NET Framework sürümünü kullanarak oluşturduysanız, genellikle bunu .NET Framework 4,5 ve onun nokta sürümleri (4.5.1 ve 4.5.2), .NET Framework 4,6 ve nokta sürümleri (4.6.1 ve 4.6.2), .NET Framework 4,7 ve kendi nokta sürümleri (4.7.1 ve 4.7.2) ya da 4,8 .NET Framework kolayca yükseltebilirsiniz. Projenizi Visual Studio’da açın. Projeniz Visual Studio 'nun önceki bir sürümünde oluşturulduysa, **Proje uyumluluğu** iletişim kutusu otomatik olarak açılır. Visual Studio 'da bir projeyi yükseltme hakkında daha fazla bilgi için bkz. [bağlantı noktası, geçiş ve yükseltme Visual Studio projeleri](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects) ve [Visual Studio 2019 Platform hedefleme ve uyumluluk](/visualstudio/releases/2019/compatibility).

 Ancak .NET Framework yapılan bazı değişiklikler kodunuzda değişiklik yapılmasını gerektirir. Ayrıca, .NET Framework 4,5 ' deki ve nokta sürümlerindeki yeni işlevsellikten yararlanmak isteyebilirsiniz .NET Framework 4,6 ve onun nokta sürümleri, .NET Framework 4,7 ve onun nokta sürümleri, .NET Framework 4,8. .NET Framework yeni bir sürümü için uygulamanızda bu tür değişiklikler yapmak genellikle *geçiş*olarak adlandırılır. Uygulamanızın geçirilmesi gerekiyorsa, bunu yeniden derlemeden .NET Framework 4,5 veya sonraki bir sürümde çalıştırabilirsiniz.

## <a name="migration-resources"></a>Geçiş kaynakları

Uygulamanızı önceki .NET Framework sürümlerinden 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 veya 4,8 sürümüne geçirmeden önce aşağıdaki belgeleri gözden geçirin:

- .NET Framework her bir sürümünü temel alan CLR sürümünü anlamak ve uygulamalarınızı başarıyla hedeflemek için yönergeleri gözden geçirmek için [sürümler ve bağımlılıklar](versions-and-dependencies.md) bölümüne bakın.

- Uygulamanızı etkileyebilecek çalışma zamanı ve yeniden hedefleme değişiklikleri hakkında bilgi edinmek için [uygulama uyumluluğunu](application-compatibility.md) gözden geçirin ve bunları nasıl işleyebileceğinizi öğrenin.

- Kodunuzda, kullanımdan kalkmış olan herhangi bir tür veya üyeyi ve önerilen alternatifleri belirlemek için, [Sınıf kitaplığındaki kullanım dışı olanları](../whats-new/whats-obsolete.md) gözden geçirin.

- Uygulamanıza eklemek isteyebileceğiniz yeni özelliklerin [açıklamaları için bkz. yenilikler.](../whats-new/index.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
- [.NET Framework 1.1'den Geçiş](migrating-from-the-net-framework-1-1.md)
- [Sürüm uyumluluğu](version-compatibility.md)
- [Sürümler ve bağımlılıklar](versions-and-dependencies.md)
- [Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma](how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [Yenilikler](../whats-new/index.md)
- [Sınıf Kitaplığı'nda Artık Kullanılmayanlar](../whats-new/whats-obsolete.md)
- [.NET Framework resmi destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [.NET Framework 4 geçiş sorunları](net-framework-4-migration-issues.md)
