---
title: DotNet New için özel şablonlar
description: Herhangi bir .NET projesi veya dosya türü için özel şablonlar hakkında bilgi edinin.
author: thraka
ms.date: 05/20/2020
ms.openlocfilehash: 19855c99b240b66dfa819e70d4a1bee5c8ed14ed
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761921"
---
# <a name="custom-templates-for-dotnet-new"></a>DotNet New için özel şablonlar

[.NET Core SDK](https://dotnet.microsoft.com/download) , zaten yüklenmiş ve kullanıma hazırmış birçok şablon ile birlikte gelir. [ `dotnet new` Komut](dotnet-new.md) yalnızca bir şablonu kullanmanın ve ayrıca şablonların nasıl yükleneceğini ve kaldırılacağını gösteren bir yoldur. .NET Core 2,0 ile başlayarak, bir uygulama, hizmet, araç veya sınıf kitaplığı gibi herhangi bir proje türü için kendi özel şablonlarınızı oluşturabilirsiniz. Hatta bir yapılandırma dosyası gibi bir veya daha fazla bağımsız dosyayı çıkaran bir şablon oluşturabilirsiniz.

NuGet *. nupkg* dosyasına doğrudan başvurarak veya şablonu içeren bir dosya sistemi dizini belirterek herhangi bir NuGet akışında bir NuGet paketinden özel şablonlar yükleyebilirsiniz. Şablon altyapısı, şablon kullanılırken değerleri değiştirmenizi, dosyaları dahil ve dışlamalarını ve özel işleme işlemlerini yürütmeyi sağlayan özellikler sunar.

Şablon altyapısı açık kaynaktır ve çevrimiçi kod deposu GitHub 'da [DotNet/şablon](https://github.com/dotnet/templating/) oluşturma ' dır. Üçüncü taraflardan şablonlar da dahil olmak üzere diğer şablonlar, GitHub 'da [Yeni DotNet Için kullanılabilir şablonlarda](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) bulunur. Özel şablonlar oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [DotNet New için kendi şablonlarınızı oluşturma](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) ve [DotNet/şablon GitHub depo wiki](https://github.com/dotnet/templating/wiki).

> [!NOTE]
> Şablon örnekleri [DotNet/DotNet-Template-Samples](https://github.com/dotnet/dotnet-template-samples) GitHub deposunda mevcuttur. Bununla birlikte, şablonların nasıl çalıştığını öğrenmek için bu örnekler iyi bir kaynaktır, depo arşivlenir ve artık korunmaz. Örnekler güncel olmayabilir ve çalışmayabilir.

Bir yönergeyi izlemek ve şablon oluşturmak için, [DotNet yeni öğretici için özel şablon oluşturma](../tutorials/cli-templates-create-item-template.md) makalesine bakın.

### <a name="net-default-templates"></a>.NET varsayılan şablonları

[.NET Core SDK](https://dotnet.microsoft.com/download)yüklediğinizde, konsol uygulamaları, sınıf kitaplıkları, birim testi projeleri, ASP.NET Core uygulamalar ( [angular](https://angular.io/) ve [tepki](https://facebook.github.io/react/) verme projeleri dahil) ve yapılandırma dosyaları dahil olmak üzere proje ve dosya oluşturmaya yönelik bir düzine yerleşik şablon üzerinden karşılaşırsınız. Yerleşik şablonları listelemek için `dotnet new` komutunu `-l|--list` seçeneğiyle çalıştırın:

```dotnetcli
dotnet new --list
```

## <a name="configuration"></a>Yapılandırma

Şablon, aşağıdaki bölümlerden oluşur:

- Kaynak dosya ve klasörler.
- Bir yapılandırma dosyası (*Template. JSON*).

### <a name="source-files-and-folders"></a>Kaynak dosya ve klasörler

Kaynak dosya ve klasörler, şablon altyapısının komut çalıştırıldığında kullanmasını istediğiniz dosya ve klasörleri içerir `dotnet new <TEMPLATE>` . Şablon altyapısı, proje üretmek için kaynak kodu olarak *runacitme projelerini* kullanmak üzere tasarlanmıştır. Bunun birkaç avantajı vardır:

- Şablon altyapısı, projenizin kaynak koduna özel belirteçler eklemesine gerek yoktur.
- Kod dosyaları özel dosyalar değildir veya şablon altyapısıyla çalışmak için herhangi bir şekilde değiştirilmez. Bu nedenle, genellikle projelerle çalışırken kullandığınız araçlar şablon içeriğiyle de çalışır.
- Diğer projelerinizden herhangi biri için yaptığınız gibi şablon projelerinizi oluşturup hata ayıkladınız.
- Projeye bir *./em Template.exe veya JSON* yapılandırma dosyası ekleyerek, var olan bir projeden hızlıca bir şablon oluşturabilirsiniz.

Şablonda depolanan dosya ve klasörler, biçimsel .NET proje türleriyle sınırlı değildir. Şablon altyapısı çıkış olarak yalnızca bir dosya üretse bile, kaynak dosyalar ve klasörler, şablon kullanıldığında oluşturmak istediğiniz içerikten oluşabilir.

Şablon tarafından oluşturulan dosyalar, *Template. JSON* yapılandırma dosyasında sağladığınız mantık ve ayarlara göre değiştirilebilir. Kullanıcı, seçenekleri komuta geçirerek bu ayarları geçersiz kılabilir `dotnet new <TEMPLATE>` . Özel mantığın ortak bir örneği, bir şablon tarafından dağıtılan kod dosyasındaki bir sınıf veya değişken için bir ad sağlar.

### <a name="templatejson"></a>Template. JSON

*Template. JSON* dosyası, şablonun kök dizinindeki bir *. Template. config* klasörüne yerleştirilir. Dosya, şablon altyapısına yapılandırma bilgileri sağlar. En düşük yapılandırma, aşağıdaki tabloda gösterilen üyeleri gerektirir ve bu, işlevsel bir şablon oluşturmak için yeterlidir.

| Üye            | Tür          | Açıklama |
| ----------------- | ------------- | ----------- |
| `$schema`         | URI           | *Template. JSON* dosyası için JSON şeması. JSON şemalarını destekleyen düzenleyiciler, şema belirtildiğinde JSON düzenlemesi özelliklerini etkinleştirir. Örneğin, [Visual Studio Code](https://code.visualstudio.com/) IntelliSense 'i etkinleştirmek için bu üyeyi gerektirir. Değerini kullanın `http://json.schemastore.org/template` . |
| `author`          | string        | Şablonun yazarı. |
| `classifications` | dizi (dize) | Bir kullanıcının, arama yaparken şablonu bulmak için kullanabileceği şablonun sıfır veya daha fazla özelliği. Sınıflandırmalar, komutu kullanılarak oluşturulan şablonlar listesinde göründüğünde *Etiketler* sütununda da görüntülenir `dotnet new -l|--list` . |
| `identity`        | string        | Bu şablon için benzersiz bir ad. |
| `name`            | string        | Kullanıcıların göreceği şablonun adı. |
| `shortName`       | string        | Şablon adının Kullanıcı tarafından belirtildiği, GUI aracılığıyla seçilmemiş ortamlar için geçerli olan şablonu seçmek üzere varsayılan bir Özet adı. Örneğin, CLı komutlarıyla bir komut isteminden Şablonlar kullanılırken kısa ad yararlı olur. |

*Template. JSON* dosyasının tam şeması [JSON Şema deposunda](http://json.schemastore.org/template)bulunur. *Template. JSON* dosyası hakkında daha fazla bilgi için bkz. [DotNet şablon oluşturma wiki](https://github.com/dotnet/templating/wiki).

#### <a name="example"></a>Örnek

Örneğin, burada iki içerik dosyası içeren bir şablon klasörü verilmiştir: *Console.cs* ve *README. txt*. *Template. JSON* dosyasını içeren *. Template. config* adlı gerekli klasör olduğunu unutmayın.

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

*Template. JSON* dosyası aşağıdakine benzer şekilde görünür:

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

*MyTemplate* klasörü, yüklenebilir bir şablon paketidir. Paket yüklendikten sonra, `shortName` komutu ile kullanılabilir `dotnet new` . Örneğin, `dotnet new adatumconsole` `console.cs` ve `readme.txt` dosyalarını geçerli klasöre çıktı.

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Bir NuGet paketine (nupkg dosyası) şablon paketleme

Özel bir şablon [DotNet Pack](dotnet-pack.md) komutu ve bir *. csproj* dosyası ile paketlenmiştir. Alternatif olarak, [NuGet](https://docs.microsoft.com/nuget/tools/nuget-exe-cli-reference) , [NuGet Pack](https://docs.microsoft.com/nuget/tools/cli-ref-pack) komutuyla birlikte bir *. nuspec* dosyası ile birlikte kullanılabilir. Ancak NuGet, Linux ve MacOS 'ta Windows ve [mono](https://www.mono-project.com/) üzerinde .NET Framework gerektirir.

*. Csproj* dosyası geleneksel bir Code-Project *. csproj* dosyasından biraz farklıdır. Aşağıdaki ayarlara dikkat edin:

01. `<PackageType>`Ayar eklenir ve olarak ayarlanır `Template` .
01. `<PackageVersion>`Ayar eklenir ve geçerli bir [NuGet sürüm numarasına](/nuget/reference/package-versioning)ayarlanır.
01. `<PackageId>`Ayar eklenir ve benzersiz bir tanımlayıcıya ayarlanır. Bu tanımlayıcı, şablon paketini kaldırmak için kullanılır ve NuGet akışları tarafından şablon paketinizi kaydetmek için kullanılır.
01. Genel meta veri ayarları ayarlanmalıdır: `<Title>` , `<Authors>` , `<Description>` , ve `<PackageTags>` .
01. `<TargetFramework>`Şablon işlemi tarafından üretilen ikilinin kullanılmasa bile, ayarın ayarlanması gerekir. Aşağıdaki örnekte olarak ayarlanır `netstandard2.0` .

*. Nupkg* NuGet paketi biçimindeki bir şablon paketi, tüm şablonların paket içindeki *içerik* klasöründe depolanmasını gerektirir. Oluşturulan *. nupkg* 'nin bir şablon paketi olarak yüklenememesini sağlamak için bir *. csproj* dosyasına eklemenin daha fazla ayarı vardır:

01. `<IncludeContentInPack>`Ayar, `true` projenin, NuGet paketine **içerik** olarak ayarlandığı herhangi bir dosyayı içerecek şekilde ayarlanır.
01. `<IncludeBuildOutput>`Ayar, `false` NuGet paketinden derleyici tarafından oluşturulan tüm ikilileri dışarıda bırakacak şekilde ayarlanır.
01. `<ContentTargetFolders>`Ayar olarak ayarlanır `content` . Bu, **içerik** olarak ayarlanmış dosyaların NuGet paketindeki *içerik* klasörüne depolandığından emin olur. NuGet paketindeki bu klasör DotNet şablon sistemi tarafından ayrıştırılır.

Tüm kod dosyalarının şablon projeniz tarafından derlenmesinden dışlanmasını sağlamanın kolay bir yolu `<Compile Remove="**\*" />` , proje dosyanızdaki öğeyi bir öğe içinde kullanmaktır `<ItemGroup>` .

Şablon paketinizi oluşturmanın kolay bir yolu, tüm şablonları tek tek klasörlere koymak ve ardından, *. csproj* dosyanız ile aynı dizinde bulunan *bir şablon klasörünün içindeki her bir şablon* klasörünü kullanmaktır. Bu şekilde, tek bir proje öğesi kullanarak *şablonlarda* tüm dosya ve klasörleri **içerik**olarak ekleyebilirsiniz. `<ItemGroup>`Öğesinin içinde bir `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />` öğe oluşturun.

Yukarıdaki tüm yönergeleri izleyen örnek bir *. csproj* dosyası aşağıda verilmiştir. *Şablonlar* alt klasörünü *içerik* paketi klasörüne paketler ve tüm kod dosyalarını derlenmeden dışlar.

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

Aşağıdaki örnekte, bir şablon paketi oluşturmak için *. csproj* kullanarak dosya ve klasör yapısı gösterilmektedir. *MyDotnetTemplates. csproj* dosya ve *şablonlar* klasörü, *project_folder*adlı bir dizinin kökünde bulunur. *Şablonlar* klasörü, *mytemplate1* ve *mytemplate2*olmak üzere iki şablon içerir. Her şablonda, bir *Template. JSON* yapılandırma dosyası olan içerik dosyaları ve *. Template. config* klasörü bulunur.

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

Bir paket yüklemek için [DotNet New-i |--Install](dotnet-new.md) komutunu kullanın.

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Nuget.org adresinde depolanan bir NuGet paketinden şablon yüklemek için

Bir şablon paketini yüklemek için NuGet paket tanımlayıcısını kullanın.

```dotnetcli
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Yerel nupkg dosyasından bir şablon yüklemek için

*. Nupkg* NuGet paket dosyasının yolunu belirtin.

```dotnetcli
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Bir dosya sistemi dizininden şablon yüklemek için

Şablonlar, yukarıdaki örnekteki *mytemplate1* klasörü gibi bir şablon klasöründen yüklenebilir. *. Template. config* klasörünün klasör yolunu belirtin. Şablon dizini yolunun mutlak olması gerekmez. Ancak, bir klasörden yüklenen bir şablonu kaldırmak için mutlak bir yol gereklidir.

```dotnetcli
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a>Yüklü şablonların bir listesini alın

Kaldırma komutu, başka parametreler olmadan, tüm yüklü şablonları listeler.

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

Sonraki öğelerin ilk düzeyi, `Currently installed items:` bir şablonu kaldırma bölümünde kullanılan tanımlayıcılardır. Ve yukarıdaki örnekteki `Microsoft.DotNet.Common.ItemTemplates` ve `Microsoft.DotNet.Common.ProjectTemplates.3.0` listelenmiştir. Şablon bir dosya sistemi yolu kullanılarak yüklenmişse, bu tanımlayıcı *. Template. config* klasörünün klasör yolu olacaktır.

## <a name="uninstalling-a-template"></a>Bir şablonu kaldırma

Bir paketi kaldırmak için [DotNet New-u |--Uninstall](dotnet-new.md) komutunu kullanın.

Paket, bir NuGet akışı veya doğrudan bir *. nupkg* dosyası tarafından yüklendiyse, tanımlayıcıyı sağlayın.

```dotnetcli
dotnet new -u <NUGET_PACKAGE_ID>
```

Paket *. Template. config* klasörü için bir yol belirtilerek yüklendiyse, paketi kaldırmak için bu **mutlak** yolu kullanın. Şablonun mutlak yolunu komut tarafından belirtilen çıkışta görebilirsiniz `dotnet new -u` . Daha fazla bilgi için yukarıdaki [yüklü şablonlar listesini al](#get-a-list-of-installed-templates) bölümüne bakın.

```dotnetcli
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Özel şablon kullanarak proje oluşturma

Bir şablon yüklendikten sonra, `dotnet new <TEMPLATE>` başka bir önceden yüklenmiş şablonla yaptığınız gibi komutu yürüterek şablonu kullanın. Ayrıca [options](dotnet-new.md#options) `dotnet new` , şablon ayarlarında yapılandırdığınız şablona özgü seçenekler dahil olmak üzere komut için seçenekler de belirtebilirsiniz. Şablonun kısa adını doğrudan komuta sağlayın:

```dotnetcli
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet New için özel şablon oluşturma (öğretici)](../tutorials/cli-templates-create-item-template.md)
- [DotNet/şablon oluşturma GitHub deposu wiki](https://github.com/dotnet/templating/wiki)
- [DotNet/DotNet-şablon-örnek GitHub deposu](https://github.com/dotnet/dotnet-template-samples)
- [DotNet New için kendi şablonlarınızı oluşturma](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [JSON Şema deposunda *Template. JSON* şeması](http://json.schemastore.org/template)
