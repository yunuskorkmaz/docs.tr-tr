---
title: .NET core CLI genişletilebilirlik modeli
description: Komut satırı arabirimi (CLI) araçlarını nasıl genişletebileceğinizi öğreneceğiz.
author: blackdwarf
ms.author: mairaw
ms.date: 04/12/2017
ms.openlocfilehash: 9f54479704f547ada567619a82b24a47a0b104c4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204618"
---
# <a name="net-core-cli-tools-extensibility-model"></a>.NET core CLI araçları genişletilebilirlik modeli

Bu belgede, .NET Core komut satırı arabirimi (CLI) araçlarını genişletmek ve her biri sürücü senaryoları açıklayın farklı yöntemleri kapsar.
Araçları kullanma ve bunun yanı sıra farklı türlerde araçlar oluşturma görürsünüz.

## <a name="how-to-extend-cli-tools"></a>CLI araçlarını genişletme
CLI araçları üç temel şekilde genişletilebilir:

1. [Proje başına temelinde NuGet paketleri](#per-project-based-extensibility)

   Proje başına araçları projenin bağlamı içinde yer alır, ancak geri yükleme yoluyla kolay yükleme sağlarlar.

2. [Özel hedefleri NuGet paketleri](#custom-targets)

   Özel hedefleri özel görevleri birlikte derleme işlemini kolayca genişletmenizi sağlar.

3. [Sistem yolu](#path-based-extensibility)

   YOL tabanlı araçlar, tek bir makinede kullanılabilir olan genel, projeler arası araçlar için uygundur.

Yukarıda özetlenen, üç genişletilebilirlik mekanizması dışlamaz. Bir ya da tamamını kullanabilirsiniz veya onları birleşimi. Hangisinin seçmek için büyük ölçüde uzantınız ile elde etmek çalıştığınız hedef bağlıdır.

## <a name="per-project-based-extensibility"></a>Proje başına tabanlı genişletilebilirliği
Proje başına Araçlar [framework bağımlı dağıtımları](../deploying/index.md#framework-dependent-deployments-fdd) NuGet paketleri olarak dağıtılır. Araçlar, yalnızca onlara başvuran ve bunlar geri yüklenir, proje bağlamında kullanılabilir. Komut bulunamadığı için (örneğin, projesini içeren dizin dışında) bir projenin bağlamı dışında çağırma başarısız olur.

Proje dosyası dışında bir şey gerekli olmadığından bu araçlar, derleme sunucuları için mükemmeldir. Derleme işlem çalıştırmalarını derlemeler geri için proje ve araçlar kullanılabilir olacak. Her proje yalnızca belirli bir dilde yazılabilir olduğundan gibi F # dil projeleri aynı zamanda bu kategoride bulunan.

Son olarak, bu genişletilebilirlik modeli proje çıkışı erişmesi gereken araçları oluşturulması için destek sağlar. Örneğin, çeşitli Razor Görünüm Araçları [ASP.NET](https://www.asp.net/) MVC uygulamaları bu kategoriye girer.

### <a name="consuming-per-project-tools"></a>Proje başına araçları kullanma
Bu araçlar kullanan gerektirir eklemek bir `<DotNetCliToolReference>` proje dosyanıza kullanmak istediğiniz her aracı için öğesi. İçinde `<DotNetCliToolReference>` öğesi, araç bulunduğu paket başvurusu ve ihtiyacınız olan sürümü belirtin. Çalıştırdıktan sonra [ `dotnet restore` ](dotnet-restore.md), Aracı'nı ve bağımlılıklarını geri yüklenir.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Proje yürütme için yapı çıkışını yüklemek için gereken araçları için normal bağımlılıkları proje dosyasında altında listelenen genellikle başka bir bağımlılık yoktur. CLI, yapı altyapısı olarak MSBuild kullandığından, bu aracın bölümlerini özel MSBuild yazılması öneririz [hedefleri](/visualstudio/msbuild/msbuild-targets) ve [görevleri](/visualstudio/msbuild/msbuild-tasks), sonra bunlar daha sonra genel derleme işleminde yer alabilir. Ayrıca, bunlar alabilirsiniz kolayca çıktı dosyalarının konumu gibi yapılandırma yoluyla oluşturulmakta olan geçerli yapılandırmasını üretilen tüm veriler, vb. Bu bilgiler, herhangi bir hedef okunabilir MSBuild özellikleri kümesi olur. NuGet kullanarak bu belgede daha sonra özel bir hedef ekleme görebilirsiniz.

Basit bir proje için basit bir salt araçları aracı ekleme örneği gözden geçirelim. Adlı bir örnek komut verilen `dotnet-api-search` belirtilen API'si aracılığıyla NuGet paketlerinin aramanıza olanak sağlayan, bu aracı kullanan bir konsol uygulamasının proje dosyası şu şekildedir:

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

`<DotNetCliToolReference>` Öğesi benzer bir şekilde yapılandırıldığı `<PackageReference>` öğesi. Bu, geri yüklemek için araç ve sürümü içeren paketin paket kimliği gerekiyor.

### <a name="building-tools"></a>Yapı araçları
Belirtildiği gibi yalnızca taşınabilir konsol uygulamaları araçlardır. Diğer bir konsol uygulaması oluşturmayı tercih gibi araçları oluşturun.
Bunu derledikten sonra kullandığınız [ `dotnet pack` ](dotnet-pack.md) vb. kodunuzu, bağımlılıkları hakkında bilgi içeren bir NuGet paketi (.nupkg dosyası) oluşturmak için komutu. Paket, ancak içindeki ikili gerçek aracı uygulama için istediğiniz adı verebilirsiniz, kuralı için uygun olan `dotnet-<command>` sırayla `dotnet` onu çağırmak için.

> [!NOTE]
> .NET Core komut satırı araçları RC3 öncesi sürümlerinde `dotnet pack` komut neden bir hata vardı `runtime.config.json` aracıyla değil ve heyecanla. Çalışma zamanı hatalarını, dosya sonuçlarında eksik. Bu davranış karşılaşırsanız, en son araçları ve deneyin güncelleştirdiğinizden emin olması `dotnet pack` yeniden.

Aracı'nı kullanan kullanıcı, Araçlar taşınabilir uygulamaları olduğundan, aracı çalıştırmak için aracın derlendiği .NET Core kitaplıkları sürümüne sahip olmanız gerekir. Aracı tarafından kullanılan ve yer almıyor, .NET Core kitaplıkları içinde herhangi bir bağımlılık geri ve NuGet önbelleğine yerleştirilmesi. Tüm aracı bu nedenle, .NET Core kitaplıkları derlemelerden yanı sıra derlemeleri NuGet önbellekten kullanarak Çalıştır.

Bu tür araçların bunları kullanan projenin bağımlılık grafı denetiminin dışında tamamen ayrı olan bir bağımlılık grafiği vardır. Geri yükleme işlemi önce projenin bağımlılıkları yükler ve her biri araçları ve bunların bağımlılıklarını yükler.

Daha zengin örnekler ve bu farklı birleşimlerini bulabilirsiniz [.NET Core CLI depo](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).
Ayrıca bkz [kullanılan araçları uygulaması](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) aynı depodaki.

### <a name="custom-targets"></a>Özel hedefleri
NuGet yeteneğine sahip [paket özel MSBuild hedeflerini ve özellik dosyalarını](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package). .NET Core CLI araçları, MSBuild kullanmak için taşıma ile aynı mekanizması genişletilebilirlik artık .NET Core projeleri için geçerlidir. Derleme işlemini genişletme istediğinizde ya da yapı çağırıldığı yapılandırmayı incelemek istediğiniz veya oluşturulan dosyalar gibi yapı işleminde yapıtlar erişmek istediğinizde, bu tür bir genişletilebilirlik kullanırsınız , vs.

Aşağıdaki örnekte, hedefin proje gördüğünüz kullanarak dosya `csproj` söz dizimi. Bu bildirir [ `dotnet pack` ](dotnet-pack.md) ne derlemelerine yanı sıra hedef dosyaları yerleştirmek paket komutunu *derleme* paket klasöründen. Bildirim `<ItemGroup>` sahip öğe `Label` özelliğini `dotnet pack instructions`, hedef altında tanımlanmış.

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

Özel hedefleri tüketen yapılır sağlayarak bir `<PackageReference>` işaret eden paket ve Genişletilmekte olan proje içinde sürümü. Araçları özel hedefleri paket kaybı projenin bağımlılık kapanış dahil.

Özel hedef kullanarak yalnızca nasıl yapılandırmanız üzerinde bağlıdır. MSBuild hedefi olduğundan, güvenebileceğiniz bir belirtilen hedef sonra başka bir hedef çalıştırın ve ayrıca el ile çağrılabilir `dotnet msbuild -t:<target-name>` komutu.

Ancak, kullanıcılarınıza daha iyi bir kullanıcı deneyimi sağlamak istiyorsanız, proje başına Araçlar ve özel hedefleri birleştirebilirsiniz. Bu senaryoda, her proje araç aslında yalnızca ne olursa olsun gerekli parametreleri ve gerekli çevirir kabul [ `dotnet msbuild` ](dotnet-msbuild.md) hedef yürüterek çağırma. Bu tür bir synergy örneği gördüğünüz [MVP Zirvesi 2016 HACK Maratonunda örnekleri](https://github.com/dotnet/MVPSummitHackathon2016) depoda [ `dotnet-packer` ](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) proje.

### <a name="path-based-extensibility"></a>YOL tabanlı genişletilebilirliği
YOL tabanlı genişletilebilirliği, genellikle kavramsal olarak tek bir projede birden fazla kapsayan bir aracı gerek duyduğunuz geliştirme makineler için kullanılır. Bu uzantı mekanizması en büyük dezavantajı, bu aracın bulunduğu makineye bağlıdır ' dir. Başka bir makineye ihtiyacınız varsa, bunu dağıtmak gerekir.

Bu düzen CLI araç takımı genişletilebilirlik çok kolaydır. İçinde anlatıldığı gibi [.NET Core CLI genel bakış](index.md), `dotnet` sürücü sonra adlı herhangi bir komutu çalıştırabilir `dotnet-<command>` kuralı. Varsayılan çözümleme mantığı ilk çeşitli konumlardan araştırmaları ve son olarak sisteme yolu geri döner. İstenen komut yolu sistemde mevcut ve çağrılabilir, bir ikili dosyadır `dotnet` sürücü, çağırılır.

Dosyanın yürütülebilir olması gerekir. UNIX sistemlerde aracılığıyla yürütme biti ayarlanmış herhangi bir şeyi yani `chmod +x`. Windows üzerinde kullanabileceğiniz *cmd* dosyaları.

Çok basit bir "Merhaba Dünya" aracı uygulaması bir göz atalım. Her ikisi de kullanacağız `bash` ve `cmd` Windows üzerinde.
Aşağıdaki komutu yalnızca konsolda "Hello World" echo.

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

MacOS, biz bu komut dosyası olarak kaydedebilirsiniz `dotnet-hello` ve ile yürütülebilir, biti `chmod +x dotnet-hello`. İçinde bir sembolik bağlantısını ardından oluşturabiliriz `/usr/local/bin` komutunu kullanarak `ln -s <full_path>/dotnet-hello /usr/local/bin/`. Bu, komutu kullanarak çağırmak mümkün hale getirir `dotnet hello` söz dizimi.

Windows üzerinde Biz bu komut dosyası olarak kaydedebilirsiniz `dotnet-hello.cmd` ve sistem yolunda bir konuma yerleştirin (veya zaten yolunda bir klasöre ekleyebilirsiniz). Bundan sonra yalnızca kullanabilirsiniz `dotnet hello` Bu örneği çalıştırmak için.
