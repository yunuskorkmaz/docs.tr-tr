---
title: Yeni dotnet için özel şablonlar
description: Herhangi bir türde .NET proje veya dosya için özel şablonlar hakkında bilgi edinin.
author: thraka
ms.date: 06/14/2019
ms.openlocfilehash: d7e9c549ff132deb4682ba81ab5ff354d6cc1522
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169624"
---
# <a name="custom-templates-for-dotnet-new"></a>Yeni dotnet için özel şablonlar

[.NET Core SDK'sı](https://www.microsoft.com/net/download/core) birçok zaten yüklü şablonlar ve kullanımınıza hazır birlikte gelir. [ `dotnet new` Komut](dotnet-new.md) yalnızca şablon aynı zamanda yüklemek ve şablonları kaldırmak nasıl kullanılacağını yolu değildir. .NET Core 2.0 ile başlayarak, herhangi bir türde gibi bir uygulama, hizmet, aracı veya sınıf kitaplığı projesi için kendi özel şablonlarınızı oluşturabilirsiniz. Hatta çıkaran bir veya daha fazla bağımsız dosyaları, bir yapılandırma dosyası gibi bir şablon oluşturabilirsiniz.

Özel şablonlar akış, bir NuGet başvurarak herhangi bir NuGet üzerindeki bir NuGet paketini yükleyebilirsiniz *.nupkg* doğrudan veya şablon içeren bir dosya sistemi dizin belirterek dosya. Şablon altyapısı, değerleri değiştirebilir, içerir ve dosyaları dışarıda bırak olanak tanır ve şablonunuzu kullanıldığında özel işlemleri yürüten özellikleri sunar.

Şablon altyapısı açık kaynaklıdır ve çevrimiçi kod deposundaki altındadır [dotnet/şablon](https://github.com/dotnet/templating/) GitHub üzerinde. Ziyaret [dotnet/dotnet-şablonu-samples](https://github.com/dotnet/dotnet-template-samples) şablonları örnekleri için depo. Üçüncü taraf şablonları dahil olmak üzere daha fazla şablon adresten [yeni dotnet şablonları](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) GitHub üzerinde. Özel şablon oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [yeni dotnet için kendi şablonlarınızı oluşturmak nasıl](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) ve [dotnet/şablon GitHub deposunu Wiki](https://github.com/dotnet/templating/wiki).

Bir kılavuz uygulayın ve bir şablon oluşturmak için bkz: [yeni dotnet için özel bir şablon oluşturma](~/docs/core/tutorials/create-custom-template.md) öğretici.

### <a name="net-default-templates"></a>.NET varsayılan şablonları

Yüklediğinizde [.NET Core SDK'sı](https://www.microsoft.com/net/download/core)projeleri oluşturmak için yerleşik şablonlar üzerinde bir düzine Al ve dosyaları, dahil konsol uygulamaları, sınıf kitaplıkları, birim test projeleri, ASP.NET Core uygulamaları (dahil olmak üzere [Angular](https://angular.io/) ve [React](https://facebook.github.io/react/) projeler) ve yapılandırma dosyaları. Yerleşik şablonlar listelemek için çalıştırma `dotnet new` komutunu `-l|--list` seçeneği:

```console
dotnet new --list
```

## <a name="configuration"></a>Yapılandırma

Şablon aşağıdaki bölümlerden oluşur:

- Kaynak dosya ve klasörler.
- Bir yapılandırma dosyası (*template.json*).

### <a name="source-files-and-folders"></a>Kaynak dosyalar ve klasörler

Kaynak dosyaları ve klasörleri kullanmak üzere hangi dosya ve klasörleri, istediğiniz şablon altyapısı dahil `dotnet new <TEMPLATE>` komutu çalıştırın. Şablon altyapısı kullanmak üzere tasarlanmış *çalıştırılabilir projeleri* gibi kaynak kod projeleri oluşturmak için. Bu, birçok faydası vardır:

- Şablon motoru özel belirteçler projenizin kaynak koda eklemesine gerektirmez.
- Kod dosyaları, özel dosyaları değil veya şablon altyapısı ile çalışmak üzere herhangi bir şekilde değiştirdi. Bu nedenle, normalde projeleriyle çalışırken kullandığınız araçları da şablon içeriği ile çalışır.
- Oluşturun, çalıştırın ve herhangi diğer projeleriniz için yaptığınız gibi şablon projelerini hata ayıklama.
- Yalnızca ekleyerek bir şablonu var olan bir projeden hızlı bir şekilde oluşturabilirsiniz bir *./.template.config/template.json* projeye yapılandırma dosyası.

Şablonda depolanan dosya ve klasörleri resmi .NET proje türleri için sınırlı değildir. Kaynak dosyalar ve klasörler, şablon kullanıldığında, şablon altyapısı çıktısını olarak yalnızca bir dosya üretse oluşturmak istediğiniz tüm içeriklerin oluşabilir.

Şablon tarafından oluşturulan dosyaları içinde sağladığınız ayarları ve mantıksal dayalı değiştirilebilir *template.json* yapılandırma dosyası. Seçenekleri geçirme, kullanıcı bu ayarları geçersiz kılabilirsiniz `dotnet new <TEMPLATE>` komutu. Yaygın olarak karşılaşılan örneklerden özel mantığı bir sınıfı veya şablon tarafından dağıtılan kod dosyasında değişken için bir ad sağlar.

### <a name="templatejson"></a>Template.JSON

*Template.json* dosya yerleştirilir bir *. template.config* şablonunun kök dizininde klasör. Dosya, şablon altyapısı yapılandırma bilgileri sağlar. Bir işlev şablonu oluşturmak yeterli olan aşağıdaki tabloda gösterilen üyeleri en az yapılandırma gerektirir.

| Üye            | Tür          | Açıklama |
| ----------------- | ------------- | ----------- |
| `$schema`         | URI           | JSON şemasını *template.json* dosya. Şema belirtildiğinde JSON şema desteği düzenleyicileri JSON düzenleme özelliklerini etkinleştirin. Örneğin, [Visual Studio Code](https://code.visualstudio.com/) IntelliSense'i etkinleştirmek bu üye gerektirir. Değeri kullanın `http://json.schemastore.org/template`. |
| `author`          | dize        | Şablon yazarı. |
| `classifications` | Array(String) | Sıfır veya daha fazla kullanıcı için arama yaparken şablonu bulmak için kullanıyor olabileceğiniz şablonun özelliklerini. Sınıflandırmalar da görünür *etiketleri* şablonları listesinde göründüğünde sütun üretilen kullanarak `dotnet new -l|--list` komutu. |
| `identity`        | dize        | Bu şablon için benzersiz bir ad. |
| `name`            | dize        | Kullanıcılar görmelisiniz şablonunun adı. |
| `shortName`       | dize        | Şablon adı GUI seçili olmayan bir kullanıcı tarafından burada belirtilen ortam için geçerli şablonu seçmek için bir varsayılan toplu özellik adı. Örneğin, kısa ad şablonları bir komut isteminden CLI komutları ile kullanıldığında yararlıdır. |

İçin tam şema *template.json* dosya konumunda bulundu [JSON şema Store](http://json.schemastore.org/template). Hakkında daha fazla bilgi için *template.json* bkz [dotnet şablon wiki](https://github.com/dotnet/templating/wiki).

#### <a name="example"></a>Örnek

Örneğin, iki içerik dosyalarını içeren bir şablon klasörü şöyledir: *console.cs* ve *readme.txt*. Adında gereken klasör var olduğuna dikkat edin ele *. template.config* içeren *template.json* dosya.

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

*Template.json* dosyasını aşağıdaki gibi görünür:

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Travis Chau",
  "classifications": [ "Common", "Console" ],
  "identity": "AdatumCorporation.ConsoleTemplate.CSharp",
  "name": "Adatum Corporation Console Application",
  "shortName": "adatumconsole"
}
```

*Şablonum* yüklenebilir bir şablon paketi bir klasördür. Paketi yüklendikten sonra `shortName` kullanılabilir `dotnet new` komutu. Örneğin, `dotnet new adatumconsole` çıkış `console.cs` ve `readme.txt` geçerli klasörle dosyaları.

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Bir NuGet paketine (nupkg dosyası) bir şablon paketleme

Özel bir şablon ile paketlenmiştir [dotnet paketi](dotnet-pack.md) komut ve *.csproj* dosya. Alternatif olarak, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) kullanılabilir [nuget paketi](https://docs.microsoft.com/nuget/tools/cli-ref-pack) komutu ile birlikte bir *.nuspec* dosya. Ancak, Windows üzerinde .NET Framework NuGet gerektirir ve [Mono](https://www.mono-project.com/) Linux ve Macos'ta.

*.Csproj* dosyasıdır geleneksel bir kod-projeden biraz farklı *.csproj* dosya. Şunlara dikkat edin:

01. `<PackageType>` Ayarı eklenir ve kümesine `Template`.
01. `<PackageVersion>` Ayarı eklenir ve geçerli bir kümesi [NuGet sürüm numarası](/nuget/reference/package-versioning).
01. `<PackageId>` Ayarı eklenir ve benzersiz bir tanımlayıcı ile ayarlayın. Bu tanımlayıcı, şablon paketi kaldırmak için kullanılır ve NuGet tarafından kullanılır, şablon paketi kaydetmek için akışları.
01. Genel meta veri ayarları ayarlanmalıdır: `<Title>`, `<Authors>`, `<Description>`, ve `<Tags>`.
01. `<TargetFramework>` Ayarı ayarlanmalıdır, halde şablonunun işlem tarafından üretilen ikili kullanılmaz. Aşağıdaki örnekte ayarlanmış `netstandard2.0`.

Biçiminde bir şablon paketi bir *.nupkg* NuGet paketini gerektiren tüm şablonları depolanması *içeriği* paket içindeki klasör. Birkaç daha fazla ayar eklemek için bir *.csproj* oluşturulan emin olmak için dosya *.nupkg* bir şablon paketi yüklenebilir:

01. `<IncludeContentInPack>` Ayarı `true` proje ayarlar olarak herhangi bir dosya eklemek için **içeriği** NuGet paketi olarak.
01. `<IncludeBuildOutput>` Ayarı `false` NuGet paketinden derleyici tarafından oluşturulan tüm ikili dosyaları hariç tutmak için.
01. `<ContentTargetFolders>` Ayarı `content`. Bu dosyalar olarak ayarlayın xenapp'i **içeriği** depolanır *içeriği* NuGet paketi klasörüne. NuGet paketi bu klasöre dotnet şablon sistem tarafından ayrıştırılır.

Şablon projeniz tarafından derlenen tüm kod dosyaları hariç tutmak için kolay bir yol kullanmaktır `<Compile Remove="**\*" />` proje dosyanızın içine öğesi bir `<ItemGroup>` öğesi.

Tüm Şablonları ayrı bir klasör ve ardından her şablon klasörü içine koymak için şablon paketi yapısı için kolay bir yol olan bir *şablonları* aynı dizinde klasörünün, *.csproj* dosya. Bu şekilde tüm dosya ve klasörleri eklemek için bir tek proje öğesi kullanabilir *şablonları* olarak **içerik**. İçinde bir `<ItemGroup>` öğesi oluşturmak bir `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` öğesi.

İşte bir örnek *.csproj* tüm yukarıdaki yönergeleri izleyen dosya. Bu paketleri *şablonları* alt klasöre *içeriği* paketi klasörü ve Eylemi'ni her kod dosyasını hariç tutar.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <Tags>dotnet-new;templates;contoso</Tags>
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

Aşağıdaki örneği kullanarak dosya ve klasör yapısını gösterir. bir *.csproj* bir şablon paketi oluşturmak için. *MyDotnetTemplates.csproj* dosya ve *şablonları* klasör adında bir dizin kökünde bulunan *project_folder*. *Şablonları* klasörünü içeren iki şablon *mytemplate1* ve *mytemplate2*. Her şablon içerik dosyalarına sahip ve bir *. template.config* klasörüyle bir *template.json* yapılandırma dosyası.

```text
project_folder
│   MyDotnetTemplates.csproj
│
└───templates
    ├───mytemplate1
    │   │   console.cs
    │   │   readme.txt
    │   │
    │   └───.template.config
    │           template.json
    │
    └───mytemplate2
        │   otherfile.cs
        │
        └───.template.config
                template.json
```

## <a name="installing-a-template"></a>Bir şablon yüklenirken

Kullanım [yeni dotnet -i |--yükleme](dotnet-new.md) bir paketini yüklemek için komutu.

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Bir şablon nuget.org depolanan bir NuGet paketini yüklemek için

Bir şablon paketi yüklemek için NuGet paket tanımlayıcısı kullanın.

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Bir şablon nupkg yerel dosyadan yüklemek için

Yolu sağlayan bir *.nupkg* NuGet paket dosyası.

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Bir şablon bir dosya sistemi dizinden yüklemek için

Şablonları yüklenebilir bir şablon klasöründen gibi *mytemplate1* Yukarıdaki örnekteki klasör. Klasör yolunu belirtin *. template.config* klasör. Şablon dizini yolu mutlak olması gerekmez. Ancak, bir klasörden yüklü olan bir şablonu kaldırmak için bir mutlak yol gereklidir.

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a>Yüklü şablonlar listesinden Al

Kaldırma komutu hiçbir parametre olmadan, yüklü tüm şablonları listeler.

```console
dotnet new -u
```

Bu komut aşağıdaki çıktıya benzer bir şey döndürür:

```console
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)
  Microsoft.DotNet.Common.ProjectTemplates.3.0
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
...
```

Öğelerden sonra ilk düzeyini `Currently installed items:` olan bir şablonu kaldırma içinde kullanılan tanımlayıcıları. Ve yukarıdaki örnekte, `Microsoft.DotNet.Common.ItemTemplates` ve `Microsoft.DotNet.Common.ProjectTemplates.3.0` listelenir. Bu tanımlayıcı bir dosya sistemi yolu kullanarak şablonu yüklenmişse, klasör yolunu, olur *. template.config* klasör.

## <a name="uninstalling-a-template"></a>Bir şablon kaldırma

Kullanım [yeni dotnet -u |--kaldırma](dotnet-new.md) paketi kaldırmak için komutu.

Paket bir NuGet akışı tarafından ya da yüklenmişse bir *.nupkg* doğrudan dosya, tanımlayıcı sağlar.

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

Paket bir yolunu belirterek yüklendiyse *. template.config* klasöründe kullanan **mutlak** paketi kaldırma yolu. Şablon tarafından sağlanan çıkış mutlak yolu gördüğünüz `dotnet new -u` komutu. Daha fazla bilgi için [yüklü şablonlar listesinden alma](#get-a-list-of-installed-templates) yukarıdaki bölümde.

```console
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Özel bir şablon kullanarak bir proje oluşturun

Şablon yüklendikten sonra şablonu yürüterek kullanmak `dotnet new <TEMPLATE>` diğer önceden yüklenmiş şablonu olduğu gibi komutu. Belirtebilirsiniz [seçenekleri](dotnet-new.md#options) için `dotnet new` şablon ayarlarında yapılandırdığınız şablon özgü seçenekleri dahil olmak üzere komutu. Şablonun doğrudan komutuna kısa ad belirtin:

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni dotnet (eğitim) için özel bir şablon oluşturma](../tutorials/create-custom-template.md)
- [DotNet/şablon GitHub deposunu Wiki](https://github.com/dotnet/templating/wiki)
- [DotNet/dotnet-şablonu-örnekleri GitHub deposu](https://github.com/dotnet/dotnet-template-samples)
- [Dotnet için kendi şablonlarınızı yeni oluşturma](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [*Template.JSON* JSON şema Store şema](http://json.schemastore.org/template)
