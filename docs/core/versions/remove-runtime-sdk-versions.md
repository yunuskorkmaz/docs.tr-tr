---
title: .NET Core çalışma süresini ve SDK'yı kaldırın
description: Bu makalede, .NET Core Runtime ve SDK'nın şu anda hangi sürümlerinin yüklendiği ve windows, mac ve Linux'ta bunların nasıl kaldırılılabildiğini nasıl belirleyeceğiz açıklanmaktadır.
ms.date: 12/17/2019
author: billwagner
ms.author: wiwagn
ms.custom: updateeachrelease
ms.openlocfilehash: 71c11825981c6259a779e1ac8f947a41618e922d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398841"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>.NET Çekirdek Çalışma Süresi ve SDK nasıl kaldırılır?

Zaman içinde ,.NET Core çalışma zamanı ve SDK'nın güncelleştirilmiş sürümlerini yüklerken, .NET Core'un eski sürümlerini makinenizden kaldırmak isteyebilirsiniz. Çalışma zamanının eski sürümlerini kaldırmak, [.NET Core sürüm seçimiyle](selection.md)ilgili makalede ayrıntılı olarak açıklandığı gibi paylaşılan çerçeve uygulamalarını çalıştırmak için seçilen çalışma süresini değiştirebilir.

## <a name="should-i-remove-a-version"></a>Bir sürümü kaldırmalı mıyım?

[.NET Core sürüm seçim](selection.md) davranışları ve .NET Core'un güncelleştirmeler arasında çalışma zamanı uyumluluğu, önceki sürümlerin güvenli bir şekilde kaldırılmasını sağlar. .NET Core çalışma zamanı güncelleştirmeleri, 1.x ve 2.x gibi ana sürüm 'bandı' içinde uyumludur. Ayrıca, .NET Core SDK'nın yeni sürümleri genellikle çalışma zamanının önceki sürümlerini uyumlu bir şekilde hedefleyen uygulamalar oluşturma yeteneğini korur.

Genel olarak, yalnızca uygulamanız için gereken çalışma sürelerinin en son SDK ve en son yama sürümüne ihtiyacınız vardır. Eski SDK veya Runtime sürümlerini tutmanın **project.json**tabanlı uygulamaları korumayı içerdiği durumlar. Uygulamanızın önceki SDK'lar veya çalışma süreleri için belirli nedenleri olmadığı sürece, eski sürümleri güvenle kaldırabilirsiniz.

## <a name="determine-what-is-installed"></a>Nenin yüklü olduğunu belirleme

.NET Core 2.1 ile başlayarak ,.NET CLI,.makinenize yüklenen SDK ve çalışma süresini listelemek için kullanabileceğiniz seçeneklere sahiptir.  Makinenize yüklenen SDK'ların listesini görmek için kullanın. [`dotnet --list-sdks`](../tools/dotnet.md#options) Makinenizde yüklü çalışma sürelerinin listesini görmek için kullanın. [`dotnet --list-runtimes`](../tools/dotnet.md#options) Aşağıdaki metin, Windows, macOS veya Linux için tipik çıktıyı gösterir:

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

Aşağıdaki komutu çalıştırarak:

```dotnetcli
dotnet --list-sdks
```

Aşağıdakilere benzer çıktı alırsınız:

```console
2.1.200-preview-007474 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007480 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007509 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007570 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007576 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007587 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007589 [C:\Program Files\dotnet\sdk]
2.1.200 [C:\Program Files\dotnet\sdk]
2.1.201 [C:\Program Files\dotnet\sdk]
2.1.202 [C:\Program Files\dotnet\sdk]
2.1.300-preview2-008533 [C:\Program Files\dotnet\sdk]
2.1.300 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009063 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009088 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009171 [C:\Program Files\dotnet\sdk]
```

Ve aşağıdaki komutu çalıştırarak:

```dotnetcli
dotnet --list-runtimes
```

Aşağıdakilere benzer çıktı alırsınız:

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.0.6 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.7 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.9 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
```

# <a name="linux"></a>[Linux](#tab/linux)

Aşağıdaki komutu çalıştırarak:

```dotnetcli
dotnet --list-sdks
```

Aşağıdakilere benzer çıktı alırsınız:

```console
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]
```

Ve aşağıdaki komutu çalıştırarak:

```dotnetcli
dotnet --list-runtimes
```

Aşağıdakilere benzer çıktı alırsınız:

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
```

# <a name="macos"></a>[Macos](#tab/macos)

Aşağıdaki komutu çalıştırarak:

```dotnetcli
dotnet --list-sdks
```

Aşağıdakilere benzer çıktı alırsınız:

