---
title: Dotnet için özel bir şablon yeni oluştur
description: Bu eğlenceli dotnet yeni komutu için özel bir şablon oluşturmayı öğrenin öğretici.
author: guardrex
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 9ff58634daa6d51c10df9a3c9a1af0fd6420c69c
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="create-a-custom-template-for-dotnet-new"></a>Dotnet için özel bir şablon yeni oluştur

Bu öğretici şunların nasıl yapıldığını gösterir için:

- Temel şablonunu var olan bir proje veya yeni bir konsol uygulama projesi oluşturun.
- Nuget.org veya yerel bir dağıtım şablonu paketi *nupkg* dosya.
- Yerel nuget.org şablon yükleme *nupkg* dosya ya da yerel dosya sistemi.
- Şablon kaldırın.

Bu öğreticiyi tam bir örnek üzerinden geçmek isterseniz, indirme [örnek proje şablonu](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package). Örnek şablon NuGet dağıtımı için yapılandırılmıştır.

İndirilen örnek dosya sistemi dağıtımı ile kullanmak istiyorsanız, aşağıdakileri yapın:

- İçeriğini taşımak *içerik* klasörü örnek bir düzey yukarı *GarciaSoftware.ConsoleTemplate.CSharp* klasör.
- Boş silme *içerik* klasör.
- Silme *nuspec* dosya.

## <a name="prerequisites"></a>Önkoşullar

- Yükleme [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) veya sonraki sürümler.
- Başvuru konusunu okuyun [yeni dotnet için özel şablonlar](../tools/custom-templates.md).

## <a name="create-a-template-from-a-project"></a>Bir şablonu bir proje oluşturun

Kullanım onaylanıp var olan bir proje derler ve çalıştıran veya yeni bir konsol uygulama projesi için sabit diskinizde bir klasör oluşturun. Bu öğretici proje klasörünün adını olduğunu varsayar *GarciaSoftware.ConsoleTemplate.CSharp* depolandığı *Documents\Templates* kullanıcının profilindeki. Eğitmen proje şablonu adı şu biçimdedir  *\<şirket adı >.\< Şablon türü >. \<Programlama dili >*, ancak proje ve şablonu istediğiniz herhangi bir şey adı boş.

