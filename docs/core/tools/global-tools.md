---
title: .NET core genel araçları
description: .NET Core genel araçları nelerdir ve bunlar için kullanılabilen .NET Core CLI komutları genel bakış.
author: KathleenDollard
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 077ffd53f1ba2988c80a637aaa109a66139736b0
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697098"
---
# <a name="net-core-global-tools-overview"></a>.NET core genel araçlarına genel bakış

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

Bir .NET Core genel bir konsol uygulaması içeren özel bir NuGet paketi aracıdır. Genel bir aracı makinenizde PATH ortam değişkeni bulunan bir varsayılan konum ya da özel bir konuma yüklenebilir.

.NET Core genel aracı kullanmak istiyorsanız:

* Aracı (genellikle bir Web sitesi veya GitHub sayfası) hakkında bilgiler bulun.
* Yazar ve akış (genellikle NuGet.org) için Giriş İstatistikleri denetleyin.
* Aracı yükleyin.
* Aracı'nı arayın.
* Aracı güncelleştirin.
* Aracı'nı kaldırın.

> [!IMPORTANT]
> .NET core genel araçları, yolunuza görünür ve tam güvende çalıştırma. Yazarın güvenmediğiniz sürece .NET Core genel araçları yüklemeyin.

## <a name="find-a-net-core-global-tool"></a>.NET Core genel aracı Bul

Şu anda, .NET Core komut satırı arabirimi (CLI) bir genel aracı arama özelliği yoktur.

