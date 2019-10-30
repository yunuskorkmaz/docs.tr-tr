---
title: .NET Framework 'den .NET Core 'a bağlantı noktası
description: Bir .NET Framework projesi .NET Core 'a taşıma konusunda yararlı bulabileceğiniz yardım alabileceğiniz işlem ve bulma araçlarını anlayın.
author: cartermp
ms.date: 10/22/2019
ms.custom: seodec18
ms.openlocfilehash: 89f00e5c6ce7f3cea7a3135c9b2856c54a70da40
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038526"
---
# <a name="overview-of-the-porting-process-from-net-framework-to-net-core"></a>.NET Framework 'den .NET Core 'a taşıma işlemine genel bakış

Şu anda .NET Core 'a taşıma konusunda ilgilendiğiniz .NET Framework çalışan bir kodunuz olabilir. Bu makale şunları sağlar:

* Taşıma işlemine genel bakış.
* Kodunuzu .NET Core 'a taşırken yararlı bulabileceğiniz araçların bir listesi.

## <a name="overview-of-the-porting-process"></a>Taşıma işlemine genel bakış

Projenizi .NET Core 'a taşıma sırasında aşağıdaki işlemi kullanmanızı öneririz:

1. .NET Framework 4.7.2 veya üstünü hedeflemek için bağlantı noktası yapmak istediğiniz tüm projeleri yeniden hedefleyin.

   Bu adım, .NET Core belirli bir API 'YI desteklemedikleri zaman .NET Framework özel hedefler için API alternatifleri kullanmanıza da sağlar.

2. Derlemelerinizi çözümlemek ve .NET Core 'a taşınabilir olup olmadığını görmek için [.net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) 'ni kullanın.

   API taşınabilirlik Çözümleyicisi Aracı, derlenmiş derlemelerinizi analiz eder ve bir rapor oluşturur. Bu rapor, üst düzey bir taşınabilirlik özetini ve kullanmakta olduğunuz her API 'nin, NET Core 'da kullanılamayan bir dökümünü gösterir.

3. Bazı platformlarda <xref:System.PlatformNotSupportedException> oluşturan API 'Leri ve bazı diğer olası uyumluluk sorunlarını belirlemek için, projelerinize [.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) 'ni yükler.

   Bu araç, taşınabilirlik Çözümleyicisi 'ne benzer, ancak .NET Core üzerinde şeyler oluşturabilirliğini çözümlemek yerine, çalışma zamanında <xref:System.PlatformNotSupportedException> oluşturacak şekilde bir API kullanıyorsanız analiz edilir. .NET Framework 4.7.2 veya üzeri bir sürümü taşıyorsanız, bu yaygın olmasa da kontrol etmeniz iyidir.

4. `packages.config` bağımlılıklarınızın tümünü, [Visual Studio 'daki Dönüştürme aracıyla](/nuget/consume-packages/migrate-packages-config-to-package-reference) [packagereference](/nuget/consume-packages/package-references-in-project-files) biçimine dönüştürün.

   Bu adım, eski `packages.config` biçiminden bağımlılıklarınızı dönüştürmeyi içerir. `packages.config`, .NET Core üzerinde çalışmaz, bu nedenle paket bağımlılıklarınız varsa bu dönüştürme gereklidir.

5. .NET Core için yeni projeler oluşturun ve kaynak dosyaları üzerine kopyalayın veya mevcut proje dosyanızı bir araçla dönüştürmeyi deneyin.

   .NET Core .NET Framework göre Basitleştirilmiş (ve farklı) bir [Proje dosyası biçimi](../tools/csproj.md) kullanır. Devam etmek için proje dosyalarınızı bu biçime dönüştürmeniz gerekir.

6. Test kodunuzun bağlantı noktası.

   .NET Core 'a geçiş yapmak, kod tabanınızda önemli bir değişiklik olduğundan, test etmeniz, kodunuzun bağlantı noktası oluşturduğunuz gibi testler çalıştırabilmeniz için, testlerinizi almak kesinlikle önerilir. MSTest, xUnit ve NUnit tüm .NET Core üzerinde çalışır.

Ayrıca, bir işlemde [DotNet TRY-Convert](https://github.com/dotnet/try-convert) aracı Ile .NET Core proje dosyası biçiminde daha küçük çözümler veya ayrı projeler için bağlantı kurmayı deneyebilirsiniz. `dotnet try-convert` tüm projeleriniz için çalışması garanti edilmez ve bağımlılarınızın bağlı olduğunu fark ettiğiniz davranıştaki değişikliklere neden olabilir. Otomatikleştirilmiş olabilecek temel şeyleri otomatikleştiren bir _Başlangıç noktası_ olarak kullanılmalıdır. Projenin geçirilmesi için garantili bir çözüm değildir.

>[!div class="step-by-step"]
>[Next](net-framework-tech-unavailable.md)
