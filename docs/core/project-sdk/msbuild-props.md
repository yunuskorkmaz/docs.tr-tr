---
title: Microsoft.NET.Sdk için MSBuild özellikleri
description: .NET Core SDK tarafından anlaşılan MSBuild özellikleri için başvuru.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: d4a204a1e0216313418d278ec3bd333f72db8751
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399184"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>.NET Core SDK projeleri için MSBuild özellikleri

Bu sayfada .NET Core projelerini yapılandırmak için MSBuild özellikleri açıklanmaktadır.

> [!NOTE]
> Bu sayfa devam eden bir çalışmadır ve .NET Core SDK için yararlı MSBuild özelliklerinin tümlerini listelemiyor. Ortak MSBuild özelliklerinin listesi [için](/visualstudio/msbuild/common-msbuild-project-properties)bkz.

## <a name="framework-properties"></a>Çerçeve özellikleri

- [Hedef Çerçeve](#targetframework)
- [Hedef Çerçeveler](#targetframeworks)
- [NetStandardimplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>Hedef Çerçeve

Özellik, `TargetFramework` uygulamanın hedef çerçeve sürümünü belirtir ve bu sürüm de örtülü olarak bir [meta pakete](../packages.md#metapackages)başvurur. Geçerli hedef çerçeve monikers listesi için, [SDK tarzı projelerde Hedef çerçeveleri](../../standard/frameworks.md#supported-target-framework-versions)bakın.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Daha fazla bilgi için, [SDK tarzı projelerde Hedef çerçeveleri'ne](../../standard/frameworks.md)bakın.

### <a name="targetframeworks"></a>Hedef Çerçeveler

Uygulamanızın `TargetFrameworks` birden çok platformu hedeflemesini istediğinizde özelliği kullanın. Geçerli hedef çerçeve monikers listesi için, [SDK tarzı projelerde Hedef çerçeveleri](../../standard/frameworks.md#supported-target-framework-versions)bakın.

> [!NOTE]
> (Tekil) `TargetFramework` belirtilmişse bu özellik yoksayılır.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

Daha fazla bilgi için, [SDK tarzı projelerde Hedef çerçeveleri'ne](../../standard/frameworks.md)bakın.

### <a name="netstandardimplicitpackageversion"></a>NetStandardimplicitPackageVersion

> [!NOTE]
> Bu özellik yalnızca `netstandard1.x`. Bu kullanan `netstandard2.x`projeler için geçerli değildir.

`NetStandardImplicitPackageVersion` [Metapackage](../packages.md#metapackages) sürümünden daha düşük bir çerçeve sürümü belirtmek istediğinizde özelliği kullanın. Aşağıdaki örnekteki proje dosyası `netstandard1.3` hedefleri, ancak 1.6.0 sürümünü `NETStandard.Library`kullanır.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a>Özellikleri yayımlama

- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

Özellik, `RuntimeIdentifier` proje için tek bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır. RID, bağımsız bir dağıtımyayımlanmasını sağlar.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

Özellik, `RuntimeIdentifiers` proje için yarı sütunlu sınırlı bir [çalışma zamanı tanımlayıcıları (RIDs)](../rid-catalog.md) listesini belirtmenize olanak tanır. Birden çok çalışma süreleri için yayımlamanız gerekiyorsa bu özelliği kullanın. `RuntimeIdentifiers`doğru varlıkların grafikte olduğundan emin olmak için geri yükleme zamanında kullanılır.

> [!TIP]
> `RuntimeIdentifier`(tekil) yalnızca tek bir çalışma süresi gerektiğinde daha hızlı yapılar sağlayabilir.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a>UseAppHost

Özellik `UseAppHost` .NET Core SDK'nın 2.1.400 sürümünde tanıtıldı. Bir dağıtım için yerel yürütülebilir oluşturulup oluşturulmadığını denetler. Kendi kendine yeten dağıtımlar için yerel yürütülebilir bir işlem gereklidir.

.NET Core 3.0 ve sonraki sürümlerinde, varsayılan olarak çerçeveye bağımlı bir yürütülebilir oluşturulur. `UseAppHost` Özelliği, yürütülebilir nesli devre dışı bırakacak şekilde `false` ayarlayın.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

Dağıtım hakkında daha fazla bilgi için [bkz.](../deploying/index.md)

## <a name="compile-properties"></a>Özellikleri derleme

### <a name="langversion"></a>LangVersion

Özellik, `LangVersion` belirli bir programlama dili sürümünü belirtmenize olanak tanır. Örneğin, C# önizleme özelliklerine erişmek istiyorsanız, `LangVersion` `preview`' e ayarlayın.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

Daha fazla bilgi için [C# dil sürümüne](../../csharp/language-reference/configure-language-version.md#override-a-default)bakın.

## <a name="nuget-packages"></a>NuGet paketleri

- [PaketReferans](#packagereference)
- [VarlıkTargetFallback](#assettargetfallback)

### <a name="packagereference"></a>PaketReferans

Öğe, `PackageReference` bir NuGet bağımlılığı belirtmenize olanak tanır. Örneğin, [meta paket](../packages.md#metapackages)yerine tek bir pakete başvurmak isteyebilirsiniz. Öznitelik `Include` paket kimliğini belirtir. Aşağıdaki örnekteki proje dosyası snippet [System.Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvurur.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

Daha fazla bilgi için [proje dosyalarındaki Paket başvurularına](/nuget/consume-packages/package-references-in-project-files)bakın.

### <a name="assettargetfallback"></a>VarlıkTargetFallback

Özellik, `AssetTargetFallback` projenizin başvurulup tükettiği projeler ve NuGet paketleri için ek uyumlu çerçeve sürümleri belirtmenize olanak tanır. Örneğin, bir paket bağımlılığı nı `PackageReference` kullanarak belirtirseniz, ancak bu paket projelerinizinkiyle `TargetFramework`uyumlu `AssetTargetFallback` varlıklar içermiyorsa, özellik devreye girer. Başvurulan paketin uyumluluğu, ''' `AssetTargetFallback`'de belirtilen her hedef çerçeve kullanılarak yeniden denetlenir.

Özelliği bir veya daha fazla [hedef çerçeve sürümüne](../../standard/frameworks.md#supported-target-framework-versions)ayarlayabilirsiniz. `AssetTargetFallback`

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a>Hedefleri paketleme ve geri yükleme

MSBuild 15.1 `pack` tanıtıldı `restore` ve nuget paketleri oluşturmak ve bir yapının parçası olarak geri için hedefler. Bu hedefler için MSBuild özellikleri hakkında `PackageTargetFallback`bilgi için, [bkz.](/nuget/reference/msbuild-targets)

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild şema başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties)
- [NuGet paketi için MSBuild özellikleri](/nuget/reference/msbuild-targets#pack-target)
- [NuGet geri yüklemesi için MSBuild özellikleri](/nuget/reference/msbuild-targets#restore-properties)
- [Yapıyı özelleştirme](/visualstudio/msbuild/customize-your-build)