```console
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]
```

Ve aşağıdaki komutu çalıştırarak:

```dotnetcli
dotnet --list-runtimes
```

Aşağıdakilere benzer çıktı alırsınız:

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

---

## <a name="uninstall-net-core"></a>.NET Core'u kaldır

# <a name="windows"></a>[Windows](#tab/windows)

.NET Core, .NET Core çalışma zamanı ve SDK sürümlerini kaldırmak için Windows **Ekle/Kaldır** iletişim kutusunu kullanır. Aşağıdaki şekilde .NET çalışma zamanı ve SDK yüklü çeşitli sürümleri ile **Programlar Ekle/ Kaldır** iletişim kutusunu gösterir.

![.NET Core'u kaldırmak için program ekleme / kaldırma](./media/remove-runtime-sdk-versions/programs-and-features.png)

Makinenizden kaldırmak istediğiniz sürümleri seçin ve **Kaldır'ı**tıklatın.

# <a name="linux"></a>[Linux](#tab/linux)

Linux'ta .NET Core'u (SDK veya çalışma süresi) kaldırmak için daha fazla seçenek vardır. .NET Core'u kaldırmanın en iyi yolu ,.NET Core'u yüklemek için kullandığınız eylemi yansıtmaktır. Ayrıntılar seçtiğiniz dağıtıma ve yükleme yöntemine bağlıdır.

> [!IMPORTANT]
> Red Hat kurulumları için ,NET Core'un yüklenmesi ve yüklenmesi hakkında bilgi almak için [Red Hat Getting Started Guide'a](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) başvurun.

.NET Core 2.1 ile başlayarak, bir paket yöneticisi kullanarak yükseltirken .NET Core SDK'yı kaldırmanız gerekmez. Paket yöneticisi `update` `refresh` veya komutları, daha yeni bir sürümün başarılı bir şekilde yüklenmesi yle eski sürümü otomatik olarak kaldırır.

Bir paket yöneticisi kullanarak .NET Core'u yüklediyseniz, .NET SDK'yı veya çalışma süresini kaldırmak için aynı paket yöneticisini kullanırsınız. .NET Core kurulumları en popüler paket yöneticilerini destekler. Ortamınızdaki kesin sözdizimi için dağıtımınızın paket yöneticisine ilişkin belgelere başvurun:

