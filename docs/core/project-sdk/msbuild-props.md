---
title: Microsoft. NET. SDK için MSBuild özellikleri
description: .NET Core SDK anlayan MSBuild özelliklerine yönelik başvuru.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 800ff59310d8437d7f770bf20a5bdf37714f8515
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795579"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>.NET Core SDK projeleri için MSBuild özellikleri

Bu sayfa, .NET Core projelerini yapılandırmaya yönelik MSBuild özelliklerini açıklar. Özelliğin alt öğeleri olarak her bir özellik için *meta verileri* belirtebilirsiniz.

> [!NOTE]
> Bu sayfa devam eden bir çalışmadır ve .NET Core SDK için tüm yararlı MSBuild özelliklerini listelemez. Ortak MSBuild özelliklerinin bir listesi için bkz. [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Çerçeve özellikleri

- [TargetFramework](#targetframework)
- [Targetçerçeveler](#targetframeworks)
- [Netstandardımplicitpackageversion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework

`TargetFramework` Özelliği, bir [metapackage](../packages.md#metapackages)örtük olarak başvurduğu uygulamanın hedef Framework sürümünü belirtir. Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).

### <a name="targetframeworks"></a>Targetçerçeveler

Uygulamanızın birden `TargetFrameworks` çok platformu hedeflemesini istediğinizde özelliğini kullanın. Geçerli hedef çerçeve takma adların listesi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md#supported-target-framework-versions).

> [!NOTE]
> `TargetFramework` (Tekil) belirtilmişse bu özellik yoksayılır.

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

Daha fazla bilgi için bkz. [SDK stili projelerde hedef çerçeveler](../../standard/frameworks.md).

### <a name="netstandardimplicitpackageversion"></a>Netstandardımplicitpackageversion

> [!NOTE]
> Bu özellik yalnızca kullanan `netstandard1.x`projeler için geçerlidir. Kullanan `netstandard2.x`projeler için uygulanmaz.

`NetStandardImplicitPackageVersion` [Metapackage](../packages.md#metapackages) sürümünden daha düşük bir çerçeve sürümü belirtmek istediğinizde özelliğini kullanın. Aşağıdaki örnekteki proje dosyası hedefler `netstandard1.3` , ancak 1.6.0 sürümünü kullanır. `NETStandard.Library`

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a>Paket özellikleri

Projenizden oluşturulan paketi betimleyen, `PackageId`, `PackageVersion`, `PackageIcon`ve `Title` `Description` gibi özellikleri belirtebilirsiniz. Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [Pack Target](/nuget/reference/msbuild-targets#pack-target).

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties"></a>Özellikleri Yayımla

- [Runtimeıdentifier](#runtimeidentifier)
- [Runtimetanımlayıcıtanımlayıcıları](#runtimeidentifiers)
- [TrimmerRootAssembly](#trimmerrootassembly)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>Runtimeıdentifier

`RuntimeIdentifier` Özelliği, proje için tek bir [çalışma zamanı tanımlayıcısı (RID)](../rid-catalog.md) belirtmenize olanak tanır. RID, kendi kendine içerilen bir dağıtımı yayımlamayı mümkün.

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a>Runtimetanımlayıcıtanımlayıcıları

`RuntimeIdentifiers` Özelliği, proje için bir [çalışma zamanı tanımlayıcıları (RID 'ler)](../rid-catalog.md) için noktalı virgülle ayrılmış bir liste belirtmenize olanak tanır. Birden çok çalışma zamanı için yayımlamanız gerekiyorsa bu özelliği kullanın. `RuntimeIdentifiers`, doğru varlıkların grafikte olduğundan emin olmak için geri yükleme zamanında kullanılır.

> [!TIP]
> `RuntimeIdentifier`(tekil) yalnızca tek bir çalışma zamanı gerektiğinde daha hızlı derlemeler sağlayabilir.

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a>TrimmerRootAssembly

Öğe `TrimmerRootAssembly` , bir derlemeyi [*kırpmanıza*](../deploying/trim-self-contained.md)dışlamanızı sağlar. Kırpma, çalışma zamanının kullanılmayan parçalarını paketlenmiş bir uygulamadan kaldırma işlemidir. Bazı durumlarda, kırpma gerekli başvuruları yanlış kaldırabilir.

Aşağıdaki XML, `System.Security` derlemeyi kırpmaya dışlar.

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a>UseAppHost

`UseAppHost` Özelliği, .NET Core SDK 2.1.400 sürümünde tanıtılmıştı. Dağıtım için yerel bir yürütülebilir dosyanın oluşturulup oluşturulmayacağını denetler. Kendi kendine kapsanan dağıtımlar için yerel bir yürütülebilir dosya gereklidir.

.NET Core 3,0 ve sonraki sürümlerinde, çerçeveye bağlı bir yürütülebilir dosya varsayılan olarak oluşturulur. Yürütülebilir dosyanın `UseAppHost` üretilmesini devre `false` dışı bırakmak için özelliğini olarak ayarlayın.

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

Dağıtım hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md).

## <a name="compile-properties"></a>Derleme özellikleri

- [LangVersion](#langversion)

### <a name="langversion"></a>LangVersion

Özelliği `LangVersion` , belirli bir programlama dili sürümü belirtmenizi sağlar. Örneğin, C# önizleme özelliklerine erişmek istiyorsanız, olarak `LangVersion` `preview`ayarlayın.

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Daha fazla bilgi için bkz. [C# dil sürümü oluşturma](../../csharp/language-reference/configure-language-version.md#override-a-default).

## <a name="run-time-configuration-properties"></a>Çalışma zamanı yapılandırma özellikleri

Uygulamanın proje dosyasında MSBuild özelliklerini belirterek bazı çalışma zamanı davranışları yapılandırabilirsiniz. Çalışma zamanı davranışını yapılandırmanın diğer yolları hakkında daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md).

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

`ConcurrentGarbageCollection` Özelliği [Background (eşzamanlı) Çöp toplamanın](../../standard/garbage-collection/background-gc.md) etkinleştirilip etkinleştirilmeyeceğini yapılandırır. Arka plan atık toplamayı `false` devre dışı bırakmak için değerini olarak ayarlayın. Daha fazla bilgi için bkz. [System. GC. eşzamanlı/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a>Invariantgenelleştirme

`InvariantGlobalization` Özelliği, uygulamanın *Genelleştirme sabit* modunda çalışıp çalışmadığını yapılandırır, bu, kültüre özgü verilere erişimi olmayan anlamına gelir. Değeri `true` Genelleştirme sabit modunda çalışacak şekilde ayarlayın. Daha fazla bilgi için bkz. [sabit mod](../run-time-config/globalization.md#invariant-mode).

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a>RetainVMGarbageCollection

`RetainVMGarbageCollection` Özelliği, çöp toplayıcıyı, daha sonra kullanılmak üzere veya serbest bırakmak için silinen bellek segmentlerini bir bekleme listesine koymak üzere yapılandırır. Değeri, çöp toplayıcıya kesimleri bir bekleme listesine koymasını `true` söyler. Daha fazla bilgi için bkz. [System. GC. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a>ServerGarbageCollection

`ServerGarbageCollection` Özelliği, uygulamanın [iş istasyonu çöp toplamayı veya sunucu çöp toplamayı](../../standard/garbage-collection/workstation-server-gc.md)kullanıp kullanmadığını yapılandırır. Değerini `true` sunucu çöp toplamayı kullanacak şekilde ayarlayın. Daha fazla bilgi için bkz. [System. GC. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a>ThreadPoolMaxThreads

`ThreadPoolMaxThreads` Özelliği, çalışan iş parçacığı havuzu için en fazla iş parçacığı sayısını yapılandırır. Daha fazla bilgi için bkz. [en fazla iş parçacığı](../run-time-config/threading.md#maximum-threads).

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a>ThreadPoolMinThreads

`ThreadPoolMinThreads` Özelliği, çalışan iş parçacığı havuzu için en az iş parçacığı sayısını yapılandırır. Daha fazla bilgi için bkz. [En düşük iş parçacıkları](../run-time-config/threading.md#minimum-threads).

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a>TieredCompilation

Özelliği `TieredCompilation` , Just-ın-TIME (JIT) derleyicisinin [katmanlı derlemeyi](../whats-new/dotnet-core-3-0.md#tiered-compilation)kullanıp kullanmadığını yapılandırır. Katmanlı derlemeyi devre dışı `false` bırakmak için değerini olarak ayarlayın. Daha fazla bilgi için bkz. [katmanlı derleme](../run-time-config/compilation.md#tiered-compilation).

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a>Tieredcompilationquickjıt

`TieredCompilationQuickJit` ÖZELLIĞI, JIT derleyicisinin hızlı JIT kullanıp kullanmadığını yapılandırır. Hızlı JıT 'i devre `false` dışı bırakmak için değerini olarak ayarlayın. Daha fazla bilgi için bkz. [hızlı JIT](../run-time-config/compilation.md#quick-jit).

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a>Tieredcompilationquickjıtfordöngüleri

`TieredCompilationQuickJitForLoops` ÖZELLIĞI, JIT derleyicisinin döngüleri içeren YÖNTEMLERDE hızlı JIT kullanıp kullanmadığını yapılandırır. Döngüleri içeren yöntemlerde hızlı `true` JIT 'i etkinleştirmek için değerini olarak ayarlayın. Daha fazla bilgi için bkz. [döngüler Için hızlı JIT](../run-time-config/compilation.md#quick-jit-for-loops).

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties"></a>Başvuru özellikleri

- [AssetTargetFallback](#assettargetfallback)
- [PackageReference](#packagereference)
- [ProjectReference](#projectreference)
- [Başvuru](#reference)
- [Özellikleri geri yükle](#restore-properties)

### <a name="assettargetfallback"></a>AssetTargetFallback

Özelliği `AssetTargetFallback` , proje başvuruları ve NuGet paketleri için ek uyumlu çerçeve sürümlerini belirtmenizi sağlar. Örneğin, kullanarak `PackageReference` bir paket bağımlılığı belirtirseniz ancak bu paket `TargetFramework`, projelerinizle uyumlu olan varlıkları içermiyorsa, `AssetTargetFallback` özelliği yürütmeye gelir. Başvurulan paketin uyumluluğu, içinde `AssetTargetFallback`belirtilen her bir hedef çerçeve kullanılarak yeniden denetlenir.

`AssetTargetFallback` Özelliğini bir veya daha fazla [hedef çerçeve sürümüne](../../standard/frameworks.md#supported-target-framework-versions)ayarlayabilirsiniz.

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a>PackageReference

, `PackageReference` Bir NuGet paketine bir başvuruyu tanımlar. Örneğin, [metapackage](../packages.md#metapackages)yerine tek bir pakete başvurmak isteyebilirsiniz.

`Include` Öznitelik, paket kimliğini belirtir. `Version` Öznitelik, sürümü veya sürüm aralığını belirtir. En düşük sürüm, en yüksek sürüm, Aralık veya tam eşleşme belirtme hakkında bilgi için bkz. [Sürüm aralıkları](/nuget/concepts/package-versioning#version-ranges). Aşağıdaki meta verileri bir proje başvurusuna de ekleyebilirsiniz: `IncludeAssets`, `ExcludeAssets`, ve. `PrivateAssets`

Aşağıdaki örnekteki proje dosyası kod parçacığı [System. Runtime](https://www.nuget.org/packages/System.Runtime/) paketine başvurur.

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

Daha fazla bilgi için bkz. [Proje dosyalarındaki paket başvuruları](/nuget/consume-packages/package-references-in-project-files).

### <a name="projectreference"></a>ProjectReference

Öğe `ProjectReference` , başka bir projeye yönelik bir başvuru tanımlar. Başvurulan proje bir NuGet paket bağımlılığı olarak eklenir, diğer bir `PackageReference`deyişle, ile aynı şekilde işlenir.

`Include` Öznitelik, projenin yolunu belirtir. Aşağıdaki meta verileri bir proje başvurusuna de ekleyebilirsiniz: `IncludeAssets`, `ExcludeAssets`, ve. `PrivateAssets`

Aşağıdaki örnekteki proje dosyası kod parçacığı adlı `Project2`bir projeye başvurur.

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a>Başvuru

Öğe `Reference` , derleme dosyasına bir başvuru tanımlar.

`Include` Öznitelik, dosyanın adını belirtir ve `HintPath` alt öğe derleme yolunu belirtir.

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a>Özellikleri geri yükle

Başvurulan bir paketin geri yüklenmesi, tüm doğrudan bağımlılıklarını ve bu bağımlılıkların tüm bağımlılıklarını yükler. `RestorePackagesPath` Ve `RestoreIgnoreFailedSources`gibi özellikler belirterek paket geri yüklemesini özelleştirebilirsiniz. Bu ve diğer özellikler hakkında daha fazla bilgi için bkz. [hedefi geri yükleme](/nuget/reference/msbuild-targets#restore-target).

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild şema başvurusu](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Ortak MSBuild özellikleri](/visualstudio/msbuild/common-msbuild-project-properties)
- [NuGet paketi için MSBuild özellikleri](/nuget/reference/msbuild-targets#pack-target)
- [NuGet geri yükleme için MSBuild özellikleri](/nuget/reference/msbuild-targets#restore-properties)
- [Bir derlemeyi özelleştirme](/visualstudio/msbuild/customize-your-build)
