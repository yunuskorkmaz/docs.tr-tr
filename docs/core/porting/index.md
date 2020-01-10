---
title: .NET Framework 'den .NET Core 'a bağlantı noktası
description: Bir .NET Framework projesi .NET Core 'a taşıma konusunda yararlı bulabileceğiniz yardım alabileceğiniz işlem ve bulma araçlarını anlayın.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: b5b010acbccf134afe800aa5bb98a0ae6e9ffa25
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777356"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>.NET Framework .NET Core 'a taşıma ile genel bakış

Şu anda .NET Core 'a taşıma konusunda ilgilendiğiniz .NET Framework çalışan bir kodunuz olabilir. Bu makalede aşağıdakiler sunulmaktadır:

* Taşıma işlemine genel bakış.
* Kodunuzu .NET Core 'a taşırken yararlı bulabileceğiniz araçların bir listesi.

## <a name="overview-of-the-porting-process"></a>Taşıma işlemine genel bakış

Projenizi .NET Core 'a taşıma sırasında aşağıdaki işlemi kullanmanızı öneririz:

1. .NET Framework 4.7.2 veya üstünü hedeflemek için, bağlantı noktası yapmak istediğiniz tüm projeleri yeniden hedefleyin.

   Bu adım, .NET Core belirli bir API 'YI desteklemedikleri zaman .NET Framework özel hedefler için API alternatifleri kullanmanıza da sağlar.

2. Derlemelerinizi çözümlemek ve .NET Core 'a taşınabilir olup olmadığını görmek için [.net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) 'ni kullanın.

   API taşınabilirlik Çözümleyicisi Aracı, derlenmiş derlemelerinizi analiz eder ve bir rapor oluşturur. Bu rapor, üst düzey bir taşınabilirlik özetini ve kullanmakta olduğunuz her API 'nin, NET Core 'da kullanılamayan bir dökümünü gösterir.

3. Bazı platformlarda <xref:System.PlatformNotSupportedException> oluşturan API 'Leri ve bazı diğer olası uyumluluk sorunlarını belirlemek için, projelerinize [.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) 'ni yükler.

   Bu araç taşınabilirlik Çözümleyicisi ile benzerdir, ancak .NET Core üzerinde nesnelerin oluşturabildiğini çözümlemek yerine, çalışma zamanında <xref:System.PlatformNotSupportedException> oluşturacak şekilde bir API kullanıp kullandığınızı analiz eder. .NET Framework 4.7.2 veya üzeri bir sürümü taşıyorsanız, bu yaygın olmasa da kontrol etmeniz iyidir.

4. `packages.config` bağımlılıklarınızın tümünü, [Visual Studio 'daki Dönüştürme aracıyla](/nuget/consume-packages/migrate-packages-config-to-package-reference) [packagereference](/nuget/consume-packages/package-references-in-project-files) biçimine dönüştürün.

   Bu adım, eski `packages.config` biçiminden bağımlılıklarınızı dönüştürmeyi içerir. `packages.config`, .NET Core üzerinde çalışmaz, bu nedenle paket bağımlılıklarınız varsa bu dönüştürme gereklidir.

5. .NET Core için yeni projeler oluşturun ve kaynak dosyaları üzerine kopyalayın veya mevcut proje dosyanızı bir araçla dönüştürmeyi deneyin.

   .NET Core .NET Framework göre Basitleştirilmiş (ve farklı) bir [Proje dosyası biçimi](../tools/csproj.md) kullanır. Devam etmek için proje dosyalarınızı bu biçime dönüştürmeniz gerekir.

6. Test kodunuzun bağlantı noktası.

   .NET Core 'a taşıma işlemi, kod tabanınızda önemli bir değişiklik olduğundan, kodunuzun bağlantı noktası oluşturduğunuz testleri çalıştırabilmeniz için test projelerinizin bağlantı noktası yapılması önemle önerilir. MSTest, xUnit ve NUnit tüm .NET Core üzerinde çalışır.

Ayrıca, [DotNet TRY-Convert](https://github.com/dotnet/try-convert) aracı Ile .NET Core proje dosyası biçimine tek bir işlemde daha küçük çözümler veya tek tek projeler için bağlantı kurmayı deneyebilirsiniz. `dotnet try-convert` tüm projeleriniz için çalışma garantisi verilmez ve bağımlı olduğunuz davranışta hafif değişikliklere neden olabilir. Otomatikleştirilmiş olabilecek temel şeyleri otomatikleştiren bir _Başlangıç noktası_ olarak kullanın. Projenin geçirilmesi için garantili bir çözüm değildir.

## <a name="next-steps"></a>Sonraki adımlar

>[!div class="nextstepaction"]
>[.NET Core 'da kullanılamayan teknolojiler](net-framework-tech-unavailable.md)
