---
title: .NET Framework'den .NET Core'a bağlantı noktası
description: Taşıma işlemini anlayın ve bir .NET Framework projesini .NET Core'a taşımayaparken yararlı olabileceğiniz araçları keşfedin.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: e483bb6e48dad6c3bf71bfa81e704a137fc02094
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75937312"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>.NET Framework'den .NET Core'a taşımaya genel bakış

Şu anda .NET Core'a taşımak istediğiniz .NET Framework'de çalışan kodunuz olabilir. Bu makalede aşağıdakiler sunulmaktadır:

* Taşıma işlemine genel bakış.
* Kodunuzu .NET Core'a taşımanızda yararlı olabileceğiniz araçların listesi.

## <a name="overview-of-the-porting-process"></a>Taşıma işlemine genel bakış

Projenizi .NET Core'a taşımayaparken aşağıdaki işlemi kullanmanızı öneririz:

1. .NET Framework 4.7.2 veya daha yüksek bir hedefe bağlantı noktası yapmak istediğiniz tüm projeleri yeniden hedeflenin.

   Bu adım, .NET Core belirli bir API'yi desteklemediğinde .NET Framework'e özgü hedefler için API alternatiflerini kullanabilmesini sağlar.

2. Derlemelerinizi analiz etmek ve .NET Core'a taşınabilir olup olmadıklarını görmek için [.NET Taşınabilirlik Çözümleyicisini](../../standard/analyzers/portability-analyzer.md) kullanın.

   API Taşınabilirlik Çözümleyiciaracı derlenmiş derlemelerinizi analiz eder ve bir rapor oluşturur. Bu rapor, net core'da bulunmayan üst düzey taşınabilirlik özetini ve kullandığınız her API'nın dökümünü gösterir.

3. Bazı platformlarda ve diğer bazı olası uyumluluk sorunlarını <xref:System.PlatformNotSupportedException> oluşturan API'leri tanımlamak için [.NET API çözümleyicisini](../../standard/analyzers/api-analyzer.md) projelerinize yükleyin.

   Bu araç taşınabilirlik çözümleyicisine benzer, ancak kod .NET Core üzerinde inşa edebilirsiniz eğer analiz yerine, bir API çalıştıran zamanda bir <xref:System.PlatformNotSupportedException> atacak bir şekilde bir API kullanıyorsanız analiz eder. .NET Framework 4.7.2 veya daha yüksek bir yerden hareket ediyorsanız, bu yaygın olmasa da, bunu kontrol etmek iyidir. .NET Core'da özel durumlar oluşturan API'ler hakkında daha fazla bilgi [için,.NET Core'da her zaman özel durumlar oluşturan API'lere](../compatibility/unsupported-apis.md)bakın.

4. Visual `packages.config` [Studio'daki dönüştürme aracıyla](/nuget/consume-packages/migrate-packages-config-to-package-reference)tüm bağımlılıklarınızı [PackageReference](/nuget/consume-packages/package-references-in-project-files) biçimine dönüştürün.

   Bu adım, bağımlılıklarınızı eski `packages.config` biçimden dönüştürmeyi içerir. `packages.config`.NET Core üzerinde çalışmaz, bu nedenle paket bağımlılıklarınız varsa bu dönüştürme gereklidir.

5. .NET Core için yeni projeler oluşturun ve kaynak dosyaları kopyalayın veya varolan proje dosyanızı bir araçla dönüştürmeye çalışın.

   .NET Core, .NET Framework'den daha basitleştirilmiş (ve farklı) bir [proje dosyası biçimi](../tools/csproj.md) kullanır. Devam etmek için proje dosyalarınızı bu biçime dönüştürmeniz gerekir.

6. Test kodunuzu port.

   .NET Core'a geçiş kod tabanınızda önemli bir değişiklik olduğundan, kodunuzu üzerinde bağlantı darken testleri çalıştırabilmeniz için test projelerinizi taşımanız önerilir. MSTest, xUnit ve NUnit 'in tümü .NET Core üzerinde çalışır.

Ayrıca, [dotnet try-convert](https://github.com/dotnet/try-convert) aracıyla tek bir işlemdeki küçük çözümleri veya tek tek projeleri .NET Core proje dosya biçimine taşımayı deneyebilirsiniz. `dotnet try-convert`tüm projeleriniz için çalışacağı garanti edilmez ve bağlı olduğunuz davranışta ince değişikliklere neden olabilir. Otomatikleştirilebilen temel şeyleri otomatikleştiren bir _başlangıç noktası_ olarak kullanın. Bir projeyi geçirmek için garantili bir çözüm değildir.

## <a name="next-steps"></a>Sonraki adımlar

>[!div class="nextstepaction"]
>[Bağımlılıkları analiz edin](third-party-deps.md)
