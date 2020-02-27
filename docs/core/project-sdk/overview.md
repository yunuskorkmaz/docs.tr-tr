---
title: .NET Core proje SDK 'sına genel bakış
description: .NET Core proje SDK 'Ları hakkında bilgi edinin.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: c41b25bf7933e7b1f6cb50da5e52dc0b312f5c74
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626251"
---
# <a name="net-core-project-sdks"></a>.NET Core proje SDK 'Ları

.NET Core projeleri bir yazılım geliştirme seti (SDK) ile ilişkilendirilir. Her proje SDK 'Sı, bir dizi MSBuild [hedefi](/visualstudio/msbuild/msbuild-targets) ve kodu derleme, paketleme ve yayımlama ile ilgili [görevlerden](/visualstudio/msbuild/msbuild-tasks) oluşur.

## <a name="available-sdks"></a>Kullanılabilir SDK 'lar

.NET Core için aşağıdaki SDK 'lar mevcuttur:

| Kimlik | Açıklama | Depo|
| - | - | - |
| `Microsoft.NET.Sdk` | .NET Core SDK | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | .NET Core [Web SDK 'sı](/aspnet/core/razor-pages/web-sdk) | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | .NET Core [Razor SDK 'sı](/aspnet/core/razor-pages/sdk) |
| `Microsoft.NET.Sdk.Worker` | .NET Core Worker hizmeti SDK 'Sı |
| `Microsoft.NET.Sdk.WindowsDesktop` | .NET Core WinForms ve WPF SDK |

.NET Core SDK, .NET Core için temel SDK 'dir. Diğer SDK 'lar .NET Core SDK başvuruda bulunur ve diğer SDK 'lar ile ilişkili projeler için kullanılabilen tüm .NET Core SDK özellikleri vardır. Örneğin, Web SDK 'Sı, hem .NET Core SDK hem de Razor SDK 'sına bağlıdır.

Ayrıca kendi SDK 'nizi, NuGet aracılığıyla dağıtılabilecek şekilde yazabilirsiniz.

## <a name="project-files"></a>Proje dosyaları

.NET Core projeleri [MSBuild](/visualstudio/msbuild/msbuild) biçimine dayanır. Projeler için *. csproj* ve projeler için F# *. fsproj* gıbı uzantılara sahip proje dosyaları, XML biçimindedir. C# MSBuild proje dosyasının kök öğesi [Proje](/visualstudio/msbuild/project-element-msbuild) öğesidir. `Project` öğesinin hangi SDK (ve sürümü) kullanacağınızı belirten isteğe bağlı bir `Sdk` özniteliği vardır. .NET Core araçlarını kullanmak ve kodunuzu derlemek için `Sdk` özniteliğini [kullanılabilir SDK](#available-sdks) 'Lar tablosundaki kimliklerden birine ayarlayın.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

NuGet 'den gelen bir SDK belirtmek için, adın sonundaki sürümü ekleyin veya *Global. JSON* dosyasındaki adı ve sürümü belirtin.

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

Bu yollarla bir SDK 'ya başvurmak, .NET Core için proje dosyalarını büyük ölçüde basitleştirir. Proje değerlendirilirken MSBuild, proje dosyasının en üstünde `Sdk.props` için örtük içeri aktarmalar ekler ve alt kısımdaki `Sdk.targets`.

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
> Bir Windows makinesinde, *%ProgramFiles%\dotnet\sdk\\[Version] \Sdks\Microsoft.net.Sdk\Sdk* klasöründe *SDK. props* ve *SDK. targets* dosyaları bulunabilir.

### <a name="preprocess-the-project-file"></a>Proje dosyasını ön işleme

SDK ve hedefleri `dotnet msbuild -preprocess` komutu kullanılarak eklendikten sonra, tam genişletilmiş projeyi MSBuild olarak görebilirsiniz. [`dotnet msbuild`](../tools/dotnet-msbuild.md) komutunun [ön işleme](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) anahtarı, hangi dosyaların içeri aktarılacağını, kaynaklarını ve derleme için gerçekten projeyi oluşturmadan bunların katkılarını gösterir.

Projede birden çok hedef çerçeve varsa, komutun sonuçlarını MSBuild özelliği olarak belirterek yalnızca bir çerçeveye odaklayın. Örnek:

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>Varsayılan derleme şunları içerir

