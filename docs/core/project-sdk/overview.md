---
title: .NET Core projesi SDK'ya genel bakış
description: .NET Core projesi SDK'ları hakkında bilgi edinin.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 32e14993326c6f17d6470249fe5a545180348631
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399177"
---
# <a name="net-core-project-sdks"></a>.NET Çekirdek projesi SDK'ları

.NET Core projeleri bir yazılım geliştirme kiti (SDK) ile ilişkilidir. Her proje SDK, kod derleme, paketleme ve yayımlamadan sorumlu bir MSBuild [hedefleri](/visualstudio/msbuild/msbuild-targets) ve ilişkili [görevler](/visualstudio/msbuild/msbuild-tasks) kümesidir.

## <a name="available-sdks"></a>Kullanılabilir SDK'lar

.NET Core için aşağıdaki SDK'lar mevcuttur:

| Kimlik | Açıklama | Repo|
| - | - | - |
| `Microsoft.NET.Sdk` | .NET Çekirdek SDK | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | .NET Çekirdek [Web SDK](/aspnet/core/razor-pages/web-sdk) | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | .NET [ÇekirdekLi Jilet SDK](/aspnet/core/razor-pages/sdk) |
| `Microsoft.NET.Sdk.Worker` | .NET Çekirdek İşçi Servisi SDK |
| `Microsoft.NET.Sdk.WindowsDesktop` | .NET Çekirdek Kazanç Formları ve WPF SDK |

.NET Core SDK, .NET Core'un temel SDK'sudur. Diğer SDK'lar .NET Core SDK'ya başvurur ve diğer SDK'larla ilişkili projeler de mevcut tüm .NET Core SDK özelliklerine sahiptir. Örneğin Web SDK hem .NET Core SDK'ya hem de Razor SDK'ya bağlıdır.

Ayrıca NuGet üzerinden dağıtılabilir kendi SDK yazabilirsiniz.

## <a name="project-files"></a>Proje dosyaları

.NET Core projeleri [MSBuild](/visualstudio/msbuild/msbuild) formatına dayanır. C# projeleri için *.csproj* ve F# projeleri için *.fsproj* gibi uzantıları olan proje dosyaları XML formatındadır. MSBuild proje dosyasının kök öğesi [Proje](/visualstudio/msbuild/project-element-msbuild) öğesidir. Öğe, `Project` hangi `Sdk` SDK'nın (ve sürümünün) kullanılacağını belirten isteğe bağlı bir özniteliğe sahiptir. .NET Core araçlarını kullanmak ve kodunuzu `Sdk` oluşturmak için, özniteliği [Kullanılabilir SDK'lar](#available-sdks) tablosundaki iYe'lerden birine ayarlayın.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

NuGet'den gelen bir SDK belirtmek için, adın sonundaki sürümü ekleyin veya *global.json* dosyasında adı ve sürümü belirtin.

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

SDK belirtmek için başka bir yolu üst düzey [Sdk](/visualstudio/msbuild/sdk-element-msbuild) elemanı ile:

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

Bir SDK'ya bu yollardan biriyle başvurmak ,NET Core için proje dosyalarını büyük ölçüde basitleştirir. MSBuild, projeyi değerlendirirken proje `Sdk.props` dosyasının üst kısmında ve `Sdk.targets` en altta örtülü içeri aktarım ekler.

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
> Bir Windows makinesinde, *Sdk.props* ve *Sdk.targets* dosyaları *%ProgramFiles%\dotnet\sdk\\[sürüm]\Sdks\Microsoft.NET.Sdk\Sdk* klasöründe bulunabilir.

### <a name="preprocess-the-project-file"></a>Proje dosyasını ön işleme

MSBuild SDK ve hedefleri `dotnet msbuild -preprocess` komutu kullanarak dahil edildikten sonra gördüğü gibi tamamen genişletilmiş proje görebilirsiniz. Komutun [`dotnet msbuild`](../tools/dotnet-msbuild.md) [ön işlem](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) anahtarı, hangi dosyaların içe aktarıldığı, kaynakları ve projeyi gerçekten oluşturmadan yapıya katkıları gösterir.

Projenin birden çok hedef çerçevesi varsa, komutun sonuçlarını MSBuild özelliği olarak belirterek yalnızca bir çerçeveye odakla. Örnek:

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>Varsayılan derleme içerir

Varsayılan öğeler ve katıştırılmış kaynaklar derlemek için içerir ve hariç SDK tanımlanır. SDK dışı .NET Framework projelerinin aksine, varsayılanlar en yaygın kullanım durumlarını kapsadığından, bu öğeleri proje dosyanızda belirtmeniz gerekmez. Bu, anlaşılması daha kolay olan ve gerekirse elle düzenleme nin daha kolay olduğu daha küçük proje dosyalarına yol açar.

