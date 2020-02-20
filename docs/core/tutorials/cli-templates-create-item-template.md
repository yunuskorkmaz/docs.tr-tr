---
title: DotNet New-.NET Core CLI için bir öğe şablonu oluşturun
description: DotNet New komutu için bir öğe şablonu oluşturmayı öğrenin. Öğe şablonları, herhangi bir sayıda dosya içerebilir.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: 5f4038e863d9bb59df470d3516c08fd2ad29c078
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503560"
---
# <a name="tutorial-create-an-item-template"></a>Öğretici: öğe şablonu oluşturma

.NET Core ile projeler, dosyalar, hatta kaynaklar üreten şablonlar oluşturabilir ve dağıtabilirsiniz. Bu öğretici, `dotnet new` komutuyla kullanılmak üzere şablonlar oluşturmayı, yüklemeyi ve kaldırmayı öğretir.

Serinin bu bölümünde şunları yapmayı öğreneceksiniz:

> [!div class="checklist"]
>
> * Öğe şablonu için bir sınıf oluşturma
> * Şablon yapılandırma klasörünü ve dosyasını oluşturma
> * Dosya yolundan şablon yükler
> * Bir öğe şablonunu test etme
> * Öğe şablonunu kaldırma

## <a name="prerequisites"></a>Önkoşullar

