---
title: .NET Framework'te bağlantı noktası koddan .NET Core
description: Taşıma işlemlerini anlamanıza ve .NET Core için bir .NET Framework projesi taşırken faydalı bulabileceğiniz araçları keşfedin.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 870320c8467237e87a2675ec5cfb57647026d8ec
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903562"
---
# <a name="port-your-code-from-net-framework-to-net-core"></a>.NET Framework kodunuzu .NET Core için bağlantı noktası

.NET Framework üzerinde çalışan kod kendinizi, kodunuzu .NET Core üzerinde çok çalışan ilginizi çekebilir. Taşıma işlemine genel bakış şöyledir ve Araçlar listesi, .NET Core için kodunuzu taşırken yararlı olabilir.

## <a name="overview-of-the-porting-process"></a>Taşıma işlemine genel bakış

Bu, projeniz .NET Core taşırken göz önüne almanız tavsiye ederiz işlemidir. Her adım işlemin daha fazla makalelerinde daha ayrıntılı ele alınmıştır.

1. Tanımlamak ve üçüncü taraf bağımlılıklarınızı hesap.

   Bu adım, hangi üçüncü taraf bağımlılıkları olan, bağımlı nasıl anlamayı gerektirir bunları sağlanmıyorsa de .NET Core ve adımları çalıştırırsanız, kontrol etmek için uygulayabileceğiniz nasıl. Ayrıca nasıl bağımlılıklarınızı üzerinden a geçirebileceğiniz kapsar [PackageReference](/nuget/consume-packages/package-references-in-project-files) ' de .NET Core kullanılan biçim.

2. Hedef .NET Framework'ü 4.7.2 taşımak istediğiniz tüm projeleri yeniden hedefle veya üzeri.

   Bu adım, belirli bir API'yi .NET Core desteklemediğinde, API alternatifleri .NET Framework özel hedefler için kullanabileceğiniz sağlar.

3. Kullanım [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) bütünleştirilmiş kodlarınızı analiz edin ve kendi sonuçlarına göre bağlantı noktası için bir plan geliştirin.

   API taşınabilirlik Çözümleyicisi aracını, derlenen bütünleştirilmiş kodlarınızı analiz eder ve bir üst düzey taşınabilirlik Özet gösteren bir rapor ve .NET Core üzerinde kullanılamayan, kullanmakta olduğunuz her API bir dökümünü oluşturur. Bu raporu analizini yanı sıra kullanabilirsiniz, nasıl, kodunuzu üzerinden bağlantı noktası bir plan geliştirmek için kod tabanı.

4. Testleri kod bağlantı noktası.

   .NET Core'a taşıma kod temeliniz için önemli değişiklik olduğundan, yüksek oranda kodunuzu üzerinden bağlantı noktası olarak testleri çalıştırabilmeniz için unity'nin, testlerinizi almak için önerilir. .NET Core, MSTest, xUnit ve Nunit'i destekler.

5. Taşıma için planınızı yürütün!

Aşağıdaki liste, taşıma işlemi sırasında kullanılacak yararlı bulabileceğiniz araçları gösterir:

* .NET portability Analyzer - [komut satırı aracını](https://github.com/Microsoft/dotnet-apiport/releases) veya [Visual Studio Uzantısı](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer), nasıl taşınabilir kod arasında .NET Framework ve .NET Core ile olan bir rapor oluşturabilen bir araç zinciri bir derleme tarafından bütünleştirilmiş kod çözümleme sorunları. Daha fazla bilgi için [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md).
* .NET API Çözümleyicisi - olası uyumluluk risk bulur bir Roslyn çözümleyicinizi C# farklı platformlarda API'leri ve kullanım dışı API'lere giden çağrıların algılar. Daha fazla bilgi için [.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md).
* Ters paket arama - A [yararlı web hizmeti](https://packagesearch.azurewebsites.net) türü için arama yapın ve bu türü içeren paketleri olanak tanır.

Ayrıca, bağlantı noktası daha küçük çözümleri veya .NET Core proje dosyası biçimi ile tek tek projelere deneyebilirsiniz [CsprojToVs2017](https://github.com/hvanbakel/CsprojToVs2017) aracı.

> [!WARNING] 
> CsprojToVs2017 üçüncü taraf bir araçtır. Tüm projeleriniz için çalışacak bir garanti yoktur ve ince değişiklikler, bağımlı davranış neden. CsprojToVs2017 olarak kullanılmalıdır bir _başlangıç noktası_ otomatikleştirilebilir temel işlemleri otomatikleştirir. Bu geçişi proje dosya biçimleri için garantili bir çözüm değildir.

>[!div class="step-by-step"]
>[Next](net-framework-tech-unavailable.md)
