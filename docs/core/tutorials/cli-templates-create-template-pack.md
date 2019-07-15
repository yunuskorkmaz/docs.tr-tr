---
title: Dotnet için bir şablon paketi Yeni Oluştur
description: Dotnet yeni bir komut için bir şablon paketi oluşturacak bir csproj dosyasının nasıl oluşturulacağını öğrenin.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: df8c33856195ba7feacd32203e4a885997b50ad2
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877185"
---
# <a name="tutorial-create-a-template-pack"></a>Öğretici: Bir şablon paketi oluşturma

.NET Core ile oluşturabilir ve projeleri, dosyaları, kaynaklar oluşturmak şablonlar dağıtın. Bu öğretici oluşan oluşturmak, yüklemek ve kaldırmak, şablonları ile kullanılmak öğretir bir serinin üçüncü bölümüdür `dotnet new` komutu.

Serisinin bu bölümünde şunları öğrenirsiniz nasıl yapılır:

> [!div class="checklist"]
> * Bir şablon paketi oluşturmak için _.csproj* proje oluşturma
> * Paket için proje dosyasını yapılandırın
> * NuGet paket dosyasından bir şablonu yükleyin
> * Paket kimliğiyle bir şablonu Kaldır

## <a name="prerequisites"></a>Önkoşullar

* Tam [bölüm 1](cli-templates-create-item-template.md) ve [2. bölüm](cli-templates-create-project-template.md) Bu öğretici serisinin.

  Bu öğreticide, bu öğreticinin ilk iki bölümlerinde oluşturulan iki şablon kullanılır. Şablon olarak bir klasöre kopyalamanız sürece farklı bir şablon kullanabilirsiniz mümkündür _working\templates\\_  klasör.

* Bir terminal açın ve gidin _working\templates\\_  klasör.

## <a name="create-a-template-pack-project"></a>Bir şablon paketi projesi oluşturun

Şablon dosyası şeklinde bir veya daha fazla şablon paketidir. Yüklediğinizde veya bir paketi kaldırın, tüm şablonları paketinde eklendiğinde veya kaldırıldığında, sırasıyla. Bu öğretici serisinin önceki bölümlerini yalnızca bireysel şablonlarıyla birlikte çalıştı. Dolu olmayan bir şablon paylaşmak için şablonu klasörüne kopyalayıp bu klasöre yüklemek sahip. Çünkü bir şablon paketi birden fazla şablon içinde olabilir ve tek bir dosya paylaşımı daha kolay olur.

Şablon paketleri, bir NuGet paketi tarafından temsil edilir ( _.nupkg_) dosyası. Ayrıca, herhangi bir NuGet paketi gibi bir NuGet akışı için bir şablon paketi karşıya yükleyebilirsiniz. `dotnet new -i` Komut akış NuGet paketinden şablon paketi yüklemeyi destekler. Ayrıca, bir şablon paketini yükleyebilirsiniz. bir _.nupkg_ doğrudan dosya.

Normalde kullandığınız bir C# Kodu derlemek ve bir ikili oluşturmak için proje dosyası. Ancak, projeyi bir şablon paketi oluşturmak için de kullanılabilir. Ayarlarını değiştirerek _.csproj_, herhangi bir kod derlemesini önlemek ve bunun yerine şablonlarınızın kaynakları olarak tüm varlıkları içerir. Bu proje oluşturulurken bir şablon paketi NuGet paketi oluşturur.

Oluşturduğunuz paketi içerecektir [öğe şablonu](cli-templates-create-item-template.md) ve [paketi şablonu](cli-templates-create-project-template.md) önceden oluşturulmuş. Şu iki şablonlara gruplandırılmış çünkü _working\templates\\_  kullanabiliriz klasöründe _çalışma_ klasör _.csproj_ dosya.

Terminalinizde gidin _çalışma_ klasör. Yeni proje oluşturma ve kümesinin adı `templatepack` ve geçerli klasörle çıkış klasörü.

```console
dotnet new console -n templatepack -o .
```

`-n` Parametre kümeleri _.csproj_ dosya adına _templatepack.csproj_ ve `-o` parametreleri geçerli dizinde dosyaları oluşturur. Aşağıdaki çıktıya benzer bir sonuç görmeniz gerekir.

