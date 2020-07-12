---
title: " .NET Core araçları"
description: .NET Core araçları 'nı yüklemek, kullanmak, güncelleştirmek ve kaldırmak. Küresel araçlar, araç yolu araçları ve yerel araçları içerir.
author: KathleenDollard
ms.date: 02/12/2020
ms.openlocfilehash: 583dbb461543d1efb7328d55f6ecce4a99afcaca
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226614"
---
# <a name="how-to-manage-net-core-tools"></a>.NET Core araçlarını yönetme

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

.NET Core Aracı, konsol uygulaması içeren özel bir NuGet paketidir. Aşağıdaki yollarla makinenize bir araç yüklenebilir:

* Genel bir araç olarak.

  Araç ikilileri, PATH ortam değişkenine eklenen bir varsayılan dizine yüklenir. Aracı, konumunu belirtmeden makinedeki herhangi bir dizinden çağırabilirsiniz. Makinedeki tüm dizinler için bir aracın bir sürümü kullanılır.

* Özel bir konumda (araç yolu aracı olarak da bilinir) genel bir araç olarak.

  Araç ikilileri, belirttiğiniz bir konuma yüklenir. Aracı, yükleme dizininden ya da komut adı ile dizin sağlayarak ya da yolu PATH ortam değişkenine ekleyerek çağırabilirsiniz. Makinedeki tüm dizinler için bir aracın bir sürümü kullanılır.

* Yerel bir araç olarak (.NET Core SDK 3,0 ve üzeri için geçerlidir).

  Araç ikilileri bir varsayılan dizine yüklenir. Aracı, yükleme dizininden veya alt dizinlerinden herhangi birine çağırabilirsiniz. Farklı dizinler aynı aracın farklı sürümlerini kullanabilir.
  
  .NET CLı, bir dizine yerel olarak hangi araçların yüklendiğini izlemek için bildirim dosyalarını kullanır. Bildirim dosyası, bir kaynak kod deposunun kök dizininde kaydedildiğinde, bir katkıda bulunan depoyu kopyalayabilir ve bildirim dosyalarında listelenen tüm araçları yükleyen tek bir .NET Core CLI komutu çağırabilirler.

> [!IMPORTANT]
> .NET Core araçları tam güvende çalışır. Yazara güvenmediğiniz müddetçe .NET Core aracını yüklemeyin.

## <a name="find-a-tool"></a>Araç bulun

Şimdilik, .NET Core bir araç arama özelliğine sahip değildir. Araç bulmak için bazı yollar şunlardır:

* [Natemcmaster/DotNet-Tools](https://github.com/natemcmaster/dotnet-tools) GitHub deposundaki araçların listesine bakın.
* .NET araçları aramak için [araç al](https://www.toolget.net/) 'ı kullanın.
* [DotNet/aspnetcore GitHub deposunun Araçlar dizininde](https://github.com/dotnet/aspnetcore/tree/master/src/Tools)ASP.NET Core ekibi tarafından oluşturulan araçların kaynak koduna bakın.
* [.NET Core DotNet tanılama araçları](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools)' nın tanılama araçları hakkında bilgi edinin.
* [NuGet](https://www.nuget.org) Web sitesinde arama yapın. Ancak, NuGet sitesi henüz araç paketleri için arama yapmanızı sağlayan bir özelliğe sahip değildir.

## <a name="check-the-author-and-statistics"></a>Yazarı ve istatistikleri denetleme

.NET Core araçları tam güvende çalıştırıldıklarından ve küresel araçlar PATH ortam değişkenine eklendiğinden, bunlar çok güçlü olabilir. Güvenmediğiniz kişilerden araç indirmeyin.

Araç NuGet üzerinde barındırılıyorsa, aracı arayarak yazarı ve istatistikleri kontrol edebilirsiniz.

## <a name="install-a-global-tool"></a>Küresel bir araç yükler

Bir aracı genel araç olarak yüklemek için, `-g` `--global` Aşağıdaki örnekte gösterildiği gibi [DotNet aracının Install](dotnet-tool-install.md)veya seçeneğini kullanın:

```dotnetcli
dotnet tool install -g dotnetsay
```

Çıktı, aşağıdaki örneğe benzer şekilde aracı ve yüklü sürümü çağırmak için kullanılan komutu gösterir:

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

Bir araç ikililerinin varsayılan konumu işletim sistemine bağlıdır:

| İşletim Sistemi          | Yol                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

SDK ilk çalıştırıldığında, bu konum kullanıcının yoluna eklenir, bu nedenle genel araçlar araç konumunu belirtmeden herhangi bir dizinden çağrılabilir.

Araç erişimi, makineye genel değil, kullanıcıya özeldir. Genel araç yalnızca aracı yükleyen kullanıcı tarafından kullanılabilir.

### <a name="install-a-global-tool-in-a-custom-location"></a>Özel bir konuma genel araç yükler

Bir aracı özel bir konuma genel araç olarak yüklemek için, `--tool-path` Aşağıdaki örneklerde gösterildiği gibi [DotNet araç install](dotnet-tool-install.md)seçeneğini kullanın.

Windows'da:

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

Linux veya macOS 'ta:

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

.NET Core SDK, bu konumu otomatik olarak PATH ortam değişkenine eklemez. [Bir araç yolu aracını çağırmak](#invoke-a-tool-path-tool)için aşağıdaki yöntemlerden birini kullanarak komutun kullanılabilir olduğundan emin olmanız gerekir:

* Yükleme dizinini PATH ortam değişkenine ekleyin.
* Aracı çağırdığınızda aracın tam yolunu belirtin.
* Yükleme dizini içinden aracı çağırın.

## <a name="install-a-local-tool"></a>Yerel bir araç yükler

**.NET Core 3,0 SDK ve üzeri için geçerlidir.**

Yalnızca yerel erişim için bir araç yüklemek üzere (geçerli dizin ve alt dizinler için), aracın bir araç bildirim dosyasına eklenmesi gerekir. Bir araç bildirim dosyası oluşturmak için şu komutu çalıştırın `dotnet new tool-manifest` :

```dotnetcli
dotnet new tool-manifest
```

Bu komut, *. config* dizininde *dotnet-tools.js* adlı bir bildirim dosyası oluşturur. Bildirim dosyasına yerel bir araç eklemek için, [DotNet aracı install](dotnet-tool-install.md) komutunu kullanın ve **omit** `--global` `--tool-path` Aşağıdaki örnekte gösterildiği gibi, ve seçeneklerini atlayın:

```dotnetcli
dotnet tool install dotnetsay
```

Komut çıktısı, aşağıdaki örneğe benzer şekilde, yeni yüklenen aracın hangi bildirim dosyasına olduğunu gösterir:

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

Aşağıdaki örnekte, iki yerel araç yüklü olan bir bildirim dosyası gösterilmektedir:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    },
    "dotnetsay": {
      "version": "2.1.3",
      "commands": [
        "dotnetsay"
      ]
    }
  }
}
```

Genellikle deponun kök dizinine yerel bir araç eklersiniz. Bildirim dosyasını depoya iade ettikten sonra, depodan kod kullanıma alan geliştiriciler en son bildirim dosyasını alır. Bildirim dosyasında listelenen tüm araçları yüklemek için şu komutu çalıştırırlar `dotnet tool restore` :

```dotnetcli
dotnet tool restore
```

Çıktı hangi araçların geri yüklendiğini gösterir:

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a>Belirli bir araç sürümünü yükler

Bir aracın yayın öncesi sürümünü veya belirli bir sürümünü yüklemek için, `--version` Aşağıdaki örnekte gösterildiği gibi seçeneğini kullanarak sürüm numarasını belirtin:

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a>Araç kullanma

Bir aracı çağırmak için kullandığınız komut, yüklediğiniz paketin adından farklı olabilir. Geçerli Kullanıcı için makinede yüklü olan tüm araçları göstermek için [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanın:

```dotnetcli
dotnet tool list
```

Çıktı, aşağıdaki örneğe benzer şekilde her bir aracın sürümünü ve komutunu gösterir:

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

Bu örnekte gösterildiği gibi listede yerel araçlar gösterilmektedir. Genel araçları görmek için `--global` seçeneğini kullanın ve araç yolu araçlarını görmek için `--tool-path` seçeneğini kullanın.

### <a name="invoke-a-global-tool"></a>Küresel bir araç çağır

Genel araçlar için, araç komutunu kendi kendine kullanın. Örneğin, komut `dotnetsay` veya ise `dotnet-doc` , bu, komutu çağırmak için kullandığınız şeydir:

```console
dotnetsay
dotnet-doc
```

Komut önekiyle başlıyorsa `dotnet-` , aracı çağırmak için alternatif bir yol, `dotnet` komutunu kullanmak ve araç komut önekini atlamanızı sağlar. Örneğin, komut ise, `dotnet-doc` aşağıdaki komut aracı çağırır:

```dotnetcli
dotnet doc
```

Ancak, aşağıdaki senaryoda `dotnet` küresel bir araç çağırmak için komutunu kullanamazsınız:

* Küresel bir araç ve yerel bir araç tarafından önekli aynı komut vardır `dotnet-` .
* Genel aracı yerel araç kapsamında olan bir dizinden çağırmak istiyorsunuz.

Bu senaryoda `dotnet doc` ve `dotnet dotnet-doc` Yerel Aracı çağırın. Genel aracı çağırmak için, komutu kendi başına kullanın:

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a>Araç yolu aracı çağırma

Seçeneği kullanılarak yüklenen küresel bir aracı çağırmak için `tool-path` , [Bu makalede daha önce](#install-a-global-tool-in-a-custom-location)anlatıldığı gibi komutun kullanılabilir olduğundan emin olun.

### <a name="invoke-a-local-tool"></a>Yerel bir araç çağır

Yerel bir aracı çağırmak için, `dotnet` yükleme dizini içinden komutunu kullanmanız gerekir. `dotnet tool run <COMMAND_NAME>`Aşağıdaki örneklerde gösterildiği gibi Long formunu () veya kısa biçimi ( `dotnet <COMMAND_NAME>` ) kullanabilirsiniz:

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

Komutun öneki varsa `dotnet-` , aracı çağırdığınızda öneki dahil edebilir veya atlayabilirsiniz. Örneğin, komut ise `dotnet-doc` Aşağıdaki örneklerden herhangi biri yerel aracı çağırır:

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a>Bir aracı güncelleştirme

Bir aracın güncelleştirilmesi, en son kararlı sürümle birlikte kaldırılıp yeniden yüklenmesini içerir. Bir aracı güncelleştirmek için, bu aracı yüklemek için kullandığınız seçenekle [DotNet araç Update](dotnet-tool-update.md) komutunu kullanın:

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

Yerel bir araç için SDK, geçerli dizin ve üst dizinlere bakarak paket KIMLIĞINI içeren ilk bildirim dosyasını bulur. Herhangi bir bildirim dosyasında böyle bir paket KIMLIĞI yoksa, SDK en yakın bildirim dosyasına yeni bir giriş ekler.

## <a name="uninstall-a-tool"></a>Araç kaldırma

Bir aracı, aracı yüklemek için kullandığınız seçenekle [DotNet Aracı kaldırma](dotnet-tool-uninstall.md) komutunu kullanarak kaldırın:

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path <packagename>
dotnet tool uninstall <packagename>
```

Yerel bir araç için SDK, geçerli dizin ve üst dizinlere bakarak paket KIMLIĞINI içeren ilk bildirim dosyasını bulur.

## <a name="get-help-and-troubleshoot"></a>Yardım alın ve sorun giderin

Kullanılabilir komutların bir listesini almak için `dotnet tool` aşağıdaki komutu girin:

```dotnetcli
dotnet tool --help
```

Araç kullanım yönergelerini almak için aşağıdaki komutlardan birini girin veya aracın Web sitesini görüntüleyin:

```dotnetcli
<command> --help
dotnet <command> --help
```

Bir araç yüklenemediğinde veya çalışmazsa, bkz. [.NET Core araç kullanımı sorunlarını giderme](troubleshoot-usage-issues.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: .NET Core CLI kullanarak bir .NET Core aracı oluşturma](global-tools-how-to-create.md)
- [Öğretici: .NET Core CLI kullanarak .NET Core küresel aracı 'nı yükleyip kullanın](global-tools-how-to-use.md)
- [Öğretici: .NET Core CLI kullanarak bir .NET Core yerel aracı yükleyip kullanın](local-tools-how-to-use.md)
