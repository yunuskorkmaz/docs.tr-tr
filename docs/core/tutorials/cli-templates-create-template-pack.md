---
title: DotNet New için bir şablon paketi oluşturma
description: DotNet yeni komut için bir şablon paketi oluşturacak bir csproj dosyası oluşturmayı öğrenin.
author: thraka
ms.date: 12/10/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 3a72f68f5634c9ee5b137baf12a279130861e61a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787834"
---
# <a name="tutorial-create-a-template-pack"></a>Öğretici: şablon paketi oluşturma

.NET Core ile projeler, dosyalar, hatta kaynaklar üreten şablonlar oluşturabilir ve dağıtabilirsiniz. Bu öğretici, `dotnet new` komutuyla kullanılmak üzere şablonlar oluşturmayı, yüklemeyi ve kaldırmayı öğretir ve bir serinin üçüncü bölümüdür.

Serinin bu bölümünde şunları nasıl yapacağınızı öğreneceksiniz:

> [!div class="checklist"]
>
> * Bir şablon paketi derlemek için \*. csproj projesi oluşturma
> * Paketleme için proje dosyasını yapılandırma
> * NuGet paket dosyasından şablon yükler
> * Bir şablonu paket KIMLIĞIYLE kaldır

## <a name="prerequisites"></a>Prerequisites

* Bu öğretici serisinin [1](cli-templates-create-item-template.md) . ve [2. bölümünü](cli-templates-create-project-template.md) doldurun.

  Bu öğretici, Bu öğreticinin ilk iki bölümünde oluşturulan iki şablonu kullanır. Şablonu, klasör olarak _working\templates\\_ klasörüne kopyaladığınız sürece farklı bir şablon kullanabilirsiniz.

* Bir Terminal açın ve _çalışma\\_ klasörüne gidin.

## <a name="create-a-template-pack-project"></a>Şablon paketi projesi oluşturma

Bir şablon paketi, bir dosyada paketlenmiş bir veya daha fazla şablondur. Bir paketi yüklediğinizde veya kaldırdığınızda, paketin içerdiği tüm şablonlar sırasıyla eklenir veya kaldırılır. Bu öğretici serisinin önceki kısımları yalnızca bireysel şablonlarla birlikte çalışmıştır. Paketlenmiş olmayan bir şablonu paylaşmak için, şablon klasörünü kopyalamanız ve bu klasör aracılığıyla kurmanız gerekir. Bir şablon paketi içinde birden fazla şablon olabileceğinden ve tek bir dosya olduğundan, paylaşma daha kolay olur.

Şablon paketleri, bir NuGet paketi ( _. nupkg_) dosyası tarafından temsil edilir. Tüm NuGet paketleri gibi, şablon paketini bir NuGet akışına de yükleyebilirsiniz. `dotnet new -i` komutu, bir NuGet paketi akışından şablon paketi yüklemeyi destekler. Ayrıca, bir _. nupkg_ dosyasından doğrudan bir şablon paketi de yükleyebilirsiniz.

Normalde, kod derlemek C# ve bir ikili oluşturmak için bir proje dosyası kullanırsınız. Ancak, proje bir şablon paketi oluşturmak için de kullanılabilir. _. Csproj_ayarlarını değiştirerek, bu kodun herhangi bir kodu derlemesine engel olabilir ve bunun yerine şablonlarınızın tüm varlıklarını kaynak olarak dahil edebilirsiniz. Bu proje oluşturulduğunda, bir şablon paketi NuGet paketi oluşturur.

Oluşturacağınız paket, daha önce oluşturulan [öğe şablonunu](cli-templates-create-item-template.md) ve [paket şablonunu](cli-templates-create-project-template.md) içerir. İki şablonu _working\templates\\_ klasörüne grupladığımızda, _. csproj_ dosyası için _çalışma_ klasörünü kullanabiliriz.

Terminalinizde _çalışma_ klasörüne gidin. Yeni bir proje oluşturun ve adı `templatepack` ve çıkış klasörünü geçerli klasöre ayarlayın.

```dotnetcli
dotnet new console -n templatepack -o .
```

`-n` parametresi _. csproj_ dosya adını _templatepack. csproj_olarak ayarlar. `-o` parametresi, geçerli dizindeki dosyaları oluşturur. Aşağıdaki çıktıya benzer bir sonuç görmeniz gerekir.

```console
C:\working> dotnet new console -n templatepack -o .
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

Ardından, en sevdiğiniz düzenleyicide _templatepack. csproj_ dosyasını açın ve IÇERIĞI aşağıdaki XML ile değiştirin:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <PackageTags>dotnet-new;templates;contoso</PackageTags>

    <TargetFramework>netstandard2.0</TargetFramework>

    <IncludeContentInPack>true</IncludeContentInPack>
    <IncludeBuildOutput>false</IncludeBuildOutput>
    <ContentTargetFolders>content</ContentTargetFolders>
  </PropertyGroup>

  <ItemGroup>
    <Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />
    <Compile Remove="**\*" />
  </ItemGroup>

</Project>
```