```console
C:\working> dotnet new console -n templatepack -o .
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

Ardından, açık _templatepack.csproj_ dosya sık kullandığınız düzenleyicinizde ve içeriği aşağıdaki XML ile değiştirin:

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

`<PropertyGroup>` Yukarıdaki XML ayarlarında üç gruplar halinde ayrılmış. İlk grup, bir NuGet paketi için gerekli özellikleri ile ilgilenir. Üç `<Package` ile NuGet paketinizi üzerinde bir NuGet akışı tanımlamak için özellikleri paketlemek ayarlara sahip. Özellikle `<PacakgeId>` değeri bir dizin yolu yerine tek bir ada sahip bir şablon paketi kaldırmak için kullanılır. Ayrıca, bir NuGet akışı tarafından bir şablon paketi yüklemek için de kullanılabilir. Diğer ayarlar gibi `<Title>` ve `<Tags>` NuGet üzerinde görüntülenen meta verilerle akışa sahip. NuGet ayarları hakkında daha fazla bilgi için bkz. [NuGet ve MSBuild özellikleri](/nuget/reference/msbuild-targets).

`<TargetFramework>` Derlemek ve proje paketi için paketi komutu çalıştırdığınızda MSBuild düzgün şekilde çalışması ayarı ayarlanmalıdır.

Son üç ayarları oluşturulduğunda, proje düzgün uygun NuGet klasöründe şablonları içerecek şekilde yapılandırarak paketi gerekir.

`<ItemGroup>` İki ayarlarını içerir. İlk olarak, `<Content>` ayarı her şeyi içeren _şablonları_ klasör içeriği. Ayrıca tüm hariç tutmak için ayarlanmış _bin_ klasör veya _obj_ herhangi önlemek için klasör derlenmiş kod (test ve şablonlarınızı derlenmiş varsa) dahil olan. İkinci olarak, `<Compile>` ayarı derlenmesini bulundukları fark etmeksizin tüm kod dosyaları hariç tutar. Bu ayar, kodu derlemek çalışan bir şablon paketi oluşturmak için kullanılan proje engeller _şablonları_ klasör hiyerarşisi.

## <a name="build-and-install"></a>Derleme ve yükleme

Bu dosyayı kaydedin ve ardından Paketi komutu çalıştırın

```console
dotnet pack
```

Bu komut, projeyi oluşturun ve bu pakette olmalıdır bir NuGet oluşturma _working\bin\Debug_ klasör.

```console
C:\working> dotnet pack
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

Ardından, şablon paketi dosyasını yükleyin `dotnet new -i PATH_TO_NUPKG_FILE` komutu.

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

NuGet paketi için bir NuGet akışı karşıya yüklediyseniz, kullanabileceğiniz `dotnet new -i PACKAGEID` komut nerede `PACKAGEID` aynı `<PackageId>` ayarını _.csproj_ dosya. Bu paket kimliği, NuGet paket tanımlayıcısı ile aynıdır.

## <a name="uninstall-the-template-pack"></a>Şablon paketi kaldırma

Şablon paketi, ile nasıl yüklediğiniz ne olursa olsun _.nupkg_ dosyası doğrudan veya NuGet akışı, bir şablon paketi kaldırma aynıdır. Kullanım `<PackageId>` kaldırmak istediğiniz şablonu. Çalıştırarak yüklü şablonları listesini alabilirsiniz `dotnet new -u` komutu.

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

Çalıştırma `dotnet new -u AdatumCorporation.Utility.Templates` şablonu kaldırmak için. `dotnet new` Komut önceden yüklenmiş şablonlar atlamak Yardım bilgilerini çıktısı.

Tebrikler! yüklemiş ve bir şablon paketi kaldırıldı. 

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla şablonları hakkında en zaten hangisinin öğrendiğinize göre bilgi edinmek için [yeni dotnet için özel şablonları](../tools/custom-templates.md) makalesi.

* [DotNet/şablon GitHub deposunu Wiki](https://github.com/dotnet/templating/wiki)
* [DotNet/dotnet-şablonu-örnekleri GitHub deposu](https://github.com/dotnet/dotnet-template-samples)
* [*Template.JSON* JSON şema Store şema](http://json.schemastore.org/template)