.NET Core genel araçları bulabilirsiniz [NuGet](https://www.nuget.org). Ancak, NuGet henüz özellikle .NET Core genel araçları için arama yapmanıza izin vermez.

Aracı önerilerinde blog gönderileri ya da buna ayrıca bulabilirsiniz [dotnet/natemcmaster-tools](https://github.com/natemcmaster/dotnet-tools) GitHub depo.

Genel ASP.NET ekibi tarafından oluşturulan araçları için kaynak kodunu da görebilirsiniz [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub depo.

## <a name="check-the-author-and-statistics"></a>Yazar ve istatistikleri denetleyin

.NET Core genel araçları tam güvende çalıştırma ve genelde yol üzerinde yüklü olduğundan, bunlar çok güçlü olabilir. Araçlar güvenmediğiniz kişilerden yüklemeyin.

Aracı NuGet üzerinde barındırılıyorsa, aracı için arama yaparak yazar ve istatistikleri kontrol edebilirsiniz.

## <a name="install-a-global-tool"></a>Genel bir aracı yükleyin

Genel bir aracı yüklemek için kullandığınız [dotnet aracı yükleme](dotnet-tool-install.md) .NET Core CLI komutu. Aşağıdaki örnek bir genel aracın varsayılan konumda nasıl yükleneceğini gösterir:

```console
dotnet tool install -g dotnetsay
```

Aracı yüklü değilse, hata iletileri görüntülenir. Beklediğiniz akışları teslim denetleyin.

Bir yayın öncesi sürüm veya aracı belirli bir sürümünü yüklemek çalışıyorsanız, aşağıdaki biçimi kullanarak sürüm numarasını belirtebilirsiniz:

```console
dotnet tool install -g <package-name> --version <version-number>
```

Yükleme başarılı olursa, aracı ve yüklü sürüm çağırmak için kullanılan komut aşağıdaki örneğe benzer gösteren bir ileti görüntülenir:

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

Varsayılan dizini veya belirli bir konuma genel araçları yüklenebilir. Varsayılan dizinler şunlardır:

| İŞLETİM SİSTEMİ          | Yol                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

SDK'yı ilk kez çalıştırdığınızda, genel yüklü araçları doğrudan olarak adlandırılan şekilde bu konumları kullanıcının yoluna eklenir.

Genel araçları kullanıcıya özgü olduğuna dikkat edin, genel makine değil. Makinenin tüm kullanıcıları için kullanılabilir olan bir genel aracı yükleyemezsiniz olan kullanıcıya özgü anlamına gelir. Aracı yalnızca, aracı yüklendiği her bir kullanıcı profili için kullanılabilir.

Genel araçları Ayrıca belirli bir dizindeki yüklenebilir. Belirli bir dizindeki yüklendiğinde kullanıcı komutu kullanılabiliyorsa, belirtilen dizinle komutu çağırarak yolunda bu dizine dahil ederek emin olmalısınız ya da belirtilen dizin içinde aracından çağırma.
Bu durumda, .NET Core CLI bu konuma otomatik olarak PATH ortam değişkenine eklemez.

## <a name="use-the-tool"></a>Aracını kullanma

Aracı yüklendikten sonra kendi komutunu kullanarak çağırabilirsiniz. Komut paket adı ile aynı olabileceğini unutmayın.

Komut ise `dotnetsay`, kendisiyle çağırın:

```console
dotnetsay
```

Aracı Yazar bağlamında görünmesi aracı istedik varsa `dotnet` istemi, bunlar yazdığınız bu şekilde olarak çağrı `dotnet <command>`, gibi:

```console
dotnet doc
```

Hangi araçların bir yüklü genel aracını kullanarak yüklü paketleri listeleyerek paketinde bulunan bulabilirsiniz [dotnet araç listesi](dotnet-tool-list.md) komutu.

Kullanım yönergeleri aracın Web sitesindeki ya da aşağıdaki komutlardan birini yazarak da arayabilirsiniz:

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a>Nerede sorun çıkabilir

Genel araçlardır [framework bağımlı uygulamaları](../deploying/index.md#framework-dependent-deployments-fdd), bunlar Bel makinenize yüklü bir .NET çekirdeği çalışma zamanı anlamına gelir. Beklenen çalışma zamanı bulunmazsa, bunlar gibi normal .NET çekirdeği çalışma zamanı İleri alma kurallarını uygulayın:

* Bir uygulama belirtilen birincil ve ikincil sürüm en yüksek düzeltme sürümüne İleri yapar.
* Bir ana eşleşen ve ikincil sürüm numarası ile eşleşen hiçbir çalışma zamanı sonraki daha yüksek alt sürüm kullanılır.
* İleri çalışma zamanı Önizleme sürümleri veya Önizleme ve yayın sürümleri arasında oluşmaz. Bu nedenle, genel Önizleme sürümleri kullanılarak oluşturulan araçları yeniden ve yazar tarafından yeniden yayımlanması ve gerekir yeniden.
* Genel .NET Core 2.1 Preview 1'de oluşturulan araçları ile ek sorunlar oluşabilir. Daha fazla bilgi için bkz: [.NET Core 2.1 Preview 2 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).

Bir uygulama uygun bir çalışma zamanı bulamazsanız, çalıştırmak başarısız olur ve bir hata bildirir.

Bir önceki Önizleme sırasında oluşturulan bir genel aracı, şu anda yüklü .NET çekirdeği çalışma zamanları ile çalışmayabilir gerçekleşebilir başka bir sorun olmasıdır. Hangi çalışma zamanları makinenizde aşağıdaki komutu kullanarak yüklü olan görebilirsiniz:

```console
dotnet --list-runtimes
```

Genel aracı yazarına başvurun ve bunlar derlenir ve güncelleştirilmiş sürüm numarası olan NuGet için kendi aracı paketi yeniden yayımlamanız varsa bkz. NuGet paketi güncelleştirdikten sonra kopyanızı güncelleştirebilirsiniz.

İlk kullanım üzerinde PATH ortam değişkeni varsayılan konumları eklemek .NET Core CLI çalışır. Ancak, birkaç burada konumu değil eklenmesi YOLUNU otomatik olarak senaryo vardır gibi:

* Ayarlamış olmanız `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` ortam değişkeni.
* .NET Core SDK'sını kullanarak yüklediyseniz macOS üzerinde *. tar.gz* dosyaları ve *.pkg*.
* Linux üzerinde yolu yapılandırmak için kabuk ortam dosyasını düzenlemeniz gerekir.

## <a name="other-cli-commands"></a>Diğer CLI komutları

.NET Core SDK destek .NET Core genel araçları diğer komutlarını içerir. Herhangi birini kullanan `dotnet tool` aşağıdaki seçeneklerden birini komutlarıyla:

* `--global` veya `-g` komutu kullanıcı genelinde geçerli genel araçları olduğunu belirtir.
* `--tool-path` özel bir konuma için genel araçları belirtir.

Öğrenmek için genel araçlar için hangi komutları kullanılabilir:

```console
dotnet tool --help
```

Genel bir aracı güncelleştirme kaldırıp en son kararlı sürümü ile yeniden yüklemeyi içerir. Genel bir aracı güncelleştirmek için [dotnet aracı güncelleştirme](dotnet-tool-update.md) komutu:

```console
dotnet tool update -g <packagename>
```

Genel aracını kullanarak kaldırma [dotnet Aracı kaldırma](dotnet-tool-uninstall.md):

```console
dotnet tool uninstall -g <packagename>
```

Genel, sürüm ve komutları yanı sıra makine yüklü araçların tümünü görüntülemek için kullanın [dotnet araç listesi](dotnet-tool-list.md) komutu:

```console
dotnet tool list -g
```