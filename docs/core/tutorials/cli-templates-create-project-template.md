---
title: dotnet yeni için bir proje şablonu oluşturma
description: dotnet yeni komutu için proje şablonu oluşturmayı öğrenin.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: f53f4037f832265a35f65bf2e5096c7e5a37bcf1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503527"
---
# <a name="tutorial-create-a-project-template"></a>Öğretici: Proje şablonu oluşturma

.NET Core ile, projeler, dosyalar ve hatta kaynaklar oluşturan şablonlar oluşturabilir ve dağıtabilirsiniz. Bu öğretici, `dotnet new` komutla birlikte kullanılmak üzere şablonoluşturma, yükleme ve kaldırma yı öğreten bir serinin ikinci bölümüdür.

Serinin bu bölümünde nasıl öğreneceksiniz:

> [!div class="checklist"]
>
> * Proje şablonunun kaynaklarını oluşturma
> * Şablon config klasörünü ve dosyasını oluşturma
> * Dosya yolundan şablon yükleme
> * Öğe şablonu test edin
> * Öğe şablonu kaldırma

## <a name="prerequisites"></a>Önkoşullar

* Bu öğretici serisinin tam [bölüm 1.](cli-templates-create-item-template.md)
* Bir terminal açın ve _çalışma\şablonlar_ klasörüne gidin.

## <a name="create-a-project-template"></a>Proje şablonu oluşturma

Proje şablonları, kullanıcıların çalışan bir kod kümesiyle başlamasını kolaylaştıran çalışmaya hazır projeler üretir. .NET Core, konsol uygulaması veya sınıf kitaplığı gibi birkaç proje şablonu içerir. Bu örnekte, C# 8.0'ı etkinleştiren ve bir giriş `async main` noktası üreten yeni bir konsol projesi oluşturursunuz.

Terminalinizde, _çalışma\şablonlar_ klasörüne gidin ve _consoleasync_adında yeni bir alt klasör oluşturun. Alt klasörü girin `dotnet new console` ve standart konsol uygulamasını oluşturmak için çalıştırın. Yeni bir şablon oluşturmak için bu şablon tarafından üretilen dosyaları düzenlersiniz.

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a>Program.cs değiştirin

_program.cs_ dosyasını açın. Konsol projesi nde eşzamanlı giriş noktası yok, o yüzden bunu ekleyelim. Kodunuzu aşağıdakiyle değiştirin ve dosyayı kaydedin.

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

## <a name="modify-consoleasynccsproj"></a>consoleasync.csproj değiştir

Projenin kullandığı C# dil sürümünü sürüm 8.0 olarak güncelleyelim. _Consoleasync.csproj_ dosyasını edin `<LangVersion>` ve ayarı bir `<PropertyGroup>` düğüme ekleyin.

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

Proje şablonu tamamlanmadan önce, doğru çalıştığından ve çalıştığından emin olmak için bu şablonu sınamalısınız.

Terminalinizde aşağıdaki komutu çalıştırın.

```dotnetcli
dotnet run
```

Aşağıdaki çıktıyı alırsınız.

```console
Hello World with C# 8.0!
```

Kullanarak oluşturulan _obj_ ve _bin_ klasörlerini `dotnet run`silebilirsiniz. Bu dosyaları silerken, şablonunuzun yalnızca şablonunuzla ilgili dosyaları içermesini ve bir yapı eyleminin sonucu olan dosyaları içermemesini sağlar.

Oluşturulan şablonun içeriğine sahip olduğunuza göre, şablonun kök klasöründe şablon config'ini oluşturmanız gerekir.

## <a name="create-the-template-config"></a>Şablon config oluşturma

Şablonlar .NET Core'da şablonunuzun kökünde bulunan özel bir klasör ve config dosyası tarafından tanınır. Bu öğreticide, şablon klasörünüz _çalışma\templates\consoleasync_adresinde bulunur.

Bir şablon oluşturduğunuzda, şablon klasöründeki tüm dosya ve klasörler özel config klasörü dışında şablonun bir parçası olarak dahil edilir. Bu config klasörü _.template.config_olarak adlandırılır.

