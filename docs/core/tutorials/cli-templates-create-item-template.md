---
title: Dotnet yeni - .NET Core CLI için bir öğe şablonu oluşturma
description: dotnet yeni komutu için bir öğe şablonu oluşturmayı öğrenin. Öğe şablonları herhangi bir sayıda dosya içerebilir.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5f4038e863d9bb59df470d3516c08fd2ad29c078
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503560"
---
# <a name="tutorial-create-an-item-template"></a>Öğretici: Öğe şablonu oluşturma

.NET Core ile, projeler, dosyalar ve hatta kaynaklar oluşturan şablonlar oluşturabilir ve dağıtabilirsiniz. Bu öğretici, `dotnet new` komutla birlikte şablon oluşturma, yükleme ve kaldırma yı öğreten bir serinin parçasıdır.

Serinin bu bölümünde, nasıl öğreneceksiniz:

> [!div class="checklist"]
>
> * Öğe şablonu için sınıf oluşturma
> * Şablon config klasörünü ve dosyasını oluşturma
> * Dosya yolundan şablon yükleme
> * Öğe şablonu test edin
> * Öğe şablonu kaldırma

## <a name="prerequisites"></a>Önkoşullar

* [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümler.
* Başvuru makalesini okuyun [Dotnet yeni için özel şablonlar](../tools/custom-templates.md).

  Başvuru makalesi, şablonlar ve bunların nasıl bir araya getirilenlerle ilgili temel bilgileri açıklar. Bu bilgilerin bir kısmı burada yinelenecektir.

* Bir terminal açın ve _çalışma\şablonlar_ klasörüne gidin.

## <a name="create-the-required-folders"></a>Gerekli klasörleri oluşturma

Bu seri, şablon kaynağınızın bulunduğu bir "çalışma klasörü" ve şablonlarınızı sınamak için kullanılan bir "test klasörü" kullanır. Çalışma klasörü ve sınayın klasörü aynı üst klasör altında olmalıdır.

İlk olarak, üst klasörü oluşturmak, adı önemli değil. Ardından, _çalışma_adlı bir alt klasör oluşturun. _Çalışma_ klasörünün içinde _şablonlar_adlı bir alt klasör oluşturun.

Ardından, _test_adlı üst klasörün altında bir klasör oluşturun. Klasör yapısı aşağıdaki gibi görünmelidir.

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a>Öğe şablonu oluşturma

Öğe şablonu, bir veya daha fazla dosya içeren belirli bir şablon türüdür. Bu tür şablonlar, config, kod veya çözüm dosyası gibi bir şey oluşturmak istediğinizde yararlıdır. Bu örnekte, dize türüne uzantı yöntemi ekleyen bir sınıf oluşturursunuz.

Terminalinizde, _çalışma\şablonlar_ klasörüne gidin ve _uzantılar_adlı yeni bir alt klasör oluşturun. Klasörü girin.

```console
working
└───templates
    └───extensions
```

_CommonExtensions.cs_ adlı yeni bir dosya oluşturun ve sık kullanılan metin düzenleyicisiyle açın. Bu sınıf, bir dize içeriğini tersine çeviren adlı `Reverse` bir uzantı yöntemi sağlar. Aşağıdaki kodu yapıştırın ve dosyayı kaydedin:

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

Oluşturulan şablonun içeriğine sahip olduğunuza göre, şablonun kök klasöründe şablon config'ini oluşturmanız gerekir.

## <a name="create-the-template-config"></a>Şablon config oluşturma

Şablonlar .NET Core'da şablonunuzun kökünde bulunan özel bir klasör ve config dosyası tarafından tanınır. Bu öğreticide, şablon klasörünüz _çalışma\templates\extensions_adresinde bulunur.

Bir şablon oluşturduğunuzda, şablon klasöründeki tüm dosya ve klasörler özel config klasörü dışında şablonun bir parçası olarak dahil edilir. Bu config klasörü _.template.config_olarak adlandırılır.

İlk olarak, _.template.config_adlı yeni bir alt klasör oluşturun, girin. Ardından, _template.json_adında yeni bir dosya oluşturun. Klasör yapınız şu şekilde görünmelidir:

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

En sevdiğiniz metin düzenleyicisi ile _template.json'u_ açın ve aşağıdaki JSON koduna yapıştırın ve kaydedin.

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

Bu config dosyası şablonunuzun tüm ayarlarını içerir. Temel ayarları görebilirsiniz, gibi `name` `shortName`ve , ama aynı `tags/type` zamanda ayarlanmış `item`bir değer var. Bu, şablonunuzu öğe şablonu olarak kategorilere ayırıyor. Oluşturduğunuz şablon türünde herhangi bir kısıtlama yoktur. Ve `item` `project` değerler, kullanıcıların aradıkları şablon türünü kolayca filtreleyebilmeleri için .NET Core'un önerdiği ortak adlardır.

Öğe, `classifications` çalıştırdığınızda `dotnet new` ve şablonların listesini aldığınızda gördüğünüz **etiketler** sütununa temsil eder. Kullanıcılar sınıflandırma etiketlerine göre de arama yapabilir. .json dosyasındaki `tags` \*özelliği `classifications` etiket listesiyle karıştırmayın. Ne yazık ki benzer adlı iki farklı şey konum. *template.json* dosyası için tam şema [JSON Schema Store'da](http://json.schemastore.org/template)bulunur. *template.json* dosyası hakkında daha fazla bilgi [için, dotnet templating wiki](https://github.com/dotnet/templating/wiki)bakın.

Artık geçerli bir _.template.config/template.json_ dosyanız olduğuna göre, şablonunuz yüklenmeye hazırdır. Terminalinizde _uzantılar_ klasörüne gidin ve geçerli klasörde bulunan şablonu yüklemek için aşağıdaki komutu çalıştırın:

* **Windows'da**:`dotnet new -i .\`
* **Linux veya macOS üzerinde:**`dotnet new -i ./`

Bu komut, sizinkini içermesi gereken yüklü şablonlar listesini çıkartır.

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

## <a name="test-the-item-template"></a>Öğe şablonu test edin

Artık yüklü bir öğe şablonu var, test edin. _Test/_ klasöre gidin ve `dotnet new console`yeni bir konsol uygulaması oluşturun. Bu `dotnet run` komutu ile kolayca test edebilirsiniz çalışan bir proje oluşturur.

```dotnetcli
dotnet new console
```

Aşağıdakine benzer çıktı alırsınız.

```console
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\test\test.csproj...
  Restore completed in 54.82 ms for C:\test\test.csproj.

Restore succeeded.
```

Projeyi ile çalıştırın.

```dotnetcli
dotnet run
```

Aşağıdaki çıktıyı alırsınız.

```console
Hello World!
```

Ardından, `dotnet new stringext` şablondan _CommonExtensions.cs_ oluşturmak için çalıştırın.

```dotnetcli
dotnet new stringext
```

Aşağıdaki çıktıyı alırsınız.

```console
The template "Example templates: string extensions" was created successfully.
```

Şablon tarafından _Program.cs_ sağlanan uzantı `"Hello World"` yöntemiyle dizeyi tersine çevirmek için Program.cs kodu değiştirin.

```csharp
Console.WriteLine("Hello World!".Reverse());
```

Programı yeniden çalıştırın ve sonucun tersine çevrildiğini görürsünüz.

```dotnetcli
dotnet run
```

Aşağıdaki çıktıyı alırsınız.

```console
!dlroW olleH
```

Tebrikler! .NET Core ile bir öğe şablonu oluşturdunuz ve dağıttınız. Bu öğretici serinin bir sonraki bölümüne hazırlık olarak, oluşturduğunuz şablonu kaldırmanız gerekir. Test klasöründeki tüm _test_ dosyaları da sildiğinizden emin olun. Bu, bu öğreticinin bir sonraki ana bölümü için hazır temiz bir duruma geri dönecektir.

## <a name="uninstall-the-template"></a>Şablonu kaldırma

Şablonu dosya yoluna göre yüklediğiniz için, **şablonu mutlak** dosya yolu ile kaldırmanız gerekir. `dotnet new -u` Komutu çalıştırarak yüklenen şablonların listesini görebilirsiniz. Şablonunuzun en son listelenmesi gerekir. Komutla `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` şablonunuzu kaldırmak için listelenen yolu kullanın.

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
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

Şablonu kaldırmak için aşağıdaki komutu çalıştırın.

```dotnetcli
dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir öğe şablonu oluşturdunuz. Proje şablonu oluşturmayı öğrenmek için bu öğretici seriye devam edin.

> [!div class="nextstepaction"]
> [Proje şablonu oluşturma](cli-templates-create-project-template.md)