- [apt-get(8)](https://linux.die.net/man/8/apt-get) Ubuntu dahil olmak üzere Debian tabanlı sistemler tarafından kullanılır.
- [yum(8)](https://linux.die.net/man/8/yum) Fedora, CentOS ve Oracle Linux'ta kullanılır.
- [zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) openSUSE ve SUSE Linux Enterprise System (SLES) üzerinde kullanılır.
- [dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) Fedora'da kullanılır.

Hemen hemen her durumda, bir paketi `remove`kaldırmak için komutu .

Çoğu paket yöneticisi için .NET Core SDK `dotnet-sdk`kurulumuiçin paket adı, sürüm numarası takip eder. .NET Core SDK'nın 2.1.300 sürümü `2.1` nden başlayarak ve çalışma zamanının sürümünden başlayarak, yalnızca büyük ve küçük sürüm numaraları gereklidir: örneğin, .NET `dotnet-sdk-2.1`Core SDK sürüm 2.1.300 paket olarak başvurulabilir. Önceki sürümler tüm sürüm dizesini gerektirir: örneğin, `dotnet-sdk-2.1.200` .NET Core SDK'nın 2.1.200 sürümü için gerekli olacaktır.

SDK değil, yalnızca çalışma süresini yüklemiş makineler için paket adı `dotnet-runtime-<version>` .NET Core çalışma zamanı `aspnetcore-runtime-<version>` ve tüm çalışma zamanı yığını içindir.

.NET Core yüklemeleri 2.0'dan önce, SDK paket yöneticisi kullanılarak kaldırıldığında ana bilgisayar uygulamasını kaldırmadı. Kullanarak, `apt-get`komutu:

```bash
apt-get remove dotnet-host
```

'ye bağlı bir sürüm olmadığını `dotnet-host`unutmayın.

Bir tarball kullanarak yüklediyseniz, el ile yöntemi kullanarak .NET Core'u kaldırmanız gerekir.

SDK'ları ve çalışma sürelerini, bu sürümü içeren dizini kaldırarak ayrı ayrı kaldırırsınız. Örneğin, 1.0.1 SDK ve çalışma süresini kaldırmak için aşağıdaki bash komutlarını kullanırsınız:

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

SDK ve çalışma zamanı nın üst dizinleri, `dotnet --list-sdks` önceki `dotnet --list-runtimes` tabloda gösterildiği gibi, ve komuttan çıktıda listelenir.

# <a name="macos"></a>[Macos](#tab/macos)

Mac'te, bu sürümü içeren dizini kaldırarak SDK'ları ve çalışma sürelerini ayrı ayrı kaldırmanız gerekir. Örneğin, 1.0.1 SDK ve çalışma süresini kaldırmak için aşağıdaki bash komutlarını kullanırsınız:

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

SDK ve çalışma zamanı nın üst dizinleri, `dotnet --list-sdks` önceki `dotnet --list-runtimes` tabloda gösterildiği gibi, ve komuttan çıktıda listelenir.

---

## <a name="net-core-uninstall-tool"></a>.NET Core Kaldırma Aracı

[.NET Çekirdek Kaldırma](../additional-tools/uninstall-tool.md) Aracı`dotnet-core-uninstall`( ) bir sistemden .NET Core SDK'ları ve çalışma sürelerini kaldırmanızı sağlar. Hangi sürümlerin kaldırılması gerektiğini belirtmek için seçenekler topluluğu kullanılabilir.

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a>.NET Core SDK sürümlerinde Visual Studio bağımlılığı

Visual Studio 2019 sürüm 16.3'ten önce Visual Studio yükleyiciler bağımsız .NET Core SDK yükleyicisini aradılar. Sonuç olarak, Windows **Programları Ekle/Kaldır** iletişim kutusunda SDK sürümleri görünür. Visual Studio tarafından tek başına yükleyici kullanılarak yüklenen .NET Core SDK'ların kaldırılması Visual Studio'yu bozabilir. SDK'ları kaldırdıktan sonra Visual Studio'da sorun yaşıyorsanız, Visual Studio'nun belirli sürümünde Onarım'ı çalıştırın. Aşağıdaki tabloda .NET Core SDK sürümlerindeki Visual Studio bağımlılıklarından bazıları gösterilmektedir:

| Visual Studio sürüm | .NET Core SDK sürümü |
| -- | -- |
|  Visual Studio 2019 sürüm 16.2  | .NET Çekirdek SDK 2.2.4xx, 2.1.8xx |
|  Visual Studio 2019 sürüm 16.1 | .NET Çekirdek SDK 2.2.3xx, 2.1.7xx |
| Visual Studio 2019 sürüm 16.0 | .NET Çekirdek SDK 2.2.2xx, 2.1.6xx |
| Visual Studio 2017 sürümü 15.9 | .NET Çekirdek SDK 2.2.1xx, 2.1.5xx |
| Visual Studio 2017 sürümü 15.8 | .NET Çekirdek SDK 2.1.4xx |

Visual Studio 2019 sürüm 16.3 ile başlayan Visual Studio, .NET Core SDK'nın kendi kopyasından sorumludur. Bu nedenle, Artık Bu SDK sürümlerini **Programlar Ekle/Kaldır** iletişim kutusunda görmezsiniz.

## <a name="remove-the-nuget-fallback-folder"></a>NuGet geri dönüş klasörünü kaldırma

.NET Core 3.0 SDK'dan önce,.NET Core SDK yükleyiciler NuGet paketlerini saklamak için *NuGetFallbackFolder'ı* kullanmıştı. Bu önbellek `dotnet restore` gibi işlemler sırasında `dotnet build /t:Restore`kullanılmıştır. `NuGetFallbackFolder` *C:\Program Files\dotnet\sdk* adresinde Windows'da ve */usr/local/share/dotnet/sdk* adresinde bulunur.

Bu klasörü kaldırmak isteyebilirsiniz, eğer:

* Yalnızca .NET Core 3.0 SDK veya sonraki sürümleri kullanarak geliştiriyorsunuz.
* .NET Core SDK sürümlerini 3.0'dan önce kullanıyorsunuz, ancak çevrimiçi olarak çalışabilirsiniz ve işler bir kez daha yavaş olabilir.

NuGet geri dönüş klasörünü kaldırmak istiyorsanız, silebilirsiniz, ancak bunu yapmak için yönetici ayrıcalıklarına ihtiyacınız vardır.

*Dotnet* klasörünü silmek önerilmez. Bunu yapmak, daha önce yüklediğiniz tüm genel araçları kaldırır. Ayrıca, Windows'da:

- Visual Studio 2019 sürüm 16.3 ve sonraki sürümlerini kıracaksınız. Kurtarmak için **Onarım'ı** çalıştırabilirsiniz.
- **Programları Ekle/Kaldır** iletişim kutusunda .NET Core SDK girişleri varsa, bunlar yetim kalır.
