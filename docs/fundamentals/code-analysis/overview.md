---
title: .NET 'teki kod analizi
titleSuffix: ''
description: .NET SDK 'da kaynak kodu analizi hakkında bilgi edinin.
ms.date: 12/04/2020
ms.topic: overview
ms.custom: updateeachrelease
helpviewer_keywords:
- code analysis
- code analyzers
ms.openlocfilehash: efc440adb59da1ef9838ec5445d9c55544c14380
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216479"
---
# <a name="overview-of-net-source-code-analysis"></a>.NET kaynak kodu çözümlemesine genel bakış

.NET derleyici platformu (Roslyn) çözümleyicileri, C# veya Visual Basic kodunuzda kod kalitesi ve kod stili sorunları olup olmadığını inceler. .NET 5,0 ' den itibaren bu çözümleyiciler .NET SDK 'ya dahildir ve bunları ayrı olarak yüklemeniz gerekmez. Projeniz .NET 5 veya sonraki bir sürümünü hedefliyorsa, kod analizi varsayılan olarak etkindir. Projeniz, örneğin .NET Core, .NET Standard veya .NET Framework gibi farklı bir .NET uygulamasını hedefliyorsanız, [Enablenetçözümleyiciler](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) özelliğini olarak ayarlayarak Kod analizini el ile etkinleştirmeniz gerekir `true` .

.NET 5 + SDK ' ya geçmek istemiyorsanız veya bir NuGet paket tabanlı modeli tercih ediyorsanız, çözümleyiciler [Microsoft. CodeAnalysis. Netçözümleyiciler NuGet paketinde](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)de mevcuttur. İsteğe bağlı sürüm güncelleştirmeleri için paket tabanlı bir model tercih edebilirsiniz.

> [!NOTE]
> .NET Çözümleyicileri hedef çerçeve belirsiz. Diğer bir deyişle, projenizin belirli bir .NET uygulamasını hedeflemesi gerekmez. Çözümleyiciler, `net5.0` ve gibi önceki .NET sürümlerinin yanı sıra hedeflenen projeler için de çalışır `netcoreapp3.1` `net472` .

Kural ihlalleri bir çözümleyici tarafından bulunursa, her kuralın nasıl [yapılandırıldığına](configuration-options.md)bağlı olarak öneri, uyarı veya hata olarak bildirilir. Kod Analizi ihlalleri, derleyici hatalarından ayırt edilebilmesi için "CA" veya "IDE" önekiyle birlikte görüntülenir.

## <a name="code-quality-analysis"></a>Kod kalitesi analizi

*Code Quality Analysis* ("caxxxx") kuralları, güvenlik, performans, tasarım ve diğer sorunlar Için C# veya Visual Basic kodunuzu inceler. Varsayılan olarak, .NET 5,0 veya üstünü hedefleyen projeler için analiz etkindir. [Enablenetçözümleyiciler](../../core/project-sdk/msbuild-props.md#enablenetanalyzers) özelliğini olarak ayarlayarak, önceki .NET sürümlerini hedefleyen projelerde Kod analizini etkinleştirebilirsiniz `true` . Ayrıca, olarak ayarlayarak projeniz için kod analizini devre dışı bırakabilirsiniz `EnableNETAnalyzers` `false` .

> [!TIP]
> Visual Studio kullanıyorsanız:
>
> - Birçok çözümleyici kuralı, sorunu gidermek için uygulayabileceğiniz ilişkili *kod düzeltmeleri* vardır. Kod düzeltmeleri ampul simgesi menüsünde gösterilir.
> - Kod analizini etkinleştirebilir veya devre dışı bırakabilir Çözüm Gezgini ' de bir projeye sağ tıklayıp **Özellikler**  >  **Kod Analizi** > sekmesi ' ni seçerek **.net Çözümleyicileri**' ni etkinleştirebilirsiniz.

