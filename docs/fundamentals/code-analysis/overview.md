---
title: .NET 'teki kod analizi
titleSuffix: ''
description: .NET SDK 'da kaynak kodu analizi hakkında bilgi edinin.
ms.date: 08/22/2020
ms.topic: overview
ms.custom: updateeachrelease
helpviewer_keywords:
- code analysis
- code analyzers
ms.openlocfilehash: 8efac4d5e3fddcb9fdc6e08bcc933f2776420ced
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739980"
---
# <a name="overview-of-net-source-code-analysis"></a>.NET kaynak kodu çözümlemesine genel bakış

.NET derleyici platformu (Roslyn) çözümleyicileri, C# veya Visual Basic kodunuzda kod kalitesi ve kod stili sorunları olup olmadığını inceler. .NET 5.0’dan itibaren bu çözümleyiciler, .NET SDK’ya dahildir. .NET 5 + SDK ' ya geçmek istemiyorsanız veya bir NuGet paket tabanlı modeli tercih ediyorsanız, çözümleyiciler `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet paketinde](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)de mevcuttur. İsteğe bağlı sürüm güncelleştirmeleri için paket tabanlı bir model tercih edebilirsiniz.

> [!NOTE]
> .NET Çözümleyicileri hedef platform belirsiz. Diğer bir deyişle, projenizin belirli bir .NET platformunu hedeflemesi gerekmez. Çözümleyiciler, `net5.0` ve gibi önceki .NET sürümlerinin yanı sıra hedeflenen projeler için de çalışır `netcoreapp` `netstandard` `net472` .

