---
title: DotNet New için bir proje şablonu oluşturun
description: DotNet New komutu için bir proje şablonu oluşturmayı öğrenin.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: f53f4037f832265a35f65bf2e5096c7e5a37bcf1
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503527"
---
# <a name="tutorial-create-a-project-template"></a>Öğretici: proje şablonu oluşturma

.NET Core ile projeler, dosyalar, hatta kaynaklar üreten şablonlar oluşturabilir ve dağıtabilirsiniz. Bu öğretici, `dotnet new` komutuyla kullanılmak üzere şablonlar oluşturmayı, yüklemeyi ve kaldırmayı öğretir.

Serinin bu bölümünde şunları nasıl yapacağınızı öğreneceksiniz:

> [!div class="checklist"]
>
> * Proje şablonunun kaynaklarını oluşturma
> * Şablon yapılandırma klasörünü ve dosyasını oluşturma
> * Dosya yolundan şablon yükler
> * Bir öğe şablonunu test etme
> * Öğe şablonunu kaldırma

## <a name="prerequisites"></a>Önkoşullar

* Bu öğretici serisinin [1. bölümünü](cli-templates-create-item-template.md) doldurun.
* Bir Terminal açın ve _working\templates_ klasörüne gidin.

## <a name="create-a-project-template"></a>Proje şablonu oluşturma

Proje şablonları, kullanıcıların çalışan bir kod kümesiyle başlamasını kolaylaştıran, çalıştırmaya yönelik olarak çalışan projeler oluşturur. .NET Core, konsol uygulaması veya sınıf kitaplığı gibi bazı proje şablonları içerir. Bu örnekte, 8,0 sağlayan C# ve bir `async main` giriş noktası üreten yeni bir konsol projesi oluşturacaksınız.

Terminalinizde, _working\templates_ klasörüne gidin ve _consoleasync_adlı yeni bir alt klasör oluşturun. Standart konsol uygulamasını oluşturmak için alt klasörü girin ve `dotnet new console` çalıştırın. Bu şablon tarafından oluşturulan dosyaları düzenleyerek yeni bir şablon oluşturabilirsiniz.

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a>Program.cs Değiştir

_Program.cs_ dosyasını açın. Konsol projesi zaman uyumsuz bir giriş noktası kullanmaz, bu nedenle bunu ekleyelim. Kodunuzu aşağıdaki şekilde değiştirin ve dosyayı kaydedin.

```csharp
using System;
using System.Threading.Tasks;

namespace consoleasync
{
    class Program
    {
        static async Task Main(string[] args)
        {
            await Console.Out.WriteAsync("Hello World with C# 8.0!");
        }
    }
}
```

## <a name="modify-consoleasynccsproj"></a>Consoleasync. csproj öğesini Değiştir

Projenin 8,0 sürümünü kullandığı C# dil sürümünü güncelleştirelim. _Consoleasync. csproj_ dosyasını düzenleyin ve `<PropertyGroup>` düğümüne `<LangVersion>` ayarını ekleyin.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a>Projeyi derleme

Bir proje şablonunu tamamlamadan önce, derlendiğinden ve düzgün çalıştığından emin olmak için test etmeniz gerekir.

Terminalinizde aşağıdaki komutu çalıştırın.

```dotnetcli
dotnet run
```

Aşağıdaki çıktıyı alırsınız.

```console
Hello World with C# 8.0!
```

`dotnet run`kullanarak oluşturulan _obj_ ve _bin_ klasörlerini silebilirsiniz. Bu dosyaların silinmesi, şablonunuzun yalnızca şablonlarınız ile ilgili dosyaları ve bir yapı eylemi sonucu olan dosyaları içerip içermemesini sağlar.

Artık oluşturulan şablonun içeriğine sahip olduğunuza göre, şablonun kök klasöründe şablon yapılandırmasını oluşturmanız gerekir.

## <a name="create-the-template-config"></a>Şablon yapılandırması oluşturma

Şablonlar, .NET Core 'da şablonunuzun kökünde bulunan özel bir klasör ve yapılandırma dosyası tarafından tanınır. Bu öğreticide, şablon klasörünüz _working\templates\consoleasync_adresinde bulunur.

Bir şablon oluşturduğunuzda, şablon klasöründeki tüm dosyalar ve klasörler, özel yapılandırma klasörü hariç, şablonun bir parçası olarak dahil edilir. Bu yapılandırma klasörü _. Template. config_olarak adlandırılır.

İlk olarak, _. Template. config_adlı yeni bir alt klasör oluşturun, bunu girin. Ardından, _Template. JSON_adlı yeni bir dosya oluşturun. Klasör yapınız şöyle görünmelidir.

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

