---
title: .NET Core csproj biçimine eklemeler
description: Varolan ve .NET Core csproj dosyaları arasındaki farklar hakkında bilgi edinin
author: blackdwarf
ms.author: mairaw
ms.date: 09/22/2017
ms.openlocfilehash: 1e356d0123328fe703f672c38cb5ee7799cb574c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>.NET Core csproj biçimine eklemeler

Bu belge için proje dosyalarını taşımak bir parçası olarak eklenen değişiklikleri özetlenmektedir *project.json* için *csproj* ve [MSBuild](https://github.com/Microsoft/MSBuild). Genel proje dosyasının söz dizimi ve başvuru hakkında daha fazla bilgi için bkz: [MSBuild proje dosyası](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgeleri.  

## <a name="implicit-package-references"></a>Örtük paket başvuruları
Metapackages örtük olarak başvuru belirtilen hedef framework(s) göre `<TargetFramework>` veya `<TargetFrameworks>` proje dosyanızın özelliği. `<TargetFrameworks>` yoksayılır `<TargetFramework>` olduğu belirtildiğinde, sipariş bağımsızdır.

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp1.1</TargetFramework>
 </PropertyGroup>
 ```
 
 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp1.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a>Önerileri
Bu yana `Microsoft.NETCore.App` veya `NetStandard.Library` metapackages dolaylı olarak başvurulan, bizim önerilen en iyi uygulamalar şunlardır:

* .NET Core veya .NET standart hedeflerken açık bir başvuru hiçbir zaman sahip `Microsoft.NETCore.App` veya `NetStandard.Library` metapackages aracılığıyla bir `<PackageReference>` , proje dosyasında öğesi.
* Belirli bir çalışma zamanı sürümü .NET Core hedeflerken gerekiyorsa, kullanması gereken `<RuntimeFrameworkVersion>` projenizdeki özelliği (örneğin, `1.0.4`) metapackage başvuran yerine.
    * Kullanıyorsanız bu durum oluşabilir [müstakil dağıtımları](../deploying/index.md#self-contained-deployments-scd) ve 1.0.0 belirli düzeltme eki sürümü gerekir, örneğin LTS çalışma zamanı.
* Belirli bir sürümünü gerekiyorsa `NetStandard.Library` .NET standart hedeflerken metapackage kullanabilir `<NetStandardImplicitPackageVersion>` özelliği ve kümesi sürümü, gerekir.
* Açıkça ekleme yok veya güncelleştirme ya da başvurular `Microsoft.NETCore.App` veya `NetStandard.Library` .NET Framework projelerinde metapackage. Herhangi bir sürümünü `NetStandard.Library` NuGet bir .NET standart tabanlı NuGet paketini otomatik olarak kullanarak bu sürümü yüklendiğinde gereklidir.

## <a name="default-compilation-includes-in-net-core-projects"></a>Varsayılan derleme .NET Core projelerinde içerir
Git ile *csproj* biçimi son SDK sürümlerde, yeni varsayılan içerir ve derleme öğeleri ve katıştırılmış kaynaklar SDK özellikler dosyalar için dışlar yerimize. Bu, artık bu öğeler, proje dosyasında belirtmek gerektiği anlamına gelir. 

Bunu yapmak için ana nedeni, proje dosyanızdaki gösterip azaltmaktır. Oluşturduğunuz her projede tekrarlamanız gerekmez; böylece SDK'ın mevcut Varsayılanları en yaygın kullanım örnekleri, kapsamalıdır. Bu, gerektiğinde el ile düzenleme yanı sıra anlamak daha kolay küçük proje dosyalarına yol açar. 

Aşağıdaki tabloda hangi öğesi ve hangi gösterilmektedir [globs](https://en.wikipedia.org/wiki/Glob_(programming)) her ikisi de dahil ve SDK'ın dışlanan: 

| Öğe           | Glob içerir                              | Glob Dışla                                                  | Glob Kaldır                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Derleme           | \*\*/\*.cs (veya diğer dil uzantıları) | \*\*/\*.kullanıcı;  \*\*/\*.\* Proj;  \* \* / \*.sln;  \* \* / \*.vssscc  | Yok                        |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.kullanıcı; \*\*/\*.\* Proj; \* \* / \*.sln; \* \* / \*.vssscc     | Yok                        |
| Yok.              | \*\*/\*                                   | \*\*/\*.kullanıcı; \*\*/\*.\* Proj; \* \* / \*.sln; \* \* / \*.vssscc     | - \*\*/\*.cs; \* \* / \*.resx |

Projenizde globs varsa ve en yeni SDK kullanarak oluşturmak denerseniz, aşağıdaki hata iletisi alırsınız:

> Yinelenen Derleme öğeleri dahil. .NET SDK'sı, varsayılan olarak proje dizininizden derleme öğeleri içerir. Proje dosyasından bu öğeleri kaldırmak veya açıkça bunları proje dosyanızda dahil etmek istiyorsanız 'false' 'EnableDefaultCompileItems' özelliğini ayarlayın. 

Bu hataya alabilmek için ya da açık kaldırabilirsiniz `Compile` olanlarla eşleşmesi öğeleri önceki tabloda listelenen veya ayarlayabilirsiniz `<EnableDefaultCompileItems>` özelliğine `false`, şöyle:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
Bu özelliği ayarlamak `false` örtük ekleme geçersiz kılar ve davranışı geri burada b projenizde varsayılan globs belirlemek için önceki SDK döner. 

Bu değişiklik ana değiştirmez, diğer mekanizması içerir. Örneğin, uygulamanız ile yayımlanan için bazı dosyaları belirlemek istiyorsanız, ancak içinde bilinen mekanizmaları kullanmaya devam edebilirsiniz *csproj* söz konusu (örneğin, `<Content>` öğesi).

`<EnableDefaultCompileItems>` yalnızca devre dışı bırakır `Compile` globs örtük gibi diğer globs etkilemez ancak `None` için de geçerlidir glob \*.cs öğeleri. Nedeniyle **Çözüm Gezgini** Göster devam edecek \*.cs öğeleri olarak eklenen projenin bir parçası olarak `None` öğeleri. Benzer şekilde, kullandığınız `<EnableDefaultNoneItems>` örtük devre dışı bırakmak için `None` glob.

Devre dışı bırakmak için **tüm örtük globs**, ayarlayabileceğiniz `<EnableDefaultItems>` özelliğine `false` aşağıdaki örnekteki gibi:
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="recommendation"></a>Öneri
Csproj ile varsayılan globs projenizden kaldırın ve yalnızca uygulama/kitaplığınızın çeşitli senaryolar için (örneğin, çalışma zamanı ve NuGet paketleme) gereken yapıların globs ile dosya yollarını ekleyin öneririz.

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>MSBuild tarafından görülen şekilde tüm proje görme

Bu csproj değişiklikleri proje dosyalarını büyük ölçüde kolaylaştırma olsa da, SDK'sı ve hedeflerine dahil edilen sonra MSBuild tarafından görülen şekilde tam olarak genişletilmiş proje görmek isteyebilirsiniz. Proje ile önişle [ `/pp` geçiş](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) , [ `dotnet msbuild` ](dotnet-msbuild.md) komutu, hangi dosyaların içeri aktarılan hangi gösterir, kaynakları ve Katkıları oluşturulacak gerçekte Proje oluşturma:

`dotnet msbuild /pp:fullproject.xml`

Projenin birden çok hedef çerçeveyi varsa, komutun sonuçlarını yalnızca bunlardan biri üzerinde bir MSBuild özelliği olarak belirterek odaklanmış olur:

`dotnet msbuild /p:TargetFramework=netcoreapp2.0 /pp:fullproject.xml`

## <a name="additions"></a>Eklemeler

### <a name="sdk-attribute"></a>SDK özniteliği 
`<Project>` Öğesinin *.csproj* dosya adlı yeni bir öznitelik sahip `Sdk`. `Sdk` SDK olacağı belirtir projesi tarafından kullanılan. SDK'sı olarak [katmanlama belge](cli-msbuild-architecture.md) açıklar, MSBuild kümesidir [görevleri](/visualstudio/msbuild/msbuild-tasks) ve [hedefleri](/visualstudio/msbuild/msbuild-targets) .NET Core kodu oluşturabilir. İki ana SDK'ları ile .NET Core araçları gönderdiğimiz:

1. .NET Core SDK kimliği `Microsoft.NET.Sdk`
2. .NET Core web SDK kimliği `Microsoft.NET.Sdk.Web`

Olmasına gerek `Sdk` özniteliği bu kimlikleri birine üzerinde `<Project>` .NET Core araçlarını kullanın ve kodunuzu oluşturmak için öğesi. 

### <a name="packagereference"></a>PackageReference
Öğesi, bir NuGet bağımlılığı projede belirtir. `Include` Özniteliği paket kimliğini belirtir. 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Sürüm
`Version` geri yüklemek için paketin sürümünü belirtir. Öznitelik kurallarına uyar [NuGet sürüm](/nuget/create-packages/dependency-versions#version-ranges) düzeni. Bir tam sürüm eşleşiyorsa varsayılan davranıştır. Örneğin, belirten `Version="1.2.3"` NuGet gösterime eşdeğerdir `[1.2.3]` tam 1.2.3 için paketin sürümü.

#### <a name="includeassets-excludeassets-and-privateassets"></a>IncludeAssets, ExcludeAssets ve PrivateAssets
`IncludeAssets` özniteliği belirtir. pakete ait varlıklar tarafından belirtilen `<PackageReference>` kullanılması. 

`ExcludeAssets` özniteliği belirtir. pakete ait varlıklar tarafından belirtilen `<PackageReference>` değil kullanılması.

`PrivateAssets` özniteliği belirtir. pakete ait varlıklar tarafından belirtilen `<PackageReference>` bunlar sonraki projeye akış değil ancak bu kullanılması. 

> [!NOTE]
> `PrivateAssets` eşdeğer olan *project.json*/*xproj* `SuppressParent` öğesi.

Bu öznitelik, bir veya daha fazla aşağıdaki öğeleri içerebilir:

* `Compile` – lib klasörünün içeriğini karşı derlemek kullanılabilir.
* `Runtime` – çalışma zamanı klasörünün içeriğini dağıtılır.
* `ContentFiles` – içeriği *Content dosyaları* klasörü kullanılır.
* `Build` – özellik/hedefleri oluşturma klasöründe kullanılır.
* `Native` – içeriği yerel varlıklar çalışma zamanı için çıkış klasörüne kopyalanır.
* `Analyzers` – Çözümleyiciler kullanılır.

Alternatif olarak, öznitelik içerebilir:

* `None` – varlıklar hiçbiri kullanılır.
* `All` – Tüm varlıklar kullanılır.

### <a name="dotnetclitoolreference"></a>DotNetCliToolReference
`<DotNetCliToolReference>` öğe unsuru, proje bağlamında geri yüklemek için kullanıcının istediği CLI aracı belirtir. Bir yerini alır `tools` düğümünde *project.json*. 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a>Sürüm
`Version` geri yüklemek için paketin sürümünü belirtir. Öznitelik kurallarına uyar [NuGet sürüm](/nuget/create-packages/dependency-versions#version-ranges) düzeni. Bir tam sürüm eşleşiyorsa varsayılan davranıştır. Örneğin, belirten `Version="1.2.3"` NuGet gösterime eşdeğerdir `[1.2.3]` tam 1.2.3 için paketin sürümü.

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers
`<RuntimeIdentifiers>` Öğesi noktalı virgülle ayrılmış bir listesini belirtmenize olanak sağlar [çalışma zamanı tanımlayıcıları (RID)](../rid-catalog.md) projesi için. RID müstakil dağıtımları yayımlamayı etkinleştirin. 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>RuntimeIdentifier
`<RuntimeIdentifier>` Öğesi yalnızca bir belirtmenize olanak verir [çalışma zamanı tanımlayıcı (RID)](../rid-catalog.md) projesi için. RID kendi içinde bulunan bir dağıtım yayımlamayı etkinleştirin. 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a>PackageTargetFallback 
`<PackageTargetFallback>` Öğesi paketleri geri yüklenirken kullanılacak uyumlu hedefleri kümesi belirtmenize olanak sağlar. Dotnet kullanmak paketleri izin vermek için tasarlanmış [TxM (hedef x takma ad)](/nuget/schema/target-frameworks) dotnet TxM bildirmeyin paketlerle çalışılacak. Projenizi TxM dotnet kullanan sonra bağlı olduğu gereken üzerinde de tüm paketler dotnet TxM, sahiptir ve eklediğiniz sürece `<PackageTargetFallback>` dotnet ile uyumlu olacak şekilde dotnet olmayan platformları izin vermek üzere projenize. 

Aşağıdaki örnek, projenizdeki tüm hedefleri için geri dönüşler sağlar: 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

Aşağıdaki örnekte yalnızca geri dönüşler belirtir `netcoreapp1.0` hedef:

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp1.0'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a>NuGet meta veri özellikleri
MSbuild için taşıma ile biz bir NuGet paketi sevk kullanıldığında giriş meta verileri taşınmış *project.json* için *.csproj* dosyaları. İçinde gitmek sahip oldukları için MSBuild özellikleri girdileridir bir `<PropertyGroup>` grubu. Paketleme işleminin girdi olarak kullanılırken kullanılan özelliklerin listesi aşağıda verilmiştir `dotnet pack` komut veya `Pack` MSBuild hedef başka bir deyişle SDK'ın bir parçası. 

### <a name="ispackable"></a>IsPackable
Proje dolu olup olmadığını belirten bir Boole değeri. Varsayılan değer `true` şeklindedir. 

### <a name="packageversion"></a>PackageVersion
Sonuçta elde edilen paket olacaktır sürümünü belirtir. NuGet sürüm dizesi biçimlerinin kabul eder. Varsayılan değer değerini `$(Version)`, diğer bir deyişle, özelliğin `Version` projesinde. 

### <a name="packageid"></a>Paket kimliği
Sonuçta elde edilen paket adını belirtir. Belirtilmezse, `pack` işlemi varsayılan olarak kullanmaya `AssemblyName` veya dizin adıyla paketin adı. 

### <a name="title"></a>Başlık
Nuget.org ve Visual Studio'da Paket Yöneticisi gibi UI görünümlerde genellikle kullanılan paket, bir insan kolay başlığı. Paket kimliği belirtilmezse, bunun yerine kullanılır.

### <a name="authors"></a>Yazarlar
Nuget.org profil adları eşleşen paketleri yazarlar noktalı virgülle ayrılmış listesi. Bunlar nuget.org NuGet galerisinde görüntülenir ve paketleri çapraz başvuru için aynı yazarlar tarafından kullanılır.

### <a name="description"></a>Açıklama
Paket UI görüntü için uzun bir açıklaması.

### <a name="copyright"></a>Telif Hakkı
Telif Hakkı ayrıntıları paketi için.

### <a name="packagerequirelicenseacceptance"></a>PackageRequireLicenseAcceptance
İstemci paketi lisans paketi yüklemeden önce kabul etmek için tüketici sor olup olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir.

### <a name="packagelicenseurl"></a>PackageLicenseUrl
Paketi uygulanabilir lisans bir URL.

### <a name="packageprojecturl"></a>PackageProjectUrl
Paketin giriş sayfası, genellikle kullanıcı Arabiriminde gösterilen URL'sini nuget.org yanı sıra görüntüler.

### <a name="packageiconurl"></a>PackageIconUrl
UI görüntü paketinde simgesi olarak kullanılacak bir URL saydam arka plan 64 x 64 görüntüsüyle.

### <a name="packagereleasenotes"></a>PackageReleaseNotes
Paket için sürüm notları.

### <a name="packagetags"></a>PackageTags
Etiketleri noktalı virgülle ayrılmış bir listesi, paket belirler.

### <a name="packageoutputpath"></a>PackageOutputPath
Paketlenmiş paket bırakılacak çıkış yolu belirler. Varsayılan değer `$(OutputPath)`. 

### <a name="includesymbols"></a>IncludeSymbols
Bu Boole değeri, projenin dolu olduğunda paketi bir ek simge paketi oluşturmak gösterir. Bu paket sahip bir *. symbols.nupkg* uzantısı ve DLL birlikte PDB dosyalarını ve diğer çıktı dosyalarını kopyalayın.

### <a name="includesource"></a>IncludeSource
Bu Boole değeri paketi işlemi bir kaynak paketi oluşturmalısınız olup olmadığını gösterir. Kaynak Paketi kitaplığın kaynak kodu yanı sıra PDB dosyalarını içerir. Kaynak dosyaları altında konur `src/ProjectName` elde edilen paket dosyasındaki dizin. 

### <a name="istool"></a>IsTool
Tüm çıktı dosyaları için kopyalanıp kopyalanmayacağını belirtir *Araçları* klasörü yerine *lib* klasör. Bu farklı olduğuna dikkat edin bir `DotNetCliTool` , belirtilen ayarlayarak `PackageType` içinde *.csproj* dosya.

### <a name="repositoryurl"></a>RepositoryUrl
Depo URL'si paket için kaynak kodunu bulunduğu yerde ve/veya hangi onu oluşturulmakta olan gelen belirtir. 

### <a name="repositorytype"></a>RepositoryType
Depo türünü belirtir. Varsayılan değer "git" dir. 

### <a name="nopackageanalysis"></a>NoPackageAnalysis
Paketi paket analiz paketi oluşturduktan sonra çalışmayacağını belirtir.

### <a name="minclientversion"></a>MinClientVersion
Nuget.exe ve Visual Studio Paket Yöneticisi tarafından zorlanan bu paketi yükleyebilmek için NuGet istemci en düşük sürümünü belirtir.

### <a name="includebuildoutput"></a>IncludeBuildOutput
Bu Boole değerleri belirtir yapı çıktı derlemeler halinde dolu olup olmadığını *.nupkg* dosya ya da değil.

### <a name="includecontentinpack"></a>IncludeContentInPack
Bu Boole değeri tüm öğeler, bir tür sahip olup olmadığını belirtir `Content` elde edilen paketinde otomatik olarak eklenecektir. Varsayılan, `true` değeridir. 

### <a name="buildoutputtargetfolder"></a>BuildOutputTargetFolder
Çıktı derlemelerinin nereye yerleştireceğinizi klasörü belirtir. Çıktı derlemelerinin (ve diğer çıktı dosyaları) ilgili framework klasörlerine kopyalanır.

### <a name="contenttargetfolders"></a>ContentTargetFolders
Bu özellik, tüm içerik dosyalarının nerede tamamlamalıdır, varsayılan konumu belirtir `PackagePath` kendileri için belirtilmemiş. Varsayılan değer "içerik; Content dosyaları".

### <a name="nuspecfile"></a>NuspecFile
Göreli veya mutlak bir yol *.nuspec* paketleme için kullanılan dosya. 

> [!NOTE]
> Varsa *.nuspec* dosyası belirtilmediyse, kullanıldığı **özel olarak** bilgileri ve herhangi bir bilgi projelerinde paketleme kullanılmadığı için. 

### <a name="nuspecbasepath"></a>NuspecBasePath
Temel yolu *.nuspec* dosya.

### <a name="nuspecproperties"></a>NuspecProperties
Noktalı virgülle ayrılmış listesini anahtar = değer çiftleri.
