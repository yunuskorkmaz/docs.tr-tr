---
title: .NET Core küresel araçları
description: .NET Core genel araçlarının ne olduğuna ve bunlara yönelik .NET Core CLI komutlarına genel bakış.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 9ff7e33a50eb0c5fb649b44dda6d72412a134584
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202583"
---
# <a name="net-core-global-tools-overview"></a>.NET Core genel araçlarına genel bakış

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

.NET Core küresel Aracı, konsol uygulaması içeren özel bir NuGet paketidir. Bir genel araç, makinenizde, PATH ortam değişkenine veya özel bir konuma dahil olan varsayılan bir konumda yüklenebilir.

.NET Core küresel aracı kullanmak istiyorsanız:

* Araçla ilgili bilgileri bulun (genellikle bir Web sitesi veya GitHub sayfası).
* Akışın giriş sayfasındaki yazar ve istatistikleri denetleyin (genellikle NuGet.org).
* Aracı 'nı yükler.
* Aracı çağırın.
* Aracı güncelleştirin.
* Aracı kaldırın.

> [!IMPORTANT]
> .NET Core küresel araçları yolunuzda görünür ve tam güvende çalışır. Yazara güvenmediğiniz .NET Core küresel araçlarını yüklemeyin.

## <a name="find-a-net-core-global-tool"></a>.NET Core küresel aracı bulma

Şu anda .NET Core komut satırı arabiriminde (CLı) genel bir araç arama özelliği yoktur.

