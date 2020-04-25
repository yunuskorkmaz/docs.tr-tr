---
title: .NET Framework’ten .NET Core’a taşıma
description: Bir .NET Framework projesi .NET Core 'a taşıma konusunda yararlı bulabileceğiniz yardım alabileceğiniz işlem ve bulma araçlarını anlayın.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: c6797a5b3a97ddd01f86498d896e859baf8997be
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158298"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>.NET Framework .NET Core 'a taşıma ile genel bakış

Şu anda .NET Core 'a taşıma konusunda ilgilendiğiniz .NET Framework çalışan bir kodunuz olabilir. Bu makalede aşağıdakiler sunulmaktadır:

* Taşıma işlemine genel bakış.
* Kodunuzu .NET Core 'a taşırken yararlı bulabileceğiniz araçların bir listesi.

## <a name="overview-of-the-porting-process"></a>Taşıma işlemine genel bakış

Birçok proje için .NET Framework .NET Core 'a (veya .NET Standard) taşıma görece bir şekilde ileriye doğru. Gerekli sayıda değişiklik vardır, ancak birçoğu aşağıda özetlenen desenleri izler. Uygulama modelinin .NET Core 'da (kitaplıklar, konsol uygulamaları ve Masaüstü uygulamaları gibi) kullanılabildiği projeler genellikle küçük değişiklikler gerektirir. Yeni bir uygulama modeli gerektiren projeler (örneğin, ASP.NET ' den ASP.NET Core taşıma gibi), biraz daha fazla iş gerektirir, ancak birçok desende dönüştürme sırasında kullanılabilecek analoglarından vardır. Bu belge, kod temellerini hedef .NET Standard veya .NET Core 'a başarıyla dönüştürmek üzere kullanıcılara çalışan ana stratejileri tanımlamaya yardımcı olmalıdır ve dönüştürme iki düzeyde ele alınacaktır: çözüm genelinde ve projeye özel. Uygulama modeline özgü dönüşümlerde yönergeler için en alttaki bağlantılara bakın.

Projenizi .NET Core 'a taşıma sırasında aşağıdaki işlemi kullanmanızı öneririz. Bu adımların her biri, davranış değişikliklerine yönelik olası yerleri tanıtır, bu nedenle sonraki adımlara devam etmeden önce kitaplığınızı veya uygulamanızı yeterince test ettirdiğinizden emin olun. İlk adımlar, projenizin .NET Standard veya .NET Core 'a yönelik bir anahtara hazırlanmaya yöneliktir. Birim testleriniz varsa, çalışmakta olduğunuz üründeki değişiklikleri test etmeye devam edebilmeniz için önce bunları dönüştürmeniz en iyisidir. .NET Core 'a taşıma işlemi, kod tabanınızda önemli bir değişiklik olduğundan, kodunuzun bağlantı noktası oluşturduğunuz testleri çalıştırabilmeniz için test projelerinizin bağlantı noktası yapılması önemle önerilir. MSTest, xUnit ve NUnit tüm .NET Core üzerinde çalışır.

## <a name="getting-started"></a>Başlarken

Aşağıdaki araçlar işlem boyunca kullanılacaktır:

- Visual Studio 2019
- [.Net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) 'ni indirin
- _Isteğe bağlı_ DotNet 'yi yüklemeyi [deneyin-Dönüştür](https://github.com/dotnet/try-convert)

## <a name="porting-a-solution"></a>Çözüm taşıma

Bir çözümde birden çok proje olduğunda, projeleri belirli bir sırada ele almanız gerektiğinden taşıma daha karmaşık görünebilir. Dönüştürme işlemi, çözümdeki diğer projelere bağımlılığı olmayan projelerin önce dönüştürülmesi ve tüm çözüm üzerinden devam etmesi için bir alt yaklaşım olmalıdır.

Sipariş projelerinin geçirilmesi gerektiğini belirlemek için aşağıdaki araçları kullanabilirsiniz:

- [Visual Studio 'Daki bağımlılık diyagramları](/visualstudio/modeling/create-layer-diagrams-from-your-code) , bir çözümde kodun yönlendirilmiş bir grafiğini oluşturabilir.
- Proje `msbuild _SolutionPath_ /t:GenerateRestoreGraphFile /p:RestoreGraphOutputPath=graph.dg.json` başvuruları listesini içeren bir JSON belgesi oluşturmak için öğesini çalıştırın.

## <a name="per-project-steps"></a>Proje adımları başına

Projenizi .NET Core 'a taşıma sırasında aşağıdaki işlemi kullanmanızı öneririz:

1. `packages.config` [Visual Studio 'daki Dönüştürme aracıyla](/nuget/consume-packages/migrate-packages-config-to-package-reference)tüm bağımlılıklarınızı [packagereference](/nuget/consume-packages/package-references-in-project-files) biçimine dönüştürün.

   Bu adım, bağımlılıklarınızı eski `packages.config` biçimden dönüştürmeyi içerir. `packages.config`, .NET Core üzerinde çalışmaz, bu nedenle paket bağımlılıklarınız varsa bu dönüştürme gereklidir. Ayrıca, yalnızca bir projede doğrudan kullandığınız bağımlılıklara gerek duyar, bu da daha sonra yönetmeniz gereken bağımlılıkların sayısını azaltarak daha sonra daha kolay bir hale getirir.

1. Proje dosyanızı yeni SDK stili dosya yapısına dönüştürün. .NET Core için yeni projeler oluşturabilir ve kaynak dosyaları üzerine kopyalayabilir ya da mevcut proje dosyanızı bir araçla dönüştürmeyi deneyebilirsiniz.

   .NET Core .NET Framework göre Basitleştirilmiş (ve farklı) bir [Proje dosyası biçimi](../tools/csproj.md) kullanır. Devam etmek için proje dosyalarınızı bu biçime dönüştürmeniz gerekir. Bu proje stili, bu noktada yine de hedeflemek istediğiniz .NET Framework de hedeflemesini sağlar.

   En küçük çözüm veya tek bir işlemde, [DotNet TRY-Convert](https://github.com/dotnet/try-convert) aracı Ile .NET Core proje dosyası biçimine bir işlem üzerinden bağlantı kurmayı deneyebilirsiniz. `dotnet try-convert`Tüm projeleriniz için çalışma garantisi verilmez ve bağımlı olduğunuz davranışta hafif değişikliklere neden olabilir. Otomatikleştirilmiş olabilecek temel şeyleri otomatikleştiren bir _Başlangıç noktası_ olarak kullanın. SDK stil projeleri tarafından kullanılan hedeflerde eski stil projesi dosyalarıyla karşılaştırılan birçok fark olduğundan, projenin geçirilmesi için garantili bir çözüm değildir.

1. .NET Framework 4.7.2 veya üstünü hedeflemek için, bağlantı noktası yapmak istediğiniz tüm projeleri yeniden hedefleyin.

   Bu adım, .NET Core belirli bir API 'YI desteklemedikleri zaman .NET Framework özel hedefler için API alternatifleri kullanmanıza da sağlar.

1. Tüm bağımlılıkları en son sürüme güncelleştirin. Projeler, .NET Standard desteği olmayan kitaplıkların eski sürümlerini kullanıyor olabilir. Ancak, sonraki sürümler bunu basit bir anahtarla destekleyebilir. Kitaplıklarda önemli değişiklikler varsa, bu durum kod değişiklikleri gerektirebilir.

1. Derlemelerinizi çözümlemek ve .NET Core 'a taşınabilir olup olmadığını görmek için [.net taşınabilirlik Çözümleyicisi](../../standard/analyzers/portability-analyzer.md) 'ni kullanın.

   .NET taşınabilirlik Çözümleyicisi Aracı, derlenmiş derlemelerinizi analiz eder ve bir rapor oluşturur. Bu rapor, üst düzey bir taşınabilirlik özetini ve kullanmakta olduğunuz her API 'nin, NET Core 'da kullanılamayan bir dökümünü gösterir. Aracı kullanırken, yalnızca dönüştürdüğünüz tek projeyi, gerekli olabilecek API değişikliklerine odaklanmak üzere gönder. API 'lerin çoğunun .NET Core 'da eşdeğer kullanılabilirliği vardır ve bu, ' ye geçmek isteyeceksiniz.

   Çözümleyici tarafından oluşturulan raporları okurken önemli bilgiler, kullanılmakta olan gerçek API 'lardır ve hedef platform için desteğin yüzdesi değildir. Birçok API .NET Standard/çekirdek içinde eşdeğer seçeneklere sahiptir ve bu nedenle kitaplığınızın veya uygulamanızın API için gereken senaryoları anlamak, taşınabilirliğin belirlenmesini sağlamaya yardımcı olur.

   API 'Lerin eşdeğer olmadığı bazı durumlar vardır ve platformlar için bazı derleyici Önişlemci yönergeleri (yani, `#if NET45`) yapmanız gerekir. Bu noktada, projeniz .NET Framework hedeflemeye devam eder. Bu hedeflenen durumların her biri için, bir senaryo olarak anlayabileceği iyi bilinen koşullar kullanılması önerilir.  Örneğin, .NET Core 'da AppDomain desteği sınırlıdır, ancak derlemeleri yükleme ve kaldırma senaryosunda .NET Core 'da kullanılamayan yeni bir API vardır. Bu kodu kodda işlemenin yaygın bir yolu şöyle olacaktır:

   ```csharp
   #if FEATURE_APPDOMAIN_LOADING
   // Code that uses appdomains
   #elif FEATURE_ASSEMBLY_LOAD_CONTEXT
   // Code that uses assembly load context
   #else
   #error Unsupported platform
   #endif
   ```

1. Bazı platformlarda ve diğer olası Uyumluluk sorunlarından oluşan <xref:System.PlatformNotSupportedException> API 'leri tanımlamak için, projelerinize [.NET API Çözümleyicisi](../../standard/analyzers/api-analyzer.md) 'ni yükler.

   Bu araç taşınabilirlik Çözümleyicisi ile benzerdir, ancak kodun .NET Core üzerinde oluşturulup oluşturulmayacağını çözümlemek yerine, bir API 'yi çalışma zamanında oluşturacak şekilde <xref:System.PlatformNotSupportedException> kullanıp kullanmayacağınızı analiz eder. .NET Framework 4.7.2 veya üzeri bir sürümü taşıyorsanız, bu yaygın olmasa da kontrol etmeniz iyidir. .NET Core üzerinde özel durumlar oluşturan API 'Ler hakkında daha fazla bilgi için bkz. [.NET Core üzerinde her zaman özel durum oluşturan API 'ler](../compatibility/unsupported-apis.md).

1. Bu noktada, .NET Core 'u (genellikle uygulamalar için) veya .NET Standard (kitaplıklar için) hedeflemek için geçiş yapabilirsiniz.

   .NET Core ve .NET Standard arasındaki seçim büyük ölçüde projenin çalıştırılacağı yere bağlıdır. Diğer uygulamalar tarafından tüketilen veya NuGet aracılığıyla dağıtılan bir kitaplıktır, genellikle .NET Standard hedeflenecek. Ancak, yalnızca performans veya diğer nedenlerle .NET Core 'da kullanılabilen API 'Ler olabilir; Bu durumda, .NET Core, büyük olasılıkla bir .NET Standard derlemesi ile daha az performans veya işlevselliğe sahip olacak şekilde hedeflenmelidir. .NET Standard hedefleyerek, proje yeni platformlarda (WebAssembly gibi) çalıştırılmaya hazırlanacaktır. Projenin belirli uygulama çerçeveleri üzerinde bağımlılıkları varsa (örneğin, ASP.NET Core), hedef, bağımlılıkların desteklediklerinize göre sınırlandırılır.

   .NET Framework veya .NET Standard için koşullu derleme koduna yönelik bir ön işlemci yönergesi yoksa, proje dosyasında aşağıdakileri bulmak kadar basit olacaktır:

   ```xml
   <TargetFramework>net472</TargetFramework>
   ```

   ve istediğiniz çerçeveye geçiş yapın. .NET Core 3,1 için şu şekilde olur:

   ```xml
   <TargetFramework>netcoreapp3.1</TargetFramework>
   ```

   Ancak, .NET Framework özgü yapıları desteklemeye devam etmek istediğiniz bir kitaplıktır, bunu aşağıdaki ile değiştirerek [Çoklu hedefleyebilirsiniz](../../standard/library-guidance/cross-platform-targeting.md) :

   ```xml
   <TargetFrameworks>net472;netstandard2.0</TargetFrameworks>
   ```

   Windows 'a özgü API 'Ler kullanıyorsanız (kayıt defteri erişimi gibi), [Windows Uyumluluk Paketi](./windows-compat-pack.md)' ni yükleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Analyze dependencies](third-party-deps.md)
> [ASP.NET Core geçiş için](/aspnet/core/migration/proper-to-2x) bağımlılıklar[paketi NuGet paketi](../deploying/creating-nuget-packages.md)
> ASP.net