### <a name="enabled-rules"></a>Etkin kurallar

Aşağıdaki kurallar, varsayılan olarak, .NET 5,0 ' de etkinleştirilmiştir.

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

Bu kuralların önem derecesini devre dışı bırakmak veya hatalara yükseltmek için değiştirebilirsiniz. Ayrıca, [daha fazla kural da etkinleştirebilirsiniz](#enable-additional-rules).

- Her .NET SDK sürümünde bulunan kuralların listesi için bkz. [çözümleyici yayınları](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).
- Tüm kod kalitesi kurallarının bir listesi için bkz. [kod kalitesi kuralları](quality-rules/index.md).

### <a name="enable-additional-rules"></a>Ek kuralları etkinleştir

*Analiz modu* , hiçbir yerde, bazı veya tüm kuralların etkin olduğu önceden tanımlanmış bir kod analizi yapılandırmasına başvurur. Varsayılan analiz modunda, [derleme uyarıları olarak](#enabled-rules)yalnızca az sayıda kural etkindir. Proje dosyasındaki [analysismode](../../core/project-sdk/msbuild-props.md#analysismode) özelliğini ayarlayarak projenizin analiz modunu değiştirebilirsiniz. İzin verilen değerler şunlardır:

| Değer | Açıklama |
| - | - |
| `AllDisabledByDefault` | Bu en koruyucu moddur. Tüm kurallar varsayılan olarak devre dışıdır. Bunları etkinleştirmek için tek tek kuralların seçmeli olarak [tercih](configuration-options.md) edebilirsiniz.<br /><br />`<AnalysisMode>AllDisabledByDefault</AnalysisMode>` |
| `AllEnabledByDefault` | Bu en agresif moddur. Tüm kurallar derleme uyarıları olarak etkinleştirilir. Bağımsız kuralların devre dışı bırakılacağını seçerek [devre dışı bırakabilirsiniz](configuration-options.md) .<br /><br />`<AnalysisMode>AllEnabledByDefault</AnalysisMode>` |
| `Default` | Tek bir kuralların uyarı olarak etkinleştirildiği varsayılan mod olan, diğerleri yalnızca ilgili kod düzeltmeleriyle Visual Studio IDE önerileri olarak etkinleştirilir ve REST tamamen devre dışı bırakılır. Onları devre dışı bırakmak için bağımsız kuralların seçmeli olarak [tercih edilebilir veya dışında](configuration-options.md) bırakabilirsiniz.<br /><br />`<AnalysisMode>Default</AnalysisMode>` |

Kullanılabilir her bir kuralın varsayılan önem derecesini bulmak ve kuralın varsayılan analiz modunda etkinleştirilip etkinleştirilmediğini anlamak için [kuralların tam listesine](https://github.com/dotnet/roslyn-analyzers/blob/master/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md)bakın.

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

## <a name="code-style-analysis"></a>Kod stili analiz

*Kod stili analiz* ("ıdexxxx") kuralları, kod tabanınızda tutarlı kod stili tanımlamanızı ve bakımını sağlar. Varsayılan etkinleştirme ayarları şunlardır:

- Komut satırı derlemesi: komut satırı Derlemeleriyle ilgili tüm .NET projeleri için, varsayılan olarak kod stili çözümleme devre dışıdır.

  .NET 5,0 ' den başlayarak, [derleme üzerinde kod stili analizini](#enable-on-build)hem komut satırında hem de Visual Studio içinde etkinleştirebilirsiniz. Kod stili ihlalleri, uyarı veya "IDE" ön eki ile hatalar olarak görüntülenir. Bu, derleme zamanında tutarlı kod stilleri zorlamanıza olanak sağlar.

- Visual Studio: kod stili analizi, varsayılan olarak Visual Studio içindeki tüm .NET projeleri için [kod yeniden düzenleme hızlı eylemleri](/visualstudio/ide/code-generation-in-visual-studio)olarak etkinleştirilmiştir.

Kod stili analiz kurallarının tam listesi için bkz. [kod stili kuralları](style-rules/index.md).

### <a name="enable-on-build"></a>Derlemede etkinleştir

.NET 5,0 SDK ve sonraki sürümlerinde, komut satırından ve Visual Studio 'da oluştururken kod stili analizini etkinleştirebilirsiniz. (Ancak, performans nedenleriyle, tek [bir kod stili kuralları](https://github.com/dotnet/roslyn/blob/9f87b444da9c48a4d492b19f8337339056bf2b95/src/Analyzers/Core/Analyzers/EnforceOnBuildValues.cs#L95) yalnızca VISUAL Studio IDE 'de de geçerlidir.)

Derlemede kod stili analizini etkinleştirmek için şu adımları izleyin:

1. [Enforcecodestyleınbuild](../../core/project-sdk/msbuild-props.md#enforcecodestyleinbuild) MSBuild özelliğini olarak ayarlayın `true` .

1. Bir *. editorconfig* dosyasında, derleme üzerinde çalıştırmak istediğiniz her "IDE" kod stili kuralını bir uyarı veya hata olarak [yapılandırın](configuration-options.md) . Örneğin:

   ```ini
   [*.{cs,vb}]
   # IDE0040: Accessibility modifiers required (escalated to a build warning)
   dotnet_diagnostic.IDE0040.severity = warning
   ```

   Alternatif olarak, bir kategorinin tamamını bir uyarı veya hata olması için varsayılan olarak yapılandırabilir ve ardından bu kategoride, derlemede çalıştırmak istemediğiniz kuralları seçmeli olarak kapatabilirsiniz. Örneğin:

   ```ini
   [*.{cs,vb}]

   # Default severity for analyzer diagnostics with category 'Style' (escalated to build warnings)
   dotnet_analyzer_diagnostic.category-Style.severity = warning

   # IDE0040: Accessibility modifiers required (disabled on build)
   dotnet_diagnostic.IDE0040.severity = silent
   ```

> [!NOTE]
> Kod stili analiz özelliği deneysel olur ve .NET 5 ile .NET 6 sürümleri arasında değişebilir.

## <a name="suppress-a-warning"></a>Bir uyarıyı gösterme

Bir kural ihlalini gizlemek için, bu kural KIMLIĞI için önem derecesi seçeneğini `none` bir EditorConfig dosyasında olarak ayarlayın. Örneğin:

```ini
dotnet_diagnostic.CA1822.severity = none
```

Visual Studio, kod analizi kurallarından gelen uyarıları bastırmak için ek yollar sağlar. Daha fazla bilgi için bkz. [Ihlalleri gösterme](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).

Kural özellikleri hakkında daha fazla bilgi için bkz. [kural önem derecesini yapılandırma](configuration-options.md#severity-level).

## <a name="third-party-analyzers"></a>Üçüncü taraf çözümleyiciler

Resmi .NET çözümleyicilerine ek olarak, [StyleCop](https://www.nuget.org/packages/StyleCop.Analyzers/), [roslynator](https://www.nuget.org/packages/Roslynator.Analyzers/), [xUnit Çözümleyicileri](https://www.nuget.org/packages/xunit.analyzers/)ve [sonar Çözümleyicisi](https://www.nuget.org/packages/SonarAnalyzer.CSharp/)gibi üçüncü taraf Çözümleyicileri de yükleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod kalitesi analiz kuralı başvurusu](quality-rules/index.md)
- [Kod stili analiz kuralı başvurusu](style-rules/index.md)
- [Visual Studio’da kod analizi](/visualstudio/code-quality/roslyn-analyzers-overview)
- [.NET Compiler Platform SDK’sı](../../csharp/roslyn-sdk/index.md)
- [Öğretici: ilk çözümleyicinizi ve kod düzeltmesini yazma](../../csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix.md)
