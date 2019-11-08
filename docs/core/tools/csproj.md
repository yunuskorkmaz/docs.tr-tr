---
title: .NET Core için csproj biçimine eklemeler
description: Mevcut ve .NET Core csproj dosyaları arasındaki farklılıklar hakkında bilgi edinin
ms.date: 04/08/2019
ms.openlocfilehash: 4ce9227839a610308071c36185b63db8b1ee86ed
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739299"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>.NET Core için csproj biçimine eklemeler

Bu belge, Project *. JSON* 'dan *csproj* ve [MSBuild](https://github.com/Microsoft/MSBuild)'e geçiş kapsamında proje dosyalarına eklenen değişiklikleri özetler. Genel proje dosyası sözdizimi ve başvurusu hakkında daha fazla bilgi için bkz. [MSBuild proje dosyası](/visualstudio/msbuild/msbuild-project-file-schema-reference) belgeleri.

## <a name="implicit-package-references"></a>Örtük paket başvuruları

Meta paketlere, proje dosyanızın `<TargetFramework>` veya `<TargetFrameworks>` özelliğinde belirtilen hedef çatılar temelinde örtülü olarak başvurulur. `<TargetFramework>` belirtilmişse `<TargetFrameworks>` yok sayılır. Daha fazla bilgi için bkz. [paketler, Metapackages ve çerçeveler](../packages.md). 

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp2.1</TargetFramework>
 </PropertyGroup>
 ```

 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a>Öneri

`Microsoft.NETCore.App` veya `NETStandard.Library` metapaketlerine örtük olarak başvurulduğundan, önerilen en iyi yöntemler şunlardır:

- .NET Core veya .NET Standard hedeflenirken, proje dosyanızdaki bir `<PackageReference>` öğe aracılığıyla `Microsoft.NETCore.App` veya `NETStandard.Library` metapaketlerine açık bir başvuruya sahip olmaz.
- .NET Core 'u hedeflerken çalışma zamanının belirli bir sürümüne ihtiyacınız varsa, metapackage 'e başvurmak yerine projenizde `<RuntimeFrameworkVersion>` özelliğini (örneğin, `1.0.4`) kullanmanız gerekir.
  - Bu, [kendi kendine kapsanan dağıtımlar](../deploying/index.md#self-contained-deployments-scd) kullanıyorsanız ve örneğin 1.0.0 LTS çalışma zamanının belirli bir düzeltme eki sürümüne ihtiyaç duyuyorsanız meydana gelebilir.
- .NET Standard hedef alırken `NETStandard.Library` metapackage belirli bir sürümüne ihtiyacınız varsa `<NetStandardImplicitPackageVersion>` özelliğini kullanabilir ve ihtiyacınız olan sürümü ayarlayabilirsiniz.
- .NET Framework projelerindeki `Microsoft.NETCore.App` veya `NETStandard.Library` metapackage 'e yönelik başvuruları açıkça eklemeyin veya güncelleştirin. .NET Standard tabanlı bir NuGet paketi kullanılırken `NETStandard.Library` ' ın herhangi bir sürümü gerekliyse, NuGet bu sürümü otomatik olarak yüklenir.

## <a name="implicit-version-for-some-package-references"></a>Bazı paket başvurularının örtük sürümü

[`<PackageReference>`](#packagereference) çoğu kullanımları, kullanılacak NuGet paketi sürümünü belirtmek için `Version` özniteliğini ayarlamayı gerektirir. .NET Core 2,1 veya 2,2 kullanırken ve [Microsoft. aspnetcore. app](/aspnet/core/fundamentals/metapackage-app) ya da [Microsoft. Aspnetcore. All](/aspnet/core/fundamentals/metapackage)ile başvurulduğunda öznitelik gereksizdir. .NET Core SDK, bu paketlerin kullanılması gereken sürümünü otomatik olarak seçebilir.

### <a name="recommendation"></a>Öneri

`Microsoft.AspNetCore.App` veya `Microsoft.AspNetCore.All` paketlerine başvurulduğunda, sürümünü belirtmeyin. Bir sürüm belirtilmişse, SDK uyarı NETSDK1071 üretebilir. Bu uyarıyı onarmak için aşağıdaki örnekteki gibi paket sürümünü kaldırın:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> Bilinen sorun: .NET Core 2,1 SDK 'Sı yalnızca proje Microsoft. NET. SDK. Web 'i kullandığında bu söz dizimini destekliyordu. Bu, .NET Core 2,2 SDK 'sında çözümlenir.

ASP.NET Core metapaketlerine yapılan bu başvuruların çoğu normal NuGet paketlerinden biraz farklı bir davranışı vardır. Bu metapaketleri kullanan uygulamaların [çerçeveye bağımlı dağıtımları](../deploying/index.md#framework-dependent-deployments-fdd) ASP.NET Core paylaşılan çerçeveden otomatik olarak yararlanır. Meta paketleri kullandığınızda başvurulan ASP.NET Core NuGet paketlerinden **hiçbir** varlık uygulamayla birlikte dağıtılır — ASP.NET Core paylaşılan çerçeve bu varlıkları içerir. Paylaşılan çerçevede bulunan varlıklar, uygulama başlatma süresini artırmak üzere hedef platform için iyileştirilmiştir. Paylaşılan Framework hakkında daha fazla bilgi için bkz. [.NET Core dağıtım paketleme](../build/distribution-packaging.md).

Bir *Sürüm belirtilmişse* , çerçeveye bağımlı dağıtımlar için ASP.NET Core paylaşılan Framework 'ün *En düşük* sürümü ve kendi içinde olan dağıtımlar için *tam* sürüm olarak değerlendirilir. Bu, aşağıdaki sonuçlara sahip olabilir:

- Sunucuda yüklü ASP.NET Core sürümü, PackageReference üzerinde belirtilen sürümden küçükse .NET Core işlemi başlayamaz. Metapackage güncelleştirmeleri, Azure gibi barındırma ortamlarında güncelleştirmeler kullanılabilir hale getirilinceye kadar sıklıkla NuGet.org üzerinde kullanılabilir. PackageReference üzerindeki sürümün ASP.NET Core güncelleştirilmesi, dağıtılan bir uygulamanın başarısız olmasına neden olabilir.
- Uygulama [kendi içindeki bir dağıtım](../deploying/index.md#self-contained-deployments-scd)olarak dağıtılırsa, uygulama .NET Core için en son güvenlik güncelleştirmelerini içermeyebilir. Bir sürüm belirtilmediğinde, SDK otomatik olarak kapsanan dağıtıma en yeni ASP.NET Core sürümünü ekleyebilir.

## <a name="default-compilation-includes-in-net-core-projects"></a>.NET Core projelerinde varsayılan derleme dahildir

En son SDK sürümlerindeki *csproj* biçimine geçiş ile, derleme öğeleri ve katıştırılmış kaynaklar için varsayılan ekleme ve DıŞMALARı SDK Özellikler dosyalarına taşıdık. Bu, artık proje dosyanızda bu öğeleri belirtmeniz gerekmediği anlamına gelir.

Bunu yapmanın asıl nedeni, proje dosyanızdaki dağınıklığı azaltmaktır. SDK 'da bulunan varsayılanlar en yaygın kullanım durumlarını kapsamalıdır, bu nedenle bunları oluşturduğunuz her projede tekrarlamaya gerek yoktur. Bu, anlaşılması çok daha kolay olan daha küçük proje dosyalarına ve gerekirse el ile düzenlemeye yol açar.

Aşağıdaki tabloda, SDK 'nın hangi öğesi ve hangi [genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) dahil olduğu ve hangilerinin hariç olduğu gösterilmektedir:

| Öğe           | Glob 'yi dahil et                              | Glob 'yi hariç tut                                                  | Glob 'yi kaldır              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Se           | \* \* / \*. cs (veya diğer dil uzantıları) | \* \* / \*. Kullanıcı;   \* \* / \*. \*proj;   \* 0 1 2. sln;   3 4 5 6. vssscc  | Yok                      |
| EmbeddedResource  | \* \* / \*. resx                              | \* \* / \*. Kullanıcı;  \* \* / \*. \*proj;  \* 0 1 2. sln;  3 4 5 6. vssscc     | Yok                      |
| Yok.              | \*\*/\*                                   | \* \* / \*. Kullanıcı;  \* \* / \*. \*proj;  \* 0 1 2. sln;  3 4 5 6. vssscc     | \* \* / \*. cs;  \* \* / \*. resx   |

> [!NOTE]
> **Dıdb 'Yi Dışla** , sırasıyla `$(BaseOutputPath)` ve `$(BaseIntermediateOutputPath)` MSBuild özellikleriyle temsil edilen `./bin` ve `./obj` klasörlerini her zaman dışlar. Bütün olarak, tüm dışlar `$(DefaultItemExcludes)` ile temsil edilir.

Projenizde genelleştirmeler varsa ve en yeni SDK kullanarak derlemeyi denerseniz, şu hatayı alırsınız:

> Yinelenen derleme öğeleri eklendi. .NET SDK, varsayılan olarak proje dizininizdeki derleme öğelerini içerir. Bu öğeleri proje dosyanıza kaldırabilir ya da bunları proje dosyanıza açıkça dahil etmek istiyorsanız ' Enabledefaultcompileıtems ' özelliğini ' false ' olarak ayarlayabilirsiniz.

Bu hatayı çözmek için, önceki tabloda listelenenlere uyan açık `Compile` öğelerini kaldırabilir veya `<EnableDefaultCompileItems>` özelliğini aşağıdaki gibi `false` olarak ayarlayabilirsiniz:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Bu özelliğin `false` olarak ayarlanması, örtük dahil edilmesini devre dışı bırakır ve projenizde varsayılan genelleştirmeler belirtmeniz gereken önceki SDK 'ların davranışına geri dönülmesini sağlar.

Bu değişiklik, diğer dahil olmak üzere ana mekana 'yi değiştirmez. Bununla birlikte, örneğin, uygulamanızla yayımlanacak bazı dosyalar belirtmek istiyorsanız, bilinen mekanizmaların *csproj* içinde yine de kullanabilirsiniz (örneğin, `<Content>` öğesi).

`<EnableDefaultCompileItems>` yalnızca `Compile` genelleştirmeler devre dışı bırakır, ancak \*.cs öğeleri için de geçerli olan örtük `None` glob gibi diğer genelleştirmeler 'yi etkilemez. Bu nedenle **Çözüm Gezgini** , `None` öğe olarak dahil olmak üzere projenin bir parçası olarak \*.cs öğelerini göstermeye devam edecektir. Benzer bir şekilde, örtük `None` glob 'yi devre dışı bırakmak için `<EnableDefaultNoneItems>` ' ı false olarak ayarlayabilirsiniz:

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

**Tüm örtük genelleştirmeler**devre dışı bırakmak için `<EnableDefaultItems>` özelliğini aşağıdaki örnekte olduğu gibi `false` olarak ayarlayabilirsiniz:

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>Tüm projeyi MSBuild tarafından görüyor

Bu csproj proje dosyalarını büyük ölçüde basitleştirirken, SDK ve hedefleri dahil edildikten sonra MSBuild tarafından, tam genişletilmiş projeyi görmek isteyebilirsiniz. Projeyi gerçekten oluşturmadan, hangi dosyaların içeri aktarılacağını, kaynaklarını ve yapıya katkılarını gösteren [`dotnet msbuild`](dotnet-msbuild.md) komutunun [`/pp` anahtarıyla](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) projeyi önceden işleyin:

`dotnet msbuild -pp:fullproject.xml`

Projede birden çok hedef çerçeve varsa, komutun sonuçları MSBuild özelliği olarak belirtilerek yalnızca birine odaklanmalıdır:

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a>Üzerine

### <a name="sdk-attribute"></a>SDK özniteliği

*. Csproj* dosyasının kök `<Project>` öğesi, `Sdk` adlı yeni bir özniteliğe sahiptir. `Sdk`, proje tarafından hangi SDK 'nın kullanılacağını belirtir. [Katman, katmanlama belgesinde](cli-msbuild-architecture.md) açıklandığı gibi, .NET Core kodu oluşturabileceğiniz MSBuild [görevleri](/visualstudio/msbuild/msbuild-tasks) ve [hedefleri](/visualstudio/msbuild/msbuild-targets) kümesidir. .NET Core için aşağıdaki SDK 'lar mevcuttur:

1. `Microsoft.NET.Sdk` KIMLIĞINE sahip .NET Core SDK
2. `Microsoft.NET.Sdk.Web` KIMLIKLI .NET Core Web SDK 'Sı
3. `Microsoft.NET.Sdk.Razor` KIMLIKLI .NET Core Razor sınıf kitaplığı SDK 'Sı
4. KIMLIĞI `Microsoft.NET.Sdk.Worker` olan .NET Core Worker hizmeti (.NET Core 3,0 ' den beri)
5. KIMLIĞI `Microsoft.NET.Sdk.WindowsDesktop` olan .NET Core WinForms ve WPF (.NET Core 3,0 ' den beri)

.NET Core araçları 'nı kullanabilmeniz ve kodunuzu derlemek için `<Project>` öğesindeki bu kimliklerden birine ayarlanmış `Sdk` özniteliğine sahip olmanız gerekir.

### <a name="packagereference"></a>PackageReference

`<PackageReference>` item öğesi [, projede bir NuGet bağımlılığı](/nuget/consume-packages/package-references-in-project-files)belirtir. `Include` özniteliği paket KIMLIĞINI belirtir.

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Version

Gerekli `Version` özniteliği geri yüklenecek paketin sürümünü belirtir. Öznitelik, [NuGet sürüm oluşturma](/nuget/reference/package-versioning#version-ranges-and-wildcards) şemasının kurallarına uyar. Varsayılan davranış, tam bir sürüm eşleşmedir. Örneğin, `Version="1.2.3"` belirtilmesi, paketin tam 1.2.3 sürümü için NuGet gösterimi `[1.2.3]` eşdeğerdir.

#### <a name="includeassets-excludeassets-and-privateassets"></a>Includevarlıklarını, Excludevarlıklarını ve Privatevarlıkları

`IncludeAssets` özniteliği, `<PackageReference>` tarafından belirtilen pakete ait olan varlıkların tüketilmesi gerektiğini belirtir. Varsayılan olarak, tüm paket varlıkları dahil edilmiştir.

`ExcludeAssets` özniteliği, `<PackageReference>` tarafından belirtilen pakete ait olan varlıkların tüketilmediğini belirtir.

`PrivateAssets` özniteliği, `<PackageReference>` tarafından belirtilen pakete ait olan varlıkların tüketilmesi ancak bir sonraki projeye akolmaması gerektiğini belirtir. `Analyzers`, `Build` ve `ContentFiles` varlıkları bu öznitelik mevcut olmadığında varsayılan olarak özeldir.

> [!NOTE]
> `PrivateAssets`, *Project. json*/*xproj* `SuppressParent` öğesi ile eşdeğerdir.

Bu öznitelikler, birden fazla listeleniyorsa noktalı virgül `;` karakteriyle ayrılmış aşağıdaki öğelerden bir veya daha fazlasını içerebilir:

- `Compile` – *LIB* klasörünün içeriği, derleme için kullanılabilir.
- `Runtime`: *çalışma zamanı* klasörünün içeriği dağıtılır.
- `ContentFiles` – *ContentFiles* klasörünün içeriği kullanılır.
- `Build` – *Build* klasöründeki props/targets kullanılır.
- `Native`: yerel varlıklardan içerik çalışma zamanı için *Çıkış* klasörüne kopyalanır.
- `Analyzers` – çözümleyiciler kullanılır.

Alternatif olarak, öznitelik şunları içerebilir:

- `None` – varlıkların hiçbiri kullanılmaz.
- `All` – tüm varlıklar kullanılır.

### <a name="dotnetclitoolreference"></a>Dotnetclientoolreference

`<DotNetCliToolReference>` item öğesi, kullanıcının proje bağlamında geri yüklemek istediği CLı aracını belirtir. *Project. JSON*içinde `tools` düğümünün yerini alır.

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a>Version

`Version`, geri yüklenecek paketin sürümünü belirtir. Öznitelik, [NuGet sürüm oluşturma](/nuget/create-packages/dependency-versions#version-ranges) şemasının kurallarına uyar. Varsayılan davranış, tam bir sürüm eşleşmedir. Örneğin, `Version="1.2.3"` belirtilmesi, paketin tam 1.2.3 sürümü için NuGet gösterimi `[1.2.3]` eşdeğerdir.

### <a name="runtimeidentifiers"></a>Runtimetanımlayıcıtanımlayıcıları

`<RuntimeIdentifiers>` Property öğesi, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır.
RID 'Ler, kendi kendine kapsanan dağıtımları yayımlamayı etkinleştirir.

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>Runtimeıdentifier

`<RuntimeIdentifier>` Property öğesi, proje için yalnızca bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır. RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

Birden çok çalışma alanına yayımlamanız gerekiyorsa bunun yerine `<RuntimeIdentifiers>` (plural) kullanın. `<RuntimeIdentifier>`, yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.

### <a name="packagetargetfallback"></a>PackageTargetFallback

`<PackageTargetFallback>` Property öğesi, paketler geri yüklenirken kullanılacak bir dizi uyumlu hedef belirtmenize olanak tanır. DotNet [TXE (hedef x takma adı)](/nuget/schema/target-frameworks) kullanan paketlere bir DotNet TXD bildirmeyin paketlerle çalışmak üzere tasarlanmıştır. Projeniz DotNet TXD 'yi kullanıyorsa, DotNet olmayan platformların DotNet ile uyumlu olmasını sağlamak üzere projenize `<PackageTargetFallback>` ' ı eklemediğiniz sürece, bağımlı olduğu tüm paketlerin DotNet TXD olması gerekir.

Aşağıdaki örnek, projenizdeki tüm hedeflerin geri dönüşlerinizi sağlar:

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

Aşağıdaki örnek yalnızca `netcoreapp2.1` hedefi için fallyedekler belirtir:

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a>Derleme olayları

Derleme öncesi ve derleme sonrası olaylarının proje dosyasında belirtilme biçimi değişmiştir. $ (ProjectDir) gibi makrolar çözümlenmediğinden, PreBuildEvent ve PostBuildEvent özelliklerinin SDK stili proje biçiminde kullanılması önerilmez. Örneğin, aşağıdaki kod artık desteklenmemektedir:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

SDK stili projelerde `PreBuild` veya `PostBuild` adlı bir MSBuild hedefi kullanın ve `PreBuild` veya `AfterTargets` özelliği için `BeforeTargets` özelliğini ayarlayın. Önceki örnek için aşağıdaki kodu kullanın:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
>MSBuild hedefleri için herhangi bir ad kullanabilirsiniz, ancak Visual Studio IDE `PreBuild` ve `PostBuild` hedeflerini tanır. bu nedenle, Visual Studio IDE 'de komutları düzenleyebilmeniz için bu adları kullanmanızı öneririz. 

## <a name="nuget-metadata-properties"></a>NuGet meta veri özellikleri

MSBuild 'e taşıma ile, *Project. JSON* 'dan *. csproj* dosyalarına bir NuGet paketi paketleme sırasında kullanılan giriş meta verilerini taşıdık. Girdiler MSBuild özellikleridir, bu nedenle `<PropertyGroup>` grubu içinde gitmeleri gerekir. Aşağıda, `dotnet pack` komutunu veya SDK 'nın parçası olan `Pack` MSBuild hedefini kullanırken paketleme işlemine giriş olarak kullanılan özelliklerin listesi verilmiştir:

### <a name="ispackable"></a>Ispackable

Projenin paketlenemeyeceğini belirten bir Boole değeri. Varsayılan değer `true` şeklindedir.

### <a name="packageversion"></a>PackageVersion

Elde edilen paketin sahip olacağı sürümü belirtir. Tüm NuGet sürüm dizesi formlarını kabul eder. Varsayılan değer `$(Version)`, diğer bir deyişle, projedeki `Version` ' dir.

### <a name="packageid"></a>PackageID

Sonuç paketinin adını belirtir. Belirtilmezse, `pack` işlemi varsayılan olarak paketin adı olarak `AssemblyName` veya dizin adını kullanmaktır.

### <a name="title"></a>Başlık

Genellikle, Kullanıcı arabiriminde kullanılan ve Visual Studio 'da paket yöneticisi olarak görüntülenen, paketin kolay bir başlığı. Belirtilmemişse, bunun yerine paket KIMLIĞI kullanılır.

### <a name="authors"></a>Yazarlar

Nuget.org üzerindeki profil adlarıyla eşleşen paket yazarları için noktalı virgülle ayrılmış bir liste. Bunlar, nuget.org üzerindeki NuGet galerisinde görüntülenir ve aynı yazarlara göre çapraz başvuru için kullanılır.

### <a name="packagedescription"></a>PackageDescription

UI görüntüleme paketinin uzun açıklaması.

### <a name="description"></a>Açıklama

Derleme için uzun bir açıklama. `PackageDescription` belirtilmezse, bu özellik paketin açıklaması olarak da kullanılır.

### <a name="copyright"></a>Yaptırımlar

Paket için telif hakkı ayrıntıları.

### <a name="packagerequirelicenseacceptance"></a>Packagerequirelicensekabulünü

İstemcinin paketi yüklemeden önce paket lisansını kabul etmesini isteyip istemeyeceğini belirten bir Boole değeri. Varsayılan, `false` değeridir.

### <a name="packagelicenseexpression"></a>PackageLicenseExpression

Bir [Spdx lisans tanımlayıcısı](https://spdx.org/licenses/) veya ifadesi. Örneğin, `Apache-2.0`.

[Spdx lisans tanımlayıcılarının](https://spdx.org/licenses/)listesi aşağıda verilmiştir. NuGet.org, lisans türü ifadesi kullanılırken yalnızca OSı veya FSF onaylı lisansları kabul eder.

Lisans ifadelerinin tam sözdizimi aşağıda, [Abnf](https://tools.ietf.org/html/rfc5234)içinde açıklanmıştır.

```abnf
license-id            = <short form license identifier from https://spdx.org/spdx-specification-21-web-version#h.luq9dgcle9mo>

