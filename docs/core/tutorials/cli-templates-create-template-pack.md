---
title: dotnet yeni için bir şablon paketi oluşturma
description: Dotnet yeni komutu için bir şablon paketi oluşturacak bir csproj dosyası oluşturmayı öğrenin.
author: thraka
ms.date: 12/10/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5bc926861dd6a501d7c2d24bd5f7c4116cc78b2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503496"
---
# <a name="tutorial-create-a-template-pack"></a>Öğretici: Şablon paketi oluşturma

.NET Core ile, projeler, dosyalar ve hatta kaynaklar oluşturan şablonlar oluşturabilir ve dağıtabilirsiniz. Bu öğretici, `dotnet new` komutla birlikte kullanmak üzere şablonoluşturma, yükleme ve kaldırma yı öğreten bir serinin üçüncü bölümüdür.

Serinin bu bölümünde nasıl öğreneceksiniz:

> [!div class="checklist"]
>
> * Şablon \*paketi oluşturmak için .csproj projesi oluşturma
> * Paketleme için proje dosyasını yapılandırma
> * NuGet paket dosyasından şablon yükleme
> * Şablonu paket kimliğine göre kaldırma

## <a name="prerequisites"></a>Önkoşullar

* Bu öğretici serisinin [bölüm 1](cli-templates-create-item-template.md) ve [bölüm 2](cli-templates-create-project-template.md) tamamlayın.

  Bu öğretici, bu öğreticinin ilk iki parçasında oluşturulan iki şablonu kullanır. Şablonu klasör olarak kopyaladığınız sürece farklı bir şablon _kullanabilirsiniz.\\ _

* Bir terminal açın ve _\\ çalışma_ klasörüne gidin.

## <a name="create-a-template-pack-project"></a>Şablon paketi projesi oluşturma

Şablon paketi, dosyaya paketlenmiş bir veya daha fazla şablondur. Bir paketi yüklediğinizde veya kaldırdığınızda, pakette bulunan tüm şablonlar sırasıyla eklenir veya kaldırılır. Bu öğretici serinin önceki bölümleri yalnızca tek tek şablonlarla çalıştı. Paketlenmemiş bir şablonu paylaşmak için şablon klasörünü kopyalamanız ve bu klasör üzerinden yüklemeniz gerekir. Şablon paketinde birden fazla şablon olabileceğinden ve tek bir dosya olduğundan, paylaşmak daha kolaydır.

Şablon paketleri nuget paketi (_.nupkg_) dosyası yla temsil edilir. Ayrıca, herhangi bir NuGet paketi gibi, şablon paketini bir NuGet akışına yükleyebilirsiniz. Komut, `dotnet new -i` NuGet paket akışından şablon paketi yüklemeyi destekler. Ayrıca, bir _.nupkg_ dosyasından doğrudan bir şablon paketi yükleyebilirsiniz.

Normalde kod derlemek ve ikili oluşturmak için bir C# proje dosyası kullanırsınız. Ancak, proje bir şablon paketi oluşturmak için de kullanılabilir. _.csproj'un_ayarlarını değiştirerek, kodu derlemesini engelleyebilir ve bunun yerine şablonlarınızın tüm varlıklarını kaynak olarak ekleyebilirsiniz. Bu proje oluşturulduğunda, bir şablon paketi NuGet paketi üretir.

Oluşturacağınız paket, daha önce oluşturulmuş [öğe şablonu](cli-templates-create-item-template.md) ve [paket şablonuna](cli-templates-create-project-template.md) dahil olur. İki şablonu _çalışma\şablonlar\\ _ klasöründe gruplandırdığımız için _,.csproj_ dosyasının _çalışma_ klasörünü kullanabiliriz.

Terminalinizde, _çalışma_ klasörüne gidin. Yeni bir proje oluşturun ve `templatepack` adı ve çıktı klasörünü geçerli klasöre ayarlayın.

```dotnetcli
dotnet new console -n templatepack -o .
```

Parametre `-n` _.csproj_ dosya adını _templatepack.csproj_olarak ayarlar. Parametre `-o` geçerli dizindeki dosyaları oluşturur. Aşağıdaki çıktıya benzer bir sonuç görmeniz gerekir.

```dotnetcli
dotnet new console -n templatepack -o .
```

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

