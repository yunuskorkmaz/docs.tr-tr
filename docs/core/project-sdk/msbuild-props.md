---
title: Microsoft. NET. SDK için MSBuild özellikleri
description: MSBuild özellikleri ve .NET SDK tarafından anlaşılan öğeler için başvuru.
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: e35ccc3540756a4cb7905d5864caf65cded4362b
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189992"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a>.NET SDK projeleri için MSBuild başvurusu

Bu sayfa, MSBuild özelliklerine ve .NET projelerini yapılandırmak için kullanabileceğiniz öğelere yönelik bir başvurudur.

> [!NOTE]
> Bu sayfa devam eden bir çalışmadır ve .NET SDK için tüm kullanışlı MSBuild özelliklerini listelemez. Ortak MSBuild özelliklerinin bir listesi için bkz. [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Çerçeve özellikleri

- [TargetFramework](#targetframework)
- [Targetçerçeveler](#targetframeworks)
- [Netstandardımplicitpackageversion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework

`TargetFramework`Özelliği, uygulamanın hedef Framework sürümünü belirtir. Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-frameworks).

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).

### <a name="targetframeworks"></a>Targetçerçeveler

`TargetFrameworks`Uygulamanızın birden çok platformu hedeflemesini istediğinizde özelliğini kullanın. Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-frameworks).

> [!NOTE]
> `TargetFramework`(Tekil) belirtilmişse bu özellik yoksayılır.

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).

### <a name="netstandardimplicitpackageversion"></a>Netstandardımplicitpackageversion

> [!NOTE]
> Bu özellik yalnızca kullanan projeler için geçerlidir `netstandard1.x` . Kullanan projeler için uygulanmaz `netstandard2.x` .

`NetStandardImplicitPackageVersion`Metapackage sürümünden daha düşük bir çerçeve sürümü belirtmek istediğinizde özelliğini kullanın. Aşağıdaki örnekteki proje dosyası hedefler, `netstandard1.3` ancak 1.6.0 sürümünü kullanır `NETStandard.Library` .

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a>Paket özellikleri

