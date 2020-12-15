---
title: DotNet New için bir proje şablonu oluşturun
description: DotNet New komutu için bir proje şablonu oluşturmayı öğrenin.
author: adegeo
ms.date: 12/11/2020
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: ed40cfd303c70c7b8f198a0f5b593bf1e1ebeaf8
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513139"
---
# <a name="tutorial-create-a-project-template"></a>Öğretici: proje şablonu oluşturma

.NET ile, projeler, dosyalar ve hatta kaynaklar üreten şablonlar oluşturabilir ve dağıtabilirsiniz. Bu öğretici, komutuyla kullanılmak üzere şablonlar oluşturmayı, yüklemeyi ve kaldırmayı öğretir `dotnet new` .

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

Proje şablonları, kullanıcıların çalışan bir kod kümesiyle başlamasını kolaylaştıran, çalıştırmaya yönelik olarak çalışan projeler oluşturur. .NET, konsol uygulaması veya sınıf kitaplığı gibi bazı proje şablonları içerir. Bu örnekte, C# 9,0 ' i sağlayan ve bir giriş noktası üreten yeni bir konsol projesi oluşturacaksınız `async main` .

Terminalinizde, _working\templates_ klasörüne gidin ve _consoleasync_ adlı yeni bir alt klasör oluşturun. `dotnet new console`Standart konsol uygulamasını oluşturmak için alt klasörü girin ve çalıştırın. Bu şablon tarafından oluşturulan dosyaları düzenleyerek yeni bir şablon oluşturabilirsiniz.

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
            await Console.Out.WriteAsync("Hello World with C# 9.0!");
        }
    }
}
```

## <a name="modify-consoleasynccsproj"></a>Consoleasync. csproj öğesini Değiştir

Projenin 9,0 sürümüne kullandığı C# dil sürümünü güncelleştirelim. _Consoleasync. csproj_ dosyasını düzenleyin ve `<LangVersion>` ayarı bir `<PropertyGroup>` düğüme ekleyin.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>

    <LangVersion>9.0</LangVersion>

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
Hello World with C# 9.0!
```

Kullanılarak oluşturulan _obj_ ve _bin_ klasörlerini silebilirsiniz `dotnet run` . Bu dosyaların silinmesi, şablonunuzun yalnızca şablonlarınız ile ilgili dosyaları ve bir yapı eyleminden kaynaklanan hiçbir dosyayı içerdiğini sağlar.

Artık oluşturulan şablonun içeriğine sahip olduğunuza göre, şablonun kök klasöründe şablon yapılandırmasını oluşturmanız gerekir.

## <a name="create-the-template-config"></a>Şablon yapılandırması oluşturma

Şablonlar, .NET 'te şablonunuzun kökünde bulunan özel bir klasör ve yapılandırma dosyası tarafından tanınır. Bu öğreticide, şablon klasörünüz _working\templates\consoleasync_ adresinde bulunur.

Bir şablon oluşturduğunuzda, şablon klasöründeki tüm dosyalar ve klasörler, özel yapılandırma klasörü hariç, şablonun bir parçası olarak dahil edilir. Bu yapılandırma klasörü _.template.config_ olarak adlandırılmıştır.

İlk olarak, _.template.config_ adlı yeni bir alt klasör oluşturun, girin. Ardından, _üzerindetemplate.js_ adlı yeni bir dosya oluşturun. Klasör yapınız şöyle görünmelidir.

```console
working
└───templates
    └───consoleasync
        └───.template.config
                template.json
```