Ardından, en sevdiğiniz düzenleyicide _templatepack.csproj_ dosyasını açın ve içeriği aşağıdaki XML ile değiştirin:

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

Yukarıdaki `<PropertyGroup>` XML'deki ayarlar üç gruba ayrılır. İlk grup, NuGet paketi için gerekli özelliklerle ilgilenir. Üç `<Package` ayar, paketinizi NuGet akışında tanımlamak için NuGet paket özellikleriyle ilgilidir. Özellikle `<PackageId>` değer, dizin yolu yerine tek bir adla şablon paketini kaldırmak için kullanılır. NuGet akışından şablon paketini yüklemek için de kullanılabilir. NuGet akışında `<Title>` `<PackageTags>` görüntülenen meta veriler gibi kalan ayarlar ve ilgili. NuGet ayarları hakkında daha fazla bilgi için [NuGet ve MSBuild özelliklerine](/nuget/reference/msbuild-targets)bakın.

Ayarı, `<TargetFramework>` projeyi derlemek ve paketlemek için paket komutunu çalıştırdığınızda MSBuild'in düzgün çalışacak şekilde ayarlanması gerekir.

Son üç ayar, oluşturulduğunda şablonları NuGet paketindeki uygun klasöre eklemek için projeyi doğru şekilde yapılandırmakile ilgilidir.

İki `<ItemGroup>` ayar içerir. Ayar, `<Content>` _şablonlar_ klasöründeki her şeyi içerik olarak içerir. Ayrıca, derlenmiş herhangi bir kodun (şablonlarınızı test ettiyseniz ve derlediyseniz) eklenmesini önlemek için herhangi bir _depo kutusu_ klasörünü veya _obj_ klasörünü hariç tutmak için ayarlanmıştır. İkinci olarak, `<Compile>` ayar, nerede olurlarsa olsunlar tüm kod dosyalarının derlemisini hariç tutar. Bu ayar, şablon paketi oluşturmak için kullanılan projenin _şablonlar_ klasörü hiyerarşisinde kodu derlemeye çalışmasına engel lenir.

## <a name="build-and-install"></a>Oluşturma ve yükleme

Bu dosyayı kaydedin ve paket komutunu çalıştırın

```dotnetcli
dotnet pack
```

Bu komut projenizi oluşturur ve bu _çalışma\bin\Hata Ayıklama_ klasöründe bir NuGet paketi oluşturur.

```dotnetcli
dotnet pack
```

```console
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

Ardından, şablon paketi dosyasını `dotnet new -i PATH_TO_NUPKG_FILE` komutla yükleyin.

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

NuGet paketini nuget akışına yüklediyseniz, `dotnet new -i PACKAGEID` _.csproj_ dosyasındaki `<PackageId>` ayarla aynı olan `PACKAGEID` komutu kullanabilirsiniz. Bu paket kimliği NuGet paket tanımlayıcısı ile aynıdır.

## <a name="uninstall-the-template-pack"></a>Şablon paketini kaldırma

Şablon paketini doğrudan _.nupkg_ dosyasıyla veya NuGet akışıyla nasıl yüklediğinizönemli olursa olsun, şablon paketini kaldırmak aynıdır. Kaldırmak `<PackageId>` istediğiniz şablonun kullanın. `dotnet new -u` Komutu çalıştırarak yüklenen şablonların bir listesini alabilirsiniz.

```dotnetcli
dotnet new -u
```

```console
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

Şablonu kaldırmak için çalıştırın. `dotnet new -u AdatumCorporation.Utility.Templates` Komut, `dotnet new` daha önce yüklediğiniz şablonları atlayacak yardım bilgilerini çıktıracaktır.

Tebrikler! bir şablon paketi yüklemiş ve kaldırmışsınız.

## <a name="next-steps"></a>Sonraki adımlar

Çoğu zaten öğrenmiş olduğunuz şablonlar hakkında daha fazla bilgi edinmek [için dotnet yeni](../tools/custom-templates.md) makalesi için Özel şablonlara bakın.

* [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki)
* [dotnet/dotnet-şablon-örnekleri GitHub repo](https://github.com/dotnet/dotnet-template-samples)
* [json Schema Mağazası'nda *template.json* şema](http://json.schemastore.org/template)
