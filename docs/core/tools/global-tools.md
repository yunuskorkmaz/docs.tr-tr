---
title: .NET Çekirdek araçları
description: .NET Core araçlarının nasıl yüklenir, kullanılır, güncellenir ve kaldırılır. Genel araçları, araç yolu araçlarını ve yerel araçları kapsar.
author: KathleenDollard
ms.date: 02/12/2020
ms.openlocfilehash: 2f0101c6385c41eda49bcb2458428c1f14552617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847799"
---
# <a name="how-to-manage-net-core-tools"></a>.NET Core araçları nasıl yönetilir?

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

.NET Core aracı, konsol uygulaması içeren özel bir NuGet paketidir. Bir alet makinenize aşağıdaki yollarla takılabilir:

* Küresel bir araç olarak.

  Araç ikilileri, PATH ortamı değişkenine eklenen varsayılan bir dizine yüklenir. Aracı konumunu belirtmeden makinedeki herhangi bir dizinden çağırabilirsiniz. Bir aletin bir sürümü makinedeki tüm dizinler için kullanılır.

* Özel bir konumda genel bir araç olarak (araç yolu aracı olarak da bilinir).

  Araç ikilileri belirttiğiniz bir konuma yüklenir. Aracı yükleme dizininden veya komut adı ile dizini sağlayarak veya dizini PATH ortamı değişkenine ekleyerek çağırabilirsiniz. Bir aletin bir sürümü makinedeki tüm dizinler için kullanılır.

* Yerel bir araç olarak (.NET Core SDK 3.0 ve sonrası için geçerlidir).

  Araç ikilileri varsayılan bir dizinde yüklenir. Aracı yükleme dizininden veya alt dizinişlerinden çağırırsınız. Farklı dizinler aynı aracın farklı sürümlerini kullanabilir.
  
  .NET CLI, hangi araçların bir dizine yerel olarak yüklenmiş olarak yüklendiğine göre bildirim dosyalarını kullanır. Bildirim dosyası bir kaynak kodu deposunun kök dizinine kaydedildiğinde, katılımcı depoyu klonlayabilir ve bildirim dosyalarında listelenen tüm araçları yükleyen tek bir .NET Core CLI komutunu çağırabilir.

> [!IMPORTANT]
> .NET Core araçları tam güven içinde çalışır. Yazara güvenmediğiniz sürece bir .NET Core aracı yüklemeyin.

## <a name="find-a-tool"></a>Bir araç bulma

Şu anda,.NET Core'un bir araç arama özelliği yok. Araçları bulmanın bazı yolları şunlardır:

* [Natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub deposundaki araçların listesine bakın.
* .NET araçlarını aramak için [ToolGet'i](https://www.toolget.net/) kullanın.
* ASP.NET Core ekibi tarafından oluşturulan araçların kaynak koduna [dotnet/aspnetcore GitHub deposunun Araçlar dizininde](https://github.com/dotnet/aspnetcore/tree/master/src/Tools)bakın.
* [.NET Core dotnet tanılama araçları](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools)hakkında bilgi edinin.
* [NuGet](https://www.nuget.org) web sitesini arayın. Ancak, NuGet sitesinde henüz yalnızca araç paketleri için arama yapmanızı sağlayan bir özellik yoktur.

## <a name="check-the-author-and-statistics"></a>Yazarı ve istatistikleri kontrol edin

.NET Core araçları tam güven içinde çalıştırıladığından ve genel araçlar PATH ortamı değişkenine eklenmiştir, bunlar çok güçlü olabilir. Güvenmediğiniz kişilerden araçlar indirmeyin.

Araç NuGet'de barındırılırsa, aracı arayarak yazarı ve istatistikleri kontrol edebilirsiniz.

## <a name="install-a-global-tool"></a>Genel bir araç yükleme

Bir aracı genel bir araç olarak `-g` `--global` yüklemek için, aşağıdaki örnekte gösterildiği [gibi, dotnet aracı yükleme](dotnet-tool-install.md)seçeneğini veya seçeneğini kullanın:

```dotnetcli
dotnet tool install -g dotnetsay
```

Çıktı, aracı çağırmak için kullanılan komutu ve yüklenen sürümü aşağıdaki örneğe benzer şekilde gösterir:

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

Bir aracın ikilileri için varsayılan konum işletim sistemine bağlıdır:

| İşletim Sistemi          | Yol                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Bu konum, SDK ilk çalıştırıldığında kullanıcının yoluna eklenir, böylece araç konumu belirtilmeden herhangi bir dizinden genel araçlar çağrılabilir.

Araç erişimi kullanıcıya özgüdür, makine geneli değildir. Genel bir araç yalnızca aracı yükleyen kullanıcı tarafından kullanılabilir.

### <a name="install-a-global-tool-in-a-custom-location"></a>Genel bir aracı özel bir konuma yükleme

Bir aracı özel bir konumda genel bir araç `--tool-path` olarak yüklemek için, aşağıdaki örneklerde gösterildiği gibi [dotnet aracı yükleme](dotnet-tool-install.md)seçeneğini kullanın.

Windows'da:

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

Linux veya macOS'ta:

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

.NET Core SDK bu konumu PATH ortamı değişkenine otomatik olarak eklemez. [Bir araç yolu aracını çağırmak](#invoke-a-tool-path-tool)için, aşağıdaki yöntemlerden birini kullanarak komutun kullanılabilir olduğundan emin olsanız:

* Yükleme dizini PATH ortamı değişkenine ekleyin.
* Aracı çağırdığınızda araca giden tam yolu belirtin.
* Aracı yükleme dizininin içinden çağırın.

## <a name="install-a-local-tool"></a>Yerel bir araç yükleme

**.NET Core 3.0 SDK ve sonrası için geçerlidir.**

Yalnızca yerel erişim için bir araç yüklemek için (geçerli dizin ve alt dizinler için), bir araç bildirimi dosyasına eklenmesi gerekir. Bir araç bildirimi dosyası oluşturmak `dotnet new tool-manifest` için komutu çalıştırın:

```dotnetcli
dotnet new tool-manifest
```

Bu *komut,.config* dizininin altında *dotnet-tools.json* adlı bir bildirim dosyası oluşturur. Bildirim dosyasına yerel bir araç eklemek [için, dotnet aracı yükleme](dotnet-tool-install.md) komutunu kullanın ve aşağıdaki örnekte gösterildiği gibi `--global` seçenekleri `--tool-path` **atlayın:**

```dotnetcli
dotnet tool install dotnetsay
```

Komut çıktısı, yeni yüklenen aracın hangi dosyada olduğunu aşağıdaki örneğe benzer şekilde gösterir:

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

Aşağıdaki örnekte, iki yerel araç yüklü bir bildirim dosyası gösterilmektedir:

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

Genellikle deponun kök dizinine yerel bir araç eklersiniz. Manifesto dosyasını depoya iade ettikten sonra, depodan kodu kullanıma alan geliştiriciler en son bildirim dosyasını alır. Bildirim dosyasında listelenen tüm araçları yüklemek için `dotnet tool restore` aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet tool restore
```

Çıktı, hangi araçların geri yüklendiğine işaret ediyor:

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a>Belirli bir araç sürümünü yükleme

Bir ön sürüm sürümünü veya bir aracın belirli bir sürümünü yüklemek `--version` için, aşağıdaki örnekte gösterildiği gibi seçeneği kullanarak sürüm numarasını belirtin:

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a>Bir araç kullanma

Bir aracı çağırmak için kullandığınız komut, yüklediğiniz paketin adından farklı olabilir. Geçerli kullanıcı için makinede yüklü olan tüm araçları görüntülemek için [dotnet araç listesi](dotnet-tool-list.md) komutunu kullanın:

```dotnetcli
dotnet tool list
```

Çıktı, aşağıdaki örneğe benzer şekilde her aracın sürümünü ve komutunu gösterir:

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

Bu örnekte gösterildiği gibi, liste yerel araçları gösterir. Genel araçları görmek `--global` için, seçeneği kullanın ve araç yolu `--tool-path` araçlarını görmek için bu seçeneği kullanın.

### <a name="invoke-a-global-tool"></a>Genel bir araç çağırma

Genel araçlar için araç komutunu tek başına kullanın. Örneğin, komut, komutu çağırmak için kullandığınız `dotnetsay` komutise: `dotnet-doc`

```console
dotnetsay
dotnet-doc
```

Komut öneki `dotnet-`ile başlarsa, aracı çağırmanın alternatif bir yolu `dotnet` komutu kullanmak ve araç komutu önekini atlamaktır. Örneğin, komut, `dotnet-doc`aşağıdaki komut aracı çağırır:

```dotnetcli
dotnet doc
```

Ancak, aşağıdaki senaryoda genel bir `dotnet` araç çağırmak için komutu kullanamazsınız:

* Genel bir araç ve yerel bir araç `dotnet-`tarafından önceden belirlenmiş aynı komuta sahiptir.
* Genel aracı yerel araç için kapsamda olan bir dizinden çağırmak istiyorsunuz.

Bu `dotnet doc` senaryoda, `dotnet dotnet-doc` ve yerel aracı çağırın. Genel aracı çağırmak için komutu tek başına kullanın:

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a>Araç yolu aracını çağırma

Seçeneği kullanarak yüklenen genel bir aracı çağırmak için, bu makalede daha [önce](#install-a-global-tool-in-a-custom-location)açıklandığı gibi komutun kullanılabilir olduğundan emin olun. `tool-path`

### <a name="invoke-a-local-tool"></a>Yerel bir aracı çağırma

Yerel bir aracı çağırmak için yükleme `dotnet` dizininin içinden komutu kullanmanız gerekir. Aşağıdaki örneklerde gösterildiği`dotnet tool run <COMMAND_NAME>`gibi uzun formu`dotnet <COMMAND_NAME>`( ) veya kısa formu ( ) kullanabilirsiniz:

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

Komut önceden `dotnet-`belirlenmişse, aracı çağırırken önek'i ekleyebilir veya atlayabilirsiniz. Örneğin, komut `dotnet-doc`, aşağıdaki örneklerden herhangi biri yerel aracı çağırır:

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a>Aracı güncelleştirme

Bir aracı güncelleştirmek, bir aracı en son kararlı sürümle kaldırmayı ve yeniden yüklemeyi içerir. Bir aracı güncelleştirmek için, aracı yüklemek için kullandığınız seçenekle [dotnet araç güncelleştirme](dotnet-tool-update.md) komutunu kullanın:

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

Yerel bir araç için SDK, geçerli dizin ve üst dizinlere bakarak paket kimliğini içeren ilk bildirim dosyasını bulur. Herhangi bir bildirim dosyasında böyle bir paket kimliği yoksa, SDK en yakın bildirim dosyasına yeni bir giriş ekler.

## <a name="uninstall-a-tool"></a>Aracı kaldırma

Aracı yüklemek için kullandığınız aynı seçenekle [dotnet aracı nı kaldır](dotnet-tool-uninstall.md) komutunu kullanarak bir aracı kaldırın:

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path<packagename>
dotnet tool uninstall <packagename>
```

Yerel bir araç için SDK, geçerli dizin ve üst dizinlere bakarak paket kimliğini içeren ilk bildirim dosyasını bulur.

## <a name="get-help-and-troubleshoot"></a>Yardım alın ve sorun giderme

Kullanılabilir `dotnet tool` komutların listesini almak için aşağıdaki komutu girin:

```dotnetcli
dotnet tool --help
```

Araç kullanım yönergelerini almak için aşağıdaki komutlardan birini girin veya aracın web sitesine bakın:

```dotnetcli
<command> --help
dotnet <command> --help
```

Bir araç yüklenmezse veya çalıştıramazsa, [Sorun Giderme .NET Core araç kullanım sorunları](troubleshoot-usage-issues.md)konusuna bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: .NET Core CLI'yi kullanarak bir .NET Core aracı oluşturun](global-tools-how-to-create.md)
- [Öğretici: .NET Core CLI'yi kullanarak bir .NET Core global aracı yükleyin ve kullanın](global-tools-how-to-use.md)
- [Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın](local-tools-how-to-use.md)
