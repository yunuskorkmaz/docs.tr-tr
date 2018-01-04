---
title: ".NET core CLI genişletilebilirlik modeli"
description: "Komut satırı arabirimi (CLI) araçları nasıl genişletebileceğini öğrenin."
keywords: "CLI, genişletilebilirlik, özel komutlar, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 04/12/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fffc3400-aeb9-4c07-9fea-83bc8dbdcbf3
ms.workload: dotnetcore
ms.openlocfilehash: 0d273510903c888f3212a57f4c28b118b73cab5c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-cli-tools-extensibility-model"></a>.NET core CLI araçlarını genişletilebilirlik modeli

Bu belge, .NET Core komut satırı arabirimi (CLI) araçları genişletir ve her biri, sürücü senaryoları açıklayan farklı yöntemleri kapsar.
Araçlar kullanma gibi farklı türlerde araçlar oluşturma görürsünüz.

## <a name="how-to-extend-cli-tools"></a>CLI araçlarını genişletme
CLI araçlarını üç temel şekilde genişletilebilir:

1. [Proje başına temelinde NuGet paketleri](#per-project-based-extensibility)

  Proje başına araçları projenin bağlamı içinde yer alır, ancak geri yükleme aracılığıyla kolay yükleme sağlarlar.

2. [Özel hedefler NuGet paketleri](#custom-targets)

  Özel hedefleri kolayca özel görevlerle derleme işlemini genişletme olanak sağlar.

3. [Sistem yolu](#path-based-extensibility)

  YOL tabanlı araçlar, tek bir makinede kullanılabilen genel, çapraz proje araçları için iyidir.

Yukarıda özetlenen üç genişletilebilirlik mekanizması özel değildir. Biri veya tümü, kullanabilirsiniz veya bir birleşimi. Hangisinin seçmek için büyük ölçüde uzantısı ile elde etmek için çalıştığınız hedef bağlıdır.

## <a name="per-project-based-extensibility"></a>Proje başına tabanlı genişletilebilirliği
Proje başına araçlardır [framework bağımlı dağıtımları](../deploying/index.md#framework-dependent-deployments-fdd) NuGet paket olarak dağıtılır. Araçlar yalnızca bunları başvuran ve, bunlar geri proje bağlamında kullanılabilir. Bağlam dışında çağırma (örneğin, projeyi içeren dizin dışında) projenin komutu bulunamadığı için başarısız olur.

Proje dosyası dışında bir şey gerekli olmadığından, bu araçları yapı sunucuları için mükemmeldir. Derleme işlem çalıştırmalarını derlemeleri geri proje için ve araçlar kullanılabilir olacaktır. Her proje yalnızca belirli bir dilde yazılabilir olduğundan gibi F # dili projeler de bu kategoride bulunan.

Son olarak, bu genişletilebilirlik modeli projesi için yerleşik çıktı erişmesi gereken araçları oluşturulması için destek sağlar. Çeşitli Razor görünüm örneği için araçlarla [ASP.NET](https://www.asp.net/) MVC uygulamaları bu kategoriye ayrılır.

### <a name="consuming-per-project-tools"></a>Proje başına araçlarını kullanma
Bu araçların tüketme gerektirir eklemek bir `<DotNetCliToolReference>` proje dosyanıza kullanmak istediğiniz her bir araçla öğesi. İçinde `<DotNetCliToolReference>` öğesi, aracı bulunduğu paketine başvurduğunuzda ve ihtiyacınız olan sürümü belirtin. Çalıştırdıktan sonra [ `dotnet restore` ](dotnet-restore.md), Aracı'nı ve onun bağımlılıklarını geri yüklenir.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Proje yürütme için derleme çıktısı yüklemek için gereken araçları için proje dosyasında normal bağımlılıkları altında listelenen genellikle başka bir bağımlılık yoktur. CLI kendi yapı altyapısı olarak MSBuild kullandığından, bu aracın bölümlerini özel MSBuild yazılması öneririz [hedefleri](/visualstudio/msbuild/msbuild-targets) ve [görevleri](/visualstudio/msbuild/msbuild-tasks), bu yana bunlar daha sonra genel derleme işleminde yer alabilir. Ayrıca, bunlar alabilirsiniz kolayca oluşturulmakta olan geçerli yapılandırmasını ve çıkış dosyalarının konumu gibi yapı aracılığıyla üretilen tüm verileri, vb. Bu bilgileri herhangi hedeften okunabilir MSBuild özellikleri kümesi olur. Bu belgenin sonraki bölümlerinde NuGet kullanarak özel bir hedef ekleme görebilirsiniz.

Şimdi basit bir proje için basit bir salt araçları aracı ekleme konusunda bir örnek gözden geçirin. Adlı bir örnek komut verilen `dotnet-api-search` için belirtilen API NuGet paketlerini arama izin verir, o aracını kullanarak bir konsol uygulamasının proje dosyası aşağıdadır:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

`<DotNetCliToolReference>` Öğesi benzer şekilde yapılandırıldığı `<PackageReference>` öğesi. Geri yükleme yapabilmek için araç ve sürümü içeren paket paketin paket Kimliğini gerekir.

### <a name="building-tools"></a>Derleme araçları
Belirtildiği gibi yalnızca taşınabilir konsol uygulamaları araçlardır. Başka bir konsol uygulaması oluşturmayı tercih gibi araçlar oluşturun.
Bu yapı sonra kullandığınız [ `dotnet pack` ](dotnet-pack.md) vb. kodunuzu, bağımlılıkları hakkında bilgi içeren bir NuGet paketi (.nupkg dosyasını) oluşturmak için komutu. Herhangi bir ad paketini yükler, ancak uygulama içinden, ikili gerçek aracı verebilirsiniz, kurala uygun olması sahip `dotnet-<command>` sırada `dotnet` onu çağırmak için.

> [!NOTE]
> .NET Core komut satırı araçları öncesi RC3 sürümlerinde `dotnet pack` komutu neden olan bir hata vardı `runtime.config.json` aracıyla paketlenmiş değil için. Bu dosya sonuçlarını hatalarla çalışma zamanında eksik. Bu davranış karşılaşırsanız, en yeni araç ve try güncelleştirdiğinizden emin olun `dotnet pack` yeniden.

Araçları taşınabilir uygulamaları olduğundan, aracı kullanma kullanıcı aracı aracını çalıştırmak için karşı oluşturulan .NET Core kitaplıkları sürümüne sahip olmalıdır. Aracı kullanır ve değil barındırılan, .NET Core kitaplıkları içinde herhangi bir bağımlılığı geri ve NuGet önbellekte yerleştirilir. Tüm aracı bu nedenle, .NET Core kitaplıkları derlemelerden yanı sıra derlemeleri NuGet önbellekten kullanarak Çalıştır.

Bu tür araçların, bunları kullanan proje bağımlılık grafikten tamamen ayrı bir bağımlılık grafiğinin vardır. Geri yükleme işlemi ilk proje bağımlılıkları yükler ve ardından her araçları ve bağımlılıklarını geri yükler.

Daha zengin örnekler ve bu konuda farklı birleşimlerini bulabilirsiniz [.NET Core CLI depodaki](https://github.com/dotnet/cli/tree/rel/1.0.1/TestAssets/TestProjects).
Ayrıca bkz [kullanılan araçlar uyarlamasını](https://github.com/dotnet/cli/tree/rel/1.0.1/TestAssets/TestPackages) aynı depodaki.

### <a name="custom-targets"></a>Özel hedefleri
NuGet yeteneğine sahip [özel MSBuild hedefleri ve özellik dosyalarını paketini](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package). .NET Core CLI araçlarını MSBuild kullanmak için taşıma ile aynı mekanizması genişletilebilirlik şimdi .NET Core projeler için geçerlidir. Bu tür genişletilebilirliği derleme işlemini genişletme istediğinizde ya da herhangi bir derleme işlemindeki oluşturulan dosyaları gibi yapılarının erişmek istediğiniz veya altında yapı çağrılır yapılandırmayı incelemek istediğinizde kullanırsınız , vs.

Aşağıdaki örnekte, hedefin proje görebilirsiniz kullanarak dosya `csproj` sözdizimi. Bu bildirir [ `dotnet pack` ](dotnet-pack.md) ne hedefleri dosyalarının yanı sıra derlemelerine yerleştirme pakete komutunu *yapı* paketin içindeki klasör. Bildirim `<ItemGroup>` olan öğeyi `Label` özelliğini `dotnet pack instructions`, hedef altında tanımlanan ve.

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

Özel hedefleri tüketen yapılır sağlayarak bir `<PackageReference>` işaret paketi ve genişletilen projesi içinde sürümü. Araçlar, özel hedefleri paket kaybı projenin bağımlılık kapatma dahil.

Özel hedef kullanarak yalnızca onu nasıl yapılandırdığınıza üzerinde bağlıdır. MSBuild hedef olduğuna göre bağlı olabilir belirli bir hedef sonra başka bir hedef çalıştırın ve ayrıca el ile kullanarak çağrılabilir `dotnet msbuild /t:<target-name>` komutu.

Ancak, kullanıcılarınıza daha iyi bir kullanıcı deneyimi sağlamak istiyorsanız, proje başına Araçlar ve özel hedefleri birleştirebilirsiniz. Bu senaryoda, proje başına aracı temelde yalnızca ne olursa olsun Parametreler gerekli ve gerekli çevirir kabul [ `dotnet msbuild` ](dotnet-msbuild.md) hedef yürütülür çağırma. Bu tür bir synergy örneği görebilirsiniz [MVP Zirvesi'ne 2016 Hackathon örnekleri](https://github.com/dotnet/MVPSummitHackathon2016) bağlantıların bulunması [ `dotnet-packer` ](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) projesi.

### <a name="path-based-extensibility"></a>YOL tabanlı genişletilebilirliği
YOL tabanlı genişletilebilirlik genellikle kavramsal olarak tek bir projede birden fazla kapsayan bir aracı ihtiyaç duyacağınız geliştirme makineler için kullanılır. Bu uzantı mekanizması en büyük dezavantajı, bu aracın bulunduğu makineye bağlıdır ' dir. Başka bir makinede ihtiyacınız varsa, bunu dağıtmak gerekir.

Bu tür CLI araç takımı genişletilebilirlik çok kolaydır. İçinde anlatıldığı gibi [.NET Core CLI genel bakış](index.md), `dotnet` sürücü sonra adlı herhangi bir komutunu çalıştırabilirsiniz `dotnet-<command>` kuralı. Varsayılan çözünürlük mantığı ilk çeşitli konumlardan araştırmaları ve son olarak sistem yolu geri döner. İstenen komut sistem yolu varsa ve çağrılabilir, bir ikili dosyadır `dotnet` sürücü, çağırılır.

Dosya çalıştırılabilir olmalıdır. UNIX sistemleri üzerinde aracılığıyla yürütme bit kümesine sahip herhangi bir şey yani `chmod +x`. Windows, kullandığınız *cmd* dosyaları.

"Hello World" aracı çok basit uygulanması bir göz atalım. Her ikisi de kullanacağız `bash` ve `cmd` Windows.
Aşağıdaki komut, konsola yalnızca bir echo "Hello World".

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

MacOS üzerinde Biz bu komut dosyası olarak kaydedebilirsiniz `dotnet-hello` ve kendi yürütülebilir biti ile `chmod +x dotnet-hello`. Buna sembolik bağlantı sonra oluşturabiliriz `/usr/local/bin` komutunu kullanarak `ln -s <full_path>/dotnet-hello /usr/local/bin/`. Bu, komutunu kullanarak çağırmak mümkün hale getirir `dotnet hello` sözdizimi.

Windows, biz bu komut dosyası olarak kaydedebilirsiniz `dotnet-hello.cmd` ve sistem yolunda bir konumda put (veya yolunda zaten bir klasöre ekleyebilirsiniz). Bundan sonra yalnızca kullanabilirsiniz `dotnet hello` Bu örneği çalıştırmak için.
