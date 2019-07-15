---
title: Dotnet için bir öğe şablonunu yeni - .NET Core CLI oluştur
description: Dotnet yeni bir komut için bir öğe şablonu oluşturmayı öğrenin. Öğe şablonları, herhangi bir sayıda dosyaları içerebilir.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: c50aaf413f08c2e4cbe3f8ce8c057e5841067c92
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877179"
---
# <a name="tutorial-create-an-item-template"></a>Öğretici: Öğe şablonu oluşturma

.NET Core ile oluşturabilir ve projeleri, dosyaları, kaynaklar oluşturmak şablonlar dağıtın. Bu öğretici, oluşturmak, yüklemek ve kaldırmak, şablonları ile kullanılmak öğretir bir dizinin birinci bölümüdür `dotnet new` komutu.

Serisinin bu bölümünde şunları öğrenirsiniz nasıl yapılır:

> [!div class="checklist"]
> * Öğe şablonu için bir sınıf oluşturma
> * Şablon yapılandırma klasör ve dosya oluşturma
> * Bir şablon bir dosya yolundan yükle
> * Öğe şablonu test
> * Öğe şablonu Kaldır

## <a name="prerequisites"></a>Önkoşullar

* [.NET core 2.2 SDK](https://www.microsoft.com/net/core) veya sonraki sürümler.
* Başvuru makaleyi okuyun [yeni dotnet için özel şablonları](../tools/custom-templates.md).

  Başvurusu makalesinde, şablonlar ve nasıl bunlar bir araya hakkında temel bilgileri açıklar. Bu bilgilerin bazıları burada reiterated.

* Bir terminal açın ve gidin _working\templates\\_  klasör.

## <a name="create-the-required-folders"></a>Gerekli klasörleri oluşturma

Bu seri, "şablonu kaynak bulunduğu bir çalışma klasörü" ve "şablonlarınızı test etmek için kullanılan bir sınama klasör" kullanır. Çalışma klasörü ve test klasörü aynı üst klasör altında olması gerekir.

İlk olarak, üst klasörü oluşturun, adı önemli değildir. Adlı bir alt klasör oluşturup _çalışma_. İçine _çalışma_ klasöründe adlı bir alt klasör oluşturun _şablonları_.

Ardından, adlı üst klasör altında bir klasör oluşturun _test_. Klasör yapısı aşağıdaki gibi görünmelidir:

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a>Öğe şablonu oluşturma

Öğe şablonu, bir veya daha fazla dosya içeren şablon belirli bir türdür. Bu tür şablon yapılandırma, kod veya çözüm dosyası gibi bir şey oluşturmak istediğinizde kullanışlıdır. Bu örnekte, dize türü için bir uzantı yöntemini ekleyen bir sınıf oluşturacaksınız.

Terminalinizde gidin _working\templates\\_  klasör adında yeni bir alt klasör oluşturup _uzantıları_. Klasörü girin.

```console
working
└───templates
    └───extensions
```

Adlı yeni bir dosya oluşturun _CommonExtensions.cs_ ve sevdiğiniz bir metin düzenleyici ile açın. Bu sınıf adlı bir genişletme yöntemi sağlayacak `Reverse` , bir dizenin içeriklerini tersine çevirir. Aşağıdaki kodu yapıştırın ve dosyayı kaydedin:

```csharp
using System;

namespace System
{
    public static class StringExtensions
    {
        public static string Reverse(this string value)
        {
            var tempArray = value.ToCharArray();
            Array.Reverse(tempArray);
            return new string(tempArray);
        }
    }
}
```

Oluşturduğunuz şablonu içeriğini olduğuna göre şablon yapılandırması şablonunun Kök klasörde oluşturmanız gerekir.

## <a name="create-the-template-config"></a>Şablon yapılandırması oluşturma

Şablonlar, .NET core'da şablonunuzun kök dizininde mevcut özel bir klasör ve yapılandırma dosyasında tarafından tanınır. Bu öğreticide, şu şablonu klasörünüze konumdadır _working\templates\extensions\\_ .

Bir şablonu oluşturduğunuzda, tüm dosya ve klasörlerin şablon klasöründe özel yapılandırma klasörü dışında şablonun parçası olarak dahil edilir. Bu yapılandırma klasörü adlı _. template.config_.

İlk olarak, adlı yeni bir alt klasör oluşturun _. template.config_, girin. Adlı yeni bir dosya oluşturup _template.json_. Klasör yapınız gibi görünmelidir:

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

Açık _template.json_ , sık kullandığınız metin düzenleyicisi ve Yapıştır aşağıdaki JSON kod ve kaydedin:

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Code" ],
  "identity": "ExampleTemplate.StringExtensions",
  "name": "Example templates: string extensions",
  "shortName": "stringext",
  "tags": {
    "language": "C#",
    "type": "item"
  }
}
```

Bu yapılandırma dosyası şablonunuz için tüm ayarları içerir. Temel ayarlar gibi görebilirsiniz `name` ve `shortName`, ancak aynı zamanda bir `tags/type` ayarlanan değer `item`. Bu şablon bir öğe şablonu kategorilere ayırır. Oluşturduğunuz şablonun türüyle ilgili bir kısıtlama yoktur. `item` Ve `project` değerler için yaygın olarak kullanılan adları .NET Core önerir ve böylece kullanıcılar bunlar aramakta olduğunuz şablon türü kolayca filtre uygulayabilirsiniz.

`classifications` Öğesini temsil eder **etiketleri** gördüğünüz çalıştırdığınızda sütun `dotnet new` ve şablon listesini alın. Kullanıcılar ayrıca arayabilirler tabanlı sınıflandırma etiketleri. Karıştırmayın `tags` özelliğinde \*.json dosyasını `classifications` Etiketler listesi. Ne yazık ki benzer şekilde adlı iki terimin farklı anlamlara oldukları. İçin tam şema *template.json* dosya konumunda bulundu [JSON şema Store](http://json.schemastore.org/template). Hakkında daha fazla bilgi için *template.json* bkz [dotnet şablon wiki](https://github.com/dotnet/templating/wiki).

Geçerli bir sahip olduğunuza göre _.template.config/template.json_ dosya, şablonunuzu yüklenmeye hazır. Terminalinizde gidin _uzantıları_ klasör ve şablon yüklemek için aşağıdaki komutu, geçerli klasörde bulunan çalıştırın:

* **Windows üzerinde**: `dotnet new -i .\`
* **Linux veya macOS üzerinde**: `dotnet new -i ./`

Bu komut sizin kapsamalıdır yüklü şablonlar listesinden çıkarır.

```console
C:\working\templates\extensions> dotnet new -i .\
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Class library                                     classlib              [C#], F#, VB      Common/Library
WPF Application                                   wpf                   [C#], VB          Common/WPF
Windows Forms (WinForms) Application              winforms              [C#], VB          Common/WinForms
Worker Service                                    worker                [C#]              Common/Worker/Web
```

## <a name="test-the-item-template"></a>Öğe şablonunda test

Yüklü bir öğe şablonunu olduğuna göre test edin. Gidin _test /_ klasörü ile yeni bir konsol uygulaması oluşturup `dotnet new console`. Bu, kolayca test ile bir çalışma projenin oluşturduğu `dotnet run` komutu.

```console
C:\test> dotnet new console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

```console
C:\test> dotnet run
Hello World!
```

Ardından, çalıştırma `dotnet new stringext` oluşturulacak _CommonExtensions.cs_ şablonundan.

```console
C:\test> dotnet new stringext
The template "Example templates: string extensions" was created successfully.
```

Kodda değişiklik _Program.cs_ tersine çevirmek için `"Hello World"` şablon tarafından sağlanan genişletme yöntemi ile dize.

```csharp
Console.WriteLine("Hello World!".Reverse());
```

Programı yeniden çalıştırın ve sonuç ters çevrilir görürsünüz.

```console
C:\test> dotnet run
!dlroW olleH
```

Tebrikler! Oluşturduğunuz ve .NET Core ile bir öğe şablonunu dağıtılmış. Bu öğretici serisinin bir sonraki bölümü için hazırlanırken oluşturduğunuz şablonu kaldırmanız gerekir. Tüm dosyaları silmek istediğinizden emin olun _test_ klasörü çok. Bununla geri temiz bir duruma hazır için bu öğreticinin sonraki ana bölüme sahip olursunuz.

## <a name="uninstall-the-template"></a>Şablonu Kaldır

Şablon dosyası yolu tarafından yüklü olduğundan, birlikte kaldırmalısınız **mutlak** dosya yolu. Çalıştırarak yüklü şablonlar listesi gördüğünüz `dotnet new -u` komutu. Şablonunuzu son listelenmelidir. Yolun listelenen şablonunuzla birlikte kaldırmak için kullanımı `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` komutu.

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
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

```console
C:\working> dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir öğe şablonu oluşturuldu. Bu öğretici serisinin devam proje şablonu oluşturmayı öğrenin.

> [!div class="nextstepaction"]
> [Bir proje şablonu oluşturma](cli-templates-create-project-template.md)