En sevdiğiniz metin düzenleyicinizle birlikte _template.js_ açın ve aşağıdaki JSON kodunu yapıştırın ve kaydedin.

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Console", "C#9" ],
  "identity": "ExampleTemplate.AsyncProject",
  "name": "Example templates: async project",
  "shortName": "consoleasync",
  "tags": {
    "language": "C#",
    "type": "project"
  }
}
```

Bu yapılandırma dosyası şablonunuz için tüm ayarları içerir. Ve gibi temel ayarları görebilir, ancak olarak `name` `shortName` ayarlanmış bir değer de vardır `tags/type` `project` . Bu, şablonunuzu bir proje şablonu olarak belirler. Oluşturduğunuz şablon türü üzerinde hiçbir kısıtlama yoktur. `item`Ve `project` değerleri, kullanıcıların aradıkları şablonun türünü kolayca filtreleyebilmesi için .NET tarafından önerilen yaygın adlardır.

`classifications`Öğe,  çalıştırdığınız `dotnet new` ve bir şablon listesi alırken gördüğünüz Etiketler sütununu temsil eder. Kullanıcılar ayrıca sınıflandırma etiketlerine göre arama yapabilir. `tags`JSON dosyasındaki özelliği `classifications` Etiketler listesiyle karıştırmayın. Benzer şekilde adlandırılan iki farklı şey vardır. Dosyadaki *template.js* tam şeması [JSON Şema deposunda](http://json.schemastore.org/template)bulunur. Dosyadaki *template.js* hakkında daha fazla bilgi için bkz. [DotNet şablon oluşturma wiki](https://github.com/dotnet/templating/wiki).

Artık dosyada geçerli bir _.template.config/template.jsolduğuna göre_ şablonunuz yüklenmeye hazırdır. Şablonu yüklemeden önce, _küme_ veya _obj_ klasörleri gibi şablonunuzda yer almasını istemediğiniz ek dosya klasörlerini ve dosyalarını sildiğinizden emin olun. Terminalinizde _consoleasync_ klasörüne gidin ve `dotnet new -i .\` geçerli klasörde bulunan şablonu yüklemek için öğesini çalıştırın. Linux veya macOS işletim sistemi kullanıyorsanız, eğik çizgi kullanın: `dotnet new -i ./` .

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

Templates                                         Short Name               Language          Tags
--------------------------------------------      -------------------      ------------      ----------------------
Console Application                               console                  [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync             [C#]              Common/Console/C#9
Class library                                     classlib                 [C#], F#, VB      Common/Library
WPF Application                                   wpf                      [C#], VB          Common/WPF
```

### <a name="test-the-project-template"></a>Proje şablonunu test etme

Artık yüklü bir proje şablonunuz olduğuna göre, test edin.

1. _Test_ klasörüne git

1. Komut ile kolayca test edebileceğiniz, çalışan bir proje üreten aşağıdaki komutla yeni bir konsol uygulaması oluşturun `dotnet run` .

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
    Hello World with C# 9.0!
    ```

Tebrikler! .NET ile bir proje şablonu oluşturdunuz ve dağıttıysanız. Bu öğretici serisinin bir sonraki kısmına hazırlanın, oluşturduğunuz şablonu kaldırmanız gerekir. Tüm dosyaları da _Test_ klasöründen sildiğinizden emin olun. Bu, Bu öğreticinin bir sonraki ana kısmına yönelik temiz bir duruma geri dönebilirsiniz.

### <a name="uninstall-the-template"></a>Şablonu kaldırma

Şablonu bir dosya yolu kullanarak yükletiğinden, **mutlak** dosya yoluyla kaldırmanız gerekir. Komutunu çalıştırarak, yüklenmiş şablonların bir listesini görebilirsiniz `dotnet new -u` . Şablonunuzun son listelenmesi gerekir. `Uninstall Command`Şablonunuzu kaldırmak için listelenmiş ' i kullanın.

```dotnetcli
dotnet new -u
```

Aşağıdakine benzer bir çıktı alırsınız.

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ProjectTemplates.2.2
    Details:
      NuGetPackageId: Microsoft.DotNet.Common.ProjectTemplates.2.2
      Version: 1.0.2-beta4
      Author: Microsoft
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
    Uninstall Command:
      dotnet new -u Microsoft.DotNet.Common.ProjectTemplates.2.2

... cut to save space ...

  C:\Test\templatetutorial\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
    Uninstall Command:
      dotnet new -u C:\working\templates\consoleasync
```

Oluşturduğunuz şablonu kaldırmak için `Uninstall Command` çıktıda gösterilen öğesini çalıştırın.

```dotnetcli
dotnet new -u C:\working\templates\consoleasync
```

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide bir proje şablonu oluşturdunuz. Hem öğe hem de proje şablonlarının kullanımı kolay bir dosyaya nasıl paketleyeceğinizi öğrenmek için, bu öğretici serisine devam edin.

> [!div class="nextstepaction"]
> [Şablon paketi oluşturma](cli-templates-create-template-pack.md)