* [.NET Core 2,2 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümleri.
* [DotNet New Için özel şablonlar](../tools/custom-templates.md)başvuru makalesine okuyun.

  Başvuru makalesinde şablonlar ve bunların nasıl birlikte yerleştirildikleri hakkında temel bilgiler açıklanmaktadır. Bu bilgilerden bazıları burada yeniden tekrarlandırılır.

* Bir Terminal açın ve _working\templates_ klasörüne gidin.

## <a name="create-the-required-folders"></a>Gerekli klasörleri oluşturma

Bu seri, şablon kaynağınızın bulunduğu bir "çalışma klasörü" ve şablonlarınızı test etmek için kullanılan bir "test klasörü" kullanır. Çalışma klasörü ve test klasörü aynı üst klasörde olmalıdır.

İlk olarak, üst klasörü oluşturun, ad önemlidir. Ardından, _çalışıyor_adlı bir alt klasör oluşturun. _Çalışma_ klasörünün içinde _Şablonlar_adlı bir alt klasör oluşturun.

Sonra, _Test_adlı üst klasör altında bir klasör oluşturun. Klasör yapısı aşağıdaki gibi görünmelidir.

```console
parent_folder
├───test
└───working
    └───templates
```

## <a name="create-an-item-template"></a>Öğe şablonu oluşturma

Öğe şablonu, bir veya daha fazla dosya içeren belirli bir şablon türüdür. Bu tür şablonlar, bir yapılandırma, kod veya çözüm dosyası gibi bir şey oluşturmak istediğinizde faydalıdır. Bu örnekte, dize türüne bir genişletme yöntemi ekleyen bir sınıf oluşturacaksınız.

Terminalinizde, _working\templates_ klasörüne gidin ve _Uzantılar_adlı yeni bir alt klasör oluşturun. Klasörü girin.

```console
working
└───templates
    └───extensions
```

_CommonExtensions.cs_ adlı yeni bir dosya oluşturun ve bu dosyayı en sevdiğiniz metin düzenleyicinizle açın. Bu sınıf, bir dizenin içeriğini tersine çevirecek `Reverse` adlı bir genişletme yöntemi sağlar. Aşağıdaki kodu yapıştırın ve dosyayı kaydedin:

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

Artık oluşturulan şablonun içeriğine sahip olduğunuza göre, şablonun kök klasöründe şablon yapılandırmasını oluşturmanız gerekir.

## <a name="create-the-template-config"></a>Şablon yapılandırması oluşturma

Şablonlar, .NET Core 'da şablonunuzun kökünde bulunan özel bir klasör ve yapılandırma dosyası tarafından tanınır. Bu öğreticide, şablon klasörünüz _working\templates\extensions_konumunda bulunur.

Bir şablon oluşturduğunuzda, şablon klasöründeki tüm dosyalar ve klasörler, özel yapılandırma klasörü hariç, şablonun bir parçası olarak dahil edilir. Bu yapılandırma klasörü _. Template. config_olarak adlandırılır.

İlk olarak, _. Template. config_adlı yeni bir alt klasör oluşturun, bunu girin. Ardından, _Template. JSON_adlı yeni bir dosya oluşturun. Klasör yapınız şöyle görünmelidir:

```console
working
└───templates
    └───extensions
        └───.template.config
                template.json
```

En sevdiğiniz metin düzenleyicinizle _Template. JSON_ ' i açın ve aşağıdaki JSON kodunu yapıştırın ve kaydedin.

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

Bu yapılandırma dosyası, şablonunuz için tüm ayarları içerir. `name` ve `shortName`gibi temel ayarları görebilirsiniz, ancak `item`olarak ayarlanmış bir `tags/type` değeri de vardır. Bu, şablonunuzu bir öğe şablonu olarak sınıflandırır. Oluşturduğunuz şablon türü üzerinde hiçbir kısıtlama yoktur. `item` ve `project` değerleri, .NET Core 'un arama yapmakta oldukları şablonun türünü kolayca filtreleyebilmesi için .NET Core 'un önerdiği yaygın adlardır.

`classifications` öğesi, `dotnet new` çalıştırdığınız ve şablonların bir listesini alacağınız zaman gördüğünüz **Etiketler** sütununu temsil eder. Kullanıcılar ayrıca sınıflandırma etiketlerine göre arama yapabilir. \*. JSON dosyasındaki `tags` özelliğini `classifications` Etiketler listesiyle karıştırmayın. Benzer şekilde adlandırılan iki farklı şey vardır. *Template. JSON* dosyasının tam şeması [JSON Şema deposunda](http://json.schemastore.org/template)bulunur. *Template. JSON* dosyası hakkında daha fazla bilgi için bkz. [DotNet şablon oluşturma wiki](https://github.com/dotnet/templating/wiki).

Artık geçerli bir _. Template. config/Template. JSON_ dosyanız olduğuna göre, şablonunuz yüklenmeye hazırdır. Terminalinizde, _Uzantılar_ klasörüne gidin ve geçerli klasörde bulunan şablonu yüklemek için şu komutu çalıştırın:

* **Windows üzerinde**: `dotnet new -i .\`
* **Linux veya macOS 'ta**: `dotnet new -i ./`

Bu komut, yüklenmiş şablonların listesini verir ve bunları içermelidir.

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

## <a name="test-the-item-template"></a>Öğe şablonunu test etme

Artık bir öğe şablonu yükleolduğunuza göre, test edin. _Teste/_ klasöre gidin ve `dotnet new console`yeni bir konsol uygulaması oluşturun. Bu, `dotnet run` komutuyla kolayca test edebileceğiniz bir çalışan proje oluşturur.

```dotnetcli
dotnet new console
```

Aşağıdakine benzer bir çıktı alırsınız.

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

Sonra, şablondan _CommonExtensions.cs_ oluşturmak için `dotnet new stringext` çalıştırın.

```dotnetcli
dotnet new stringext
```

Aşağıdaki çıktıyı alırsınız.

```console
The template "Example templates: string extensions" was created successfully.
```

`"Hello World"` dizesini, şablon tarafından sağlanmış uzantı yöntemiyle tersine çevirmek için _program.cs_ içindeki kodu değiştirin.

```csharp
Console.WriteLine("Hello World!".Reverse());
```

Programı yeniden çalıştırın ve sonucun tersine çevrilip çevrilmediğini görürsünüz.

```dotnetcli
dotnet run
```

Aşağıdaki çıktıyı alırsınız.

```console
!dlroW olleH
```

Tebrikler! .NET Core ile bir öğe şablonu oluşturup dağıttıysanız. Bu öğretici serisinin bir sonraki kısmına hazırlanın, oluşturduğunuz şablonu kaldırmanız gerekir. Tüm dosyaları da _Test_ klasöründen sildiğinizden emin olun. Bu, Bu öğreticinin bir sonraki ana kısmına yönelik temiz bir duruma geri dönebilirsiniz.

## <a name="uninstall-the-template"></a>Şablonu kaldırma

Şablonu dosya yoluna göre yükletiğinden, **mutlak** dosya yolu ile kaldırmanız gerekir. `dotnet new -u` komutunu çalıştırarak, yüklenmiş şablonların listesini görebilirsiniz. Şablonunuzun son listelenmesi gerekir. `dotnet new -u <ABSOLUTE PATH TO TEMPLATE DIRECTORY>` komutuyla şablonunuzu kaldırmak için listelenen yolu kullanın.

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
  C:\working\templates\extensions
    Templates:
      Example templates: string extensions (stringext) C#
```

Bir şablonu kaldırmak için aşağıdaki komutu çalıştırın.

```dotnetcli
dotnet new -u C:\working\templates\extensions
```

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide bir öğe şablonu oluşturdunuz. Proje şablonu oluşturmayı öğrenmek için bu öğretici serisine devam edin.

> [!div class="nextstepaction"]
> [Proje şablonu oluşturma](cli-templates-create-project-template.md)
