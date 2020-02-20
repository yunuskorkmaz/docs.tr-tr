---
title: Microsoft. NET. SDK için MSBuild özellikleri
description: .NET Core SDK anlayan MSBuild özelliklerine yönelik başvuru.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 00d9152d864ac0727a511f4c3c15abba82aab904
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503815"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>.NET Core SDK projeleri için MSBuild özellikleri

Bu sayfa, .NET Core projelerini yapılandırmaya yönelik MSBuild özelliklerini açıklar.

> [!NOTE]
> Bu sayfa devam eden bir çalışmadır ve .NET Core SDK için tüm yararlı MSBuild özelliklerini listelemez. Ortak MSBuild özelliklerinin bir listesi için bkz. [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Çerçeve özellikleri

- [TargetFramework](#targetframework)
- [Targetçerçeveler](#targetframeworks)
- [Netstandardımplicitpackageversion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>targetFramework

`TargetFramework` özelliği, uygulamanın hedef Framework sürümünü belirtir ve bu, dolaylı olarak bir [metapackage](../packages.md#metapackages)'e başvurur. Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).

### <a name="targetframeworks"></a>Targetçerçeveler

Uygulamanızın birden çok platformu hedeflemesini istediğinizde `TargetFrameworks` özelliğini kullanın. Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-framework-versions).

> [!NOTE]
> `TargetFramework` (tekil) belirtilmişse bu özellik yoksayılır.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).

### <a name="netstandardimplicitpackageversion"></a>Netstandardımplicitpackageversion

> [!NOTE]
> Bu özellik yalnızca `netstandard1.x`kullanan projeler için geçerlidir. `netstandard2.x`kullanan projeler için uygulanmaz.

[Metapackage](../packages.md#metapackages) sürümünden daha düşük bir çerçeve sürümü belirtmek istediğinizde `NetStandardImplicitPackageVersion` özelliğini kullanın. Aşağıdaki örnekteki proje dosyası `netstandard1.3` hedefler, ancak `NETStandard.Library`1.6.0 sürümünü kullanır.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a>Özellikleri Yayımla

- [Runtimeıdentifier](#runtimeidentifier)
- [Runtimetanımlayıcıtanımlayıcıları](#runtimeidentifiers)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>Runtimeıdentifier

`RuntimeIdentifier` özelliği, proje için tek bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır. RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>Runtimetanımlayıcıtanımlayıcıları

`RuntimeIdentifiers` özelliği, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır. Birden çok çalışma zamanı için yayımlamanız gerekiyorsa bu özelliği kullanın. `RuntimeIdentifiers`, doğru varlıkların grafikte olduğundan emin olmak için geri yükleme sırasında kullanılır.

> [!TIP]
> `RuntimeIdentifier` (tekil), yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a>UseAppHost

`UseAppHost` özelliği .NET Core SDK 2.1.400 sürümünde tanıtılmıştı. Dağıtım için yerel bir yürütülebilir dosyanın oluşturulup oluşturulmayacağını denetler. Kendi kendine kapsanan dağıtımlar için yerel bir yürütülebilir dosya gereklidir.

.NET Core 3,0 ve sonraki sürümlerinde, çerçeveye bağlı bir yürütülebilir dosya varsayılan olarak oluşturulur. Yürütülebilir dosyanın üretilmesini devre dışı bırakmak için `UseAppHost` özelliğini `false` olarak ayarlayın.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

Dağıtım hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).

## <a name="compile-properties"></a>Derleme özellikleri

### <a name="langversion"></a>LangVersion

`LangVersion` özelliği, belirli bir programlama dili sürümü belirtmenizi sağlar. Örneğin, C# önizleme özelliklerine erişmek istiyorsanız `LangVersion` `preview`olarak ayarlayın.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

Daha fazla bilgi için bkz [ C# . dil sürümü oluşturma](../../csharp/language-reference/configure-language-version.md#override-a-default).

## <a name="nuget-packages"></a>NuGet paketleri

- [PackageReference](#packagereference)

### <a name="packagereference"></a>PackageReference

`PackageReference` öğesi bir NuGet bağımlılığı belirtmenizi sağlar. Örneğin, [metapackage](../packages.md#metapackages)yerine tek bir pakete başvurmak isteyebilirsiniz. `Include` özniteliği paket KIMLIĞINI belirtir. Aşağıdaki örnekteki proje dosyası kod parçacığı [System. Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvurur.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

Daha fazla bilgi için bkz. [Proje dosyalarındaki paket başvuruları](/nuget/consume-packages/package-references-in-project-files).

### <a name="pack-and-restore-targets"></a>Paket ve geri yükleme hedefleri

MSBuild 15,1, bir derleme kapsamında NuGet paketleri oluşturmak ve geri yüklemek için `pack` ve `restore` hedeflerinin tanıtılmıştır. `PackageTargetFallback`da dahil olmak üzere bu hedeflerin MSBuild özellikleri hakkında bilgi için bkz. [NuGet Pack ve geri yükleme MSBuild hedefleri olarak](/nuget/reference/msbuild-targets).

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild şema başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties)
- [NuGet paketi için MSBuild özellikleri](/nuget/reference/msbuild-targets#pack-target)
- [NuGet geri yükleme için MSBuild özellikleri](/nuget/reference/msbuild-targets#restore-properties)
- [Bir derlemeyi özelleştirme](/visualstudio/msbuild/customize-your-build)
