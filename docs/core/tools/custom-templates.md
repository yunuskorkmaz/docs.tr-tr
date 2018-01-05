---
title: "Yeni dotnet için özel şablonlar"
description: "Her tür .NET proje veya dosyaları için özel şablonlar hakkında bilgi edinin."
keywords: "DotNet yeni, CLI, CLI komutu, .NET Core, şablon, şablonu oluşturma"
author: guardrex
ms.author: mairaw
ms.date: 08/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload: dotnetcore
ms.openlocfilehash: f2b712f1b8b7800f2f02c9529114e92f77e32286
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="custom-templates-for-dotnet-new"></a>Yeni dotnet için özel şablonlar

[.NET Core SDK](https://www.microsoft.com/net/download/core) ile kullanmak üzere önceden yüklenmiş birçok şablonu ile birlikte [ `dotnet new` komutu](dotnet-new.md). .NET Core 2.0 ile başlayarak, herhangi bir türde gibi bir uygulama, hizmet, aracı veya sınıf kitaplığı proje için kendi özel şablonlarınızı oluşturabilirsiniz. Hatta çıkarır bir veya daha fazla bağımsız dosyalarda, bir yapılandırma dosyası gibi bir şablon oluşturabilirsiniz.

Özel şablonlar akışı, bir NuGet başvurarak NuGet üzerinde bir NuGet paketi yükleyebilirsiniz *nupkg* doğrudan veya şablonu içeren bir dosya sistemi dizini belirterek dosya. Şablon motoru değerleri değiştirmek, içerir ve dosya ve bölgeler dosyaları dışarıda bırak olanak sağlar ve şablonunuzu kullanıldığında özel işleme işlemlerini yürütmek özellikleri sunar.

Şablon motoru açık kaynaklıdır ve çevrimiçi kod depo altındadır [dotnet/şablon](https://github.com/dotnet/templating/) github'da. Ziyaret [dotnet/dotnet-şablonu-samples](https://github.com/dotnet/dotnet-template-samples) şablonları örnekleri için depo. Üçüncü taraf şablonları dahil olmak üzere daha fazla şablon konumunda bulunan [yeni dotnet için kullanılabilir şablonlar](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) github'da. Özel şablon oluşturma ve kullanma hakkında daha fazla bilgi için bkz: [dotnet için kendi şablonlarınızı yeni oluşturma](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/) ve [dotnet/şablon GitHub deposuna Wiki](https://github.com/dotnet/templating/wiki).

İzlenecek yollar izleyin ve bir şablon oluşturmak için bkz: [dotnet için özel bir şablon yeni Oluştur](~/docs/core/tutorials/create-custom-template.md) Öğreticisi.

## <a name="configuration"></a>Yapılandırma

Bir şablon aşağıdaki bileşenlerden oluşur:

- Kaynak dosyalar ve klasörler
- Bir yapılandırma dosyası (*template.json*)

### <a name="source-files-and-folders"></a>Kaynak dosyalar ve klasörler

Kaynak dosyaları ve klasörleri kullanmak üzere hangi dosya ve klasörleri şablonu istediğiniz altyapısı dahil `dotnet new <TEMPLATE>` komutu yürütülene. Şablon motoru kullanmak üzere tasarlanmış *runnable projeleri* olarak kaynak projeleri oluşturmak için kodu. Bu, birkaç avantaj vardır:

- Şablon motoru projenizin kaynak koda özel belirteçler eklemesine gerektirmez.
- Kod dosyaları özel dosyaları veya şablon altyapısı ile çalışmak için herhangi bir şekilde değiştirdi. Bu nedenle, projeleri ile çalışırken, normalde kullandığınız araçları da şablon içeriği ile çalışır.
- Yapı, çalıştırmak ve herhangi diğer projelerinizi için yaptığınız gibi şablon projelerini hata ayıklama.
- Yalnızca ekleyerek bir şablonu varolan bir projeden hızlı bir şekilde oluşturabilirsiniz bir *template.json* projeye yapılandırma dosyası.

Şablonda depolanan dosya ve klasörleri resmi .NET proje türleri, .NET Core veya .NET Framework çözümleri gibi sınırlı değildir. Şablon kullanıldığında, bir yapılandırma dosyası veya bir çözüm dosyası gibi çıktısını için yalnızca bir dosyayı şablon motoru üreten olsa bile oluşturmak istediğiniz herhangi bir içerik kaynak dosyaları ve klasörleri oluşur. Örneğin, içeren bir şablon oluşturabilirsiniz bir *web.config* kaynak dosyası ve bir değiştirilmiş oluşturur *web.config* projeleri için şablon kullanıldığı dosyası. Kaynak dosyaları için yapılan değişiklikleri mantığı ve sağladığınız içinde ayarları dayanır *template.json* yapılandırma dosyası kullanıcı tarafından sağlanan değerler birlikte geçirilen seçenek olarak `dotnet new <TEMPLATE>` komutu.

### <a name="templatejson"></a>Template.JSON

*Template.json* dosya yerleştirilir bir *. template.config* şablonu kök dizinine klasöre. Dosya şablon motoru yapılandırma bilgileri sağlar. En düşük yapılandırmayı işlevsel bir şablon oluşturmak yeterli aşağıdaki tabloda gösterilen üyeler gerektirir.

| Üye            | Tür          | Açıklama |
| ----------------- | ------------- | ----------- |
| `$schema`         | URI           | İçin JSON şeması *template.json* dosya. Şema belirtildiğinde JSON şema desteği düzenleyicileri JSON düzenleme özellikleri etkinleştirin. Örneğin, [Visual Studio Code](https://code.visualstudio.com/) IntelliSense etkinleştirmek bu üye gerektirir. Değeri kullanın `http://json.schemastore.org/template`. |
| `author`          | dize        | Şablon yazar. |
| `classifications` | Array(String) | Sıfır veya daha fazla kullanıcı için arama yaparken şablonu bulmak için kullanabilir şablonu özelliklerini. Sınıflandırmalar da görünür *etiketleri* şablonları listesinde göründüğünde sütun üretilen kullanarak <code>dotnet new -l&#124;--list</code> komutu. |
| `identity`        | dize        | Bu şablon için benzersiz bir ad. |
| `name`            | dize        | Kullanıcıların görmelisiniz şablonunun adı. |
| `shortName`       | dize        | Şablon adı GUI seçili değilse, bir kullanıcı tarafından burada belirtilen ortamlar için geçerli şablonu seçilmesi bir varsayılan toplu özelliktir. Örneğin, bir komut isteminden şablonları CLI komutları ile kullanırken kısa ad yararlıdır. |

#### <a name="example"></a>Örnek:

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Catalina Garcia",
  "classifications": [ "Common", "Console" ],
  "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
  "name": "Garcia Software Console Application",
  "shortName": "garciaconsole"
}
```

Tam şeması *template.json* dosya konumunda bulunan [JSON şeması depolama](http://json.schemastore.org/template).

## <a name="net-default-templates"></a>.NET varsayılan şablonları

Yüklediğinizde [.NET Core SDK](https://www.microsoft.com/net/download/core)projeleri oluşturmak için yerleşik şablonlar üzerinde bir düzine almak ve konsol uygulamaları, sınıf kitaplıkları, birim dahil olmak üzere dosyaları, test projeleri, ASP.NET Core uygulamaları (de dahil olmak üzere [Angular](https://angular.io/) ve [tepki](https://facebook.github.io/react/) projeleri) ve yapılandırma dosyaları. Yerleşik şablonlar listelemek için yürütme `dotnet new` komutunu `-l|--list` seçeneği:

```console
dotnet new -l
```

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Bir NuGet paketine (nupkg dosyası) bir şablon paketleme

Windows ile özel bir şablon şu anda, paketlenmiş [nuget.exe](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) (değil [dotnet paketi](dotnet-pack.md)). Platformlar arası paketleme için kullanmayı [NuGetizer 3000](https://github.com/NuGet/Home/wiki/NuGetizer-3000).

İle birlikte proje klasörünün içeriğini kendi *.template.config/template.json* dosya, adlı bir klasöre yerleştirilir *içerik*. Yanına *içerik* klasörüne eklemek bir [ *nuspec* dosya](/nuget/create-packages/creating-a-package), bir paketin içeriğini açıklayan ve NuGet paketi oluşturma işlemi sürücüleri bir XML bildirim dosyası olduğu. İçinde bir  **\<packageTypes >** öğesinde *nuspec* içeriyor, dosya bir  **\<packageType >** öğesi ile bir `name` öznitelik değeri `Template`. Her iki *içerik* klasör ve *nuspec* dosya aynı dizinde bulunması. En düşük tablo gösterir *nuspec* dosya şablon bir NuGet paketi olarak üretmek için gereken öğeler.

| Öğe            | Tür   | Açıklama |
| ------------------ | ------ | ----------- |
| **\<yazarları >**     | dize | Nuget.org profil adları eşleşen paketleri yazarlar, virgülle ayrılmış listesi. Yazarları nuget.org NuGet galerisinde görüntülenir ve paketleri çapraz başvuru yapmak için aynı yazarlar tarafından kullanılır. |
| **\<Açıklama >** | dize | Paket UI görüntü için uzun bir açıklaması. |
| **\<Kimliği >**          | dize | Nuget.org ya da ihtiyacınız arasında benzersiz olması büyük küçük harf duyarsız paket tanımlayıcısı galeri paketi içindeki bulunacağı. Kimlikleri boşluk veya bir URL geçerli değil ve genellikle .NET ad alanı kurallarına karakter içerebilir. Bkz: [benzersiz paket tanımlayıcısı seçme ve sürüm numarasını ayarlama](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) Kılavuzu. |
| **\<packageType >** | dize | Bu öğe içine yerleştirin bir  **\<packageTypes >** öğesi arasında  **\<meta verileri >** öğeleri. Ayarlama `name` özniteliği  **\<packageType >** öğesine `Template`. |
| **\<Sürüm >**     | dize | Major.minor.patch desen aşağıdaki şekilde paketin sürümü. Sürüm numaraları, yayın öncesi soneki içerebilir, açıklandığı gibi [yayın öncesi sürümleri](/nuget/create-packages/prerelease-packages#semantic-versioning) konu. |

Bkz: [.nuspec başvuru](/nuget/schema/nuspec) tam için *nuspec* dosyası şeması. Örnek *nuspec* şablon görünür için dosya [dotnet için özel bir şablon yeni oluşturmak](~/docs/core/tutorials/create-custom-template.md) Öğreticisi.

[Paket oluşturma](/nuget/create-packages/creating-a-package#creating-the-package) kullanarak `nuget pack <PATH_TO_NUSPEC_FILE>` komutu.

## <a name="installing-a-template"></a>Bir şablon yükleme

Özel bir şablon başvurarak akış NuGet üzerinde bir NuGet paketi yükleyin bir *nupkg* doğrudan veya bir şablon yapılandırmasını içeren bir dosya sistemi dizini belirterek dosya. Kullanım `-i|--install` seçeneğini [dotnet yeni](dotnet-new.md) komutu.

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Bir şablon nuget.org depolanan bir NuGet paketi yüklemek için

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Bir şablon bir yerel nupkg dosyasından yüklemek için

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Bir dosya sistemi dizinden bir şablon yüklemek için

`FILE_SYSTEM_DIRECTORY` Projeyi içeren projeyi klasördür ve *. template.config* klasörü:

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="uninstalling-a-template"></a>Bir şablon kaldırma

Özel bir şablon bir NuGet paketi tarafından başvurarak kaldırma kendi `id` veya bir şablon yapılandırmasını içeren bir dosya sistemi dizini belirterek. Kullanım `-u|--uninstall` seçeneğiyle yüklemeniz [dotnet yeni](dotnet-new.md) komutu.

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Nuget.org depolanan NuGet paketinden bir şablonu kaldırmak için

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-local-nupkg-file"></a>Bir yerel nupkg dosyasından bir şablonu kaldırmak için

Şablonu kaldırmak istediğinizde, yolunu kullanma girişimi yok *nupkg* dosya. *Bir şablon kullanarak kaldırma işlemini denemeden `dotnet new -u <PATH_TO_NUPKG_FILE>` başarısız olur.* Paket tarafından başvuru kendi `id`:

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-file-system-directory"></a>Bir dosya sistemi dizinden bir şablonu kaldırmak için

`FILE_SYSTEM_DIRECTORY` Projeyi içeren projeyi klasördür ve *. template.config* klasörü:

```console
dotnet new -u <FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Özel bir şablon kullanarak proje oluşturma

Bir şablon yüklendikten sonra şablonu yürüterek kullanın `dotnet new <TEMPLATE>` diğer önceden yüklenmiş şablon gibi komutu. Ayrıca belirtebilirsiniz [seçenekleri](dotnet-new.md#options) için `dotnet new` şablon ayarlarını yapılandırdığınız şablon belirli seçenekleri de dahil olmak üzere komutu. Doğrudan komutuna şablonun kısa ad belirtin:

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Ayrıca bkz.

[Yeni dotnet (öğretici) için özel bir şablon oluşturma](../tutorials/create-custom-template.md)  
[DotNet/şablon GitHub deposuna Wiki](https://github.com/dotnet/templating/wiki)  
[DotNet/dotnet-şablonu-samples GitHub depo](https://github.com/dotnet/dotnet-template-samples)  
[Dotnet için kendi şablonlarınızı yeni oluşturma](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)  
[*Template.JSON* JSON şeması depolama şema](http://json.schemastore.org/template)  