Derleme öğeleri ve katıştırılmış kaynaklar için varsayılan içerir ve dışlardır SDK 'da tanımlanmıştır. SDK olmayan .NET Framework projelerinin aksine, varsayılanlar en yaygın kullanım durumlarını kapsadığından proje dosyanızda bu öğeleri belirtmeniz gerekmez. Bu, daha kolay anlaşılması gereken daha küçük proje dosyalarına ve gerekirse el ile düzenlemeye yol açar.

Aşağıdaki tabloda, .NET Core SDK hangi öğe ve hangi [genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) dahil olduğu ve dışarıda tutulduğu gösterilmektedir:

| Öğe           | Glob 'yi dahil et                              | Glob 'yi hariç tut                                                  | Glob 'yi kaldır              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Derleme           | \*\*/\*. cs (veya diğer dil uzantıları) | \*\*/\*. Kullanıcı;  \*\*/\*.\*PROJ;  \*\*/\*. sln;  \*\*/\*. vssscc  | Yok                      |
| EmbeddedResource  | \*\*/\*. resx                              | \*\*/\*. Kullanıcı; \*\*/\*.\*PROJ; \*\*/\*. sln; \*\*/\*. vssscc     | Yok                      |
| None              | \*\*/\*                                   | \*\*/\*. Kullanıcı; \*\*/\*.\*PROJ; \*\*/\*. sln; \*\*/\*. vssscc     | \*\*/\*. cs; \*\*/\*. resx |

> [!NOTE]
> `$(BaseOutputPath)` ve `$(BaseIntermediateOutputPath)` MSBuild özellikleriyle temsil edilen `./bin` ve `./obj` klasörleri varsayılan olarak genelleştirmeler çıkarılır. Dışlayarak Özellik `$(DefaultItemExcludes)`temsil edilir.

Bu öğeleri proje dosyanızda açıkça tanımlarsanız, muhtemelen şu hatayı alabilirsiniz:

**Yinelenen derleme öğeleri eklendi. .NET SDK, varsayılan olarak proje dizininizdeki derleme öğelerini içerir. Bu öğeleri proje dosyanıza kaldırabilir ya da bunları proje dosyanıza açıkça dahil etmek istiyorsanız ' Enabledefaultcompileıtems ' özelliğini ' false ' olarak ayarlayabilirsiniz.**

Hatayı gidermek için, önceki tabloda listelenen örtük öğelerle eşleşen açık `Compile` öğelerini kaldırın veya `EnableDefaultCompileItems` özelliğini `false`olarak ayarlayın, bu da örtük eklemeyi devre dışı bırakır:

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Uygulamanızda yayımlanacak bazı dosyalar gibi belirtmek istiyorsanız, bunun için bilinen MSBuild mekanizmalarını yine de kullanabilirsiniz Örneğin, `Content` öğesi.

`EnableDefaultCompileItems` yalnızca `Compile` genelleştirmeler devre dışı bırakır, ancak \*. cs öğelerine de geçerli olan örtük `None` glob gibi diğer genelleştirmeler 'yi etkilemez. Bu nedenle, Visual Studio 'daki Çözüm Gezgini, projenin bir parçası olan `None` öğeler olarak dahil \*. cs öğelerini gösterir. Örtük `None` glob 'yi devre dışı bırakmak için `EnableDefaultNoneItems` `false`olarak ayarlayın:

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

*Tüm* örtük genelleştirmeler devre dışı bırakmak için `EnableDefaultItems` özelliğini `false`olarak ayarlayın:

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a>Derlemeyi özelleştirme

[Bir derlemeyi özelleştirmek](/visualstudio/msbuild/customize-your-build)için çeşitli yollar vardır. Bir [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) veya [DotNet](../tools/index.md) komutuna bir bağımsız değişken olarak geçirerek bir özelliği geçersiz kılmak isteyebilirsiniz. Ayrıca, özelliği proje dosyasına veya bir *Dizin. Build. props* dosyasına ekleyebilirsiniz. .NET Core projelerinin yararlı özelliklerinin bir listesi için bkz. [.NET Core SDK projeleri Için MSBuild özellikleri](msbuild-props.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core’u yükleme](../install/index.md)
- [MSBuild proje SDK 'larını kullanma](/visualstudio/msbuild/how-to-use-project-sdk)