[NuGet](https://www.nuget.org)üzerinde .NET Core küresel araçları bulabilirsiniz. Ancak, NuGet henüz .NET Core küresel araçları için arama yapmanıza izin vermez.

Ayrıca, blog gönderilerinde veya [natemcmaster/DotNet-Tools](https://github.com/natemcmaster/dotnet-tools) GitHub deposunda araç önerileri de bulabilirsiniz.

[ASPNET/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub deposunda ASP.NET ekibi tarafından oluşturulan genel araçların kaynak kodunu da görebilirsiniz.

## <a name="check-the-author-and-statistics"></a>Yazarı ve istatistikleri denetleme

.NET Core küresel araçları tam güvende çalıştığı ve genellikle yolunuza yüklendiği için, bu, çok güçlü olabilir. Güvenmediğiniz kişilerden araç indirmeyin.

Araç NuGet üzerinde barındırılıyorsa, aracı arayarak yazarı ve istatistikleri kontrol edebilirsiniz.

## <a name="install-a-global-tool"></a>Küresel bir araç yükler

Küresel bir araç yüklemek için [DotNet aracı install](dotnet-tool-install.md) .NET Core CLI komutunu kullanın. Aşağıdaki örnek, genel bir aracın varsayılan konuma nasıl yükleneceğini göstermektedir:

```console
dotnet tool install -g dotnetsay
```

Araç yüklenemezse hata iletileri görüntülenir. Beklediğiniz akışların denetlendiğinden emin olun.

Bir yayın öncesi sürüm veya aracın belirli bir sürümünü yüklemeye çalışıyorsanız, sürüm numarasını aşağıdaki biçimi kullanarak belirtebilirsiniz:

```console
dotnet tool install -g <package-name> --version <version-number>
```

Yükleme başarılı olursa, aşağıdaki örneğe benzer şekilde, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösteren bir ileti görüntülenir:

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

Genel araçlar varsayılan dizine veya belirli bir konuma yüklenebilir. Varsayılan dizinler şunlardır:

| OS          | Yol                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Bu konumlar, SDK ilk kez çalıştırıldığında kullanıcının yoluna eklenir, bu nedenle genel araçlar yüklenir, böylece doğrudan çağrılabilir.

Genel araçların makineye genel değil, kullanıcıya özgü olduğunu unutmayın. Kullanıcıya özel olması, makinenin tüm kullanıcıları için kullanılabilir olan küresel bir araç yükleyemeyeceğiniz anlamına gelir. Araç yalnızca aracın yüklendiği her kullanıcı profili için kullanılabilir.

Genel araçlar, belirli bir dizine de yüklenebilir. Belirli bir dizine yüklendiğinde, kullanıcının, yolu belirtilen dizin ile çağırarak veya aracı belirtilen dizin içinden çağırarak, bu dizini da dahil ederek komutun kullanılabilir olduğundan emin olması gerekir.
Bu durumda .NET Core CLI, bu konumu otomatik olarak PATH ortam değişkenine eklemez.

## <a name="use-the-tool"></a>Aracı kullanma

Araç yüklendikten sonra, komutunu kullanarak çağırabilirsiniz. Komutun paket adı ile aynı olamayacağını unutmayın.

Komut ise `dotnetsay`, şunu ile çağırabilirsiniz:

```console
dotnetsay
```

Araç yazarı, aracın `dotnet` istem bağlamında görünmesini istiyorlarsa, bu, şöyle bir şekilde bir `dotnet <command>`şekilde yazmış olabilirler, örneğin:

```console
dotnet doc
```

Yüklü paketleri [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak listeleyerek, yüklü bir genel araç paketine hangi araçların ekleneceğini bulabilirsiniz.

Ayrıca, aracın Web sitesinde veya aşağıdaki komutlardan birini yazarak kullanım yönergelerine bakabilirsiniz:

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a>Hatalı gidebilirler

Küresel araçlar, [çerçeveye bağlı uygulamalardır](../deploying/index.md#framework-dependent-deployments-fdd)ve bu, makinenizde yüklü bir .NET Core çalışma zamanına bağlı olarak gelir. Beklenen çalışma zamanı bulunamazsa, normal .NET Core çalışma zamanı alma-iletme kurallarını izler:

* Bir uygulama, belirtilen birincil ve ikincil sürümün en yüksek düzeltme eki sürümüne ileri kaydedilir.
* Eşleşen bir ana ve alt sürüm numarasına sahip eşleşen bir çalışma zamanı yoksa, sonraki en düşük sürüm kullanılır.
* Çalışma zamanının veya önizleme sürümleri ile sürüm sürümlerinin önizleme sürümleri arasında ileri alma gerçekleşmez. Bu nedenle, önizleme sürümleri kullanılarak oluşturulan küresel araçların, yazar tarafından yeniden oluşturulması ve yeniden yayımlanması ve yeniden yüklenmesi gerekir.
* .NET Core 2,1 Preview 1 ' de oluşturulan genel araçlarla ilgili ek sorunlar oluşabilir. Daha fazla bilgi için bkz. [.NET Core 2,1 Preview 2 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).

Bir uygulama uygun bir çalışma zamanı bulamazsa, çalışmaz ve bir hata bildirir.

Başka bir sorun ortaya çıkabilir, önceki önizleme sırasında oluşturulan küresel bir araç, şu anda yüklü olan .NET Core çalışma zamanları ile çalışmayabilir. Makinenizde hangi çalışma zamanlarının yüklü olduğunu aşağıdaki komutu kullanarak görebilirsiniz:

```console
dotnet --list-runtimes
```

Genel aracının yazarına başvurun ve araç paketlerini, güncelleştirilmiş bir sürüm numarasıyla NuGet 'e yeniden derleyip yeniden yayımlayabilecekleri konusunda bilgi görüntüleyin. NuGet üzerinde paketi güncelleştirdikten sonra kopyanızı güncelleştirebilirsiniz.

.NET Core CLI, ilk kullanımındaki yol ortam değişkenine varsayılan konumları eklemeye çalışır. Ancak, konumun otomatik olarak yola eklenebileceği birkaç senaryo vardır, örneğin:

* `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` Ortam değişkenini ayarladıysanız.
* MacOS üzerinde. *tar. gz* dosyalarını *. pkg*değil kullanarak .NET Core SDK yüklediyseniz.
* Linux 'ta, yolu yapılandırmak için kabuk ortam dosyasını düzenlemeniz gerekir.

## <a name="other-cli-commands"></a>Diğer CLı komutları

.NET Core SDK .NET Core küresel araçlarını destekleyen diğer komutları içerir. Aşağıdaki seçeneklerden biriyle komutlardan birini kullanın: `dotnet tool`

* `--global`ya `-g` da komutun Kullanıcı genelindeki genel araçlara uygun olduğunu belirtir.
* `--tool-path`Küresel araçlar için özel bir konum belirtir.

Genel araçlar için hangi komutların kullanılabildiğini öğrenmek için:

```console
dotnet tool --help
```

Küresel bir aracın güncelleştirilmesi, en son kararlı sürümle kaldırılması ve yeniden yüklenmesi ile ilgilidir. Genel bir aracı güncelleştirmek için [DotNet Aracı güncelleştirme](dotnet-tool-update.md) komutunu kullanın:

```console
dotnet tool update -g <packagename>
```

[DotNet aracını kaldırma](dotnet-tool-uninstall.md)Işlemini kullanarak genel bir aracı kaldırma:

```console
dotnet tool uninstall -g <packagename>
```

Makinede yüklü olan tüm genel araçları, sürüm ve komutlarıyla birlikte göstermek için [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanın:

```console
dotnet tool list -g
```