license-exception-id  = <short form license exception identifier from https://spdx.org/spdx-specification-21-web-version#h.ruv3yl8g6czd>

simple-expression = license-id / license-id”+”

compound-expression =  1*1(simple-expression /
                simple-expression "WITH" license-exception-id /
                compound-expression "AND" compound-expression /
                compound-expression "OR" compound-expression ) /
                "(" compound-expression ")" )

license-expression =  1*1(simple-expression / compound-expression / UNLICENSED)
```

> [!NOTE]
> Tek seferde yalnızca bir `PackageLicenseExpression`, `PackageLicenseFile` ve `PackageLicenseUrl` belirtilebilir.

### <a name="packagelicensefile"></a>PackageLicenseFile

Bir SPDX tanımlayıcısı atanmamış bir lisans kullanıyorsanız paket içindeki bir lisans dosyasının yolu veya özel bir lisans (Aksi takdirde `PackageLicenseExpression` tercih edilir)

`PackageLicenseUrl`, `PackageLicenseExpression` ile birleştirilemez ve Visual Studio 15.9.4, .NET SDK 2.1.502 veya 2.2.101 ya da daha yeni bir sürümü gerektirir.

Lisans dosyasının paketlenmiş olduğundan emin olmanız gerekir, bu işlem, örnek kullanım:

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a>PackageLicenseUrl 'Si

Pakete uygulanabilen lisansın URL 'SI. (_Visual Studio 15.9.4, .NET SDK 2.1.502 ve 2.2.101 'den beri kullanım dışı_)

### <a name="packageiconurl"></a>PackageIconUrl 'Si

Kullanıcı arabirimi görüntüsündeki paketin simgesi olarak kullanılacak, saydam arka planlı bir 64x64 görüntüsünün URL 'SI.

### <a name="packagereleasenotes"></a>PackageReleaseNotes

Paket için sürüm notları.

### <a name="packagetags"></a>PackageTags

Paketi atayan etiketlerin noktalı virgülle ayrılmış listesi.

### <a name="packageoutputpath"></a>PackageOutputPath

Paketlenmiş paketin bırakılacak çıkış yolunu belirler. Varsayılan değer `$(OutputPath)`.

### <a name="includesymbols"></a>Includesymbols
Bu Boole değeri, paketin proje paketedildiğinde ek bir sembol paketi oluşturup oluşturmayacağını gösterir. Semboller paketinin biçimi `SymbolPackageFormat` özelliği tarafından denetlenir.

### <a name="symbolpackageformat"></a>SymbolPackageFormat
Semboller paketinin biçimini belirtir. "Symbols. nupkg" ise, pdb 'leri, dll 'Ler ve diğer çıktı dosyalarını içeren *. Symbols. nupkg* Uzantısı ile eski bir sembol paketi oluşturulur. "Snupkg" ise, taşınabilir pdb 'leri içeren bir snupkg sembol paketi oluşturulur. Varsayılan değer "symbols. nupkg" dır.

### <a name="includesource"></a>Includesource

Bu Boole değeri, paket işleminin bir kaynak paketi oluşturup oluşturmayacağını gösterir. Kaynak paket, kitaplığın kaynak kodunu ve PDB dosyalarını içerir. Kaynak dosyalar, elde edilen paket dosyasında `src/ProjectName` dizini altına konur.

### <a name="istool"></a>IsTool

Tüm çıkış dosyalarının *lib* klasörü yerine *Araçlar* klasörüne kopyalanıp kopyalanmayacağını belirtir. Bu, *. csproj* dosyasında `PackageType` ayarlanarak belirtilen `DotNetCliTool` ' dan farklı olduğunu unutmayın.

### <a name="repositoryurl"></a>Depourl 'Si

Paketin kaynak kodunun bulunduğu ve/veya oluşturulduğu deponun URL 'sini belirtir.

### <a name="repositorytype"></a>Repositorytype parametrelerinin sağlanması

Deponun türünü belirtir. Varsayılan değer "git" dir.

### <a name="repositorybranch"></a>Depodalı
Depodaki kaynak dalın adını belirtir. Proje bir NuGet paketinde paketlenmişse, paket meta verilerine eklenir.

### <a name="repositorycommit"></a>Kayıt yapma
Paketin hangi kaynağa göre oluşturulduğunu göstermek için isteğe bağlı depo kaydı veya değişiklik kümesi. Bu özelliğin dahil olması için `RepositoryUrl` de belirtilmelidir. Proje bir NuGet paketinde paketlenmişse, bu tamamlama veya değişiklik kümesi paket meta verilerine eklenir.

### <a name="nopackageanalysis"></a>NoPackageAnalysis

Paketi derlemeden sonra paketin paket analizini çalıştırmamalıdır.

### <a name="minclientversion"></a>MinClientVersion

NuGet. exe ve Visual Studio Paket Yöneticisi tarafından zorlanan, bu paketi yükleyesağlayan NuGet istemcisinin en düşük sürümünü belirtir.

### <a name="includebuildoutput"></a>IncludeBuildOutput

Bu Boole değerleri, derleme çıkış derlemelerinin *. nupkg* dosyasına paketedilip edilmeyeceğini belirtir.

### <a name="includecontentinpack"></a>Includecontentınpack

Bu Boole değeri, `Content` türünde olan öğelerin elde edilen pakete otomatik olarak dahil edilip edilmeyeceğini belirtir. Varsayılan, `true` değeridir.

### <a name="buildoutputtargetfolder"></a>BuildOutputTargetFolder

Çıkış derlemelerinin yerleştirileceği klasörü belirtir. Çıkış derlemeleri (ve diğer çıkış dosyaları) ilgili çerçeve klasörlerine kopyalanır.

### <a name="contenttargetfolders"></a>ContentTargetFolders

Bu özellik, kendileri için `PackagePath` belirtilmemişse, tüm içerik dosyalarının gitmesi gereken varsayılan konumu belirtir. Varsayılan değer "Content; contentFiles" dır.

### <a name="nuspecfile"></a>Nusguus dosyası

Paketleme için kullanılan *. nuspec* dosyasının göreli veya mutlak yolu.

> [!NOTE]
> *. Nuspec* dosyası belirtilmişse, **yalnızca** paketleme bilgileri için kullanılır ve projelerdeki tüm bilgiler kullanılmaz.

### <a name="nuspecbasepath"></a>Nusgubasepath

*. Nuspec* dosyasının temel yolu.

### <a name="nuspecproperties"></a>Nus, Properties

Anahtar = değer çiftlerinin noktalı virgülle ayrılmış listesi.

## <a name="assemblyinfo-properties"></a>AssemblyInfo özellikleri

Genellikle *AssemblyInfo* dosyasında bulunan [derleme öznitelikleri](../../standard/assembly/set-attributes.md) artık özelliklerden otomatik olarak oluşturulur.

### <a name="properties-per-attribute"></a>Öznitelik başına Özellikler

Her öznitelik, aşağıdaki tabloda gösterildiği gibi, içeriğini denetleyen ve diğeri oluşturmayı devre dışı bırakan bir özelliğe sahiptir:

| Öznitelik                                                      | Özellik               | Devre dışı bırakılacak Özellik                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

Notlar:

- `AssemblyVersion` ve `FileVersion` varsayılan değeri, sonek olmadan `$(Version)` değerini alır. Örneğin, `$(Version)` `1.2.3-beta.4` ise, değer `1.2.3` olur.
- `InformationalVersion` varsayılan değeri `$(Version)` ' dir.
- `InformationalVersion`, özellik varsa `$(SourceRevisionId)` ' i içerir. `IncludeSourceRevisionInInformationalVersion`kullanılarak devre dışı bırakılabilir.
- `Copyright` ve `Description` özellikleri NuGet meta verileri için de kullanılır.
- `Configuration` tüm derleme işlemiyle paylaşılır ve `dotnet` komutlarının `--configuration` parametresi aracılığıyla ayarlanır.

### <a name="generateassemblyinfo"></a>Generateassemblyınfo

Tüm AssemblyInfo üretimini etkinleştiren veya devre dışı bırakan bir Boole değeri. Varsayılan değer `true` şeklindedir.

### <a name="generatedassemblyinfofile"></a>GeneratedAssemblyInfoFile

Oluşturulan derleme bilgileri dosyasının yolu. `$(IntermediateOutputPath)` (obj) dizinindeki bir dosya için varsayılan değer.
