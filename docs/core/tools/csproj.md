---
title: .NET Core için csproj formatına eklemeler
description: Varolan ve .NET Core csproj dosyaları arasındaki farklar hakkında bilgi edinin
ms.date: 04/08/2019
ms.openlocfilehash: fadc6de43f522129970e48bc72914cf187fe3f82
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607712"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>.NET Core için csproj formatına eklemeler

Bu belge, *project.json'dan* *csproj* ve [MSBuild'e](https://github.com/Microsoft/MSBuild)taşımanın bir parçası olarak proje dosyalarına eklenen değişiklikleri özetleyilmiştir. Genel proje dosyası sözdizimi ve başvurusu hakkında daha fazla bilgi için [MSBuild proje dosya belgelerine](/visualstudio/msbuild/msbuild-project-file-schema-reference) bakın.

## <a name="implicit-package-references"></a>Örtülü paket referansları

Metapaketler, proje dosyanızın `<TargetFramework>` veya `<TargetFrameworks>` özelliğinizde belirtilen hedef çerçevesine(ler) göre dolaylı olarak başvurulur. `<TargetFrameworks>`belirtilirse, `<TargetFramework>` düzenden bağımsız olarak yoksayılır. Daha fazla bilgi için [paketlere, meta paketlere ve çerçevelere](../packages.md)bakın.

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

### <a name="recommendations"></a>Öneriler

`Microsoft.NETCore.App` Veya `NETStandard.Library` metapaketler dolaylı olarak başvuruldığından, önerilen en iyi uygulamalar şunlardır:

- .NET Core veya .NET Standard'ı hedef alırken, `Microsoft.NETCore.App` `NETStandard.Library` proje dosyanızdaki `<PackageReference>` bir öğe aracılığıyla meta paketlere hiçbir zaman açık bir başvurunuz yoktur.
- .NET Core'u hedefalırken çalışma zamanının belirli bir sürümüne `<RuntimeFrameworkVersion>` ihtiyacınız varsa, meta `1.0.4`pakete başvurmak yerine projenizdeki özelliği (örneğin) kullanmanız gerekir.
  - Bu, [bağımsız dağıtımlar](../deploying/index.md#publish-self-contained) kullanıyorsanız ve örneğin 1.0.0 LTS çalışma zamanı belirli bir yama sürümüne ihtiyacınız varsa gerçekleşebilir.
- .NET Standard'ı hedefalırken `NETStandard.Library` metapaketin belirli bir sürümüne ihtiyacınız `<NetStandardImplicitPackageVersion>` varsa, özelliği kullanabilir ve ihtiyacınız olan sürümü ayarlayabilirsiniz.
- .NET Framework projelerindeki `Microsoft.NETCore.App` veya meta paketine açıkça eklemeyin veya `NETStandard.Library` güncellemayın. .NET Standart `NETStandard.Library` tabanlı NuGet paketi kullanırken herhangi bir sürümü gerekiyorsa, NuGet bu sürümü otomatik olarak yükler.

## <a name="implicit-version-for-some-package-references"></a>Bazı paket başvuruları için örtülü sürüm

Çoğu [`<PackageReference>`](#packagereference) kullanım, kullanılacak `Version` NuGet paket sürümünü belirtmek için özniteliğin ayarını gerektirir. .NET Core 2.1 veya 2.2'yi kullanırken ve [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) veya [Microsoft.AspNetCore.All'a](/aspnet/core/fundamentals/metapackage)başvururken, ancak öznitelik gereksizdir. .NET Core SDK, bu paketlerin kullanılması gereken sürümünü otomatik olarak seçebilir.

### <a name="recommendation"></a>Öneri

Paketlere `Microsoft.AspNetCore.App` başvururken, `Microsoft.AspNetCore.All` bunların sürümünü belirtmeyin. Bir sürüm belirtilirse, SDK uyarı NETSDK1071 üretebilir. Bu uyarıyı düzeltmek için aşağıdaki örnekteki gibi paket sürümünü kaldırın:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> Bilinen sorun: .NET Core 2.1 SDK, proje Microsoft.NET.Sdk.Web'i de kullandığında bu sözdizimini yalnızca desteklenebilmiştir. Bu işlem .NET Core 2.2 SDK'da çözülür.

Core meta paketleriASP.NET ne atıfta bulunulan bu göndermeler, çoğu normal NuGet paketinden biraz farklı bir davranışa sahiptir. Bu meta paketleri kullanan uygulamaların [çerçeveye bağımlı dağıtımları,](../deploying/index.md#publish-runtime-dependent) core paylaşılan ASP.NET çerçevesinden otomatik olarak yararlanır. Meta paketleri kullandığınızda, başvurulan ASP.NET Core NuGet paketlerinden **hiçbir** varlık uygulamayla birlikte dağıtılmaz—ASP.NET Core paylaşılan çerçevesi bu varlıkları içerir. Paylaşılan çerçevedeki varlıklar, uygulama başlatma süresini iyileştirmek için hedef platform için optimize edilebiyi leştirir. Paylaşılan çerçeve hakkında daha fazla bilgi için [bkz.](../distribution-packaging.md)

Bir sürüm *belirtilirse,* bu sürüm, ASP.NET Core paylaşılan çerçevesinin çerçeveye bağımlı dağıtımlar için *en az* sürümü ve bağımsız dağıtımlar için *tam* sürüm olarak kabul edilir. Bunun sonuçları aşağıdaki gibi olabilir:

- Sunucuda yüklü ASP.NET Core sürümü PackageReference'da belirtilen sürümden daha azsa, .NET Core işlemi başlatılmaz. Meta paketteki güncelleştirmeler genellikle Azure gibi barındırma ortamlarında güncelleştirmeler kullanıma sunulmadan önce NuGet.org kullanılabilir. ASP.NET Core'a packagereference sürümü güncelleştirilmesi, dağıtılan bir uygulamanın başarısız lığa neden olabilir.
- Uygulama bağımsız bir [dağıtım](../deploying/index.md#publish-self-contained)olarak dağıtılırsa, uygulama .NET Core için en son güvenlik güncelleştirmelerini içermeyebilir. Bir sürüm belirtilmediğinde, SDK ASP.NET Core'un en yeni sürümünü otomatik olarak kendi kendine yeten dağıtıma ekleyebilir.

## <a name="default-compilation-includes-in-net-core-projects"></a>Varsayılan derleme .NET Core projelerinde içerir

En son SDK sürümlerinde *csproj* biçimine taşınması yla, öğeleri ve katıştırılmış kaynakları SDK özellik dosyalarına derlemek için varsayılan içerir ve hariç tutsak ettik. Bu, proje dosyanızda bu öğeleri artık belirtmeniz gerekolmadığı anlamına gelir.

Bunu yapmanın temel nedeni, proje dosyanızdaki dağınıklığı azaltmaktır. SDK'da bulunan varsayılanlar en yaygın kullanım durumlarını kapsamalıdır, bu nedenle oluşturduğunuz her projede bunları yinelemeye gerek yoktur. Bu, anlaşılması çok daha kolay olan ve gerekirse elle düzenleme yapan daha küçük proje dosyalarına yol açar.

Aşağıdaki tabloda, SDK'da hangi elementin ve hangi [globs'lerin](https://en.wikipedia.org/wiki/Glob_(programming)) dahil edildiği ve dışlandığı gösterilmektedir:

| Öğe           | Glob dahil et                              | Glob hariç                                                  | Glob'u çıkarın              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Derlemek           | \*\*/\*.cs (veya diğer dil uzantıları) | \*\*/\*.kullanıcı;  \*\*/\*. \*proj;  \* \* / \*  \* \* / \*  | Yok                      |
| EmbeddedResource  | \*\*/\*Resx                              | \*\*/\*.kullanıcı; \*\*/\*. \*proj; \* \* / \* \* \* / \*     | Yok                      |
| Hiçbiri              | \*\*/\*                                   | \*\*/\*.kullanıcı; \*\*/\*. \*proj; \* \* / \* \* \* / \*     | \*\*/\*.cs; \* \* /.resx \*   |

> [!NOTE]
> **Dışlama glob** her `./bin` zaman `./obj` ve `$(BaseIntermediateOutputPath)` MSBuild özellikleri tarafından `$(BaseOutputPath)` temsil edilen klasörleri hariç tutar. Bir bütün olarak, tüm dışlar `$(DefaultItemExcludes)`tarafından temsil edilir.

Projenizde globs varsa ve en yeni SDK kullanarak inşa etmeye çalışırsanız, aşağıdaki hatayı alırsınız:

> Yinelenen Derleme öğeleri dahil edildi. .NET SDK varsayılan olarak proje dizininizdeki öğeleri derle içerir. Bu öğeleri proje dosyanızdan kaldırabilir veya proje dosyanıza açıkça eklemek istiyorsanız 'Varsayılan Derleme Öğeleri' özelliğini 'false' olarak ayarlayabilirsiniz.

Bu hatayı aşmak için, önceki tabloda `Compile` listelenenöğelerle eşleşen açık öğeleri kaldırabilir veya `<EnableDefaultCompileItems>` özelliği `false`aşağıdaki gibi olarak ayarlayabilirsiniz:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Bu özelliği, `false` projenizdeki varsayılan kümeleri belirtmeniz gereken önceki SDK'ların davranışına geri dönerek, örtülü eklemeyi devre dışı bırakacaktır.

Bu değişiklik diğer içerir ana mekaniği değiştirmez. Ancak, örneğin, uygulamanızla birlikte yayımlanmak üzere bazı dosyaları belirtmek isterseniz, bunun için *csproj'da* bilinen mekanizmaları `<Content>` (örneğin, öğe) kullanabilirsiniz.

`<EnableDefaultCompileItems>`yalnızca `Compile` globs devre dışı kalır, ancak .cs öğeleri `None` için \*de geçerli olan örtük glob gibi diğer globs etkilemez. Bu nedenle, Solution \*Explorer,.cs öğelerini projenin bir parçası `None` olarak, öğeler olarak göstermeye devam eder. **Solution Explorer** Benzer bir şekilde, örtük glob devre `<EnableDefaultNoneItems>` dışı `None` kalmak için yanlış ayarlayabilirsiniz, aşağıdaki gibi:

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

**Tüm örtük globs**devre dışı kalmak `<EnableDefaultItems>` için, aşağıdaki örnekte `false` olduğu gibi özelliği ayarlayabilirsiniz:

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>MSBuild'in gördüğü gibi tüm proje nasıl görebilirsiniz?

Bu csproj değişiklikleri büyük ölçüde proje dosyalarını basitleştirmek iken, MSBuild SDK ve hedefleri dahil edildikten sonra gördüğü gibi tamamen genişletilmiş proje görmek isteyebilirsiniz. Projeyi, hangi dosyaların içe [`dotnet msbuild`](dotnet-msbuild.md) aktarıldığı, kaynaklarını ve projeye gerçekten yapılmadan yapıya katkılarını gösteren komut [ `/pp` un geçişi](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) ile projeyi önceden işleme koymak:

`dotnet msbuild -pp:fullproject.xml`

Projenin birden çok hedef çerçevesi varsa, komutun sonuçları msbuild özelliği olarak belirtilerek bunlardan yalnızca birine odaklanmalıdır:

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a>Ekleme

### <a name="sdk-attribute"></a>Sdk özniteliği

*.csproj* dosyasının kök `Sdk` `<Project>` öğesi, .. `Sdk`proje de hangi SDK'nın kullanılacağını belirtir. SDK, [katmanlama belgesinin](cli-msbuild-architecture.md) açıkladığı gibi, .NET Core kodu oluşturabilen bir MSBuild [görevleri](/visualstudio/msbuild/msbuild-tasks) ve [hedefleri](/visualstudio/msbuild/msbuild-targets) kümesidir. .NET Core için aşağıdaki SDK'lar mevcuttur:

1. .NET Çekirdek SDK kimliği ile`Microsoft.NET.Sdk`
2. .NET Core web SDK kimliği ile`Microsoft.NET.Sdk.Web`
3. .NET Core Razor Class Library SDK kimlikli`Microsoft.NET.Sdk.Razor`
4. .NET Çekirdek İşçi Servisi kimliği `Microsoft.NET.Sdk.Worker` ile (.NET Çekirdek 3.0 beri)
5. .NET Core WinForms ve WPF `Microsoft.NET.Sdk.WindowsDesktop` kimliği ile (beri .NET Core 3.0)

.NET Core `Sdk` araçlarını kullanmak ve kodunuzu oluşturmak için `<Project>` özniteliğin öğedeki kişilerden birine ayarlatması gerekir.

### <a name="packagereference"></a>PaketReferans

Madde `<PackageReference>` öğesi projede bir [NuGet bağımlılığı](/nuget/consume-packages/package-references-in-project-files)belirtir. Öznitelik `Include` paket kimliğini belirtir.

```xml
<PackageReference Include="package-id" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Sürüm

Gerekli `Version` öznitelik geri yüklemek için paketin sürümünü belirtir. [Öznitelik, NuGet sürüm aralığı](/nuget/concepts/package-versioning#version-ranges) düzeninin kurallarına saygı duyar. Varsayılan davranış en az sürüm, kapsayıcı maç. Örneğin, belirtme `Version="1.2.3"` NuGet gösterimine `[1.2.3, )` eşdeğerdir ve çözülen paketin varsa 1.2.3 sürümüne sahip olacağı anlamına gelir.

#### <a name="includeassets-excludeassets-and-privateassets"></a>Varlıkları Dahil Et, Hariç Kıymetler ve Özel Varlıklar

`IncludeAssets`öznitelik, belirtilen pakete ait varlıkların `<PackageReference>` hangilerinin tüketilmesi gerektiğini belirtir. Varsayılan olarak, tüm paket varlıkları dahildir.

`ExcludeAssets`öznitelik, belirtilen pakete ait varlıkların `<PackageReference>` tüketilmemesi gerektiğini belirtir.

`PrivateAssets`öznitelik, belirtilen pakete ait varlıkların `<PackageReference>` tüketilmesi gerektiğini, ancak bir sonraki projeye akmaması gerektiğini belirtir. Bu `Analyzers` `Build` öznitelik olmadığında , ve `ContentFiles` varlıklar varsayılan olarak özeldir.

> [!NOTE]
> `PrivateAssets`*project.json*/*xproj* `SuppressParent` elemanına eşdeğerdir.

Bu öznitelikler, birden fazla listelenmişse, yarı `;` sütunlu karakterle ayrılmış aşağıdaki öğelerden birini veya birkaçını içerebilir:

- `Compile`– *lib* klasörünün içeriğini karşı derlemek için kullanılabilir.
- `Runtime`– *çalışma zamanı* klasörünün içeriği dağıtılır.
- `ContentFiles`– *contentfiles* klasörünün içeriği kullanılır.
- `Build`– *yapı* klasöründeki sahne/hedefler kullanılır.
- `Native`– yerel varlıklardan gelen içerikler çalışma süresi için *çıktı* klasörüne kopyalanır.
- `Analyzers`– analizörler kullanılır.

Alternatif olarak, öznitelik içerebilir:

- `None`– varlıkların hiçbiri kullanılmaz.
- `All`– tüm varlıklar kullanılır.

### <a name="dotnetclitoolreference"></a>DotNetCliToolReference

Bir `<DotNetCliToolReference>` öğe öğesi, kullanıcının proje bağlamında geri yüklemek istediği CLI aracını belirtir. *Project.json'daki* `tools` düğümün yerine geçecek.

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

Artık `DotNetCliToolReference` [.NET Core Yerel Araçlar](https://aka.ms/local-tools)lehine [amortismana uymuyorum.](https://github.com/dotnet/announcements/issues/107)

#### <a name="version"></a>Sürüm

`Version`geri yüklemek için paketin sürümünü belirtir. Öznitelik [NuGet sürüm](/nuget/create-packages/dependency-versions#version-ranges) şemasının kurallarına saygı duyar. Varsayılan davranış en az sürüm, kapsayıcı maç. Örneğin, belirtme `Version="1.2.3"` NuGet gösterimine `[1.2.3, )` eşdeğerdir ve çözülen paketin varsa 1.2.3 sürümüne sahip olacağı anlamına gelir.

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

Özellik `<RuntimeIdentifiers>` öğesi, proje için yarı sütunlu sınırlı bir [Runtime Tanımlayıcıları (RIDs)](../rid-catalog.md) listesini belirtmenize olanak tanır.
RI'ler, bağımsız dağıtımların yayımlanmasını sağlar.

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>RuntimeIdentifier

Özellik `<RuntimeIdentifier>` öğesi, proje için yalnızca bir [Runtime Tanımlayıcı (RID)](../rid-catalog.md) belirtmenize olanak tanır. RID, bağımsız bir dağıtımyayımlanmasını sağlar.

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

Bunun `<RuntimeIdentifiers>` yerine birden çok çalışma süreleri için yayımlamanız gerekiyorsa (çoğul) kullanın. `<RuntimeIdentifier>`yalnızca tek bir çalışma süresi gerektiğinde daha hızlı yapılar sağlayabilir.

### <a name="packagetargetfallback"></a>PaketTargetFallback

Özellik `<PackageTargetFallback>` öğesi, paketleri geri verirken kullanılacak uyumlu hedefler kümesini belirtmenize olanak tanır. Dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) kullanan paketlerin, dotnet TxM beyan etmeyen paketlerle çalışmasına izin vermek üzere tasarlanmıştır. Projeniz dotnet TxM kullanıyorsa, dotnet olmayan platformların dotnet ile uyumlu olması `<PackageTargetFallback>` için projenize eklemediğiniz sürece, bağlı olduğu tüm paketlerin de bir dotnet TxM'si olmalıdır.

Aşağıdaki örnek, projenizdeki tüm hedefler için geri dönüşler sağlar:

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

Aşağıdaki örnekte yalnızca `netcoreapp2.1` hedef için geri dönüşler belirtilir:

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a>Etkinlikler oluşturma

Proje dosyasında ön yapı ve yapı sonrası olayların belirtilme şekli değişti. $(ProjectDir) gibi makrolar çözülmediği için PreBuildEvent ve PostBuildEvent özellikleri SDK stili proje biçiminde önerilmez. Örneğin, aşağıdaki kod artık desteklenmez:

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
</PropertyGroup>
```

SDK tarzı projelerde, `PreBuild` adı verilen bir `PostBuild` MSBuild `BeforeTargets` hedefi `PreBuild` kullanın `AfterTargets` veya `PostBuild`özelliği için veya mülkü . Önceki örnek için aşağıdaki kodu kullanın:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
>MSBuild hedefleri için herhangi bir ad kullanabilirsiniz, ancak `PreBuild` Visual `PostBuild` Studio IDE tanır ve hedefler, bu nedenle Visual Studio IDE komutları edebilirsiniz böylece bu adları kullanmanızı öneririz.

## <a name="nuget-metadata-properties"></a>NuMeta veri özelliklerini alın

MSBuild'e geçildiğinde, bir NuGet paketini *project.json'dan* *.csproj* dosyalarına paketlerken kullanılan giriş meta verilerini taşıdık. Girişler MSBuild özellikleridir, bu nedenle `<PropertyGroup>` bir grup içinde gitmeleri gerekir. SDK'nın bir parçası olan `dotnet pack` komutu veya `Pack` MSBuild hedefini kullanırken paketleme işlemine girdi olarak kullanılan özelliklerin listesi aşağıda verilmiştir:

### <a name="ispackable"></a>IsPackable

Projenin paketlenip paketlenemeyeceğini belirten bir Boolean değeri. Varsayılan değer: `true`.

### <a name="packageversion"></a>PaketSürüm

Ortaya çıkan paketin sahip olacağı sürümü belirtir. NuGet sürüm dizesinin tüm biçimlerini kabul eder. Varsayılan değer, `$(Version)`projedeki özelliğin `Version` değeridir.

### <a name="packageid"></a>Packageıd

Ortaya çıkan paketin adını belirtir. Belirtilmemişse, `pack` işlem varsayılan olarak `AssemblyName` paketin adı olarak dizin adını kullanır.

### <a name="title"></a>Başlık

Paketin insan dostu bir başlık, genellikle nuget.org ve Visual Studio Paket Yöneticisi olarak uI görüntüler kullanılır. Belirtilmemişse, bunun yerine paket kimliği kullanılır.

### <a name="authors"></a>Yazarlar

nuget.org'daki profil adlarıyla eşleşen, yarı sütunlu paket yazarlarılistesi. Bunlar nuget.org'daki NuGet Galerisi'nde görüntülenir ve aynı yazarlar tarafından çapraz başvuru paketleri için kullanılır.

### <a name="packagedescription"></a>Packagedescription

UI ekran için paketin uzun bir açıklaması.

### <a name="description"></a>Açıklama

Montaj için uzun bir açıklama. `PackageDescription` Belirtilmemişse, bu özellik paketin açıklaması olarak da kullanılır.

### <a name="copyright"></a>Telif Hakkı

Paketin telif hakkı ayrıntıları.

### <a name="packagerequirelicenseacceptance"></a>Paket GerektirirLisans Kabul

Müşterinin paketi yüklemeden önce tüketiciden paket lisansını kabul etmesini isteyip istemeyeceğini belirten bir Boolean değeri. Varsayılan değer: `false`.

### <a name="developmentdependency"></a>GeliştirmeBağımlılık

Paketin yalnızca geliştirme bağımlılığı olarak işaretlenip işaretlenmediğini belirten ve paketin diğer paketlere bağımlılık olarak dahil olmasını engelleyen Boolean değeri. PackageReference (NuGet 4.8+) ile bu bayrak, derleme zamanı varlıklarının derlemenin dışında olduğu anlamına da gelir. Daha fazla bilgi [için PackageReference için DevelopmentDependency desteğine](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference)bakın.

### <a name="packagelicenseexpression"></a>PaketLisans İfadesi

[SPDX lisans tanımlayıcısı](https://spdx.org/licenses/) veya ifadesi. Örneğin, `Apache-2.0`.

İşte [SPDX lisans tanımlayıcılarının](https://spdx.org/licenses/)tam listesi. NuGet.org, lisans türü ifadesini kullanırken yalnızca OSI veya FSF onaylı lisansları kabul eder.

Lisans ifadelerinin tam sözdizimi [ABNF'de](https://tools.ietf.org/html/rfc5234)aşağıda açıklanmıştır.

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
> Yalnızca biri `PackageLicenseExpression` `PackageLicenseFile` , `PackageLicenseUrl` ve bir seferde belirtilebilir.

### <a name="packagelicensefile"></a>PaketLisans Dosyası

SPDX tanımlayıcısı atanmamış bir lisans kullanıyorsanız veya özel bir lisanssa (Aksi takdirde `PackageLicenseExpression` tercih edilir)

Yerine `PackageLicenseUrl`, ile `PackageLicenseExpression`kombine edilemez , ve Visual Studio sürümü 15.9.4 ve .NET SDK 2.1.502 veya 2.2.101 veya daha yeni gerektirir.

Lisans dosyasının projeye, örnek kullanıma açıkça ekleyerek paketlendirdiğinden emin olmanız gerekir:

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a>PaketLisansUrl

Paket için geçerli olan lisansın URL'si. (_Visual Studio 15.9.4, .NET SDK 2.1.502 ve 2.2.101' den itibaren amortismana uymuyet_)

### <a name="packageiconurl"></a>PaketIconUrl

Kullanıcı Arabirimi ekranında paket simgesi olarak kullanılacak saydam arka plana sahip 64x64 görüntünün URL'si.

### <a name="packagereleasenotes"></a>PaketYayın Notları

Paket için notları bırakın.

### <a name="packagetags"></a>Paket Etiketler

Paketi belirleyen yarı sütunlu etiket listesi.

### <a name="packageoutputpath"></a>PackageOutputPath

Paketlenmiş paketin bırakılalı çıkış yolunu belirler. `$(OutputPath)` varsayılan değerdir.

### <a name="includesymbols"></a>Sembolleri Dahil Et
Bu Boolean değeri, proje paketlendiğinde paketin ek bir sembol paketi oluşturup oluşturmaması gerektiğini gösterir. Semboller paketinin biçimi `SymbolPackageFormat` özellik tarafından denetlenir.

### <a name="symbolpackageformat"></a>SymbolPackageFormat
Semboller paketinin biçimini belirtir. "symbols.nupkg" ise, PDB'ler, LL'ler ve diğer çıktı dosyalarını içeren bir *.symbols.nupkg* uzantısı içeren eski semboller paketi oluşturulur. "Snupkg" ise, taşınabilir PDB'leri içeren bir snupkg sembol paketi oluşturulur. Varsayılan "symbols.nupkg"dır.

### <a name="includesource"></a>IncludeSource

Bu Boolean değeri, paket işleminin bir kaynak paketi oluşturup oluşturmaması gerektiğini gösterir. Kaynak paketi, kitaplığın kaynak kodunun yanı sıra PDB dosyalarını da içerir. Kaynak dosyalar, ortaya `src/ProjectName` çıkan paket dosyasında dizinin altına konur.

### <a name="istool"></a>ıstool

Tüm çıktı dosyalarının *lib* klasörü yerine *araçlar* klasörüne kopyalanıp kopyalanmayacağını belirtir. Bu, `DotNetCliTool` *.csproj* `PackageType` dosyasında ayarlayarak belirtilen bir ,'dan farklıdır.

### <a name="repositoryurl"></a>DepoUrl

Paketin kaynak kodunun bulunduğu ve/veya oluşturulmakta olduğu deponun URL'sini belirtir.

### <a name="repositorytype"></a>DepoTipi

Deponun türünü belirtir. Varsayılan "git" dir.

### <a name="repositorybranch"></a>DepoŞubesi
Depodaki kaynak dalanın adını belirtir. Proje bir NuGet paketinde paketlendiğinde, paket meta verilerine eklenir.

### <a name="repositorycommit"></a>DepoCommit
İsteğe bağlı depo, paketin hangi kaynağa karşı üretilmediğini belirtmek için işlemeyi veya değiştirin. `RepositoryUrl`ayrıca bu özelliğin dahil edilmesi için belirtilmelidir. Proje bir NuGet paketinde paketlendiğinde, bu commit veya changeset paket meta verilerine eklenir.

### <a name="nopackageanalysis"></a>NoPackageAnalysis

Bu paket, paketi yaptıktan sonra paket çözümlemesi gerektiğini belirtir.

### <a name="minclientversion"></a>MinClientVersion

Nuget istemcisinin nuget.exe ve Visual Studio Package Manager tarafından uygulanan bu paketi yükleyebilecek minimum sürümünü belirtir.

### <a name="includebuildoutput"></a>IncludeBuildOutput

Bu Boolean değeri, yapı çıktı derlemelerinin *.nupkg* dosyasına paketlenip paketlenmemesi gerektiğini belirtir.

### <a name="includecontentinpack"></a>IncludeContentInPack

Bu Boolean değeri, türü olan öğelerin `Content` otomatik olarak ortaya çıkan pakete dahil edilip edilmeyeceğini belirtir. Varsayılan değer: `true`.

### <a name="buildoutputtargetfolder"></a>YapıÇıktıHedef Klasörü

Çıktı derlemelerinin yerleştirilen klasörü belirtir. Çıktı derlemeleri (ve diğer çıktı dosyaları) kendi çerçeve klasörlerine kopyalanır.

### <a name="contenttargetfolders"></a>İçerikHedef Klasörler

Bu özellik, onlar için belirtilmemişse `PackagePath` tüm içerik dosyalarının gitmesi gereken varsayılan konumu belirtir. Varsayılan değer "içerik;contentFiles"dır.

### <a name="nuspecfile"></a>NuspecDosya

Paketleme için kullanılan *.nuspec* dosyasına göreli veya mutlak yol.

> [!NOTE]
> *.nuspec* dosyası belirtilirse, **yalnızca** ambalaj bilgileri için kullanılır ve projelerdeki herhangi bir bilgi kullanılmaz.

### <a name="nuspecbasepath"></a>NuspecBasePath

*.nuspec* dosyası için temel yol.

### <a name="nuspecproperties"></a>NuspecÖzellikleri

Anahtar=değer çiftleri semicolon ayrılmış listesi.

## <a name="assemblyinfo-properties"></a>AssemblyInfo özellikleri

Genellikle bir *AssemblyInfo* dosyasında bulunan [derleme öznitelikleri](../../standard/assembly/set-attributes.md) artık otomatik olarak özelliklerden oluşturulur.

### <a name="properties-per-attribute"></a>Öznitelik başına özellikler

Aşağıdaki tabloda gösterildiği gibi, her öznitelik kendi içeriğini denetleyen bir özelliğe ve kendi kuşağını devre dışı devre dışı bir başkasına sahiptir:

| Öznitelik                                                      | Özellik               | Devre dışı kalım özelliği                             |
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

- `AssemblyVersion`ve `FileVersion` varsayılan sonek `$(Version)` olmadan değerini almaktır. Örneğin, `$(Version)` ise, `1.2.3-beta.4`o zaman değeri `1.2.3`olacaktır.
- `InformationalVersion`değeri `$(Version)`varsayılan.
- `InformationalVersion`özellik `$(SourceRevisionId)` varsa eklenmiştir. Bu kullanarak `IncludeSourceRevisionInInformationalVersion`devre dışı tutulabilir.
- `Copyright`ve `Description` özellikleri nuget meta verileri için de kullanılır.
- `Configuration`tüm yapı işlemi ile paylaşılır `--configuration` ve `dotnet` komutların parametresi üzerinden ayarlanır.

### <a name="generateassemblyinfo"></a>AssemblyInfo oluşturma

Tüm AssemblyInfo neslini etkinleştiren veya devre dışı eden bir Boolean. Varsayılan değer: `true`.

### <a name="generatedassemblyinfofile"></a>OluşturulanAssemblyInfoFile

Oluşturulan derleme bilgi dosyasının yolu. `$(IntermediateOutputPath)` Varsayılan olarak (obj) dizinindeki bir dosya.