`PackageId` `PackageVersion` `PackageIcon` `Title` `Description` Projenizden oluşturulan paketi betimleyen,,, ve gibi özellikleri belirtebilirsiniz. Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [Pack Target](/nuget/reference/msbuild-targets#pack-target).

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-items-and-metadata"></a>Özellikleri, öğeleri ve meta verileri Yayımla

- [Appendruntimeıdentifiertooutputpath](#appendruntimeidentifiertooutputpath)
- [AppendTargetFrameworkToOutputPath](#appendtargetframeworktooutputpath)
- [CopyLocalLockFileAssemblies](#copylocallockfileassemblies)
- [CopyToPublishDirectory](#copytopublishdirectory)
- [Tabanlarını](#linkbase)
- [Runtimeıdentifier](#runtimeidentifier)
- [Runtimetanımlayıcıtanımlayıcıları](#runtimeidentifiers)
- [TrimmerRootAssembly](#trimmerrootassembly)
- [UseAppHost](#useapphost)

### <a name="copytopublishdirectory"></a>CopyToPublishDirectory

`CopyToPublishDirectory`MSBuild öğesindeki meta veriler, öğe yayımlama dizinine kopyalandığında denetler. İzin verilen değerler `PreserveNewest` , yalnızca değiştirilirse öğeyi kopyalayan, `Always` her zaman öğeyi kopyalayan ve öğeyi `Never` hiçbir zaman kopyalamamış olan değerlerdir. Bir performans açısından, `PreserveNewest` artımlı bir derlemeyi sağladığından tercih edilir.

```xml
<ItemGroup>
  <None Update="appsettings.Development.json" CopyToOutputDirectory="PreserveNewest" CopyToPublishDirectory="PreserveNewest" />
</ItemGroup>
```

### <a name="linkbase"></a>Tabanlarını

Proje dizini ve alt dizinleri dışında olan bir öğe için, Yayımla hedefi öğenin [bağlantı meta verilerini](/visualstudio/msbuild/common-msbuild-item-metadata) kullanarak öğenin nereye kopyalanacağını tespit edin. `Link` Ayrıca, proje ağacının dışındaki öğelerin Visual Studio 'nun Çözüm Gezgini penceresinde nasıl görüntüleneceğini belirler.

`Link`Proje konisi dışında bir öğe için belirtilmemişse, varsayılan olarak öğesine ayarlanır `%(LinkBase)\%(RecursiveDir)%(Filename)%(Extension)` . `LinkBase` Proje koni dışındaki öğeler için bir senerişilebilir taban klasörü belirtmenizi sağlar. Taban klasörü altındaki klasör hiyerarşisi aracılığıyla korunur `RecursiveDir` . `LinkBase`Belirtilmemişse, `Link` yolundan çıkarılır.

```xml
<ItemGroup>
  <Content Include="..\Extras\**\*.cs" LinkBase="Shared"/>
</ItemGroup>
```

Aşağıdaki görüntüde, önceki öğe ile eklenen bir dosyanın `Include` Çözüm Gezgini ' de nasıl görüntüleyeceği gösterilmektedir.

:::image type="content" source="media/solution-explorer-linkbase.png" alt-text="Çözüm Gezgini bağlantı tabanının meta verileri içeren öğe gösteriliyor.":::

### <a name="appendtargetframeworktooutputpath"></a>AppendTargetFrameworkToOutputPath

`AppendTargetFrameworkToOutputPath`Özelliği, [hedef çerçeve adının (TFI)](../../standard/frameworks.md) çıkış yolunun ( [OutputPath](/visualstudio/msbuild/common-msbuild-project-properties#list-of-common-properties-and-parameters)tarafından tanımlanan) eklenip eklenmeyeceğini denetler. .NET SDK, hedef çerçeveyi otomatik olarak ekler ve varsa, çalışma zamanı tanımlayıcısını çıkış yoluna ekler. `AppendTargetFrameworkToOutputPath`İçin ayarı `false` , TFI 'nin çıkış yoluna eklenmesini engeller. Ancak, çıkış yolunda TFı olmadan, birden çok derleme yapıtları birbirinin üzerine yazılabilir.

Örneğin, bir .NET 5,0 uygulaması için çıkış yolu, ' dan ' ı `bin\Debug\net5.0` `bin\Debug` aşağıdaki ayarla olarak değişir:

```xml
<PropertyGroup>
  <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
</PropertyGroup>
```

### <a name="appendruntimeidentifiertooutputpath"></a>Appendruntimeıdentifiertooutputpath

`AppendRuntimeIdentifierToOutputPath`Özelliği, [çalışma zamanı TANıMLAYıCıSıNıN (RID)](../rid-catalog.md) çıkış yolunun sonuna eklenip eklenmeyeceğini denetler. .NET SDK, hedef çerçeveyi otomatik olarak ekler ve varsa, çalışma zamanı tanımlayıcısını çıkış yoluna ekler. `AppendRuntimeIdentifierToOutputPath`İçin ayarı `false` , RID 'nin çıkış yoluna eklenmesini önler.

Örneğin, bir .NET 5,0 uygulaması ve bir RID 'si için `win10-x64` çıkış yolu, ' dan ' ı `bin\Debug\net5.0\win10-x64` `bin\Debug\net5.0` aşağıdaki ayarla olarak değişir:

```xml
<PropertyGroup>
  <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
</PropertyGroup>
```

### <a name="copylocallockfileassemblies"></a>CopyLocalLockFileAssemblies

`CopyLocalLockFileAssemblies`Özelliği, diğer kitaplıklara bağımlılıkları olan eklenti projeleri için yararlıdır. Bu özelliği olarak ayarlarsanız `true` , herhangi bir NuGet paketi bağımlılığı çıkış dizinine kopyalanır. Diğer bir deyişle, `dotnet build` herhangi bir makinede kendi eklentisini çalıştırmak için çıkışını kullanabilirsiniz.

```xml
<PropertyGroup>
  <CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>
</PropertyGroup>
```

> [!TIP]
> Alternatif olarak, `dotnet publish` sınıf kitaplığını yayımlamak için kullanabilirsiniz. Daha fazla bilgi için bkz. [DotNet Publish](../tools/dotnet-publish.md).

### <a name="runtimeidentifier"></a>Runtimeıdentifier

`RuntimeIdentifier`Özelliği, proje için tek bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır. RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a>Runtimetanımlayıcıtanımlayıcıları

`RuntimeIdentifiers`Özelliği, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır. Birden çok çalışma zamanı için yayımlamanız gerekiyorsa bu özelliği kullanın. `RuntimeIdentifiers` , doğru varlıkların grafikte olduğundan emin olmak için geri yükleme zamanında kullanılır.

> [!TIP]
> `RuntimeIdentifier` (tekil) yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a>TrimmerRootAssembly

`TrimmerRootAssembly`Öğe, bir derlemeyi [*kırpmanıza*](../deploying/trim-self-contained.md)dışlamanızı sağlar. Kırpma, çalışma zamanının kullanılmayan parçalarını paketlenmiş bir uygulamadan kaldırma işlemidir. Bazı durumlarda, kırpma gerekli başvuruları yanlış kaldırabilir.

Aşağıdaki XML, `System.Security` derlemeyi kırpmaya dışlar.

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a>UseAppHost

`UseAppHost`Özelliği, bir dağıtım için yerel yürütülebilir dosyanın oluşturulup oluşturulmayacağını denetler. Kendi kendine kapsanan dağıtımlar için yerel bir yürütülebilir dosya gereklidir.

.NET Core 3,0 ve sonraki sürümlerinde, çerçeveye bağlı bir yürütülebilir dosya varsayılan olarak oluşturulur. `UseAppHost` `false` Yürütülebilir dosyanın üretilmesini devre dışı bırakmak için özelliğini olarak ayarlayın.

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

Dağıtım hakkında daha fazla bilgi için bkz. [.NET uygulama dağıtımı](../deploying/index.md).

## <a name="compile-properties"></a>Derleme özellikleri

- [Embeddedresourceusebağımlıtuponconvention](#embeddedresourceusedependentuponconvention)
- [LangVersion](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a>Embeddedresourceusebağımlıtuponconvention

Özelliği, kaynak dosyaları `EmbeddedResourceUseDependentUponConvention` ile birlikte bulunan kaynak dosyalardaki tür bilgilerden kaynak bildirim dosyası adlarının oluşturulup oluşturulmayacağını tanımlar. Örneğin, *Form1. resx* , *Form1.cs* ile aynı klasörssa ve olarak `EmbeddedResourceUseDependentUponConvention` ayarlanırsa `true` , oluşturulan *. resources* dosyası, *Form1.cs* içinde tanımlanan ilk türden alır. Örneğin, `MyNamespace.Form1` *Form1.cs* içinde tanımlanan ilk tür ise, oluşturulan dosya adı *MyNamespace. Form1. resources* olur.

> [!NOTE]
> `LogicalName`,, `ManifestResourceName` Veya `DependentUpon` meta veriler bir öğe için belirtilmişse `EmbeddedResource` , bu kaynak dosyası için oluşturulan bildirim dosyası adı bu meta verileri temel alır.

Varsayılan olarak, yeni bir .NET projesinde, bu özellik olarak ayarlanır `true` . `false`, Ve öğesi için, `LogicalName` `ManifestResourceName` Proje dosyasındaki öğe için, veya olarak ayarlanırsa,, `DependentUpon` `EmbeddedResource` kaynak bildirim dosyası adı projenin kök ad alanını ve *. resx* dosyasının göreli dosya yolunu temel alan olur. Daha fazla bilgi için bkz. [kaynak bildirim dosyalarının adlandırılması](../resources/manifest-file-names.md).

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a>LangVersion

`LangVersion`Özelliği, belirli bir programlama dili sürümü belirtmenizi sağlar. Örneğin, C# önizleme özelliklerine erişmek istiyorsanız, `LangVersion` olarak ayarlayın `preview` .

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Daha fazla bilgi için bkz. [C# dil sürümü oluşturma](../../csharp/language-reference/configure-language-version.md#override-a-default).

## <a name="default-item-inclusion-properties"></a>Varsayılan öğe içerme özellikleri

- [DefaultExcludesInProjectFolder](#defaultexcludesinprojectfolder)
- [DefaultItemExcludes](#defaultitemexcludes)
- [Enabledefaultcompileıtems](#enabledefaultcompileitems)
- [Enabledefaultembeddedresourceıtems](#enabledefaultembeddedresourceitems)
- [Enabledefaultıtems](#enabledefaultitems)
- [Enabledefaultnoneıtems](#enabledefaultnoneitems)

Daha fazla bilgi için bkz. [varsayılan içerme ve dışladığı](overview.md#default-includes-and-excludes).

### <a name="defaultitemexcludes"></a>DefaultItemExcludes

`DefaultItemExcludes`Include, exclude ve Remove genelleştirmeler dışında tutulması gereken dosya ve klasörler için glob desenleri tanımlamak üzere özelliğini kullanın. Varsayılan olarak, *./bin* ve *./obj* klasörleri, glob desenlerinden çıkarılır.

```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);**/*.myextension</DefaultItemExcludes>
</PropertyGroup>
```

### <a name="defaultexcludesinprojectfolder"></a>DefaultExcludesInProjectFolder

`DefaultExcludesInProjectFolder`Dahil etme, hariç tutma ve kaldırma genelleştirmeler dışında tutulacak proje klasöründeki dosya ve klasörler için glob desenlerini tanımlamak üzere özelliğini kullanın. Varsayılan olarak, `.` *. git* ve *. vs* gibi bir noktayla başlayan klasörler, glob desenlerinden çıkarılır.

Bu özellik, `DefaultItemExcludes` yalnızca proje klasöründeki dosya ve klasörleri dikkate almak dışında özelliğine çok benzer. Bir glob deseninin proje klasörü dışındaki öğeleri bir göreli yol ile istenmeden eşleşmesi durumunda, özelliği `DefaultExcludesInProjectFolder` yerine özelliğini kullanın `DefaultItemExcludes` .

```xml
<PropertyGroup>
  <DefaultExcludesInProjectFolder>$(DefaultExcludesInProjectFolder);**/myprefix*/**</DefaultExcludesInProjectFolder>
</PropertyGroup>
```

### <a name="enabledefaultitems"></a>Enabledefaultıtems

`EnableDefaultItems`Özelliği derleme öğelerinin, katıştırılmış kaynak öğelerinin ve `None` öğelerin projeye örtük olarak dahil edilip edilmeyeceğini denetler. `true` varsayılan değerdir. `EnableDefaultItems` `false` Tüm örtük dosya dahil edilmesini devre dışı bırakmak için özelliğini olarak ayarlayın.

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="enabledefaultcompileitems"></a>Enabledefaultcompileıtems

`EnableDefaultCompileItems`Özelliği, derleme öğelerinin projeye örtük olarak dahil edilip edilmeyeceğini denetler. `true` varsayılan değerdir. `EnableDefaultCompileItems` `false` *. Cs ve diğer dil uzantısı dosyalarının örtük olarak eklenmesini devre dışı bırakmak için özelliğini olarak ayarlayın.

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

### <a name="enabledefaultembeddedresourceitems"></a>Enabledefaultembeddedresourceıtems

`EnableDefaultEmbeddedResourceItems`Özelliği, katıştırılmış kaynak öğelerinin projeye örtük olarak dahil edilip edilmeyeceğini denetler. `true` varsayılan değerdir. `EnableDefaultEmbeddedResourceItems` `false` Gömülü kaynak dosyalarının örtük olarak eklenmesini devre dışı bırakmak için özelliğini olarak ayarlayın.

```xml
<PropertyGroup>
  <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
</PropertyGroup>
```

### <a name="enabledefaultnoneitems"></a>Enabledefaultnoneıtems

`EnableDefaultNoneItems`Özelliği, `None` öğelerin (yapı işleminde rolü olmayan dosyalar) örtük olarak projeye dahil edilip edilmeyeceğini denetler. `true` varsayılan değerdir. `EnableDefaultNoneItems`Özelliği `false` örtük olarak öğelerin dahil edilmesini devre dışı bırakmak için olarak ayarlayın `None` .

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

## <a name="code-analysis-properties"></a>Kod Analizi özellikleri

- [AnalysisLevel](#analysislevel)
- [AnalysisMode](#analysismode)
- [CodeAnalysisTreatWarningsAsErrors](#codeanalysistreatwarningsaserrors)
- [Enablenetçözümleyiciler](#enablenetanalyzers)
- [Enforcecodestyleınbuild](#enforcecodestyleinbuild)

### <a name="analysislevel"></a>AnalysisLevel

`AnalysisLevel`Özelliği, bir kod analizi düzeyi belirtmenize olanak tanır. Örneğin, önizleme kodu Çözümleyicileri için erişim istiyorsanız, `AnalysisLevel` olarak ayarlayın `preview` . `latest` varsayılan değerdir.

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

Aşağıdaki tabloda kullanılabilir seçenekler gösterilmektedir.

| Değer | Anlamı |
|-|-|
| `latest` | Yayınlanan en son kod Çözümleyicileri kullanılır. Bu varsayılan seçenektir. |
| `preview` | Önizleme aşamasında olsalar dahi, en son kod Çözümleyicileri kullanılır. |
| `5.0` | .NET 5,0 sürümü için etkinleştirilen kurallar kümesi, daha yeni kurallar kullanılabilir olsa bile kullanılır. |
| `5` | .NET 5,0 sürümü için etkinleştirilen kurallar kümesi, daha yeni kurallar kullanılabilir olsa bile kullanılır. |

### <a name="analysismode"></a>AnalysisMode

.NET SDK, .NET 5,0 ile başlayarak ["CA" kod kalitesi kurallarıyla](../../fundamentals/code-analysis/quality-rules/index.md)birlikte gönderilir. Varsayılan olarak, yalnızca [bazı kurallar](../../fundamentals/code-analysis/overview.md#enabled-rules) derleme uyarıları olarak etkinleştirilir. `AnalysisMode`Özelliği, varsayılan olarak etkinleştirilen kuralların kümesini özelleştirmenizi sağlar. Daha Agresif (geri çevirme) çözümleme moduna veya daha koruyucu (katılım) analiz moduna geçebilirsiniz. Örneğin, varsayılan olarak tüm kuralları derleme uyarıları olarak etkinleştirmek istiyorsanız, değerini olarak ayarlayın `AllEnabledByDefault` .

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

Aşağıdaki tabloda kullanılabilir seçenekler gösterilmektedir.

| Değer | Anlamı |
|-|-|
| `Default` | Belirli kuralların derleme uyarıları olarak etkinleştirildiği varsayılan mod, Visual Studio IDE önerisi olarak bazı kurallar etkinleştirilir ve geri kalanı devre dışı bırakılır. |
| `AllEnabledByDefault` | Tüm kuralların, derleme uyarıları olarak varsayılan olarak etkinleştirildiği agresif veya kabul etme modu. Bağımsız kuralların devre dışı [bırakılacağını seçerek devre dışı bırakabilirsiniz](../../fundamentals/code-analysis/configuration-options.md) . |
| `AllDisabledByDefault` | Klasik veya kabul etme modu, tüm kurallar varsayılan olarak devre dışıdır. Bunları etkinleştirmek için tek tek kuralların seçmeli olarak [tercih](../../fundamentals/code-analysis/configuration-options.md) edebilirsiniz. |

### <a name="codeanalysistreatwarningsaserrors"></a>CodeAnalysisTreatWarningsAsErrors

`CodeAnalysisTreatWarningsAsErrors`Özelliği, kod kalitesi analizi uyarılarının (CAxxxx) uyarı olarak değerlendirilip derlenmeyeceğini yapılandırmanıza olanak tanır. Projelerinizi oluştururken bayrağını kullanırsanız `-warnaserror` , [.net Code Quality Analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) uyarıları da hata olarak kabul edilir. Kod kalitesi analiz uyarılarını hata olarak kabul etmek istemiyorsanız, `CodeAnalysisTreatWarningsAsErrors` MSBuild özelliğini `false` proje dosyanızda olarak ayarlayabilirsiniz.

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a>Enablenetçözümleyiciler

.Net [Code Quality Analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) , .NET 5,0 veya üstünü hedefleyen projeler için varsayılan olarak etkinleştirilmiştir. Özelliğini olarak ayarlayarak .NET 'in önceki sürümlerini hedefleyen projeler için .NET kod analizini etkinleştirebilirsiniz `EnableNETAnalyzers` `true` . Herhangi bir projede kod analizini devre dışı bırakmak için bu özelliği olarak ayarlayın `false` .

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> .NET 5,0 ' den önceki .NET sürümlerini hedefleyen projelerde .NET kod analizini etkinleştirmenin bir diğer yolu, [Analysislevel](#analysislevel) özelliğini olarak ayarlamadır `latest` .

### <a name="enforcecodestyleinbuild"></a>Enforcecodestyleınbuild

> [!NOTE]
> Bu özellik şu anda deneysel ve .NET 5 ve .NET 6 sürümleri arasında değişebilir.

[.NET kod stili Analizi](../../fundamentals/code-analysis/overview.md#code-style-analysis) , varsayılan olarak tüm .NET projeleri için derleme üzerinde devre dışıdır. Özelliğini olarak ayarlayarak .NET projeleri için kod stili analizini etkinleştirebilirsiniz `EnforceCodeStyleInBuild` `true` .

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

Uyarı veya hata olarak [yapılandırılan](../../fundamentals/code-analysis/overview.md#code-style-analysis) tüm kod stili kuralları, derleme ve rapor ihlalleri üzerinde yürütülür.

## <a name="run-time-configuration-properties"></a>Çalışma zamanı yapılandırma özellikleri

Uygulamanın proje dosyasında MSBuild özelliklerini belirterek bazı çalışma zamanı davranışları yapılandırabilirsiniz. Çalışma zamanı davranışını yapılandırmanın diğer yolları hakkında daha fazla bilgi için bkz. [çalışma zamanı yapılandırma ayarları](../run-time-config/index.md).

- [ConcurrentGarbageCollection](#concurrentgarbagecollection)
- [Invariantgenelleştirme](#invariantglobalization)
- [RetainVMGarbageCollection](#retainvmgarbagecollection)
- [ServerGarbageCollection](#servergarbagecollection)
- [ThreadPoolMaxThreads](#threadpoolmaxthreads)
- [ThreadPoolMinThreads](#threadpoolminthreads)
- [TieredCompilation](#tieredcompilation)
- [Tieredcompilationquickjıt](#tieredcompilationquickjit)
- [Tieredcompilationquickjıtfordöngüleri](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a>ConcurrentGarbageCollection

`ConcurrentGarbageCollection`Özelliği [Background (eşzamanlı) Çöp toplamanın](../../standard/garbage-collection/background-gc.md) etkinleştirilip etkinleştirilmeyeceğini yapılandırır. `false`Arka plan atık toplamayı devre dışı bırakmak için değerini olarak ayarlayın. Daha fazla bilgi için bkz. [arka plan GC](../run-time-config/garbage-collector.md#background-gc).

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a>Invariantgenelleştirme

`InvariantGlobalization`Özelliği, uygulamanın *Genelleştirme sabit* modunda çalışıp çalışmadığını yapılandırır, bu, kültüre özgü verilere erişimi olmayan anlamına gelir. Değeri `true` Genelleştirme sabit modunda çalışacak şekilde ayarlayın. Daha fazla bilgi için bkz. [sabit mod](../run-time-config/globalization.md#invariant-mode).

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a>RetainVMGarbageCollection

`RetainVMGarbageCollection`Özelliği, çöp toplayıcıyı, daha sonra kullanılmak üzere veya serbest bırakmak için silinen bellek segmentlerini bir bekleme listesine koymak üzere yapılandırır. Değeri, `true` çöp toplayıcıya kesimleri bir bekleme listesine koymasını söyler. Daha fazla bilgi için bkz. [VM 'Yi koruma](../run-time-config/garbage-collector.md#retain-vm).

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a>ServerGarbageCollection

`ServerGarbageCollection`Özelliği, uygulamanın [iş istasyonu çöp toplamayı veya sunucu çöp toplamayı](../../standard/garbage-collection/workstation-server-gc.md)kullanıp kullanmadığını yapılandırır. Değerini `true` sunucu çöp toplamayı kullanacak şekilde ayarlayın. Daha fazla bilgi için bkz. [Workstation vs Server](../run-time-config/garbage-collector.md#workstation-vs-server).

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a>ThreadPoolMaxThreads

`ThreadPoolMaxThreads`Özelliği, çalışan iş parçacığı havuzu için en fazla iş parçacığı sayısını yapılandırır. Daha fazla bilgi için bkz. [en fazla iş parçacığı](../run-time-config/threading.md#maximum-threads).

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a>ThreadPoolMinThreads

`ThreadPoolMinThreads`Özelliği, çalışan iş parçacığı havuzu için en az iş parçacığı sayısını yapılandırır. Daha fazla bilgi için bkz. [En düşük iş parçacıkları](../run-time-config/threading.md#minimum-threads).

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a>TieredCompilation

`TieredCompilation`Özelliği, Just-In-Time (JIT) derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır. `false`Katmanlı derlemeyi devre dışı bırakmak için değerini olarak ayarlayın. Daha fazla bilgi için bkz. [katmanlı derleme](../run-time-config/compilation.md#tiered-compilation).

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a>Tieredcompilationquickjıt

`TieredCompilationQuickJit`Özelliği, JIT derleyicisinin hızlı JIT kullanıp kullanmadığını yapılandırır. `false`Hızlı JIT 'i devre dışı bırakmak için değerini olarak ayarlayın. Daha fazla bilgi için bkz. [hızlı JIT](../run-time-config/compilation.md#quick-jit).

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a>Tieredcompilationquickjıtfordöngüleri

`TieredCompilationQuickJitForLoops`Özelliği, JIT derleyicisinin döngüleri içeren yöntemlerde hızlı JIT kullanıp kullanmadığını yapılandırır. `true`Döngüleri içeren yöntemlerde hızlı JIT 'i etkinleştirmek için değerini olarak ayarlayın. Daha fazla bilgi için bkz. [döngüler Için hızlı JIT](../run-time-config/compilation.md#quick-jit-for-loops).

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a>Başvuru özellikleri ve öğeleri

- [AssetTargetFallback](#assettargetfallback)
- [DisableImplicitFrameworkReferences](#disableimplicitframeworkreferences)
- [PackageReference](#packagereference)
- [ProjectReference](#projectreference)
- [Başvuru](#reference)
- [Geri yükleme ile ilgili özellikler](#restore-related-properties)

### <a name="assettargetfallback"></a>AssetTargetFallback

`AssetTargetFallback`Özelliği, proje başvuruları ve NuGet paketleri için ek uyumlu çerçeve sürümlerini belirtmenizi sağlar. Örneğin, kullanarak bir paket bağımlılığı belirtirseniz `PackageReference` ancak bu paket, projelerinizle uyumlu olan varlıkları içermiyorsa `TargetFramework` , `AssetTargetFallback` özelliği yürütmeye gelir. Başvurulan paketin uyumluluğu, içinde belirtilen her bir hedef çerçeve kullanılarak yeniden denetlenir `AssetTargetFallback` . Bu özellik kullanımdan kaldırılan özelliğin yerini alır `PackageTargetFallback` .

`AssetTargetFallback`Özelliğini bir veya daha fazla [hedef çerçeve sürümüne](../../standard/frameworks.md#supported-target-frameworks)ayarlayabilirsiniz.

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="disableimplicitframeworkreferences"></a>DisableImplicitFrameworkReferences

`DisableImplicitFrameworkReferences`Özelliği, `FrameworkReference` .net Core 3,0 ve sonraki sürümlerini hedeflerken örtük öğeleri denetler. .NET Core 2,1 veya .NET Standard 2,0 ve önceki sürümlerini hedeflerken, bir metapackage içindeki paketlere örtük [Packagereference](#packagereference) öğelerini denetler. (Metapackage, yalnızca diğer paketlerdeki bağımlılıklardan oluşan çerçeve tabanlı bir pakettir.) Bu özellik ayrıca `System` , .NET Framework hedefleme gibi örtülü başvuruları da denetler `System.Core` .

`true`Örtük `FrameworkReference` veya [packagereference](#packagereference) öğelerini devre dışı bırakmak için bu özelliği olarak ayarlayın. Bu özelliği olarak ayarlarsanız `true` , yalnızca ihtiyacınız olan çerçevelere veya paketlere açık başvurular ekleyebilirsiniz.

```xml
<PropertyGroup>
  <DisableImplicitFrameworkReferences>true</DisableImplicitFrameworkReferences>
</PropertyGroup>
```

### <a name="packagereference"></a>PackageReference

`PackageReference`Öğe, bir NuGet paketine bir başvuru tanımlar.

`Include`Öznitelik, paket kimliğini belirtir. `Version`Öznitelik, sürümü veya sürüm aralığını belirtir. En düşük sürüm, en yüksek sürüm, Aralık veya tam eşleşme belirtme hakkında bilgi için bkz. [Sürüm aralıkları](/nuget/concepts/package-versioning#version-ranges). Ayrıca, bir paket başvurusuna [varlık öznitelikleri](#asset-attributes) ekleyebilirsiniz.

Aşağıdaki örnekteki proje dosyası kod parçacığı [System. Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvurur.

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

Daha fazla bilgi için bkz. [Proje dosyalarındaki paket başvuruları](/nuget/consume-packages/package-references-in-project-files).

#### <a name="asset-attributes"></a>Varlık öznitelikleri

`IncludeAssets`, `ExcludeAssets` Ve `PrivateAssets` meta veriler bir paket başvurusuna eklenebilir.

| Öznitelik | Açıklama |
| - | - |
| `IncludeAssets` | Tarafından belirtilen pakete ait olan varlıkların `<PackageReference>` tüketilmesi gerektiğini belirtir. Varsayılan olarak, tüm paket varlıkları dahil edilmiştir. |
| `ExcludeAssets`| Tarafından belirtilen pakete ait olan varlıkların `<PackageReference>` tüketilmediğini belirtir. |
| `PrivateAssets` | Tarafından belirtilen pakete ait olan varlıkların `<PackageReference>` tüketilmesi ancak bir sonraki projeye akolmaması gerektiğini belirtir. `Analyzers` `Build` Bu öznitelik mevcut olmadığında,, ve `ContentFiles` varlıkları varsayılan olarak özeldir. |

Bu öznitelikler, birden fazla listeleniyorsa noktalı virgülle ayırarak aşağıdaki öğelerden birini veya daha fazlasını içerebilir `;` :

- `Compile` – *LIB* klasörünün içeriği, derleme için kullanılabilir.
- `Runtime` – *çalışma zamanı* klasörünün içeriği dağıtılır.
- `ContentFiles` – *ContentFiles* klasörünün içeriği kullanılır.
- `Build` – *Build* klasöründeki props/targets kullanılır.
- `Native` – Yerel varlıklardan içerik çalışma zamanı için *Çıkış* klasörüne kopyalanır.
- `Analyzers` – çözümleyiciler kullanılır.

Alternatif olarak, öznitelik şunları içerebilir:

- `None` – varlıkların hiçbiri kullanılmaz.
- `All` – Tüm varlıklar kullanılır.

### <a name="projectreference"></a>ProjectReference

`ProjectReference`Öğe, başka bir projeye yönelik bir başvuru tanımlar. Başvurulan proje bir NuGet paket bağımlılığı olarak eklenir, diğer bir deyişle, ile aynı şekilde işlenir `PackageReference` .

`Include`Öznitelik, projenin yolunu belirtir. Aşağıdaki meta verileri bir proje başvurusuna de ekleyebilirsiniz: `IncludeAssets` , `ExcludeAssets` , ve `PrivateAssets` .

Aşağıdaki örnekteki proje dosyası kod parçacığı adlı bir projeye başvurur `Project2` .

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a>Başvuru

`Reference`Öğe, derleme dosyasına bir başvuru tanımlar.

`Include`Öznitelik, dosyanın adını belirtir ve `HintPath` meta veriler derlemenin yolunu belirtir.

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-related-properties"></a>Geri yükleme ile ilgili özellikler

Başvurulan bir paketin geri yüklenmesi, tüm doğrudan bağımlılıklarını ve bu bağımlılıkların tüm bağımlılıklarını yükler. Ve gibi özellikler belirterek paket geri yüklemesini özelleştirebilirsiniz `RestorePackagesPath` `RestoreIgnoreFailedSources` . Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [hedefi geri yükleme](/nuget/reference/msbuild-targets#restore-target).

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="run-properties"></a>Çalıştırma özellikleri

Aşağıdaki özellikler, komutuyla bir uygulama başlatmak için kullanılır [`dotnet run`](../tools/dotnet-run.md) :

- [RunArguments](#runarguments)
- [RunWorkingDirectory](#runworkingdirectory)

### <a name="runarguments"></a>RunArguments

`RunArguments`Özelliği, çalıştırıldığında uygulamaya geçirilen bağımsız değişkenleri tanımlar.

```xml
<PropertyGroup>
  <RunArguments>-mode dryrun</RunArguments>
</PropertyGroup>
```

> [!TIP]
> [ `--` Seçeneğini `dotnet run` ](../tools/dotnet-run.md#options)kullanarak uygulamaya geçirilecek ek bağımsız değişkenler belirtebilirsiniz.

### <a name="runworkingdirectory"></a>RunWorkingDirectory

`RunWorkingDirectory`Özelliği, uygulamasında başlatılacak uygulama işleminin çalışma dizinini tanımlar. Bu, mutlak bir yol veya proje diziniyle ilişkili bir yol olabilir. Bir dizin belirtmezseniz, `OutDir` çalışma dizini olarak kullanılır.

```xml
<PropertyGroup>
  <RunWorkingDirectory>c:\temp</RunWorkingDirectory>
</PropertyGroup>
```

## <a name="hosting-properties"></a>Barındırma özellikleri

- [EnableComHosting](#enablecomhosting)
- [EnableDynamicLoading](#enabledynamicloading)

### <a name="enablecomhosting"></a>EnableComHosting

Özelliği, bir `EnableComHosting` derlemenin BIR com sunucusu sağladığını gösterir. İçin ayarı `EnableComHosting` , `true` [EnableDynamicLoading](#enabledynamicloading) olduğunu da belirtir `true` .

```xml
<PropertyGroup>
  <EnableComHosting>True</EnableComHosting>
</PropertyGroup>
```

Daha fazla bilgi için bkz. [.net BILEŞENLERINI com 'Da kullanıma](../native-interop/expose-components-to-com.md)sunma.

### <a name="enabledynamicloading"></a>EnableDynamicLoading

`EnableDynamicLoading`Özelliği, bir derlemenin dinamik olarak yüklenen bir bileşen olduğunu gösterir. Bileşen bir [com kitaplığı](/windows/win32/com/the-component-object-model) veya [Yerel BIR konaktan kullanılabilecek](../tutorials/netcore-hosting.md)com olmayan bir kitaplık olabilir. Bu özelliğin olarak ayarlanması `true` aşağıdaki etkilere sahiptir:

- Dosyadaki bir *.runtimeconfig.js* oluşturulur.
- [Ileri alma](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward) , olarak ayarlanır `LatestMinor` .
- NuGet başvuruları yerel olarak kopyalanır.

```xml
<PropertyGroup>
  <EnableDynamicLoading>true</EnableDynamicLoading>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild şema başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties)
- [NuGet paketi için MSBuild özellikleri](/nuget/reference/msbuild-targets#pack-target)
- [NuGet geri yükleme için MSBuild özellikleri](/nuget/reference/msbuild-targets#restore-properties)
- [Bir derlemeyi özelleştirme](/visualstudio/msbuild/customize-your-build)