Yukarıdaki XML 'deki `<PropertyGroup>` ayarları üç gruba bölünmüştür. İlk grup, bir NuGet paketi için gereken özelliklerle ilgilidir. Üç `<Package` ayarlarının, bir NuGet akışında paketinizi tanımlamak için NuGet paket özellikleriyle olması gerekir. Özellikle `<PackageId>` değeri, şablon paketini dizin yolu yerine tek bir adla kaldırmak için kullanılır. Ayrıca, bir NuGet akışından şablon paketini yüklemek için de kullanılabilir. `<Title>` ve `<PackageTags>` gibi kalan ayarların, NuGet akışında görüntülenecek meta verilerle olması gerekir. NuGet ayarları hakkında daha fazla bilgi için bkz. [NuGet ve MSBuild özellikleri](/nuget/reference/msbuild-targets).

Projeyi derlemek ve paketetmek için paket komutunu çalıştırdığınızda MSBuild 'in düzgün çalışması için `<TargetFramework>` ayar ayarlanmalıdır.

Son üç ayar, projeyi, oluşturulduğu zaman NuGet paketindeki uygun klasöre dahil etmek için doğru şekilde yapılandırmaya sahip olmalıdır.

`<ItemGroup>` iki ayar içerir. İlk olarak, `<Content>` ayarı _Şablonlar_ klasöründeki her şeyi içerik olarak içerir. Ayrıca, derlenmiş kodların (şablonlarınızı test etmeniz ve derlediğiniz) dahil edilmesini engellemek için herhangi bir _bin_ klasörünü veya _obj_ klasörünü dışarıda bırakmak üzere ayarlanır. İkincisi, `<Compile>` ayarı, tüm kod dosyalarını nerede bulunduklarında bağımsız olarak derlemeden dışlar. Bu ayar, şablon paketi oluşturmak için kullanılan projenin _Şablonlar_ klasörü hiyerarşisindeki kodu derlemeye çalışmamasını engeller.

## <a name="build-and-install"></a>Oluşturma ve yüklemeyi

Bu dosyayı kaydedin ve ardından paket komutunu çalıştırın

```dotnetcli
dotnet pack
```

Bu komut, projenizi derler ve bu, bir NuGet paketi oluşturmak için _Working\bin\debug_ klasörü olmalıdır.

```console
C:\working> dotnet pack
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

Sonra, `dotnet new -i PATH_TO_NUPKG_FILE` komutuyla şablon paketi dosyasını yükler.

```console
C:\working> dotnet new -i C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
```

NuGet paketini bir NuGet akışına yüklediyseniz, `PACKAGEID` _. csproj_ dosyasındaki `<PackageId>` ayarıyla aynı olduğu `dotnet new -i PACKAGEID` komutunu kullanabilirsiniz. Bu paket KIMLIĞI, NuGet paket tanımlayıcısı ile aynıdır.

## <a name="uninstall-the-template-pack"></a>Şablon paketini kaldırma

Şablon paketini, _. nupkg_ dosyasıyla doğrudan veya NuGet akışı ile nasıl yükletiğinize bakılmaksızın, bir şablon paketinin kaldırılması aynı olur. Kaldırmak istediğiniz şablonun `<PackageId>` kullanın. `dotnet new -u` komutu çalıştırılarak yüklenen şablonların bir listesini alabilirsiniz.

```console
C:\working> dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      dotnet gitignore file (gitignore)
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)

... cut to save space ...

  NUnit3.DotNetNew.Template
    Templates:
      NUnit 3 Test Project (nunit) C#
      NUnit 3 Test Item (nunit-test) C#
      NUnit 3 Test Project (nunit) F#
      NUnit 3 Test Item (nunit-test) F#
      NUnit 3 Test Project (nunit) VB
      NUnit 3 Test Item (nunit-test) VB
  AdatumCorporation.Utility.Templates
    Templates:
      Example templates: async project (consoleasync) C#
      Example templates: string extensions (stringext) C#
```

Şablonu kaldırmak için `dotnet new -u AdatumCorporation.Utility.Templates` çalıştırın. `dotnet new` komutu, daha önce yüklediğiniz şablonları atlamanızı gerektiren yardım bilgilerini çıktı olarak alırsınız.

Tebrikler! bir şablon paketi yüklediniz ve kaldırdık.

## <a name="next-steps"></a>Sonraki adımlar

Zaten öğrendiğiniz şablonlar hakkında daha fazla bilgi edinmek için, [DotNet yeni makale Için özel şablonlar](../tools/custom-templates.md) bölümüne bakın.

* [DotNet/şablon oluşturma GitHub deposu wiki](https://github.com/dotnet/templating/wiki)
* [DotNet/DotNet-şablon-örnek GitHub deposu](https://github.com/dotnet/dotnet-template-samples)
* [JSON Şema deposunda *Template. JSON* şeması](http://json.schemastore.org/template)
