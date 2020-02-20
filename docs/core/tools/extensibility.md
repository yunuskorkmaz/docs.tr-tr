---
title: .NET Core CLI genişletilebilirlik modeli
description: .NET Core CLI nasıl genişletebileceğinizi öğrenin.
ms.date: 04/12/2017
ms.openlocfilehash: 56a9cedc090ddca446c0ee1a60f2ca49590e7635
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451161"
---
# <a name="net-core-cli-extensibility-model"></a>.NET Core CLI genişletilebilirlik modeli

Bu makalede .NET Core CLI genişletebileceğiniz farklı yollar ele alınmaktadır ve bunların her birini hedefleyen senaryolar açıklanacaktır.
Araçların nasıl kullanılacağı ve farklı araç türlerini nasıl oluşturacağınız hakkında bilgi edineceksiniz.

## <a name="how-to-extend-the-cli"></a>CLı 'yı genişletme
CLı üç ana şekilde genişletilebilir:

1. [Her proje temelinde NuGet paketleri aracılığıyla](#per-project-based-extensibility)

   Proje başına Araçlar, projenin bağlamı içinde bulunur, ancak geri yükleme yoluyla kolayca yüklemeye izin verir.

2. [Özel hedefleri olan NuGet paketleri aracılığıyla](#custom-targets)

   Özel hedefler, yapı sürecini özel görevlerle kolayca genişletmenizi sağlar.

3. [Sistemin yolu aracılığıyla](#path-based-extensibility)

   YOL tabanlı araçlar, tek bir makinede kullanılabilen genel, projeler arası araçlar için uygundur.

Yukarıda özetlenen üç genişletilebilirlik mekanizması dışlamalı değildir. Birini veya tümünü veya bunların bir bileşimini kullanabilirsiniz. Bunlardan biri, uzantınıza ulaşmayı denediğiniz hedefe büyük ölçüde bağlıdır.

## <a name="per-project-based-extensibility"></a>Proje tabanlı genişletilebilirlik
Proje başına Araçlar, NuGet paketleri olarak dağıtılan [çerçeveye bağımlı dağıtımlardır](../deploying/index.md#publish-runtime-dependent) . Araçlar yalnızca bunlara başvuran ve bunların geri yüklendiği proje bağlamında kullanılabilir. Proje bağlamı dışında (örneğin, projeyi içeren dizinin dışında) çağırma başarısız olur çünkü komut bulunamıyor.

Bu araçlar, derleme sunucuları için idealdir, çünkü proje dosyası dışında hiçbir şey gerekmez. Yapı işlemi, oluşturduğu proje için geri yüklemeyi çalıştırır ve araçlar kullanılabilir olacaktır. Her proje yalnızca belirli bir F#dilde yazıdıklarından, gibi dil projeleri de bu kategoride yer alabilir.

Son olarak, bu genişletilebilirlik modeli, projenin oluşturulan çıktısına erişmesi gereken araçların oluşturulmasına yönelik destek sağlar. Örneğin, [ASP.net](https://www.asp.net/) MVC uygulamalarındaki çeşitli Razor görünümü araçları bu kategoriye girer.

### <a name="consuming-per-project-tools"></a>Proje başına araçları kullanma
Bu araçların kullanılması için, kullanmak istediğiniz her bir araç için proje dosyanıza bir `<DotNetCliToolReference>` öğesi eklemenizi gerektirir. `<DotNetCliToolReference>` öğesinin içinde, aracın bulunduğu pakete başvuru ve ihtiyacınız olan sürümü belirtmeniz gerekir. [`dotnet restore`](dotnet-restore.md)çalıştırıldıktan sonra araç ve bağımlılıkları geri yüklenir.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Yürütülmesi için projenin yapı çıkışını yüklemesi gereken araçlar için, genellikle proje dosyasındaki normal bağımlılıklar altında listelenen başka bir bağımlılık vardır. CLı, yapı altyapısı olarak MSBuild kullandığından, bu aracın bu bölümlerinin özel MSBuild [hedefleri](/visualstudio/msbuild/msbuild-targets) ve [görevleri](/visualstudio/msbuild/msbuild-tasks)olarak yazılması önerilir, çünkü bu, genel derleme sürecinde bir bölüm alabilir. Ayrıca, çıkış dosyalarının konumu, oluşturulmakta olan geçerli yapılandırma vb. gibi, yapı aracılığıyla üretilen tüm ve tüm verileri kolayca alabilirler. Tüm bu bilgiler, herhangi bir hedeften okunabilecek bir MSBuild özellikleri kümesi haline gelir. Bu belgede daha sonra NuGet kullanarak özel bir hedef ekleme hakkında bilgi alabilirsiniz.

Basit bir projeye basit bir araç öncesi araç ekleme örneğini incelim. Belirtilen API için NuGet paketlerinde arama yapmanıza olanak sağlayan `dotnet-api-search` adlı örnek bir komut verildiğinde, bu aracı kullanan bir konsol uygulamasının proje dosyası aşağıda verilmiştir:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

`<DotNetCliToolReference>` öğesi `<PackageReference>` öğesi gibi benzer bir şekilde yapılandırılmıştır. Geri yükleyebilmek için aracı ve sürümünü içeren paketin paket KIMLIĞI gereklidir.

### <a name="building-tools"></a>Araç oluşturma
Belirtildiği gibi, araçlar yalnızca taşınabilir konsol uygulamalarıdır. Diğer konsol uygulamaları oluştururken araçlar oluşturursunuz.
Derlemeyi oluşturduktan sonra, kodunuzu içeren bir NuGet paketi (. nupkg dosyası) oluşturmak için [`dotnet pack`](dotnet-pack.md) komutunu, bağımlılıklarıyla ilgili bilgileri ve benzerlerini kullanın. Pakete herhangi bir ad verebilirsiniz, ancak gerçek araç ikilisinin içindeki uygulamanın, `dotnet` çağırabilmesi için `dotnet-<command>` kuralına uygun olması gerekir.

> [!NOTE]
> .NET Core komut satırı araçlarının pre-RC3 sürümlerinde `dotnet pack` komutunda, araçla paketlenmemelidir *. runtimeconfig. JSON* dosyasına neden olan bir hata vardı. Bu dosya çalışma zamanında hata oluşmasına neden olur. Bu davranışla karşılaşırsanız, en son araçları güncelleştirdiğinizden emin olun ve `dotnet pack` yeniden deneyin.

Araçlar taşınabilir uygulamalar olduğundan, aracı kullanan kullanıcının aracı çalıştırmak için, aracın oluşturulduğu .NET Core kitaplıklarının sürümüne sahip olması gerekir. Aracın kullandığı ve .NET Core kitaplıkları içinde bulunmayan diğer tüm bağımlılıklar geri yüklenir ve NuGet önbelleğine yerleştirilir. Bu nedenle, tüm araç, .NET Core kütüphanelerinin derlemeleri ve NuGet önbelleğinden derlemelerin kullanılmasıyla çalıştırılır.

Bu tür araçların, kendisini kullanan projenin bağımlılık grafiğinden tamamen ayrı olan bir bağımlılık grafiği vardır. Geri yükleme işlemi öncelikle projenin bağımlılıklarını geri yükler ve ardından araçların her birini ve bağımlılıklarını geri yükler.

[.NET Core CLI](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects)deposunda Bunun daha zengin örnekleri ve farklı birleşimlerini bulabilirsiniz.
Aynı depoda [kullanılan araçların uygulanmasını](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) da görebilirsiniz.

## <a name="custom-targets"></a>Özel hedefler

NuGet [özel MSBuild hedeflerini ve props dosyalarını paketleme](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)özelliğine sahiptir. MSBuild 'i kullanmak için .NET Core 'un taşınması sayesinde aynı genişletilebilirlik mekanizması artık .NET Core projeleri için geçerlidir. Yapı işlemini genişletmek istediğinizde veya oluşturulan dosyalar gibi yapı işlemindeki yapıtlardan herhangi birine erişmek istediğinizde veya yapının çağrıldığı yapılandırmayı incelemek istediğinizde, bu tür bir genişletilebilirlik kullanın vb.

Aşağıdaki örnekte, `csproj` sözdizimini kullanarak hedefin proje dosyasını görebilirsiniz. Bu, [`dotnet pack`](dotnet-pack.md) komutuna ne paketlenecek, hedef dosyaların yanı sıra derlemeleri paketin içindeki *Yapı* klasörüne yerleştirmesini sağlar. `Label` özelliği `dotnet pack instructions`olarak ayarlanan `<ItemGroup>` öğeye ve altında tanımlanan hedefe dikkat edin.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <Description>Sample Packer</Description>
    <VersionPrefix>0.1.0-preview</VersionPrefix>
    <TargetFramework>netstandard1.3</TargetFramework>
    <DebugType>portable</DebugType>
    <AssemblyName>SampleTargets.PackerTarget</AssemblyName>
  </PropertyGroup>
  <ItemGroup>
    <EmbeddedResource Include="Resources\Pkg\dist-template.xml;compiler\resources\**\*" Exclude="bin\**;obj\**;**\*.xproj;packages\**" />
    <None Include="build\SampleTargets.PackerTarget.targets" />
  </ItemGroup>
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
  <ItemGroup>
    <PackageReference Include="Microsoft.Extensions.DependencyModel" Version="1.0.1-beta-000933"/>
    <PackageReference Include="Microsoft.Build.Framework" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Microsoft.Build.Utilities.Core" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
  <ItemGroup />
  <PropertyGroup Label="Globals">
    <ProjectGuid>463c66f0-921d-4d34-8bde-7c9d0bffaf7b</ProjectGuid>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(TargetFramework)' == 'netstandard1.3' ">
    <DefineConstants>$(DefineConstants);NETSTANDARD1_3</DefineConstants>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <DefineConstants>$(DefineConstants);RELEASE</DefineConstants>
  </PropertyGroup>
</Project>
```

Özel hedefleri tüketen, pakete ve genişletilmekte olan projenin içindeki sürümüne işaret eden bir `<PackageReference>` sağlayarak yapılır. Araçların aksine, özel hedefler paketi, tüketen projenin bağımlılık kapanışına dahil edilir.

Özel hedefin kullanılması yalnızca nasıl yapılandırdığınıza bağlıdır. Bir MSBuild hedefi olduğundan, belirli bir hedefe bağlı olabilir, başka bir hedeften sonra çalıştırılabilir ve ayrıca `dotnet msbuild -t:<target-name>` komutu kullanılarak el ile çağrılabilir.

Ancak kullanıcılarınıza daha iyi bir kullanıcı deneyimi sağlamak istiyorsanız, proje başına araçları ve özel hedefleri birleştirebilirsiniz. Bu senaryoda, proje başına aracı temel olarak yalnızca gerekli parametreleri kabul eder ve hedefi yürütecek gerekli [`dotnet msbuild`](dotnet-msbuild.md) çağrısına çevirirler. [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) projesindeki [MVP Zirvesi 2016 Hackathon örnekleri](https://github.com/dotnet/MVPSummitHackathon2016) deposunda bu tür bir sinerjiden bahsederek denemelerini örneğini görebilirsiniz.

## <a name="path-based-extensibility"></a>YOL tabanlı genişletilebilirlik
YOL tabanlı genişletilebilirlik genellikle, kavramsal olarak tek bir projeden daha fazla yer kaplayan bir araca ihtiyacınız olan geliştirme makinelerinde kullanılır. Bu uzantı mekanizmasının ana dezavantajı, aracın bulunduğu makineye bağlı olması olabilir. Başka bir makinede ihtiyacınız varsa dağıtmanız gerekir.

CLı araç takımı genişletilebilirliği bu düzende çok basittir. [.NET Core CLI genel bakış](index.md)kapsamında da gösterildiği gibi, `dotnet` sürücü `dotnet-<command>` kuralından sonra adlandırılmış herhangi bir komutu çalıştırabilir. Varsayılan çözüm mantığı öncelikle birkaç konumu yoklamıştır ve son olarak sistem yoluna geri döner. İstenen komut sistem yolunda varsa ve çağrılabilecek bir ikili dosyaysa `dotnet` sürücü bunu çağırır.

Dosya yürütülebilir olmalıdır. UNIX sistemlerinde, bu, `chmod +x`aracılığıyla yürütme biti ayarlanmış herhangi bir şey anlamına gelir. Windows 'ta *cmd* dosyalarını kullanabilirsiniz.

Bir "Merhaba Dünya" aracının çok basit uygulamasına göz atalım. Windows üzerinde hem `bash` hem de `cmd` kullanacağız.
Aşağıdaki komut konsola yalnızca "Merhaba Dünya" yankısını sağlar.

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

MacOS 'ta bu betiği `dotnet-hello` olarak kaydedebilir ve yürütülebilir bitini `chmod +x dotnet-hello`olarak ayarlayabilirsiniz. Daha sonra komut `ln -s <full_path>/dotnet-hello /usr/local/bin/`kullanarak `/usr/local/bin` bir sembolik bağlantı oluşturuyoruz. Bu, `dotnet hello` söz dizimini kullanarak komutu çağırmayı mümkün hale getirir.

Windows 'ta, bu betiği `dotnet-hello.cmd` olarak kaydedebilir ve sistem yolundaki bir konuma koyabilirsiniz (veya zaten yolda olan bir klasöre ekleyebilirsiniz). Bundan sonra, bu örneği çalıştırmak için yalnızca `dotnet hello` kullanabilirsiniz.
