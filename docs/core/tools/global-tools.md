---
title: .NET core Araçları Genel
description: .NET Core genel araçları nedir ve bunlar için kullanılabilen .NET Core CLI komutları genel bakış.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 3bbf1e7953482dc07f05570443cf640a9fab6258
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647752"
---
# <a name="net-core-global-tools-overview"></a>.NET core Araçları Genel genel bakış

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

.NET Core genel aracı bir konsol uygulaması içeren özel bir NuGet paketidir. Genel bir aracı makinenizde yol ortam değişkeninde bulunan bir varsayılan konum ya da özel bir konuma yüklenebilir.

.NET Core genel bir aracı kullanmak istiyorsanız:

* Aracı (genellikle bir Web sitesi veya GitHub sayfası) hakkında bilgiler bulun.
* Giriş akış (genellikle NuGet.org) için istatistikleri ve yazar denetleyin.
* Aracı'nı yükleyin.
* Aracı'nı arayın.
* Aracı'nı güncelleştirin.
* Aracı'nı kaldırın.

> [!IMPORTANT]
> .NET core Araçları Genel path değişkeninize görünür ve tam güvende çalıştırma. .NET Core Araçları Genel Yazar güvenmediğiniz sürece yüklemeyin.

## <a name="find-a-net-core-global-tool"></a>.NET Core genel aracını bulun

Şu anda .NET Core komut satırı arabirimi (CLI) bir genel aracı arama özelliği yoktur.

