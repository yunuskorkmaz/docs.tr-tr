---
title: Yeni dotnet için proje şablonu oluşturma
description: Dotnet yeni bir komut için bir proje şablonu oluşturmayı öğrenin.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 31a6189c0126d6dff000bb84978c1527dbe4e2ae
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877182"
---
# <a name="tutorial-create-a-project-template"></a>Öğretici: Bir proje şablonu oluşturma

.NET Core ile oluşturabilir ve projeleri, dosyaları, kaynaklar oluşturmak şablonlar dağıtın. Bu öğreticide iki oluşturmak, yüklemek ve kaldırmak, şablonları ile kullanılmak öğretir serinin bir parçasıdır `dotnet new` komutu.

Serisinin bu bölümünde şunları öğrenirsiniz nasıl yapılır:

> [!div class="checklist"]
> * Kaynak bir proje şablonu oluşturma
> * Şablon yapılandırma klasör ve dosya oluşturma
> * Bir şablon bir dosya yolundan yükle
> * Öğe şablonu test
> * Öğe şablonu Kaldır

## <a name="prerequisites"></a>Önkoşullar

* Tam [bölüm 1](cli-templates-create-item-template.md) Bu öğretici serisinin.
* Bir terminal açın ve gidin _working\templates\\_  klasör.

## <a name="create-a-project-template"></a>Bir proje şablonu oluşturma

Kullanıcılar için başlamak kolaylaştırır proje şablonları üretim çalıştırılmaya hazır projeleri çalışan kodu ayarlayın. .NET core konsol uygulaması veya bir sınıf kitaplığı gibi birkaç proje şablonlarını içerir. Bu örnekte, sağlayan yeni bir konsol projesi oluşturacaksınız C# 8.0 ve oluşturan bir `async main` giriş noktası.

Terminalinizde gidin _working\templates\\_  klasör adında yeni bir alt klasör oluşturup _consoleasync_. Alt klasörü girin ve çalıştırma `dotnet new console` standart konsol uygulaması oluşturmak için. Yeni bir şablon oluşturmak için bu şablonu tarafından üretilen dosyaları düzenleme.

```console
working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs
```

## <a name="modify-programcs"></a>Program.cs değiştirme

Açık yukarı _program.cs_ dosya. Konsol projesi değil, bir zaman uyumsuz bir giriş noktası kullanın, bu nedenle şimdi ekleyin. Kodunuz şu şekilde değiştirin ve dosyayı kaydedin:

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

## <a name="modify-consoleasynccsproj"></a>Consoleasync.csproj değiştirme

Güncelleştirelim C# projenin kullandığı sürüm 8.0 Dil sürümü. Düzen _consoleasync.csproj_ dosya ve ekleme `<LangVersion>` ayarını bir `<PropertyGroup>` düğümü.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.2</TargetFramework>

    <LangVersion>8.0</LangVersion>

  </PropertyGroup>
  