İlk olarak, _.template.config_adlı yeni bir alt klasör oluşturun, girin. Ardından, _template.json_adında yeni bir dosya oluşturun. Klasör yapınız şu şekilde görünmelidir.

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

En sevdiğiniz metin düzenleyicisi ile _template.json'u_ açın ve aşağıdaki json koduna yapıştırın ve kaydedin.

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

Bu config dosyası, şablonunuzun tüm ayarlarını içerir. Temel ayarları görebilirsiniz `name` ve `shortName` aynı zamanda `tags/type` `project`'' için ayarlanmış bir değer de vardır. Bu, şablonunuzu proje şablonu olarak belirtir. Oluşturduğunuz şablon türünde herhangi bir kısıtlama yoktur. Ve `item` `project` değerler, kullanıcıların aradıkları şablon türünü kolayca filtreleyebilmeleri için .NET Core'un önerdiği ortak adlardır.

Öğe, `classifications` çalıştırdığınızda `dotnet new` ve şablonların listesini aldığınızda gördüğünüz **etiketler** sütununa temsil eder. Kullanıcılar sınıflandırma etiketlerine göre de arama yapabilir. Json dosyasındaki `tags` özelliği `classifications` etiket listesiyle karıştırmayın. Ne yazık ki benzer adlı iki farklı şey konum. *template.json* dosyası için tam şema [JSON Schema Store'da](http://json.schemastore.org/template)bulunur. *template.json* dosyası hakkında daha fazla bilgi [için, dotnet templating wiki](https://github.com/dotnet/templating/wiki)bakın.

Artık geçerli bir _.template.config/template.json_ dosyanız olduğuna göre, şablonunuz yüklenmeye hazırdır. Şablonu yüklemeden önce, şablonunuza dahil olmasını istemediğiniz ek dosya klasörlerini ve dosyalarını _(depo gözü_ veya _obj_ klasörleri) sildiğinizden emin olun. Terminalinizde, _consoleasync_ klasörüne gidin `dotnet new -i .\` ve geçerli klasörde bulunan şablonu yüklemek için çalıştırın. Linux veya macOS işletim sistemi kullanıyorsanız, ileri eğik `dotnet new -i ./`çizgi kullanın: .

Bu komut, sizinkini içermesi gereken yüklü şablonlar listesini çıkartır.

```dotnetcli
dotnet new -i .\
```

Aşağıdakine benzer çıktı alırsınız.

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

### <a name="test-the-project-template"></a>Proje şablonu test edin

Artık yüklü bir öğe şablonu var, test edin.

1. _Test_ klasörüne gidin

1. Komutu ile kolayca test edebilirsiniz çalışan bir proje oluşturur aşağıdaki `dotnet run` komutu ile yeni bir konsol uygulaması oluşturun.

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

Tebrikler! .NET Core ile bir proje şablonu oluşturdunuz ve dağıttınız. Bu öğretici serinin bir sonraki bölümüne hazırlık olarak, oluşturduğunuz şablonu kaldırmanız gerekir. Test klasöründeki tüm _test_ dosyaları da sildiğinizden emin olun. Bu, bu öğreticinin bir sonraki ana bölümü için hazır temiz bir duruma geri dönecektir.

### <a name="uninstall-the-template"></a>Şablonu kaldırma

Şablonu bir dosya yolu kullanarak yüklediğiniz için, şablonu **mutlak** dosya yolu ile kaldırmanız gerekir. `dotnet new -u` Komutu çalıştırarak yüklenen şablonların listesini görebilirsiniz. Şablonunuzun en son listelenmesi gerekir. Komutla `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` şablonunuzu kaldırmak için listelenen yolu kullanın.

```dotnetcli
dotnet new -u
```

Aşağıdakine benzer çıktı alırsınız.

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

Şablonu kaldırmak için aşağıdaki komutu çalıştırın.

```dotnetcli
dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir proje şablonu oluşturdunuz. Hem öğeyi hem de proje şablonlarını kullanımı kolay bir dosyaya nasıl paketlendireceklerini öğrenmek için bu öğretici seriye devam edin.

> [!div class="nextstepaction"]
> [Şablon paketi oluşturma](cli-templates-create-template-pack.md)