- [Kod kalitesi analizi ("CAxxxx" kuralları)](#code-quality-analysis)
- [Kod stili Analizi ("ıdexxxx" kuralları)](#code-style-analysis)

Kural ihlalleri bir çözümleyici tarafından bulunursa, her kuralın nasıl [yapılandırıldığına](configuration-options.md)bağlı olarak öneri, uyarı veya hata olarak bildirilir. Kod Analizi ihlalleri, derleyici hatalarından ayırt edilebilmesi için "CA" veya "IDE" önekiyle birlikte görüntülenir.

> [!TIP]
>
> - [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [xUnit Çözümleyicileri](https://www.nuget.org/packages/xunit.analyzers/)ve [sonar Çözümleyicisi](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)gibi üçüncü taraf Çözümleyicileri de yükleyebilirsiniz.
> - Visual Studio kullanıyorsanız, birçok çözümleyici kuralı, sorunu gidermek için uygulayabileceğiniz ilişkili *kod düzeltmeleri* vardır. Kod düzeltmeleri ampul simgesi menüsünde gösterilir.

## <a name="code-quality-analysis"></a>Kod kalitesi analizi

_Code Quality Analysis ("CA") kuralları_ , güvenlik, performans, tasarım ve diğer sorunlar Için C# veya Visual Basic kodunuzu inceler. Varsayılan olarak, .NET 5,0 veya üstünü hedefleyen projeler için analiz etkindir. [Enablenetçözümleyiciler](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) özelliğini olarak ayarlayarak, önceki .NET sürümlerini hedefleyen projelerde Kod analizini etkinleştirebilirsiniz `true` . Ayrıca, olarak ayarlayarak projeniz için kod analizini devre dışı bırakabilirsiniz `EnableNETAnalyzers` `false` .

> [!TIP]
> Visual Studio 'da, proje Özellikler penceresi kullanarak kod analizini etkinleştirebilir veya devre dışı bırakabilirsiniz. Projeye Özellikler penceresi erişmek için, Çözüm Gezgini içindeki bir projeye sağ tıklayın ve **Özellikler**' i seçin. Ardından, **Kod Analizi** sekmesini seçin ve ardından **.net Çözümleyicileri 'ni etkinleştirmek** için onay kutusunu işaretleyin veya temizleyin.

### <a name="enabled-rules"></a>Etkin kurallar

Aşağıdaki kurallar, varsayılan olarak .NET 5,0 Preview 8 ' de etkinleştirilmiştir.

| Tanılama KIMLIĞI | Kategori | Önem Derecesi | Açıklama |
| - | - | - | - |
| [CA1416](/visualstudio/code-quality/ca1416) | Birlikte çalışabilirlik | Uyarı | Platform uyumluluk çözümleyicisi |
| [CA1417](/visualstudio/code-quality/ca1417) | Birlikte çalışabilirlik | Uyarı | `OutAttribute`P/Invoke için dize parametrelerinde kullanmayın |
| [CA1831](/visualstudio/code-quality/ca1831) | Performans | Uyarı | `AsSpan`Uygun olduğunda dize için Aralık tabanlı dizin oluşturucular yerine kullanın |
| [CA2013](/visualstudio/code-quality/ca2013) | Güvenilirlik | Uyarı | `ReferenceEquals`Değer türleriyle kullanma |
| [CA2014](/visualstudio/code-quality/ca2014) | Güvenilirlik | Uyarı | `stackalloc`Döngülerde kullanmayın |
| [CA2015](/visualstudio/code-quality/ca2015) | Güvenilirlik | Uyarı | Öğesinden türetilen türler için sonlandırıcılar tanımlama <xref:System.Buffers.MemoryManager%601> |
| [CA2200](/visualstudio/code-quality/ca2200) | Kullanım | Uyarı | Yığın ayrıntılarını korumak için yeniden fırlatın
| [CA2247](/visualstudio/code-quality/ca2247) | Kullanım | Uyarı | TaskCompletionSource oluşturucusuna geçirilen bağımsız değişken <xref:System.Threading.Tasks.TaskCreationOptions> yerine enum olmalıdır <xref:System.Threading.Tasks.TaskContinuationOptions> |

Bu kuralların önem derecesini devre dışı bırakmak veya hatalara yükseltmek için değiştirebilirsiniz.

Kullanılabilir kod kalitesi kurallarının tam listesi için bkz. [kod kalitesi kuralları](quality-rules/index.md).

### <a name="enable-additional-rules"></a>Ek kuralları etkinleştir

.NET SDK, .NET 5,0 RC2 'den başlayarak ["CA" kod kalitesi kurallarıyla](/visualstudio/code-quality/code-analysis-for-managed-code-warnings)birlikte gönderilir. Her .NET SDK sürümünde bulunan kuralların tam listesi için bkz. [çözümleyici yayınları](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).

#### <a name="default-analysis-mode"></a>Varsayılan analiz modu

Varsayılan analiz modunda, bazı kurallar [Varsayılan olarak](#enabled-rules) derleme uyarıları olarak etkindir. Diğer bazı kurallar varsayılan olarak yalnızca ilgili kod düzeltmeleriyle Visual Studio IDE önerileri olarak etkinleştirilmiştir. Kalan kurallar varsayılan olarak devre dışıdır. [Kuralların tam listesi](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md) , her kuralın varsayılan önem derecesini ve kuralın varsayılan analiz modunda varsayılan olarak etkinleştirilip etkinleştirilmediğini belirtir.

#### <a name="custom-analysis-mode"></a>Özel analiz modu

Tek bir kuralı veya kural kategorisini etkinleştirmek veya devre dışı bırakmak için [kod çözümleme kurallarını yapılandırabilirsiniz](configuration-options.md) . Ek olarak, aşağıdaki özel analiz modlarından birine geçiş yapmak için [Analysismode](../../core/project-sdk/msbuild-props.md#analysismode) özelliğini de kullanabilirsiniz:

- _Agresif_ veya geri _çevirme_ modu: tüm kurallar, derleme uyarıları olarak varsayılan olarak etkindir. Bağımsız kuralların devre dışı [bırakılacağını seçerek devre dışı bırakabilirsiniz](configuration-options.md) .
- _Koruyucu_ veya _kabul etme_ modu: tüm kurallar varsayılan olarak devre dışıdır. Bunları etkinleştirmek için tek tek kuralların seçmeli olarak [tercih](configuration-options.md) edebilirsiniz.

### <a name="treat-warnings-as-errors"></a>Uyarıları hata olarak değerlendir

Projelerinizi oluştururken bayrağını kullanırsanız `-warnaserror` , tüm kod analizi uyarıları da hata olarak değerlendirilir. Kod kalitesi uyarılarının (CAxxxx) ' de hata olarak değerlendirilmeyeceğini istemiyorsanız `-warnaserror` , `CodeAnalysisTreatWarningsAsErrors` MSBuild özelliğini `false` proje dosyanızda olarak ayarlayabilirsiniz.

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

Herhangi bir kod çözümleme uyarısı görmeye devam edersiniz, ancak derlemenizi bozmayacaktır.

### <a name="latest-updates"></a>En son güncelleştirmeler

Varsayılan olarak, .NET SDK 'sının daha yeni sürümlerine yükselttiğinizde en son kod çözümleme kurallarını ve varsayılan kural önem derecelerine sahip olursunuz. Bu davranışı istemiyorsanız, örneğin, yeni kuralların etkin veya devre dışı olmamasını sağlamak istiyorsanız, bunu aşağıdaki yollarla geçersiz kılabilirsiniz:

- `AnalysisLevel`Bu küme için uyarıları kilitlemek üzere MSBuild özelliğini belirli bir değere ayarlayın. Daha yeni bir SDK 'ya yükselttiğinizde, bu uyarılar için hata düzeltmeleri almaya devam edersiniz, ancak yeni bir uyarı etkinleştirilmeyecektir ve mevcut bir uyarı devre dışı bırakılacaktır. Örneğin, kurallar kümesini .NET SDK 'nın 5,0 sürümüyle birlikte gelen bunlarla kilitlemek için, proje dosyanıza aşağıdaki girişi ekleyin.

  ```xml
  <PropertyGroup>
    <AnalysisLevel>5.0</AnalysisLevel>
  </PropertyGroup>
  ```

  > [!TIP]
  > Özelliği için varsayılan değer, `AnalysisLevel` `latest` .NET SDK 'sının daha yeni sürümlerine geçtiğinizde her zaman en son kod çözümleme kurallarını alacağınız anlamına gelir.

  Daha fazla bilgi edinmek ve olası değerlerin bir listesini görmek için bkz. [Analysislevel](../../core/project-sdk/msbuild-props.md#analysislevel).

- .NET SDK güncelleştirmelerinden kural güncelleştirmelerini ayırmak için [Microsoft. CodeAnalysis. Netçözümleyiciler NuGet paketini](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) yükler. Paketin yüklenmesi yerleşik SDK Çözümleyicileri kapatır ve SDK, NuGet paketinden daha yeni bir çözümleyici derleme sürümü içeriyorsa derleme uyarısı oluşturur.

## <a name="code-style-analysis"></a>Kod stili Analizi

[Kod stili Analizi](/visualstudio/ide/editorconfig-code-style-settings-reference) ("ıdexxxx" kuralları), kod tabanınızda tutarlı kod stili tanımlamanızı ve bakımını yapmanızı sağlar. Varsayılan ayarlar aşağıda verilmiştir:

- Komut satırı derlemesi: komut satırı Derlemeleriyle ilgili tüm .NET projeleri için kod stili Analizi varsayılan olarak devre dışıdır.
- Visual Studio: kod stili analizi, varsayılan olarak Visual Studio içindeki tüm .NET projeleri için [kod yeniden düzenleme hızlı eylemleri](/visualstudio/ide/code-generation-in-visual-studio)olarak etkinleştirilmiştir.

.NET 5,0 RC2 'den başlayarak, derleme üzerinde kod stili analizini hem komut satırında hem de Visual Studio içinde etkinleştirebilirsiniz. Kod stili ihlalleri, uyarı veya "IDE" ön eki ile hatalar olarak görüntülenir. Bu, derleme zamanında tutarlı kod stilleri zorlamanıza olanak sağlar.

> [!NOTE]
> Kod stili analiz özelliği deneysel bir özelliktir ve .NET 5 ve .NET 6 sürümleri arasında değişebilir.

Derlemede kod stili analizini etkinleştirme adımları:

1. [Enforcecodestyleınbuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) MSBuild özelliğini olarak ayarlayın `true` .

1. Bir *. editorconfig* dosyasında, derleme üzerinde çalıştırmak istediğiniz her "IDE" kod stili kuralını bir uyarı veya hata olarak [yapılandırın](configuration-options.md) . Örnek:

   ```ini
   [*.{cs,vb}]
   # IDE0040: Accessibility modifiers required (escalated to a build warning)
   dotnet_diagnostic.IDE0040.severity = warning
   ```

   Alternatif olarak, varsayılan olarak "stil" kategorisinin tamamını bir uyarı veya hata olarak yapılandırabilir ve ardından derlemede çalıştırmak istemediğiniz kuralları seçmeli olarak kapatabilirsiniz. Örnek:

   ```ini
   [*.{cs,vb}]

   # Default severity for analyzer diagnostics with category 'Style' (escalated to build warnings)
   dotnet_analyzer_diagnostic.category-Style.severity = warning

   # IDE0040: Accessibility modifiers required (disabled on build)
   dotnet_diagnostic.IDE0040.severity = silent
   ```

## <a name="suppress-a-warning"></a>Bir uyarıyı gösterme

Bir kural ihlalini gizlemek için, bu kural KIMLIĞI için önem derecesi seçeneğini `none` bir EditorConfig dosyasında olarak ayarlayın. Örnek:

```ini
dotnet_diagnostic.CA1822.severity = none
```

Visual Studio, kod analizi kurallarından gelen uyarıları bastırmak için ek yollar sağlar. Daha fazla bilgi için bkz. [Ihlalleri gösterme](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).

Kural özellikleri hakkında daha fazla bilgi için bkz. [kural önem derecesini yapılandırma](configuration-options.md#severity-level).

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kalitesi analiz kuralı başvurusu](quality-rules/index.md)
- [Kod stili analiz kuralı başvurusu](style-rules/index.md)
- [Visual Studio’da kod analizi](/visualstudio/code-quality/roslyn-analyzers-overview)
- [.NET Compiler Platform SDK’sı](../../csharp/roslyn-sdk/index.md)
- [Öğretici: ilk çözümleyicinizi ve kod düzeltmesini yazma](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