</Project>
```

## <a name="build-the-project"></a>Proje derleme

Bir proje şablonu tamamlamadan önce bu şekilde sıkışmalı ve emin olmak için sınamalısınız. Terminalinizde çalıştırma `dotnet run` komutunu aşağıdaki çıktıyı görmelisiniz:

```console
C:\working\templates\consoleasync> dotnet run
Hello World with C# 8.0!
```

Silebilirsiniz _obj_ ve _bin_ kullanılarak oluşturulan klasörleri `dotnet run`. Bu dosyaların silinmesi, şablonunuzu şablonunuza ilgili dosyaları ve hiçbir dosyaları yalnızca içeren bir derleme eylemi sonucunda ortaya çıkan sağlar.

Oluşturduğunuz şablonu içeriğini olduğuna göre şablon yapılandırması şablonunun Kök klasörde oluşturmanız gerekir.

## <a name="create-the-template-config"></a>Şablon yapılandırması oluşturma

Şablonlar, .NET core'da şablonunuzun kök dizininde mevcut özel bir klasör ve yapılandırma dosyasında tarafından tanınır. Bu öğreticide, şu şablonu klasörünüze konumdadır _working\templates\consoleasync\\_ .

Bir şablonu oluşturduğunuzda, tüm dosya ve klasörlerin şablon klasöründe özel yapılandırma klasörü dışında şablonun parçası olarak dahil edilir. Bu yapılandırma klasörü adlı _. template.config_.

İlk olarak, adlı yeni bir alt klasör oluşturun _. template.config_, girin. Adlı yeni bir dosya oluşturup _template.json_. Klasör yapınız gibi görünmelidir:

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

Açık _template.json_ , sık kullandığınız metin düzenleyicisi ve Yapıştır aşağıdaki JSON kod ve kaydedin:

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

Bu yapılandırma dosyası, tüm ayarlarını şablonunuz için içerir. Gördüğünüz gibi temel ayarlar `name` ve `shortName` ayrıca yoktur ancak bir `tags/type` ayarlanan değer `project`. Bu şablon proje şablonu olarak belirler. Oluşturduğunuz şablonun türüyle ilgili bir kısıtlama yoktur. `item` Ve `project` değerler için yaygın olarak kullanılan adları .NET Core önerir ve böylece kullanıcılar bunlar aramakta olduğunuz şablon türü kolayca filtre uygulayabilirsiniz.

`classifications` Öğesini temsil eder **etiketleri** gördüğünüz çalıştırdığınızda sütun `dotnet new` ve şablon listesini alın. Kullanıcılar ayrıca arayabilirler tabanlı sınıflandırma etiketleri. Karıştırmayın `tags` özelliği ile json dosyasındaki `classifications` Etiketler listesi. Ne yazık ki benzer şekilde adlı iki terimin farklı anlamlara oldukları. İçin tam şema *template.json* dosya konumunda bulundu [JSON şema Store](http://json.schemastore.org/template). Hakkında daha fazla bilgi için *template.json* bkz [dotnet şablon wiki](https://github.com/dotnet/templating/wiki).

Geçerli bir sahip olduğunuza göre _.template.config/template.json_ dosya, şablonunuzu yüklenmeye hazır. Şablon yüklemeden önce herhangi bir ek dosya, klasör ve istemediğiniz dosyaları gibi şablonunuzda dahil sildiğinizden emin olun _bin_ veya _obj_ klasörleri. Terminalinizde gidin _consoleasync_ klasör ve çalışma `dotnet new -i .\` geçerli klasöründe şablonunu yüklemek için. Bir Linux veya Mac OS x işletim sistemi kullanıyorsanız, eğik çizgi kullanın: `dotnet new -i ./`.

Bu komut sizin kapsamalıdır yüklü şablonlar listesinden çıkarır.

```console
C:\working\templates\consoleasync> dotnet new -i .\
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

### <a name="test-the-project-template"></a>Test projesi şablonu

Yüklü bir öğe şablonunu olduğuna göre test edin. Gidin _test_ klasörü ile yeni bir konsol uygulaması oluşturup `dotnet new console`. Bu, kolayca test ile bir çalışma projenin oluşturduğu `dotnet run` komutu.

```console
C:\test> dotnet new consoleasync
The template "Example templates: async project" was created successfully.
```

```console
C:\test> dotnet run
Hello World with C# 8.0!
```

Tebrikler! Oluşturduğunuz ve .NET Core proje şablonu dağıtılır. Bu öğretici serisinin bir sonraki bölümü için hazırlanırken oluşturduğunuz şablonu kaldırmanız gerekir. Tüm dosyaları silmek istediğinizden emin olun _test_ klasörü çok. Bununla geri temiz bir duruma hazır için bu öğreticinin sonraki ana bölüme sahip olursunuz.

### <a name="uninstall-the-template"></a>Şablonu Kaldır

Bir dosya yolu kullanarak şablon yüklü olduğundan, birlikte kaldırmalısınız **mutlak** dosya yolu. Çalıştırarak yüklü şablonlar listesi gördüğünüz `dotnet new -u` komutu. Şablonunuzu son listelenmelidir. Yolun listelenen şablonunuzla birlikte kaldırmak için kullanımı `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` komutu.

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
  C:\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
```

```console
C:\working> dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir proje şablonu oluşturuldu. Öğe ve proje şablonlarının bir kolayca kullanıma dosyasına paketini öğrenmek için Bu öğretici serisine devam edin.

> [!div class="nextstepaction"]
> [Bir şablon paketi oluşturma](cli-templates-create-template-pack.md)