En sevdiğiniz metin düzenleyicinizle _Template. JSON_ ' i açın ve aşağıdaki JSON kodunu yapıştırın ve kaydedin.

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Console", "C#8" ],
  "identity": "ExampleTemplate.AsyncProject",
  "name": "Example templates: async project",
  "shortName": "consoleasync",
  "tags": {
    "language": "C#",
    "type": "project"
  }
}
```

Bu yapılandırma dosyası şablonunuz için tüm ayarları içerir. `name` ve `shortName` gibi temel ayarları görebilir, ancak `project`olarak ayarlanmış bir `tags/type` değeri de vardır. Bu, şablonunuzu bir proje şablonu olarak belirler. Oluşturduğunuz şablon türü üzerinde hiçbir kısıtlama yoktur. `item` ve `project` değerleri, .NET Core 'un arama yapmakta oldukları şablonun türünü kolayca filtreleyebilmesi için .NET Core 'un önerdiği yaygın adlardır.

`classifications` öğesi, `dotnet new` çalıştırdığınız ve şablonların bir listesini alacağınız zaman gördüğünüz **Etiketler** sütununu temsil eder. Kullanıcılar ayrıca sınıflandırma etiketlerine göre arama yapabilir. JSON dosyasındaki `tags` özelliğini `classifications` Etiketler listesiyle karıştırmayın. Benzer şekilde adlandırılan iki farklı şey vardır. *Template. JSON* dosyasının tam şeması [JSON Şema deposunda](http://json.schemastore.org/template)bulunur. *Template. JSON* dosyası hakkında daha fazla bilgi için bkz. [DotNet şablon oluşturma wiki](https://github.com/dotnet/templating/wiki).

Artık geçerli bir _. Template. config/Template. JSON_ dosyanız olduğuna göre, şablonunuz yüklenmeye hazırdır. Şablonu yüklemeden önce, _küme_ veya _obj_ klasörleri gibi şablonunuzda yer almasını istemediğiniz ek dosya klasörlerini ve dosyalarını sildiğinizden emin olun. Terminalinizde _consoleasync_ klasörüne gidin ve geçerli klasörde bulunan şablonu yüklemek için `dotnet new -i .\` çalıştırın. Linux veya macOS işletim sistemi kullanıyorsanız, eğik çizgi kullanın: `dotnet new -i ./`.

Bu komut, yüklenmiş şablonların listesini verir ve bunları içermelidir.

```dotnetcli
dotnet new -i .\
```

Aşağıdakine benzer bir çıktı alırsınız.

```console
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

### <a name="test-the-project-template"></a>Proje şablonunu test etme

Artık bir öğe şablonu yükleolduğunuza göre, test edin.

1. _Test_ klasörüne git

1. `dotnet run` komutuyla kolayca test edebileceğiniz, çalışan bir proje üreten aşağıdaki komutla yeni bir konsol uygulaması oluşturun.

    ```dotnetcli
    dotnet new consoleasync
    ```

    Aşağıdaki çıktıyı alırsınız.

    ```console
    The template "Example templates: async project" was created successfully.
    ```

1. Aşağıdaki komutu kullanarak projeyi çalıştırın.

    ```dotnetcli
    dotnet run
    ```

    Aşağıdaki çıktıyı alırsınız.

    ```console
    Hello World with C# 8.0!
    ```

Tebrikler! .NET Core ile bir proje şablonu oluşturdunuz ve dağıttıysanız. Bu öğretici serisinin bir sonraki kısmına hazırlanın, oluşturduğunuz şablonu kaldırmanız gerekir. Tüm dosyaları da _Test_ klasöründen sildiğinizden emin olun. Bu, Bu öğreticinin bir sonraki ana kısmına yönelik temiz bir duruma geri dönebilirsiniz.

### <a name="uninstall-the-template"></a>Şablonu kaldırma

Şablonu bir dosya yolu kullanarak yükletiğinden, **mutlak** dosya yoluyla kaldırmanız gerekir. `dotnet new -u` komutunu çalıştırarak, yüklenmiş şablonların listesini görebilirsiniz. Şablonunuzun son listelenmesi gerekir. `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` komutuyla şablonunuzu kaldırmak için listelenen yolu kullanın.

```dotnetcli
dotnet new -u
```

Aşağıdakine benzer bir çıktı alırsınız.

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
  C:\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
```

Bir şablonu kaldırmak için aşağıdaki komutu çalıştırın.

```dotnetcli
dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide bir proje şablonu oluşturdunuz. Hem öğe hem de proje şablonlarının kullanımı kolay bir dosyaya nasıl paketleyeceğinizi öğrenmek için, bu öğretici serisine devam edin.

> [!div class="nextstepaction"]
> [Şablon paketi oluşturma](cli-templates-create-template-pack.md)
