---
title: .NET Core küresel araçları
description: .NET Core genel araçlarının ne olduğuna ve bunlara yönelik .NET Core CLI komutlarına genel bakış.
author: KathleenDollard
ms.date: 05/29/2018
ms.openlocfilehash: 665cee64cb92efd16f5528feb656b377f9f3283c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714154"
---
# <a name="net-core-global-tools-overview"></a>.NET Core genel araçlarına genel bakış

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

.NET Core küresel Aracı, konsol uygulaması içeren özel bir NuGet paketidir. Bir genel araç, makinenizde, PATH ortam değişkenine veya özel bir konuma dahil olan varsayılan bir konumda yüklenebilir.

.NET Core küresel aracı kullanmak istiyorsanız:

* Araçla ilgili bilgileri bulun (genellikle bir Web sitesi veya GitHub sayfası).
* Akışın giriş sayfasındaki yazar ve istatistikleri denetleyin (genellikle NuGet.org).
* Aracı yükleyin.
* Aracı çağırın.
* Aracı güncelleştirin.
* Aracı kaldırın.

> [!IMPORTANT]
> .NET Core küresel araçları yolunuzda görünür ve tam güvende çalışır. Yazara güvenmediğiniz .NET Core küresel araçlarını yüklemeyin.

## <a name="find-a-net-core-global-tool"></a>.NET Core küresel aracı bulma

Şu anda .NET Core komut satırı arabiriminde (CLı) genel bir araç arama özelliği yoktur. Araçların nasıl bulunacağı hakkında bazı öneriler aşağıda verilmiştir:

* [NuGet](https://www.nuget.org)üzerinde .NET Core küresel araçları bulabilirsiniz. Ancak, NuGet henüz .NET Core küresel araçları için arama yapmanıza izin vermez.
* Araç önerilerini blog gönderilerinde veya [natemcmaster/DotNet-Tools](https://github.com/natemcmaster/dotnet-tools) GitHub deposunda bulabilirsiniz.
* ASP.NET ekibi tarafından oluşturulan genel araçların kaynak kodunu [ASPNET/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub deposunda görebilirsiniz.
* [.NET Core DotNet Diagnostic küresel araçlar](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools)' da tanılama araçları hakkında bilgi edinebilirsiniz.

## <a name="check-the-author-and-statistics"></a>Yazarı ve istatistikleri denetleme

.NET Core küresel araçları tam güvende çalıştığı ve genellikle yolunuza yüklendiği için, bu, çok güçlü olabilir. Güvenmediğiniz kişilerden araç indirmeyin.

Araç NuGet üzerinde barındırılıyorsa, aracı arayarak yazarı ve istatistikleri kontrol edebilirsiniz.

## <a name="install-a-global-tool"></a>Küresel bir araç yükler

Küresel bir araç yüklemek için [DotNet aracı install](dotnet-tool-install.md) .NET Core CLI komutunu kullanın. Aşağıdaki örnek, genel bir aracın varsayılan konuma nasıl yükleneceğini göstermektedir:

```dotnetcli
dotnet tool install -g dotnetsay
```

Araç yüklenemezse hata iletileri görüntülenir. Beklediğiniz akışların denetlendiğinden emin olun.

Bir yayın öncesi sürüm veya aracın belirli bir sürümünü yüklemeye çalışıyorsanız, sürüm numarasını aşağıdaki biçimi kullanarak belirtebilirsiniz:

```dotnetcli
dotnet tool install -g <package-name> --version <version-number>
```

Yükleme başarılı olursa, aşağıdaki örneğe benzer şekilde, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösteren bir ileti görüntülenir:

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

Genel araçlar varsayılan dizine veya belirli bir konuma yüklenebilir. Varsayılan dizinler şunlardır:

| İşletim Sistemi          | Yol                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Bu konumlar, SDK ilk kez çalıştırıldığında kullanıcının yoluna eklenir, bu nedenle genel araçlar yüklenir, böylece doğrudan çağrılabilir.

Genel araçların makineye genel değil, kullanıcıya özgü olduğunu unutmayın. Kullanıcıya özel olması, makinenin tüm kullanıcıları için kullanılabilir olan küresel bir araç yükleyemeyeceğiniz anlamına gelir. Araç yalnızca aracın yüklendiği her kullanıcı profili için kullanılabilir.

Genel araçlar, belirli bir dizine de yüklenebilir. Belirli bir dizine yüklendiğinde, kullanıcının, yolu belirtilen dizin ile çağırarak veya aracı belirtilen dizin içinden çağırarak, bu dizini da dahil ederek komutun kullanılabilir olduğundan emin olması gerekir.
Bu durumda .NET Core CLI, bu konumu otomatik olarak PATH ortam değişkenine eklemez.

## <a name="use-the-tool"></a>Aracı kullanma

Araç yüklendikten sonra, komutunu kullanarak çağırabilirsiniz. Komutun paket adı ile aynı olamayacağını unutmayın.

Komut `dotnetsay`ise, şunu ile çağırın:

```console
dotnetsay
```

Araç yazarı aracın `dotnet` istem bağlamında görünmesini istiyorlarsa, bu, örneğin şöyle bir şekilde `dotnet <command>`çağrılabileceği şekilde yazmış olabilirler:

```dotnetcli
dotnet doc
```

Yüklü paketleri [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak listeleyerek, yüklü bir genel araç paketine hangi araçların ekleneceğini bulabilirsiniz.

Ayrıca, aracın Web sitesinde veya aşağıdaki komutlardan birini yazarak kullanım yönergelerine bakabilirsiniz:

```console
<command> --help
dotnet <command> --help
```

## <a name="other-cli-commands"></a>Diğer CLı komutları

.NET Core SDK .NET Core küresel araçlarını destekleyen diğer komutları içerir. Aşağıdaki seçeneklerden biriyle `dotnet tool` komutlardan birini kullanın:

* `--global` veya `-g`, komutun Kullanıcı genelindeki genel araçlara uygun olduğunu belirtir.
* `--tool-path` genel araçlar için özel bir konum belirtir.

Genel araçlar için hangi komutların kullanılabildiğini öğrenmek için:

```dotnetcli
dotnet tool --help
```

Küresel bir aracın güncelleştirilmesi, en son kararlı sürümle kaldırılması ve yeniden yüklenmesi ile ilgilidir. Genel bir aracı güncelleştirmek için [DotNet Aracı güncelleştirme](dotnet-tool-update.md) komutunu kullanın:

```dotnetcli
dotnet tool update -g <packagename>
```

[DotNet aracını kaldırma](dotnet-tool-uninstall.md)Işlemini kullanarak genel bir aracı kaldırma:

```dotnetcli
dotnet tool uninstall -g <packagename>
```

Makinede yüklü olan tüm genel araçları, sürüm ve komutlarıyla birlikte göstermek için [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanın:

```dotnetcli
dotnet tool list -g
```

## <a name="see-also"></a>Ayrıca bkz.

* [.NET Core araç kullanımı sorunlarını giderme](troubleshoot-usage-issues.md)
