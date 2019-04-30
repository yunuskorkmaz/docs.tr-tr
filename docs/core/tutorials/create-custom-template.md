---
title: Yeni dotnet için özel bir şablon oluşturma
description: Bu eğlenceli dotnet yeni komutu için özel bir şablon oluşturmayı öğrenin öğretici.
author: guardrex
ms.date: 08/12/2017
ms.custom: seodec18
ms.openlocfilehash: 3b45a24c8a249eeb99fb1a4b14918483b978980b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647416"
---
# <a name="create-a-custom-template-for-dotnet-new"></a>Yeni dotnet için özel bir şablon oluşturma

Bu öğretici, nasıl gösterir için:

- Bir temel şablon, var olan bir proje veya yeni bir konsol uygulama projesi oluşturun.
- Nuget.org veya yerel bir dağıtım için bir şablon paketi *nupkg* dosya.
- Şablon yerel nuget.org adresinden yükleyin *nupkg* dosya ya da yerel dosya sistemi.
- Şablon kaldırın.

Bu öğreticide eksiksiz bir örnek ile devam etmek isterseniz, indirme [örnek proje şablonu](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package). Örnek şablonu, NuGet dağıtımı için yapılandırılmıştır.

Dosya sistemi dağıtımı ile indirilen örnek kullanmak istiyorsanız, aşağıdakileri yapın:

- İçeriği Taşı *içeriği* klasörü örnek bir düzey yukarı *GarciaSoftware.ConsoleTemplate.CSharp* klasör.
- Boş Sil *içeriği* klasör.
- Silme *nuspec* dosya.

## <a name="prerequisites"></a>Önkoşullar

