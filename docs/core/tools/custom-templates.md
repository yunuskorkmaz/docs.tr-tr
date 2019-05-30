---
title: Yeni dotnet için özel şablonlar
description: Herhangi bir türde .NET proje veya dosya için özel şablonlar hakkında bilgi edinin.
author: mairaw
ms.date: 08/11/2017
ms.openlocfilehash: 6ce53cab308ed404974e4d736e735bc82ac04fe6
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66299915"
---
# <a name="custom-templates-for-dotnet-new"></a>Yeni dotnet için özel şablonlar

[.NET Core SDK'sı](https://www.microsoft.com/net/download/core) ile kullanmak üzere önceden yüklenmiş birçok şablonu ile birlikte gelen [ `dotnet new` komut](dotnet-new.md). .NET Core 2.0 ile başlayarak, herhangi bir türde gibi bir uygulama, hizmet, aracı veya sınıf kitaplığı projesi için kendi özel şablonlarınızı oluşturabilirsiniz. Hatta çıkaran bir veya daha fazla bağımsız dosyaları, bir yapılandırma dosyası gibi bir şablon oluşturabilirsiniz.

Özel şablonlar akış, bir NuGet başvurarak herhangi bir NuGet üzerindeki bir NuGet paketini yükleyebilirsiniz *nupkg* doğrudan veya şablon içeren bir dosya sistemi dizin belirterek dosya. Şablon altyapısı değerleri değiştirin, içerir ve dosyaları ve bölgeler dosyaları dışarıda bırak olanak sağlar ve şablonunuzu kullanıldığında özel işlemleri yürüten özellikleri sunar.

Şablon altyapısı açık kaynaklıdır ve çevrimiçi kod deposundaki altındadır [dotnet/şablon](https://github.com/dotnet/templating/) GitHub üzerinde. Ziyaret [dotnet/dotnet-şablonu-samples](https://github.com/dotnet/dotnet-template-samples) şablonları örnekleri için depo. Üçüncü taraf şablonları dahil olmak üzere daha fazla şablon adresten [yeni dotnet şablonları](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) GitHub üzerinde. Özel şablon oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [yeni dotnet için kendi şablonlarınızı oluşturmak nasıl](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) ve [dotnet/şablon GitHub deposunu Wiki](https://github.com/dotnet/templating/wiki).

Bir kılavuz uygulayın ve bir şablon oluşturmak için bkz: [yeni dotnet için özel bir şablon oluşturma](~/docs/core/tutorials/create-custom-template.md) öğretici.

## <a name="configuration"></a>Yapılandırma

Şablon aşağıdaki bileşenlerden oluşur:

- Kaynak dosyalar ve klasörler
- Bir yapılandırma dosyası (*template.json*)

### <a name="source-files-and-folders"></a>Kaynak dosyalar ve klasörler

Kaynak dosyaları ve klasörleri kullanmak üzere hangi dosya ve klasörleri, istediğiniz şablon altyapısı dahil `dotnet new <TEMPLATE>` komutu yürütülür. Şablon altyapısı kullanmak üzere tasarlanmış *çalıştırılabilir projeleri* gibi kaynak kod projeleri oluşturmak için. Bu, birçok faydası vardır:

- Şablon motoru özel belirteçler projenizin kaynak koda eklemesine gerektirmez.
- Kod dosyaları, özel dosyaları değil veya şablon altyapısı ile çalışmak üzere herhangi bir şekilde değiştirdi. Bu nedenle, normalde projeleriyle çalışırken kullandığınız araçları da şablon içeriği ile çalışır.
- Oluşturun, çalıştırın ve herhangi diğer projeleriniz için yaptığınız gibi şablon projelerini hata ayıklama.
- Yalnızca ekleyerek bir şablonu var olan bir projeden hızlı bir şekilde oluşturabilirsiniz bir *template.json* projeye yapılandırma dosyası.

Şablonda depolanan dosya ve klasörleri .NET Core veya .NET Framework çözümleri gibi resmi .NET proje türleri için sınırlı değildir. Kaynak dosyalar ve klasörler, şablon kullanıldığında, şablon altyapısı gibi bir yapılandırma dosyası veya bir çözüm dosyası çıktısı için yalnızca bir dosya üretse oluşturmak istediğiniz tüm içeriklerin oluşabilir. Örneğin, içeren bir şablon oluşturabilirsiniz. bir *web.config* kaynak dosyası ve bir değişiklik oluşturur *web.config* projeleri için dosya şablonu kullanıldığı. Kaynak dosyalarda yapılan değişiklikler, sağladığınız ayarları ve mantıksal dayalı *template.json* yapılandırma dosyası kullanıcı tarafından sağlanan değerleri birlikte geçirilen seçenek olarak `dotnet new <TEMPLATE>` komutu.

### <a name="templatejson"></a>Template.JSON

*Template.json* dosya yerleştirilir bir *. template.config* şablonunun kök dizininde klasör. Dosya, şablon altyapısı yapılandırma bilgileri sağlar. Bir işlev şablonu oluşturmak yeterli olan aşağıdaki tabloda gösterilen üyeleri en az yapılandırma gerektirir.

| Üye            | Tür          | Açıklama |
| ----------------- | ------------- | ----------- |
| `$schema`         | URI           | JSON şemasını *template.json* dosya. Şema belirtildiğinde JSON şema desteği düzenleyicileri JSON düzenleme özelliklerini etkinleştirin. Örneğin, [Visual Studio Code](https://code.visualstudio.com/) IntelliSense'i etkinleştirmek bu üye gerektirir. Değeri kullanın `http://json.schemastore.org/template`. |
| `author`          | dize        | Şablon yazarı. |
| `classifications` | Array(String) | Sıfır veya daha fazla kullanıcı için arama yaparken şablonu bulmak için kullanıyor olabileceğiniz şablonun özelliklerini. Sınıflandırmalar da görünür *etiketleri* şablonları listesinde göründüğünde sütun üretilen kullanarak <code>dotnet new -l&#124;--list</code> komutu. |
| `identity`        | dize        | Bu şablon için benzersiz bir ad. |
| `name`            | dize        | Kullanıcılar görmelisiniz şablonunun adı. |
| `shortName`       | dize        | Şablon adı GUI seçili olmayan bir kullanıcı tarafından burada belirtilen ortam için geçerli bir şablon seçerek bir varsayılan toplu özellik. Örneğin, kısa ad şablonları bir komut isteminden CLI komutları ile kullanıldığında yararlıdır. |

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

İçin tam şema *template.json* dosya konumunda bulundu [JSON şema Store](http://json.schemastore.org/template).

## <a name="net-default-templates"></a>.NET varsayılan şablonları

Yüklediğinizde [.NET Core SDK'sı](https://www.microsoft.com/net/download/core)projeleri oluşturmak için yerleşik şablonlar üzerinde bir düzine Al ve dosyaları, dahil konsol uygulamaları, sınıf kitaplıkları, birim test projeleri, ASP.NET Core uygulamaları (dahil olmak üzere [Angular](https://angular.io/) ve [React](https://facebook.github.io/react/) projeler) ve yapılandırma dosyaları. Yerleşik şablonlar listelemek için yürütme `dotnet new` komutunu `-l|--list` seçeneği:

```console
dotnet new -l
```

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Bir NuGet paketine (nupkg dosyası) bir şablon paketleme

Şu anda, özel bir şablon ile Windows iyileştirmesiyle doludur [nuget.exe](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) (değil [dotnet paketi](dotnet-pack.md)). Platformlar arası paketleme için kullanmayı [NuGetizer 3000](https://github.com/NuGet/Home/wiki/NuGetizer-3000).

İle birlikte proje klasörünün içeriğini kendi *.template.config/template.json* dosya, adlı bir klasöre yerleştirilir *içerik*. Yanındaki *içeriği* klasör ekleme bir [ *nuspec* dosya](/nuget/create-packages/creating-a-package), bir paket içeriğini açıklayan ve NuGet paketi oluşturma işlemi sürücüleri XML bildirim dosyası olduğu. İçinde bir  **\<packageTypes >** öğesinde *nuspec* dosya, içeren bir  **\<packageType >** öğesi ile bir `name` öznitelik değerini `Template`. Her iki *içeriği* klasörü ve *nuspec* dosya aynı dizinde bulunması. Tabloda, en düşük gösterilmiştir *nuspec* dosya şablon bir NuGet paketi olarak üretmek için gerekli öğeler.

| Öğe            | Tür   | Açıklama |
| ------------------ | ------ | ----------- |
| **\<Yazarlar >**     | dize | Nuget.org profil adları eşleşen paketleri yazar, virgülle ayrılmış listesi. Yazarlar nuget.org NuGet galerisinde görüntülenir ve paketleri çapraz başvuru için aynı yazarları tarafından kullanılır. |
| **\<Açıklama >** | dize | Kullanıcı Arabirimi ekranı için paketinin uzun açıklaması. |
| **\<Kimliği >**          | dize | Nuget.org veya ne olursa olsun arasında benzersiz olması gereken büyük küçük harf duyarsız paket tanımlayıcısı galeri paketi bulunacağı. Kimlikleri, boşluk veya bir URL için geçerli olmayan ve genellikle .NET ad alanı kurallarına karakterler içeremez. Bkz: [benzersiz paket tanımlayıcısı seçme ve sürüm numarasını ayarlama](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) Kılavuzu. |
| **\<packageType >** | dize | Bu öğe içinde yerleştirileceği bir  **\<packageTypes >** öğesi arasında  **\<meta veri >** öğeleri. Ayarlama `name` özniteliği  **\<packageType >** öğesine `Template`. |
| **\<Sürüm >**     | dize | Ana.İkincil.yama aşağıdaki Paket sürümü. Sürüm numaraları, yayın öncesi son içerebilir, açıklandığı [yayın öncesi sürümleri](/nuget/create-packages/prerelease-packages#semantic-versioning) konu. |

Bkz: [.nuspec başvuru](/nuget/schema/nuspec) tamamlanmış *nuspec* dosya şeması. Bir örnek *nuspec* görünür bir şablon için dosya [yeni dotnet için özel bir şablon oluşturma](~/docs/core/tutorials/create-custom-template.md) öğretici.

[Paket oluşturma](/nuget/create-packages/creating-a-package#creating-the-package) kullanarak `nuget pack <PATH_TO_NUSPEC_FILE>` komutu.

## <a name="installing-a-template"></a>Bir şablon yüklenirken

Özel bir şablon başvurarak akışı herhangi bir NuGet üzerindeki NuGet paketinden yüklemek bir *nupkg* doğrudan veya bir şablon oluşturma yapılandırması içeren bir dosya sistemi dizin belirterek dosya. Kullanım `-i|--install` seçeneğini [yeni dotnet](dotnet-new.md) komutu.

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Bir şablon nuget.org depolanan bir NuGet paketini yüklemek için

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Bir şablon nupkg yerel dosyadan yüklemek için

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Bir şablon bir dosya sistemi dizinden yüklemek için

`FILE_SYSTEM_DIRECTORY` Projeyi içeren proje klasörü ve *. template.config* klasörü:

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="uninstalling-a-template"></a>Bir şablon kaldırma

Özel bir şablon bir NuGet paketi tarafından başvurarak kaldırın, `id` veya bir şablon oluşturma yapılandırması içeren bir dosya sistemi dizin belirterek. Kullanım `-u|--uninstall` yükleme seçeneğiyle [yeni dotnet](dotnet-new.md) komutu.

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Nuget.org depolanan bir NuGet paketinden bir şablonu kaldırmak için

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-local-nupkg-file"></a>Bir yerel nupkg dosyasından bir şablonu kaldırmak için

Şablonu kaldırmak için yolu kullanmaya çalışmayın *nupkg* dosya. Bir şablon kullanarak kaldırma girişimi `dotnet new -u <PATH_TO_NUPKG_FILE>` başarısız olur. Başvuru paketi tarafından kendi `id`:

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-file-system-directory"></a>Bir dosya sistemi dizinden bir şablonu kaldırmak için

`FILE_SYSTEM_DIRECTORY` Projeyi içeren proje klasörü ve *. template.config* klasör. Yolu mutlak yol olması gerekiyor belirtildi. Göreli bir yol başarısız bir şablon kullanarak kaldırmak çalışıyor. Daha fazla bilgi için [yeni dotnet](dotnet-new.md) makalesi.

```console
dotnet new -u <FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Özel bir şablon kullanarak bir proje oluşturun

Şablon yüklendikten sonra şablonu yürüterek kullanmak `dotnet new <TEMPLATE>` diğer önceden yüklenmiş şablonu olduğu gibi komutu. Belirtebilirsiniz [seçenekleri](dotnet-new.md#options) için `dotnet new` şablon ayarlarında yapılandırdığınız belirli şablon seçenekleri dahil olmak üzere komutu. Şablonun doğrudan komutuna kısa ad belirtin:

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni dotnet (eğitim) için özel bir şablon oluşturma](../tutorials/create-custom-template.md)
- [DotNet/şablon GitHub deposunu Wiki](https://github.com/dotnet/templating/wiki)
- [DotNet/dotnet-şablonu-örnekleri GitHub deposu](https://github.com/dotnet/dotnet-template-samples)
- [Dotnet için kendi şablonlarınızı yeni oluşturma](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [*Template.JSON* JSON şema Store şema](http://json.schemastore.org/template)