1. Adlı proje kök klasör ekleme *. template.config*.
1. İçinde *. template.config* klasörü oluşturmak bir *template.json* şablonunuzu yapılandırmak için bir dosya. Daha fazla bilgi ve üye tanımları için *template.json* dosya için bkz: [yeni dotnet için özel şablonlar](../tools/custom-templates.md#templatejson) konu ve [ *template.json* JSON şeması depolama şema](http://json.schemastore.org/template).

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

Şablon tamamlandı. Bu noktada, şablon dağıtımı için iki seçeneğiniz vardır. Bu öğretici devam etmek için bir yol veya diğer seçin:

1. [NuGet dağıtım](#use-nuget-distribution): NuGet ya da yerel şablonunu yüklemek *nupkg* dosya ve yüklenmiş bir şablon kullanın.
2. [Dosya sistemi dağıtım](#use-file-system-distribution).

## <a name="use-nuget-distribution"></a>NuGet dağıtım kullanın

### <a name="pack-the-template-into-a-nuget-package"></a>Şablon bir NuGet paketi

1. NuGet paketi için bir klasör oluşturun. Öğretici, klasör adı için *GarciaSoftware.ConsoleTemplate.CSharp* kullanılan ve klasör içinde oluşturulan bir *Documents\NuGetTemplates* kullanıcının profilini klasöründe. Adlı bir klasör oluşturun *içerik* proje dosyalarını tutmak için yeni şablon klasörünü içinde.
1. İle birlikte proje klasörünüzdeki içeriğini kopyalayın, *.template.config/template.json* dosyası içine *içerik* oluşturduğunuz klasör.
1. Yanına *içerik* klasörüne eklemek bir [ *nuspec* dosya](/nuget/create-packages/creating-a-package). Bir paketin içeriğini açıklayan ve NuGet paketi oluşturma işlemi sürücüleri bir XML bildirim dosyası nuspec dosyasıdır.
   
   ![NuGet paketi düzenini gösteren dizin yapısı](./media/create-custom-template/nugetdirectorylayout.png)

1. İçinde bir  **\<packageTypes >** öğesinde *nuspec* içeriyor, dosya bir  **\<packageType >** öğesi ile bir `name` öznitelik değeri `Template`. Her iki *içerik* klasör ve *nuspec* dosya aynı dizinde bulunması. En düşük tablo gösterir *nuspec* dosya şablon bir NuGet paketi olarak üretmek için gereken öğeler.

   | Öğe            | Tür   | Açıklama |
   | ------------------ | ------ | ----------- |
   | **\<yazarları >**     | dize | Nuget.org profil adları eşleşen paketleri yazarlar, virgülle ayrılmış listesi. Yazarları nuget.org NuGet galerisinde görüntülenir ve paketleri çapraz başvuru yapmak için aynı yazarlar tarafından kullanılır. |
   | **\<Açıklama >** | dize | Paket UI görüntü için uzun bir açıklaması. |
   | **\<Kimliği >**          | dize | Nuget.org ya da ihtiyacınız arasında benzersiz olması büyük küçük harf duyarsız paket tanımlayıcısı galeri paketi içindeki bulunacağı. Kimlikleri boşluk veya bir URL geçerli değil ve genellikle .NET ad alanı kurallarına karakter içerebilir. Bkz: [benzersiz paket tanımlayıcısı seçme ve sürüm numarasını ayarlama](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) Kılavuzu. |
   | **\<packageType >** | dize | Bu öğe içine yerleştirin bir  **\<packageTypes >** öğesi arasında  **\<meta verileri >** öğeleri. Ayarlama `name` özniteliği  **\<packageType >** öğesine `Template`. |
   | **\<Sürüm >**     | dize | Major.minor.patch desen aşağıdaki şekilde paketin sürümü. Sürüm numaraları, yayın öncesi soneki içerebilir, açıklandığı gibi [yayın öncesi sürümleri](/nuget/create-packages/prerelease-packages#semantic-versioning). |

   Bkz: [.nuspec başvuru](/nuget/schema/nuspec) tam için *nuspec* dosyası şeması.

   *Nuspec* öğretici adlı için dosya *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* ve aşağıdaki içeriği içerir:

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

1. [Paket oluşturma](/nuget/create-packages/creating-a-package#creating-the-package) kullanarak `nuget pack <PATH_TO_NUSPEC_FILE>` komutu. Aşağıdaki komutu NuGet varlıklar tutan klasör konumunda varsayar *C:\Users\\\<kullanıcı > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*. Ancak klasörü, sisteminizde yerde yerleştirdiğiniz `nuget pack` komut yolu kabul *nuspec* dosyası:

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a>Paket için nuget.org yayımlama

Bir NuGet paketi yayımlamak için ' ndaki yönergeleri izleyin [oluşturma ve bir paketi yayımlamaya](/nuget/quickstart/create-and-publish-a-package#publish-the-package) konu. Ancak, hiçbir zaman yayımlandıktan sonra yalnızca delisted silinmeden gibi öğretici şablonu için NuGet yayımlama öneririz. NuGet paketi biçiminde sahip olduğunuza göre bir *nupkg* dosyası önerdiğimiz doğrudan yerel bilgisayardan şablonunu yüklemek için aşağıdaki yönergeleri izleyin *nupkg* dosya.

### <a name="install-the-template-from-a-nuget-package"></a>Şablonu bir NuGet paketi yükle

#### <a name="install-the-template-from-the-local-nupkg-file"></a>Yerel bilgisayardan şablonunu yüklemek *nupkg* dosyası

Şablondan yüklemek için *nupkg* , üretilen, dosya kullanım `dotnet new` komutunu `-i|--install` seçeneği ve yolunu girin *nupkg* dosyası:

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a>Şablon nuget.org depolanan bir NuGet paketi yükleyin

Bir şablon kullanım nuget.org depolanan bir NuGet paketi yükleyin isterseniz, `dotnet new` komutunu `-i|--install` seçeneği ve NuGet paketinin adını sağlayın:

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Örnek, yalnızca tanıtım amacıyla kullanılır. Hiç bir `GarciaSoftware.ConsoleTemplate.CSharp` nuget.org, NuGet paket ve yayımlama ve test şablonlardan NuGet kullanma öneririz yok. Komutu çalıştırırsanız, herhangi bir şablon yüklenir. Ancak, nuget.org için başvurarak yayımlanmadı bir şablon yükleyebilirsiniz *nupkg* önceki bölümde gösterildiği gibi doğrudan yerel dosya sisteminde dosya [yerel nupkg şablonunu yüklemek Dosya](#install-the-template-from-the-local-nupkg-file).

Bir şablon nuget.org bir paketin yüklemek nasıl dinamik örneği istiyorsanız kullanabileceğiniz [NUnit 3 şablonu dotnet yeni](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/). Bu şablon bir projeyi NUnit birim testi kullanacak şekilde ayarlar. Yüklemek için aşağıdaki komutu kullanın:

```console
dotnet new -i NUnit3.DotNetNew.Template
```

Liste zaman şablonlarıyla `dotnet new -l`, gördüğünüz *NUnit 3 Test projesi* kısa bir adı ile *nunit* şablon listesinde. Sonraki bölümde şablonu kullanmak hazırsınız.

![Diğer yüklü şablonlarıyla listelenen NUnit şablonu gösteren konsol penceresi](./media/create-custom-template/nunit1.png)

### <a name="create-a-project-from-the-template"></a>Bir proje şablonu oluşturma

Şablon Nuget'ten yüklendikten sonra şablonu yürüterek kullanmaya `dotnet new <TEMPLATE>` şablon motoru istediğiniz dizinin komutu animasyonun çıktı yerleştirilen (kullanmakta olduğunuz sürece `-o|--output` seçeneği belirli bir dizin belirtin). Daha fazla bilgi için bkz: [ `dotnet new` seçenekleri](~/docs/core/tools/dotnet-new.md#options). Şablonun kısa ad doğrudan tedarik `dotnet new` komutu. Bir proje NUnit şablonu oluşturmak için aşağıdaki komutu çalıştırın:

```console
dotnet new nunit
```

Konsol projesi oluşturulur ve projenin paketler geri yükleneceğini gösterir. Komutu çalıştırdıktan sonra proje kullanıma hazırdır.

![NUnit projesi oluşturur ve proje bağımlılıkları yükler gibi dotnet yeni komutunun çıkışını gösteren konsol penceresi](./media/create-custom-template/nunit2.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Nuget.org depolanan NuGet paketinden bir şablonu kaldırmak için

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Örnek, yalnızca tanıtım amacıyla kullanılır. Hiç bir `GarciaSoftware.ConsoleTemplate.CSharp` NuGet paketini nuget.org veya .NET Core SDK ile birlikte yüklenen. Komutu çalıştırırsanız, hiçbir paket/şablon kaldırılır ve şu özel durum alırsınız:
> 
> > Kaldırmak için bir şey 'GarciaSoftware.ConsoleTemplate.CSharp' adlı bulunamadı.

Yüklediyseniz [NUnit 3 şablonu dotnet yeni](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) ve istediğiniz kaldırmak için aşağıdaki komutu kullanın:

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a>Şablon yerel nupkg dosyadan kaldırın

Şablonu kaldırmak istediğinizde, yolunu kullanma girişimi yok *nupkg* dosya. *Bir şablon kullanarak kaldırma işlemini denemeden `dotnet new -u <PATH_TO_NUPKG_FILE>` başarısız olur.* Paket tarafından başvuru kendi `id`:

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a>Dosya sistemi dağıtım kullanın

Şablonu dağıtmak için proje şablonu klasörü bir konumda ağınızdaki kullanıcılar için erişilebilir yerleştirin. Kullanım `dotnet new` komutunu `-i|--install` seçeneği ve şablon klasörün yolunu belirtin (projeyi içeren projeyi klasörü ve *. template.config* klasörü).

Proje şablonu depolanır öğretici varsayar *belgeler/şablonları* kullanıcının profilini klasörü. Aşağıdaki yerine komutu şablonunu bu konumdan yüklemek \<kullanıcı > kullanıcının profil adı ile:

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a>Bir proje şablonu oluşturma

Şablon dosya sisteminden yüklendikten sonra şablonu yürüterek kullanmaya `dotnet new <TEMPLATE>` şablon motoru istediğiniz dizinin komutu animasyonun çıktı yerleştirilen (kullanmakta olduğunuz sürece `-o|--output` seçeneği belirli bir dizin belirtin). Daha fazla bilgi için bkz: [ `dotnet new` seçenekleri](~/docs/core/tools/dotnet-new.md#options). Şablonun kısa ad doğrudan tedarik `dotnet new` komutu.

Öğesinde oluşturulan yeni bir proje klasöründeki *C:\Users\\\<kullanıcı > \Documents\Projects\MyConsoleApp*, bir proje oluşturun `garciaconsole` şablonu:

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a>Şablon kaldırma

Yerel dosya sistemine şablon oluşturduysanız *C:\Users\\\<kullanıcı > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, kendisiyle kaldırmak `-u|--uninstall` anahtar ve yolu Şablon klasör:

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> Şablon, yerel dosya sisteminden kaldırmak için yol tam olarak nitelemek gerekir. Örneğin, *C:\Users\\\<kullanıcı > \Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* çalışır, ancak *./GarciaSoftware.ConsoleTemplate.CSharp* kapsayan klasörden almayacak.
> Ayrıca, şablonu yoldaki son sonlandırma dizin eğik çizgi eklemeyin.

## <a name="see-also"></a>Ayrıca bkz.

[DotNet/şablon GitHub deposuna Wiki](https://github.com/dotnet/templating/wiki)  
[DotNet/dotnet-şablonu-samples GitHub depo](https://github.com/dotnet/dotnet-template-samples)  
[Dotnet için kendi şablonlarınızı yeni oluşturma](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)  
[*Template.JSON* JSON şeması depolama şema](http://json.schemastore.org/template)  