.NET Core Araçları Genel bulabilirsiniz [NuGet](https://www.nuget.org). Ancak, NuGet henüz, özellikle .NET Core genel araçları için arama yapmanıza izin vermez.

Ayrıca araç önerilerinden blog gönderilerini veya bulabilirsiniz [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub deposu.

Genel ASP.NET ekibi tarafından oluşturulan araçlar için kaynak kodunu da görebilirsiniz [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub deposu.

## <a name="check-the-author-and-statistics"></a>Yazar ve istatistikleri denetimi

.NET Core Araçları Genel tam güvende çalıştırmak ve path değişkeninize genellikle yüklü olmadığından, çok güçlü olabilir. Araçlar güvenmediğiniz kişilerden yüklemeyin.

Araç, NuGet üzerinde barındırılıyorsa, aracı için arama yaparak yazar ve istatistikleri kontrol edebilirsiniz.

## <a name="install-a-global-tool"></a>Genel bir aracı yükleme

Genel bir aracı yüklemek için kullandığınız [dotnet aracı yükleme](dotnet-tool-install.md) .NET Core CLI komutu. Aşağıdaki örnek, varsayılan konumu genel bir aracı yüklemek gösterilmektedir:

```console
dotnet tool install -g dotnetsay
```

Aracı yüklü değilse, hata iletileri görüntülenir. Beklediğiniz akışları denetlendiği denetleyin.

Yayın öncesi bir sürümü ya da aracının belirli bir sürümü yüklemeye çalışıyorsanız, sürüm numarası şu biçimi kullanarak belirtebilirsiniz:

```console
dotnet tool install -g <package-name> --version <version-number>
```

Yükleme başarılı olursa, aracı ve yüklü sürümü çağırmak için kullanılan komut aşağıdaki örneğe benzer gösteren bir ileti görüntülenir:

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

Varsayılan dizini veya belirli bir konuma genel araçları yüklenebilir. Varsayılan dizinler şunlardır:

| İşletim Sistemi          | Yol                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

SDK'yı ilk kez çalıştırdığınızda, genel araçları yüklü doğrudan çağrılabilir için bu konumları kullanıcının yoluna eklenir.

Genel araçları kullanıcıya özgü olduğuna dikkat edin, genel makine yok. Kullanıcıya özel olan, makinenin tüm kullanıcıları için kullanılabilir olan bir genel aracı yükleyemezsiniz anlamına gelir. Aracı yalnızca, aracının yüklendiği her kullanıcı profili için kullanılabilir.

Genel araçları Ayrıca belirli bir dizindeki yüklenebilir. Belirli bir dizindeki yüklendiğinde, kullanıcı komutu kullanılabilir yolunda belirtilen dizinle komutunu çağırarak bu dizine ekleyerek emin olmanız gerekir veya belirtilen dizin içinde aracından çağırma.
Bu durumda, .NET Core CLI bu konum otomatik olarak PATH ortam değişkenine eklemez.

## <a name="use-the-tool"></a>Aracını kullanma

Aracı yüklendikten sonra komutu kullanarak çağırabilirsiniz. Komut paket adı ile aynı olabileceğini unutmayın.

Komut ise `dotnetsay`, beraber:

```console
dotnetsay
```

Aracı Yazar bağlamında görüntülenecek araç istiyordu, `dotnet` istemi yazıldığına bu şekilde olarak çağrı `dotnet <command>`, gibi:

```console
dotnet doc
```

Kullanarak yüklü paketleri listeleyerek, hangi Araçlar yüklü bir genel Aracı paketine dahil edilen bulabilirsiniz [dotnet araç listesi](dotnet-tool-list.md) komutu.

Kullanım yönergeleri Aracı'nın Web sitesinde veya aşağıdaki komutlardan birini yazarak da arayabilirsiniz:

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a>Nerede sorun çıkabilir

Genel Araçları [framework bağımlı uygulamaları](../deploying/index.md#framework-dependent-deployments-fdd), güvenin makinenizde yüklü bir .NET Core çalışma zamanı üzerinde anlamına gelir. Beklenen çalışma zamanı bulunamazsa bunlar gibi normal .NET Core çalışma zamanı sarma kuralları izleyin:

* Bir uygulama belirtilen birincil ve ikincil sürüm en yüksek düzeltme eki sürümü için İleri yapar.
* Bir eşleştirme büyük ve küçük versiyon numarasını ile eşleşen hiçbir çalışma zamanı varsa, daha yüksek bir sonraki alt sürümü kullanılır.
* İleri Sarma Önizleme ve yayın sürümleri arasında veya çalışma zamanı Önizleme sürümleri arasında oluşmaz. Bu nedenle, genel Önizleme sürümleri kullanılarak oluşturulan araçları yeniden ve yazarı tarafından yeniden yayımlanması ve gerekir yeniden.
* Genel .NET Core 2.1 önizleme 1'de oluşturulan Araçlar ek sorunlar ortaya çıkabilir. Daha fazla bilgi için [.NET Core 2.1 önizleme 2 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).

Uygun bir çalışma zamanı bir uygulamayı bulamıyorsanız, çalıştırılacak başarısız olur ve bir hata bildirir.

Başka bir sorun olabilir, daha önceki bir önizleme sırasında oluşturulan bir genel aracı, şu anda yüklü .NET Core çalışma zamanlarını çalışmayabilir ' dir. Hangi çalışma zamanları, makinenizde aşağıdaki komutu kullanarak yüklenen görebilirsiniz:

```console
dotnet --list-runtimes
```

Genel aracı yazarıyla iletişime geçin ve bunlar yeniden derleyin ve güncelleştirilmiş sürüm numarasına sahip NuGet için kendi araç paketi yeniden yayımlamanız durumunda bakın. NuGet paketi güncelleştirdiniz mi sonra kopyanızı güncelleştirebilirsiniz.

.NET Core CLI yol ortam değişkenine ilk kullanım için varsayılan konumları eklemek çalışır. Ancak, birkaç senaryo burada konumu değil eklenecek yolu otomatik olarak vardır gibi:

* Ayarladıysanız `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` ortam değişkeni.
* Macos'ta .NET Core SDK'sını kullanarak yüklediyseniz, *. tar.gz* dosyaları ve *.pkg*.
* Linux üzerinde yolu yapılandırmak için kabuk ortam dosyasını düzenlemeniz gerekir.

## <a name="other-cli-commands"></a>Başka CLI komutları

.NET Core SDK'sı, .NET Core Araçları Genel destekleyen diğer komutlar içerir. Dilediğinizi `dotnet tool` aşağıdaki seçeneklerden birini komutlarıyla:

* `--global` veya `-g` komutu geniş kullanıcı için geçerli genel araçları olduğunu belirtir.
* `--tool-path` Genel araçları için özel bir konum belirtir.

Hangi komutları için genel Araçlar kullanılabilir olduğunu öğrenmek için:

```console
dotnet tool --help
```

En son kararlı sürüm ile kaldırılmadan ve genel bir aracı güncelleştirme içerir. Genel bir aracı güncelleştirmek için [dotnet aracı güncelleştirme](dotnet-tool-update.md) komutu:

```console
dotnet tool update -g <packagename>
```

Kullanarak bir genel Aracı kaldırma [dotnet Aracı kaldırma](dotnet-tool-uninstall.md):

```console
dotnet tool uninstall -g <packagename>
```

Genel sürüm ve komutları birlikte makine üzerinde yüklü araçların tümünü görüntülemek için kullanın [dotnet araç listesi](dotnet-tool-list.md) komutu:

```console
dotnet tool list -g
```