---
title: Dotnet yeni için özel şablonlar
description: Her tür .NET projesi veya dosyası için özel şablonlar hakkında bilgi edinin.
author: thraka
ms.date: 06/14/2019
ms.openlocfilehash: 8e1ac4ca21a8a90ad0f7c9bd3dd11281eb4a6e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73420877"
---
# <a name="custom-templates-for-dotnet-new"></a>Dotnet yeni için özel şablonlar

[.NET Core SDK,](https://dotnet.microsoft.com/download) zaten yüklenmiş ve kullanmaya hazır birçok şablonla birlikte gelir. [ `dotnet new` Komut](dotnet-new.md) yalnızca şablon kullanmanın değil, şablonların nasıl yüklenir ve kaldırılabilen yoludur. .NET Core 2.0 ile başlayarak, uygulama, hizmet, araç veya sınıf kitaplığı gibi her tür proje için kendi özel şablonlarınızı oluşturabilirsiniz. Yapılandırma dosyası gibi bir veya daha fazla bağımsız dosyayı çıktılayan bir şablon bile oluşturabilirsiniz.

NuGet paketinden özel şablonlar yükleyebilirsiniz, herhangi bir NuGet akışına doğrudan nuget *.nupkg* dosyasına başvurarak veya şablonu içeren bir dosya sistemi dizini belirterek. Şablon altyapısı, değerleri değiştirmenize, dosyaları eklemenize ve hariç tutmanıza ve şablonuniz kullanıldığında özel işleme işlemlerini yürütmenize olanak tanıyan özellikler sunar.

Şablon motoru açık kaynak koddur ve çevrimiçi kod deposu GitHub'da [dotnet/templating'dedir.](https://github.com/dotnet/templating/) Şablon örnekleri için [dotnet/dotnet şablon-örnekleri](https://github.com/dotnet/dotnet-template-samples) repo'yu ziyaret edin. Üçüncü taraflardan gelen şablonlar da dahil olmak üzere daha fazla şablon, GitHub'da [yeni dotnet için Kullanılabilir şablonlarda](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) bulunur. Özel şablonlar oluşturma ve kullanma hakkında daha fazla bilgi için dotnet yeni ve [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki) [için kendi şablonlarınızı nasıl oluşturabilirsiniz'](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) a bakın.

Bir iz buzunu takip etmek ve şablon oluşturmak [için, dotnet yeni öğreticisi için özel bir şablon oluştur'a](../tutorials/cli-templates-create-item-template.md) bakın.

### <a name="net-default-templates"></a>.NET varsayılan şablonları

[.NET Core SDK'yı](https://dotnet.microsoft.com/download)yüklediğinizde, konsol uygulamaları, sınıf kitaplıkları, birim test projeleri, ASP.NET Core uygulamaları [(Açısal](https://angular.io/) ve [Tepki](https://facebook.github.io/react/) projeleri dahil) ve yapılandırma dosyaları dahil olmak üzere proje ve dosya oluşturmak için bir düzineden fazla yerleşik şablon alırsınız. Yerleşik şablonları listelemek için komutu `dotnet new` `-l|--list` seçeneğiyle çalıştırın:

```dotnetcli
dotnet new --list
```

## <a name="configuration"></a>Yapılandırma

Şablon aşağıdaki bölümlerden oluşur:

- Kaynak dosyaları ve klasörleri.
- Yapılandırma dosyası (*template.json*).

### <a name="source-files-and-folders"></a>Kaynak dosya ve klasörler

Kaynak dosya ve `dotnet new <TEMPLATE>` klasörler, komut çalıştırıldığında şablon altyapısının kullanmasını istediğiniz dosya ve klasörleri içerir. Şablon altyapısı, proje üretmek için *çalıştırılabilir projeleri* kaynak kodu olarak kullanmak üzere tasarlanmıştır. Bunun birkaç faydası vardır:

- Şablon altyapısı, projenizin kaynak koduna özel belirteçler enjekte etmenizi gerektirmez.
- Kod dosyaları özel dosyalar değildir veya şablon altyapısıyla çalışmak için herhangi bir şekilde değiştirilmez. Bu nedenle, projelerle çalışırken normalde kullandığınız araçlar şablon içeriğiyle de çalışır.
- Şablon projelerinizi, diğer projeleriniz için yaptığınız gibi oluşturur, çalıştırın ve hata ayıklarsınız.
- Projeye bir *./.template.config/template.json* yapılandırma dosyası ekleyerek varolan bir projeden hızlı bir şekilde şablon oluşturabilirsiniz.

Şablonda depolanan dosya ve klasörler resmi .NET proje türleri ile sınırlı değildir. Kaynak dosyaları ve klasörleri, şablon altyapısı çıktıolarak yalnızca bir dosya oluştursa bile, şablon kullanıldığında oluşturmak istediğiniz içerikten oluşabilir.

Şablon tarafından oluşturulan dosyalar, *template.json* yapılandırma dosyasında sağladığınız mantık ve ayarlara göre değiştirilebilir. Kullanıcı, seçenekleri `dotnet new <TEMPLATE>` komuta geçirerek bu ayarları geçersiz kılabilir. Özel mantığın yaygın bir örneği, şablon tarafından dağıtılan kod dosyasındaki bir sınıf veya değişken için ad sağlamaktır.

### <a name="templatejson"></a>template.json

*template.json* dosyası şablonun kök dizininde bir *.template.config* klasörüne yerleştirilir. Dosya şablon motoruna yapılandırma bilgileri sağlar. Minimum yapılandırma, işlevsel bir şablon oluşturmak için yeterli olan aşağıdaki tabloda gösterilen üyeleri gerektirir.

| Üye            | Tür          | Açıklama |
| ----------------- | ------------- | ----------- |
| `$schema`         | URI           | *template.json* dosyası için JSON şeması. JSON şemalarını destekleyen editörler şema belirtildiğinde JSON düzenleme özelliklerini etkinleştirin. Örneğin, [Visual Studio Code](https://code.visualstudio.com/) intelliSense etkinleştirmek için bu üye gerektirir. `http://json.schemastore.org/template`Bir değer kullanın. |
| `author`          | string        | Şablonun yazarı. |
| `classifications` | dizi(string) | Şablonu ararken bir kullanıcının şablonu bulmak için kullanabileceği sıfır veya daha fazla özellik. Sınıflandırmalar, komutu kullanarak üretilen şablonlar listesinde göründüğünde *Etiketler* sütununda `dotnet new -l|--list` da görünür. |
| `identity`        | string        | Bu şablon için benzersiz bir ad. |
| `name`            | string        | Kullanıcıların görmesi gereken şablonun adı. |
| `shortName`       | string        | Şablon adının gui üzerinden seçilmeden kullanıcı tarafından belirtildiği ortamlara uygulanan şablonu seçmek için varsayılan kısaltma adı. Örneğin, cli komutları ile bir komut istemi şablonları kullanırken kısa ad yararlıdır. |

*template.json* dosyası için tam şema [JSON Schema Store'da](http://json.schemastore.org/template)bulunur. *template.json* dosyası hakkında daha fazla bilgi [için, dotnet templating wiki](https://github.com/dotnet/templating/wiki)bakın.

#### <a name="example"></a>Örnek

Örneğin, burada iki içerik dosyası içeren bir şablon klasörü var: *console.cs* ve *readme.txt*. *Template.json* dosyasını içeren *.template.config* adlı gerekli klasör olduğunu unutmayın.

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

*template.json* dosyası aşağıdaki gibi görünür:

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

*Mytemplate* klasörü yüklenebilir bir şablon paketidir. Paket yüklendikten sonra `shortName` `dotnet new` komutu ile kullanılabilir. Örneğin, `dotnet new adatumconsole` geçerli `console.cs` klasöre `readme.txt` ve dosyaları çıktı olur.

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Şablonu NuGet paketine paketleme (nupkg dosyası)

Özel bir [şablon, dotnet paketi](dotnet-pack.md) komutu ve *.csproj* dosyasıyla birlikte paketlenir. Alternatif olarak, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) [nuget paketi](https://docs.microsoft.com/nuget/tools/cli-ref-pack) komutu ile birlikte bir *.nuspec* dosyası ile kullanılabilir. Ancak, NuGet Linux ve MacOS'ta Windows ve [Mono'da](https://www.mono-project.com/) .NET Framework gerektirir.

*.csproj* dosyası geleneksel kod-project *.csproj* dosyasından biraz farklıdır. Aşağıdaki ayarlara dikkat edin:

01. Ayar `<PackageType>` eklenir ve '' olarak `Template`ayarlanır.
01. Ayar `<PackageVersion>` eklenir ve geçerli bir [NuGet sürüm numarasına](/nuget/reference/package-versioning)ayarlanır.
01. Ayar `<PackageId>` eklenir ve benzersiz bir tanımlayıcıya ayarlanır. Bu tanımlayıcı şablon paketini kaldırmak için kullanılır ve şablon paketinizi kaydetmek için NuGet akışları tarafından kullanılır.
01. Genel meta veri ayarları `<Title>`ayarlanmalıdır: , `<Authors>`, `<Description>`, ve `<PackageTags>`.
01. Şablon `<TargetFramework>` işlemi tarafından üretilen ikili kullanılmasa bile ayar ayarlanmalıdır. Aşağıdaki örnekte ' olarak `netstandard2.0`ayarlanır.

*.nupkg* NuGet paketi biçimindeki şablon paketi, tüm şablonların paket içindeki *içerik* klasöründe depolansın. Oluşturulan *.nupkg'ın* şablon paketi olarak yüklenebilmesi için *.csproj* dosyasına eklenecek birkaç ayar daha vardır:

01. Ayar, `<IncludeContentInPack>` projenin `true` NuGet paketinde **içerik** olarak ayarlattığı herhangi bir dosyayı içerecek şekilde ayarlanmıştır.
01. Ayar, `<IncludeBuildOutput>` derleyici `false` tarafından oluşturulan tüm ikilileri NuGet paketinden hariç tutmak üzere ayarlanmıştır.
01. Ayar' `<ContentTargetFolders>` ı `content`' na göre ayarlar. Bu, **içerik** olarak ayarlanan dosyaların NuGet paketindeki *içerik* klasöründe depolandırılmasını sağlar. NuGet paketindeki bu klasör, dotnet şablon sistemi tarafından ayrıştırılır.

Tüm kod dosyalarının şablon projeniz tarafından derlenmesini hariç `<Compile Remove="**\*" />` tutmanın kolay bir yolu, proje dosyanızdaki öğeyi bir `<ItemGroup>` öğenin içinde kullanmaktır.

Şablon paketinizi yapılandırmanın kolay bir yolu, tüm şablonları tek tek klasörlere, sonra da her şablon klasörünü *.csproj* dosyanızla aynı dizinde bulunan *şablonlar* klasörünün içine koymaktır. Bu şekilde, şablonlara tüm dosya ve *klasörleri* **içerik**olarak eklemek için tek bir proje öğesi kullanabilirsiniz. Bir `<ItemGroup>` öğenin içinde `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` bir öğe oluşturun.

Aşağıda, yukarıdaki tüm yönergeleri izleyen bir örnek *.csproj* dosyası verilmiştir. *Şablonlar* alt klasörünü *içerik* paketi klasörüne paketler ve herhangi bir kod dosyasının derlenmesini hariç tutar.

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

Aşağıdaki örnekte, şablon paketi oluşturmak için *.csproj* kullanmanın dosya ve klasör yapısı gösterin. *MyDotnetTemplates.csproj* dosyası ve *şablonlar* klasörü her ikisi de *project_folder*adlı bir dizinin kökünde yer alır. *Şablonlar* klasörü iki şablon, *mytemplate1* ve *mytemplate2*içerir. Her şablonda içerik dosyaları ve *template.json* config dosyası içeren bir *.template.config* klasörü bulunur.

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

## <a name="installing-a-template"></a>Şablon yükleme

Bir paket yüklemek için [dotnet yeni -i|--install](dotnet-new.md) komutunu kullanın.

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>nuget.org'de depolanan bir NuGet paketinden şablon yüklemek için

Şablon paketi yüklemek için NuGet paket tanımlayıcısını kullanın.

```dotnetcli
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Yerel bir nupkg dosyasından şablon yüklemek için

*.nupkg* NuGet paket dosyasına giden yolu sağlayın.

```dotnetcli
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Dosya sistemi dizininden şablon yüklemek için

Şablonlar yukarıdaki örnekten *mytemplate1* klasörü gibi bir şablon klasöründen yüklenebilir. *.template.config* klasörünün klasör yolunu belirtin. Şablon dizinine giden yolun mutlak olması gerekmez. Ancak, bir klasörden yüklenen bir şablonu kaldırmak için mutlak bir yol gereklidir.

```dotnetcli
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a>Yüklü şablonların listesini alma

Diğer parametreler olmadan kaldır komutu, yüklenen tüm şablonları listeler.

```dotnetcli
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

Sonra öğelerin ilk `Currently installed items:` düzeyi, şablonu kaldırmada kullanılan tanımlayıcılardır. Ve yukarıdaki `Microsoft.DotNet.Common.ItemTemplates` örnekte, `Microsoft.DotNet.Common.ProjectTemplates.3.0` ve listelenir. Şablon bir dosya sistemi yolu kullanılarak yüklenmişse, bu tanımlayıcı *.template.config* klasörünün klasör yolu olacaktır.

## <a name="uninstalling-a-template"></a>Şablonu kaldırma

Paketi kaldırmak için [dotnet yeni -u|--kaldır](dotnet-new.md) komutunu kullanın.

Paket nuget beslemesi veya *doğrudan .nupkg* dosyası tarafından yüklenmişse, tanımlayıcıyı sağlayın.

```dotnetcli
dotnet new -u <NUGET_PACKAGE_ID>
```

Paket *.template.config* klasörüne bir yol belirterek yüklendiyse, paketi kaldırmak için bu **mutlak** yolu kullanın. `dotnet new -u` Komut tarafından sağlanan çıktıda şablonun mutlak yolunu görebilirsiniz. Daha fazla bilgi için yukarıdaki [yüklü şablonların listesini alın](#get-a-list-of-installed-templates) bölümüne bakın.

```dotnetcli
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Özel bir şablon kullanarak proje oluşturma

Şablon yüklendikten sonra, önceden yüklenmiş başka `dotnet new <TEMPLATE>` bir şablonda olduğu gibi komutu çalıştırarak şablonu kullanın. Şablon ayarlarında [options](dotnet-new.md#options) yapılandırdığınız şablona özgü seçenekler de dahil olmak `dotnet new` üzere, komuta seçenekler de belirtebilirsiniz. Şablonun kısa adını doğrudan komuta ver:

```dotnetcli
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Ayrıca bkz.

- [dotnet yeni (öğretici) için özel bir şablon oluşturma](../tutorials/cli-templates-create-item-template.md)
- [dotnet/templating GitHub repo Wiki](https://github.com/dotnet/templating/wiki)
- [dotnet/dotnet-şablon-örnekleri GitHub repo](https://github.com/dotnet/dotnet-template-samples)
- [Dotnet yeni için kendi şablonlarınızı oluşturma](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [json Schema Mağazası'nda *template.json* şema](http://json.schemastore.org/template)
