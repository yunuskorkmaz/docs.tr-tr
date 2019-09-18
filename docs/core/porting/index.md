---
title: .NET Framework 'den .NET Core 'a bağlantı noktası kodu
description: Bir .NET Framework projesi .NET Core 'a taşıma konusunda yararlı bulabileceğiniz yardım alabileceğiniz işlem ve bulma araçlarını anlayın.
author: cartermp
ms.date: 09/13/2019
ms.custom: seodec18
ms.openlocfilehash: b6c02932b5d9c7ccc2743dd38dddf2904f9c24e4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039658"
---
# <a name="port-your-code-from-net-framework-to-net-core"></a>Kodunuzun .NET Framework .NET Core 'a bağlantı noktası

.NET Framework çalışan bir kodunuz varsa, kodunuzu .NET Core 'da da çalıştırmaya ilginizi çekiyor olabilirsiniz. Aşağıda, taşıma işlemine bir genel bakış ve kodunuzu .NET Core 'a taşırken yararlı bulabileceğiniz araçların bir listesi yer alabilir.

## <a name="overview-of-the-porting-process"></a>Taşıma işlemine genel bakış

Bu işlem, projenizi .NET Core 'a taşırken uygulamanız önerilir. İşlemin her adımı, daha fazla makalede daha ayrıntılı bir şekilde ele alınmıştır.

1. Üçüncü taraf bağımlılıklarınızı belirleyip hesaba katılın.

   Bu adım, üçüncü taraf bağımlılıklarınızın ne olduğunu, bunlara nasıl bağlı olduğunu, .NET Core 'da da çalıştırıldığının nasıl kontrol alınacağını ve yoksa uygulayabileceğiniz adımları anlamayı içerir. Ayrıca, bağımlılıklarınızı .NET Core 'da kullanılan [Packagereference](/nuget/consume-packages/package-references-in-project-files) biçimine nasıl geçirebileceğiniz de ele alınmaktadır.

2. .NET Framework 4.7.2 veya üstünü hedeflemek için bağlantı noktası yapmak istediğiniz tüm projeleri yeniden hedefleyin.

   Bu adım, .NET Core belirli bir API 'YI desteklemedikleri zaman .NET Framework özel hedefler için API alternatifleri kullanmanıza da sağlar.

3. Derlemelerinizi çözümlemek ve sonuçlarına göre bağlantı noktasına bir plan geliştirmek için [.net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) ' ni kullanın.

   API taşınabilirlik Çözümleyicisi Aracı, derlenmiş derlemelerinizi analiz eder ve yüksek düzeyde bir taşınabilirlik özetini ve kullandığınız her API 'nin dökümünü ve hedeflenen .NET Core platformunda genel yüzeyini gösteren bir rapor oluşturur. Bu raporu, kodunuzun bağlantı noktasını nasıl aktarabileceğinizi gösteren bir plan geliştirmek için kod tabanınızın analizini birlikte kullanabilirsiniz.

4. Proje dosyanızı hedeflenen .NET Core sürümüne dönüştürdükten sonra, bazı platformlarda ve diğer olası Uyumluluk sorunlarından oluşan API 'leri <xref:System.PlatformNotSupportedException> tanımlamak için Roslyn tabanlı [.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) 'ni kullanabilirsiniz.

5. Test kodunuzun bağlantı noktası.

   .NET Core 'a geçiş yapmak, kod tabanınızda önemli bir değişiklik olduğundan, test etmeniz, kodunuzun bağlantı noktası oluşturduğunuz gibi testler çalıştırabilmeniz için, testlerinizi almak kesinlikle önerilir. MSTest, xUnit ve NUnit hepsi .NET Core 'u destekler.

6. Planınızı taşıma için planınızı yürütün!

Aşağıdaki listede, taşıma işlemi sırasında kullanmanın faydalı olabileceği araçlar gösterilmektedir:

* .NET taşınabilirlik Çözümleyicisi- [komut satırı aracı](https://github.com/Microsoft/dotnet-apiport/releases) veya [Visual Studio uzantısı](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), kodunuzun nasıl .NET Framework ve hedef .NET Core platformunuzun arasında olduğunu gösteren bir rapor üretebilirler. Rapor, hedef .NET Core platformunda tür ve API 'lerin derleme derleme dökümünü içerir. Daha fazla bilgi için bkz. [.net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md). Taşıma işlemine başlamadan önce .NET taşınabilirlik Çözümleyicisi aracının çalıştırılması önerilir, çünkü belirli bir hedeflenen .NET platformu genel yüzeyindeki eksik API 'lerde herhangi bir boşluk belirlemenize yardımcı olur.
* .NET API Çözümleyicisi-bazı platformlarda oluşturan <xref:System.PlatformNotSupportedException> .NET Standard API 'yi bulan, kullanım dışı API çağrılarını algılayan ve farklı platformlardaki API 'ler için C# bazı olası uyumluluk risklerini bulan bir Roslyn Çözümleyicisi. Daha fazla bilgi için bkz. [.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md). Bu çözümleyici, farklı platformlardaki çalışma zamanı davranış farklarını belirlemek için .NET Core projenizi oluşturduktan sonra yararlı olur.
* Ters paket arama-bir tür aramanızı ve bu türü içeren paketleri bulmanızı sağlayan [yararlı bir Web hizmetidir](https://packagesearch.azurewebsites.net) .

Ayrıca, [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) aracı Ile .NET Core proje dosyası biçiminde daha küçük çözümler veya ayrı projeler için bağlantı kurmayı deneyebilirsiniz.

> [!WARNING]
> CsprojToVs2017, üçüncü taraf bir araçtır. Tüm projeleriniz için çalışacağından emin olmaz ve bağlı olduğunuz davranışta hafif değişikliklere neden olabilir. CsprojToVs2017, otomatikleştirilen temel şeyleri otomatikleştiren bir _Başlangıç noktası_ olarak kullanılmalıdır. Proje dosya biçimlerini geçirmek için garantili bir çözüm değildir.

>[!div class="step-by-step"]
>[Next](net-framework-tech-unavailable.md)
