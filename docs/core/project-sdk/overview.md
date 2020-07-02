---
title: .NET Core proje SDK 'sına genel bakış
titleSuffix: ''
description: .NET Core proje SDK 'Ları hakkında bilgi edinin.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 9db62ab7774e3dd71412fa346d78ae0c62a2f81f
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803047"
---
# <a name="net-core-project-sdks"></a>.NET Core proje SDK 'Ları

.NET Core projeleri bir yazılım geliştirme seti (SDK) ile ilişkilendirilir. Her *Proje SDK 'sı* , bir dizi MSBuild [hedefi](/visualstudio/msbuild/msbuild-targets) ve kodu derleme, paketleme ve yayımlama ile ilgili [görevlerden](/visualstudio/msbuild/msbuild-tasks) oluşur. Proje SDK 'Sına başvuran bir proje bazen bir *SDK stili proje*olarak adlandırılır.

## <a name="available-sdks"></a>Kullanılabilir SDK 'lar

.NET Core için aşağıdaki SDK 'lar mevcuttur:

| ID | Açıklama | Depo|
| - | - | - |
| `Microsoft.NET.Sdk` | .NET Core SDK | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | .NET Core [Web SDK 'sı](/aspnet/core/razor-pages/web-sdk) | <https://github.com/aspnet/websdk> |
| `Microsoft.NET.Sdk.Razor` | .NET Core [Razor SDK 'sı](/aspnet/core/razor-pages/sdk) |
| `Microsoft.NET.Sdk.Worker` | .NET Core Worker hizmeti SDK 'Sı |
| `Microsoft.NET.Sdk.WindowsDesktop` | .NET Core WinForms ve WPF SDK |

.NET Core SDK, .NET Core için temel SDK 'dir. Diğer SDK 'lar .NET Core SDK başvuruda bulunur ve diğer SDK 'lar ile ilişkili projeler için kullanılabilen tüm .NET Core SDK özellikleri vardır. Örneğin, Web SDK 'Sı, hem .NET Core SDK hem de Razor SDK 'sına bağlıdır.

Ayrıca kendi SDK 'nizi, NuGet aracılığıyla dağıtılabilecek şekilde yazabilirsiniz.

## <a name="project-files"></a>Proje dosyaları

.NET Core projeleri [MSBuild](/visualstudio/msbuild/msbuild) biçimine dayanır. C# projeleri için *. csproj* ve F # projelerinde *. fsproj* gibi uzantılara sahıp proje dosyaları, XML biçimindedir. MSBuild proje dosyasının kök öğesi [Proje](/visualstudio/msbuild/project-element-msbuild) öğesidir. `Project`Öğesi `Sdk` Hangi SDK (ve sürümü) kullanacağınızı belirten isteğe bağlı bir özniteliğe sahiptir. .NET Core araçlarını kullanmak ve kodunuzu derlemek için, `Sdk` özniteliğini [kullanılabilir SDK](#available-sdks) 'lar tablosundaki kimliklerden birine ayarlayın.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

NuGet 'den gelen bir SDK belirtmek için, adın sonundaki sürümü ekleyin veya *global.js* dosyadaki adı ve sürümü belirtin.

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

SDK 'yı belirtmenin bir başka yolu da en üst düzey [SDK](/visualstudio/msbuild/sdk-element-msbuild) öğesidir:

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

Bu yollarla bir SDK 'ya başvurmak, .NET Core için proje dosyalarını büyük ölçüde basitleştirir. Proje değerlendirilirken MSBuild, `Sdk.props` Proje dosyasının üst kısmına ve alt kısmına örtük içeri aktarmalar ekler `Sdk.targets` .

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> Bir Windows makinesinde, *%ProgramFiles%\dotnet\sdk \\ [Version] \Sdks\Microsoft.net.Sdk\Sdk* klasöründe *SDK. props* ve *SDK. targets* dosyaları bulunabilir.

### <a name="preprocess-the-project-file"></a>Proje dosyasını ön işleme

SDK ve hedefleri komutu kullanılarak eklendikten sonra, tam genişletilmiş projeyi MSBuild olarak görebilirsiniz `dotnet msbuild -preprocess` . Komutun [ön işlem](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) anahtarı [`dotnet msbuild`](../tools/dotnet-msbuild.md) hangi dosyaların içeri aktarılacağını, kaynaklarını ve derleme için gerçekten projeyi oluşturmadan yapıya katkılarını gösterir.

Projede birden çok hedef çerçeve varsa, komutun sonuçlarını MSBuild özelliği olarak belirterek yalnızca bir çerçeveye odaklayın. Örneğin:

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>Varsayılan derleme şunları içerir

Derleme öğeleri, katıştırılmış kaynaklar ve öğeler için varsayılan içerir ve `None` DıŞLARDıR SDK 'da tanımlanmıştır. SDK olmayan .NET Framework projelerinin aksine, varsayılanlar en yaygın kullanım durumlarını kapsadığından proje dosyanızda bu öğeleri belirtmeniz gerekmez. Bu, proje dosyasını daha küçük ve gerekirse, el ile anlamanız ve düzenlemeyi kolaylaştırır.

Aşağıdaki tablo, hangi öğelerin ve hangi [genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) dahil edileceğini ve .NET Core SDK hariç tutulduğunu gösterir:

| Öğe           | Glob 'yi dahil et                              | Glob 'yi hariç tut                                                  | Glob 'yi kaldır              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Se           | \*\*/\*. cs (veya diğer dil uzantıları) | \*\*/\*kullanıcısını  \*\*/\*.\* PROJ  \*\*/\*. sln  \*\*/\*. vssscc  | Yok                      |
| EmbeddedResource  | \*\*/\*. resx                              | \*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc     | Yok                      |
| Hiçbiri              | \*\*/\*                                   | \*\*/\*kullanıcısını \*\*/\*.\* PROJ \*\*/\*. sln \*\*/\*. vssscc     | \*\*/\*.cs \*\*/\*. resx |

> [!NOTE]
> Ve `./bin` `./obj` MSBuild özellikleriyle temsil edilen ve klasörleri, `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` Varsayılan olarak genelleştirmeler 'tan çıkarılır. Dışlayarak özelliği tarafından temsil edilir `$(DefaultItemExcludes)` .

#### <a name="build-errors"></a>Derleme hataları

Proje dosyanızda bu öğelerden herhangi birini açıkça tanımlarsanız, büyük olasılıkla aşağıdakine benzer bir "NETSDK1022" derleme hatası alırsınız:

  > Yinelenen ' Compile ' öğeleri eklendi. .NET SDK varsayılan olarak proje dizininizdeki ' derleme ' öğelerini içerir. Bu öğeleri proje dosyanıza kaldırabilir ya da bunları proje dosyanıza açıkça dahil etmek istiyorsanız ' Enabledefaultcompileıtems ' özelliğini ' false ' olarak ayarlayabilirsiniz.

  > Yinelenen ' EmbeddedResource ' öğeleri eklendi. .NET SDK varsayılan olarak proje dizininizdeki ' EmbeddedResource ' öğelerini içerir. Bu öğeleri proje dosyanıza kaldırabilir ya da bunları proje dosyanıza açıkça dahil etmek istiyorsanız ' Enabledefaultembeddedresourceıtems ' özelliğini ' false ' olarak ayarlayabilirsiniz.

Hataları gidermek için aşağıdakilerden birini yapın:

- `Compile` `EmbeddedResource` `None` Önceki tabloda listelenenlerin bulunduğu açık, veya öğeleri kaldırın.

- `EnableDefaultItems` `false` Tüm örtük dosya eklemeyi devre dışı bırakmak için özelliğini olarak ayarlayın:

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  Uygulamanızla yayımlanacak dosyaları belirtmek istiyorsanız, bu gibi bilinen MSBuild mekanizmalarını yine de kullanabilirsiniz (örneğin, `Content` öğesi).

- ,, Veya özelliğini olarak ayarlayarak yalnızca,, `Compile` veya genelleştirmeler öğesini seçime bağlı olarak devre dışı bırakın `EmbeddedResource` `None` `EnableDefaultCompileItems` `EnableDefaultEmbeddedResourceItems` `EnableDefaultNoneItems` `false` :

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  Yalnızca genelleştirmeler 'yi devre dışı bırakırsanız `Compile` , Visual Studio 'daki Çözüm Gezgini, \* öğe olarak da dahil olmak üzere projenin bir parçası olarak. cs öğelerini gösterir `None` . Örtük glob 'yi devre dışı bırakmak için `None` , `EnableDefaultNoneItems` çok olarak ayarlayın `false` .

## <a name="customize-the-build"></a>Derlemeyi özelleştirme

[Bir derlemeyi özelleştirmek](/visualstudio/msbuild/customize-your-build)için çeşitli yollar vardır. Bir [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) veya [DotNet](../tools/index.md) komutuna bir bağımsız değişken olarak geçirerek bir özelliği geçersiz kılmak isteyebilirsiniz. Ayrıca, özelliği proje dosyasına veya bir *Dizin. Build. props* dosyasına ekleyebilirsiniz. .NET Core projelerinin yararlı özelliklerinin bir listesi için bkz. [.NET Core SDK projeleri Için MSBuild başvurusu](msbuild-props.md).

### <a name="custom-targets"></a>Özel hedefler

.NET Core projeleri, paketi tüketen projeler tarafından kullanılmak üzere özel MSBuild hedeflerini ve özelliklerini paketleyebilir. Şunları yapmak istediğinizde bu tür bir genişletilebilirlik kullanın:

- Yapı sürecini genişletin.
- Oluşturulan dosyalar gibi yapı sürecinin yapılarına erişin.
- Yapılandırmanın çağrıldığı yapılandırmayı inceleyin.

Dosyaları forma `<package_id>.targets` veya `<package_id>.props` (örneğin, `Contoso.Utility.UsefulStuff.targets` ) projenin *Build* klasörüne yerleştirerek özel derleme hedefleri veya özellikleri eklersiniz.

Aşağıdaki XML, bir *. csproj* dosyasındaki, [`dotnet pack`](../tools/dotnet-pack.md) komuta neyin paketlenecek olduğunu bildiren bir kod parçacıdır. `<ItemGroup Label="dotnet pack instructions">`Öğesi, hedef dosyalarını paketin içindeki *derleme* klasörüne koyar. `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">`Öğesi derlemeler ve *. JSON* dosyalarını *Build* klasörüne koyar.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...
  
</Project>
```

Projenizde özel bir hedef kullanmak için `PackageReference` pakete ve sürümüne işaret eden bir öğesi ekleyin. Araçların aksine, özel hedefler paketi, tüketen projenin bağımlılık kapanışına dahil edilir.

Özel hedefin nasıl kullanılacağını yapılandırabilirsiniz. Bir MSBuild hedefi olduğundan, belirli bir hedefe bağlı olabilir, başka bir hedeften sonra çalıştırılabilir veya komutu kullanılarak el ile çağrılabilir `dotnet msbuild -t:<target-name>` . Ancak, daha iyi bir kullanıcı deneyimi sağlamak için proje başına araçları ve özel hedefleri birleştirebilirsiniz. Bu senaryoda, proje başına aracı her türlü parametreyi kabul eder ve [`dotnet msbuild`](../tools/dotnet-msbuild.md) hedefi yürüten gerekli çağrıya çevirir. Bu tür sinerjiden bahsederek denemelerini 'nin bir örneğini projede [MVP Zirvesi 2016 Hackathon örnekleri](https://github.com/dotnet/MVPSummitHackathon2016) deposunda görebilirsiniz [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) .

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core 'ı yükler](../install/index.yml)
- [MSBuild proje SDK 'larını kullanma](/visualstudio/msbuild/how-to-use-project-sdk)
- [NuGet ile özel MSBuild hedeflerini ve props paketleme](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