- Yükleme [.NET Core 2.0 SDK'sını](https://www.microsoft.com/net/core) veya sonraki sürümler.
- Başvuru konusu okuma [yeni dotnet için özel şablonları](../tools/custom-templates.md).

## <a name="create-a-template-from-a-project"></a>Bir projeden bir şablon oluşturma

Kullanımı, onayladıktan varolan bir projeyi derler ve çalıştırır veya sabit sürücünüzdeki bir klasöre yeni bir konsol uygulama projesi oluşturun. Bu öğreticide, proje klasörünün adı olduğunu varsayar *GarciaSoftware.ConsoleTemplate.CSharp* depolandığı *Documents\Templates* kullanıcının profilinde. Öğretici projesinin şablon adı şu biçimdedir  *\<şirket adı >.\< Şablon türü >. \<Programlama dili >*, ancak projenizi ve şablon istediğiniz herhangi bir şey adı boş.

1. Adlı proje kök dizinine bir klasör eklemek *. template.config*.
1. İçinde *. template.config* klasör oluşturma bir *template.json* şablonunuzu yapılandırmak için bir dosya. Daha fazla bilgi ve üye tanımları için *template.json* bkz [yeni dotnet için özel şablonları](../tools/custom-templates.md#templatejson) konu ve [ *template.json* JSON şema Store şema](http://json.schemastore.org/template).

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

Şablonu tamamladınız. Bu noktada, şablon dağıtımı için iki seçeneğiniz vardır. Bu öğreticiye devam etmek için bir yol ya da diğerini seçin:

1. [NuGet dağıtım](#use-nuget-distribution): NuGet veya yerel şablonunu yüklemek *nupkg* dosya ve yüklü şablonu kullanın.
2. [Dosya sistemi dağıtım](#use-file-system-distribution).

## <a name="use-nuget-distribution"></a>NuGet dağıtım kullan

### <a name="pack-the-template-into-a-nuget-package"></a>Şablon bir NuGet paketi

1. NuGet paketi için bir klasör oluşturun. Öğretici, klasör adı için *GarciaSoftware.ConsoleTemplate.CSharp* kullanılır, ve klasörü içinde oluşturulur bir *Documents\NuGetTemplates* kullanıcı profili klasöründe. Adlı bir klasör oluşturun *içeriği* proje dosyalarını tutmak için yeni şablon klasörü içinde.
1. İle birlikte proje klasörünüzün içeriğini kopyalayın, *.template.config/template.json* dosyası içine *içeriği* oluşturduğunuz klasör.
1. Yanındaki *içeriği* klasör ekleme bir [ *nuspec* dosya](/nuget/create-packages/creating-a-package). Soubor nuspec bir paket içeriğini açıklayan ve NuGet paketi oluşturma işlemlerini yöneten bir XML bildirimi dosyasıdır.

   ![NuGet paketinin düzenini gösteren dizin yapısı](./media/create-custom-template/nuget-directory-layout.png)

1. İçinde bir  **\<packageTypes >** öğesinde *nuspec* dosya, içeren bir  **\<packageType >** öğesi ile bir `name` öznitelik değerini `Template`. Her iki *içeriği* klasörü ve *nuspec* dosya aynı dizinde bulunması. Tabloda, en düşük gösterilmiştir *nuspec* dosya şablon bir NuGet paketi olarak üretmek için gerekli öğeler.

   | Öğe            | Tür   | Açıklama |
   | ------------------ | ------ | ----------- |
   | **\<Yazarlar >**     | dize | Nuget.org profil adları eşleşen paketleri yazar, virgülle ayrılmış listesi. Yazarlar nuget.org NuGet galerisinde görüntülenir ve paketleri çapraz başvuru için aynı yazarları tarafından kullanılır. |
   | **\<Açıklama >** | dize | Kullanıcı Arabirimi ekranı için paketinin uzun açıklaması. |
   | **\<Kimliği >**          | dize | Nuget.org veya ne olursa olsun arasında benzersiz olması gereken büyük küçük harf duyarsız paket tanımlayıcısı galeri paketi bulunacağı. Kimlikleri, boşluk veya bir URL için geçerli olmayan ve genellikle .NET ad alanı kurallarına karakterler içeremez. Bkz: [benzersiz paket tanımlayıcısı seçme ve sürüm numarasını ayarlama](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) Kılavuzu. |
   | **\<packageType >** | dize | Bu öğe içinde yerleştirileceği bir  **\<packageTypes >** öğesi arasında  **\<meta veri >** öğeleri. Ayarlama `name` özniteliği  **\<packageType >** öğesine `Template`. |
   | **\<Sürüm >**     | dize | Ana.İkincil.yama aşağıdaki Paket sürümü. Sürüm numaraları, yayın öncesi son içerebilir, açıklandığı [yayın öncesi sürümleri](/nuget/create-packages/prerelease-packages#semantic-versioning). |

   Bkz: [.nuspec başvuru](/nuget/schema/nuspec) tamamlanmış *nuspec* dosya şeması.

   *Nuspec* öğretici adlı dosya *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* ve aşağıdaki içeriği içerir:

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns="http://schemas.microsoft.com/packaging/2012/06/nuspec.xsd">
     <metadata>
       <id>GarciaSoftware.ConsoleTemplate.CSharp</id>
       <version>1.0.0</version>
       <description>
         Creates the Garcia Software console app.
       </description>
       <authors>Catalina Garcia</authors>
       <packageTypes>
         <packageType name="Template" />
       </packageTypes>
     </metadata>
   </package>
   ```

1. [Paket oluşturma](/nuget/create-packages/creating-a-package#creating-the-package) kullanarak `nuget pack <PATH_TO_NUSPEC_FILE>` komutu. Aşağıdaki komutu NuGet varlıkları bulunduğu klasöre, olduğunu varsayar *C:\Users\\\<kullanıcı > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*. Ancak her yerde, sisteminizde klasörü yerleştirmek `nuget pack` komut yolu kabul *nuspec* dosyası:

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a>Nuget.org için paket yayımlama

Bir NuGet paketi yayımlamak için yönergeleri izleyin. [oluşturun ve paket yayımlama](/nuget/quickstart/create-and-publish-a-package#publish-the-package) konu. Ancak, hiçbir zaman yayımlandıktan sonra yalnızca delisted silinebilir gibi öğretici şablonu için NuGet yayımlama öneririz. NuGet paketi biçiminde olduğuna göre bir *nupkg* dosyası öneririz şablonu doğrudan yerel konumdan yüklemek için aşağıdaki yönergeleri izleyin *nupkg* dosya.

### <a name="install-the-template-from-a-nuget-package"></a>Bir NuGet paketi şablonu yükleyin

#### <a name="install-the-template-from-the-local-nupkg-file"></a>Yerel konumdan şablonunu yüklemek *nupkg* dosyası

Şablondan yüklemek için *nupkg* , üretilen, dosya kullanım `dotnet new` komutunu `-i|--install` seçenek ve yolunu belirtin *nupkg* dosyası:

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a>Nuget.org depolanan bir NuGet paketi şablonu yükleyin

Bir şablon kullanım nuget.org depolanan bir NuGet paketinden yüklemek istiyorsanız `dotnet new` komutunu `-i|--install` seçeneği ve NuGet paketinin adını sağlayın:

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Örnek yalnızca gösterim amaçlıdır. Hiç bir `GarciaSoftware.ConsoleTemplate.CSharp` nuget.org, NuGet paketini ve yayımlama ve test şablonlardan NuGet kullanma önermemekteyiz. Komutunu çalıştırın, hiçbir şablon yüklenir. Nuget.org için başvurarak yayımlanmadı bir şablon yükleyebilirsiniz ancak *nupkg* önceki bölümde gösterildiği gibi yerel dosya sisteminizde doğrudan dosya [yerel nupkg şablonu yükleme Dosya](#install-the-template-from-the-local-nupkg-file).

Bir şablon nuget.org adresindeki paketinden yüklemek canlı bir örneği isterseniz kullanabileceğiniz [NUnit 3 şablonu için yeni dotnet](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/). Bu şablon bir projeyi NUnit birim testi kullanılacak ayarlar. Yüklemek için aşağıdaki komutu kullanın:

```console
dotnet new -i NUnit3.DotNetNew.Template
```

Liste zaman şablonlarıyla `dotnet new -l`, gördüğünüz *NUnit 3 Test projesi* kısa adı ile *nunit* şablon listesinde. Sonraki bölümde şablonu kullanmaya hazırsınız.

![Diğer şablonları NUnit şablonla gösteren konsol penceresi](./media/create-custom-template/nunit-template-console-window.png)

### <a name="create-a-project-from-the-template"></a>Bir şablondan bir proje oluşturma

Şablon Nuget'ten yüklendikten sonra şablonu yürüterek kullanmak `dotnet new <TEMPLATE>` şablon Altyapısı'na istediğiniz dizine komuttan çıkış yerleştirilen (kullanmakta olduğunuz sürece `-o|--output` belirli bir dizini belirtmek için seçeneği). Daha fazla bilgi için [ `dotnet new` seçenekleri](~/docs/core/tools/dotnet-new.md#options). Şablonun kısa ad doğrudan tedarik `dotnet new` komutu. NUnit şablondan bir proje oluşturmak için aşağıdaki komutu çalıştırın:

```console
dotnet new nunit
```

Konsol projesi oluşturulur ve projenin paketleri geri olduğunu gösterir. Komutu çalıştırdıktan sonra projeyi kullanıma hazırdır.

![Konsol penceresinde proje bağımlılıklarını geri yükleme dahil olmak üzere yeni dotnet nunit çıktısını gösterir](./media/create-custom-template/dotnet-new-nunit-console-output.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Nuget.org depolanan bir NuGet paketinden bir şablonu kaldırmak için

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Örnek yalnızca gösterim amaçlıdır. Hiç bir `GarciaSoftware.ConsoleTemplate.CSharp` NuGet paketini nuget.org veya .NET Core SDK'sı ile yüklü. Komutu çalıştırırsanız, hiçbir paket/şablon kaldırılır ve şu özel durum alırsınız:
>
> > Bir şeyi kaldırmak için 'GarciaSoftware.ConsoleTemplate.CSharp' adlı nebyla nalezena.

Yüklediyseniz [NUnit 3 şablonu için yeni dotnet](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) isterseniz bunu kaldırın, aşağıdaki komutu kullanın:

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a>Şablon yerel nupkg dosyasından kaldırın.

Şablonu kaldırmak istiyorsanız, yolu kullanmaya çalışmayın *nupkg* dosya. *Bir şablon kullanarak kaldırma girişimi `dotnet new -u <PATH_TO_NUPKG_FILE>` başarısız olur.* Başvuru paketi tarafından kendi `id`:

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a>Dosya sistemi dağıtım kullanın

Şablonu dağıtmak için proje şablonu klasörüne bir konumda ağınızdaki kullanıcılar için erişilebilir yerleştirin. Kullanım `dotnet new` komutunu `-i|--install` seçenek ve şablon klasörü yolunu belirtin (projeyi içeren proje klasörü ve *. template.config* klasörü).

Bu öğretici proje şablonu depolanır varsayar *belgeleri/şablonları* kullanıcının profilin klasörü. Aşağıdaki komut değiştirme ile şablon o konumdan yüklemek \<kullanıcı > ile kullanıcının profil adı:

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a>Bir şablondan bir proje oluşturma

Şablon dosya sisteminden yüklendikten sonra şablonu yürüterek kullanmak `dotnet new <TEMPLATE>` şablon Altyapısı'na istediğiniz dizine komuttan çıkış yerleştirilen (kullanmakta olduğunuz sürece `-o|--output` belirli bir dizini belirtmek için seçeneği). Daha fazla bilgi için [ `dotnet new` seçenekleri](~/docs/core/tools/dotnet-new.md#options). Şablonun kısa ad doğrudan tedarik `dotnet new` komutu.

Oluşturulma yeni bir proje klasöründeki *C:\Users\\\<kullanıcı > \Documents\Projects\MyConsoleApp*, bir proje oluşturma `garciaconsole` şablonu:

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a>Şablonu Kaldır

Yerel dosya sisteminize şablon oluşturduysanız *C:\Users\\\<kullanıcı > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, kendisiyle kaldırma `-u|--uninstall` anahtar ve yolu Şablon klasör:

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Yerel dosya sisteminizden şablonu kaldırmak için yol tam olarak nitelemek gerekir. Örneğin, *C:\Users\\\<kullanıcı > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* içeren klasörden erişemez.
> Ayrıca, şablonu yoldaki son Sonlandırıcı directory eğik çizgi içermez.

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet/şablon GitHub deposunu Wiki](https://github.com/dotnet/templating/wiki)
- [DotNet/dotnet-şablonu-örnekleri GitHub deposu](https://github.com/dotnet/dotnet-template-samples)
- [Dotnet için kendi şablonlarınızı yeni oluşturma](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [*Template.JSON* JSON şema Store şema](http://json.schemastore.org/template)