Aşağıdaki tabloda .NET Core SDK'da hangi elementin ve hangi [globs'lerin](https://en.wikipedia.org/wiki/Glob_(programming)) dahil edildiği ve dışlandığı gösterilmektedir:

| Öğe           | Glob dahil et                              | Glob hariç                                                  | Glob'u çıkarın              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Derlemek           | \*\*/\*.cs (veya diğer dil uzantıları) | \*\*/\*.kullanıcı;  \*\*/\*. \*proj;  \* \* / \*  \* \* / \*  | Yok                      |
| EmbeddedResource  | \*\*/\*Resx                              | \*\*/\*.kullanıcı; \*\*/\*. \*proj; \* \* / \* \* \* / \*     | Yok                      |
| None              | \*\*/\*                                   | \*\*/\*.kullanıcı; \*\*/\*. \*proj; \* \* / \* \* \* / \*     | \*\*/\*.cs; \* \* /.resx \* |

> [!NOTE]
> `./bin` VE `./obj` `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` MSBuild özellikleri tarafından temsil edilen klasörler varsayılan olarak globs dışında tutulur. Hariç tutmalar özellik `$(DefaultItemExcludes)`tarafından temsil edilir.

Proje dosyanızda bu öğeleri açıkça tanımlarsanız, büyük olasılıkla aşağıdaki hatayı alırsınız:

**Yinelenen Derleme öğeleri dahil edildi. .NET SDK varsayılan olarak proje dizininizdeki öğeleri derle içerir. Bu öğeleri proje dosyanızdan kaldırabilir veya proje dosyanıza açıkça eklemek istiyorsanız 'Varsayılan Derleme Öğeleri' özelliğini 'false' olarak ayarlayabilirsiniz.**

Hatayı gidermek için, önceki `Compile` tabloda listelenen örtük öğelerle eşleşen açık `EnableDefaultCompileItems` öğeleri `false`kaldırın veya özelliği örtük eklemeyi devre dışı bırakan "aşağıdakilere" göre ayarlayın:

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Örneğin, uygulamanızla birlikte yayımlanmak üzere bazı dosyaların belirtilmek isterseniz, örneğin bu öğe için bilinen MSBuild mekanizmalarını `Content` kullanmaya devam edebilirsiniz.

`EnableDefaultCompileItems`yalnızca `Compile` globs devre dışı kalır, ancak .cs öğeleri `None` için \*de geçerli olan örtük glob gibi diğer globs etkilemez. Bu nedenle, Visual Studio'daki \*Solution Explorer,.cs öğelerini projenin `None` bir parçası olarak, öğe olarak gösterir. Örtük `None` glob devre dışı `EnableDefaultNoneItems` kalmak `false`için, ayarlayın:

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

*Tüm* örtük globs devre dışı `EnableDefaultItems` kalmak `false`için, özelliği ayarlayın:

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a>Yapıyı özelleştirme

Bir [yapıyı özelleştirmenin](/visualstudio/msbuild/customize-your-build)çeşitli yolları vardır. Bir özelliği bir [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) veya [dotnet](../tools/index.md) komutuna bağımsız değişken olarak geçirerek geçersiz kılmak isteyebilirsiniz. Özelliği proje dosyasına veya *Dizin.Build.props* dosyasına da ekleyebilirsiniz. .NET Core projelerinin yararlı özelliklerinin listesi [için ,.NET Core SDK projeleri için MSBuild özelliklerine](msbuild-props.md)bakın.

### <a name="custom-targets"></a>Özel hedefler

.NET Core projeleri, paketi tüketen projeler tarafından kullanılmak üzere özel MSBuild hedeflerini ve özelliklerini paketleyebilir. İstediğince bu tür genişletilebilirlik kullanın:

- Yapı işlemini genişletin.
- Oluşturulan dosyalar gibi yapı işleminin yapı yapılarının yapı yapılarına erişin.
- Yapının çağrıldığı yapılandırmayı denetleyin.

Dosyaları `<package_id>.targets` forma `<package_id>.props` veya (örneğin) `Contoso.Utility.UsefulStuff.targets`projenin *yapı* klasörüne yerleştirerek özel yapı hedefleri veya özellikleri eklersiniz.

Aşağıdaki XML, [`dotnet pack`](../tools/dotnet-pack.md) ne paketlenir komutu söyleyen bir *.csproj* dosyasından bir parçacıktır. Öğe, `<ItemGroup Label="dotnet pack instructions">` hedef dosyalarını paketin içindeki *yapı* klasörüne yerleştirir. Öğe `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` derlemeleri ve *.json* dosyalarını *yapı* klasörüne yerleştirir.

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

Projenizde özel bir hedef tüketmek `PackageReference` için pakete ve sürümüne işaret eden bir öğe ekleyin. Araçlardan farklı olarak, özel hedefler paketi, tüketen projenin bağımlılık kapatması dahildir.

Özel hedefin nasıl kullanılacağını yapılandırabilirsiniz. Bir MSBuild hedefi olduğundan, belirli bir hedefe bağlı olabilir, başka bir hedefin peşinden koşabilir veya `dotnet msbuild -t:<target-name>` komutu kullanarak el ile çağrılabilir. Ancak, daha iyi bir kullanıcı deneyimi sağlamak için proje başına araçları ve özel hedefleri birleştirebilirsiniz. Bu senaryoda, proje başına araç gereken parametreleri kabul eder ve [`dotnet msbuild`](../tools/dotnet-msbuild.md) bunu hedefi yürüten gerekli çağrıya çevirir. [Projedeki MVP Summit 2016 Hackathon örnekleri](https://github.com/dotnet/MVPSummitHackathon2016) repo'da [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) bu tür bir sinerji örneği görebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core'u yükle](../install/index.md)
- [MSBuild proje SDK'ları nasıl kullanılır?](/visualstudio/msbuild/how-to-use-project-sdk)
- [NuGet ile özel MSBuild hedeflerini ve sahnelerini paketle](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
