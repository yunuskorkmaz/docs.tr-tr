---
title: SDK ve .NET Core çalışma zamanı'nı Kaldır
description: Bu makalede SDK ve .NET Core çalışma zamanı hangi sürümlerinin yüklü olan, belirleme ve sonra Windows, Mac ve Linux'ta kaldırmak nasıl.
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.custom: seodec18
ms.openlocfilehash: 6204a28200f1db6350e695a9ab29502c46c25590
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129707"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>SDK ve .NET Core çalışma zamanı'nı kaldırma

Zamanla, SDK ve .NET Core çalışma zamanı güncelleştirilmiş sürümlerini yüklemek gibi .NET Core eski sürümlerini makinenizden kaldırmak isteyebilirsiniz. Çalışma zamanının daha eski sürümleri kaldırılıyor makalesinde ayrıntılı olarak paylaşılan framework uygulamaları çalıştırmak için seçilen çalışma zamanı değişebilir [.NET Core sürüm seçimi](selection.md).

## <a name="should-i-remove-a-version"></a>Ben bir sürümünü kaldırmanız gerekir?

[.NET Core sürüm seçimi](selection.md) davranışları ve .NET Core çalışma zamanı uyumluluğunu güncelleştirmeleri arasında önceki sürümlerini güvenli kaldırılmasını sağlar. .NET core çalışma zamanı güncelleştirmeleri, bir ana sürüm 1.x ve 2.x'i gibi ' bant' içinde uyumludur. Ayrıca, .NET Core SDK'sının daha yeni sürümleri, genellikle, çalışma zamanı, hedef önceki sürümleri uyumlu bir şekilde uygulamalar oluşturmanızı yapılandırabilmeyi sürdürmeniz.

Genel olarak, yalnızca en son SDK'sı ve uygulamanız için gereken çalışma zamanları en son düzeltme eki sürümü gerekir. Örnekleri burada başlatılamayan eski SDK veya çalışma zamanı sürümleri dahil koruma **project.json**-tabanlı uygulamaları. Uygulamanızı önceki bir SDK'ları veya çalışma zamanları belirli nedenlerle olmadığı sürece, eski sürümleri güvenli bir şekilde kaldırabilirsiniz.

## <a name="determine-what-is-installed"></a>Yüklü olduğunu belirleme

.NET Core 2.1 ile başlayarak, .NET CLI SDK sürümleri listelemek için kullanabileceğiniz seçenekleri ve makinenizde yüklü olan çalışma zamanı sahiptir.  Kullanım [ `dotnet --list-sdks` ](../tools/dotnet.md#options) makinenizde yüklü bir SDK'ları listesini görmek için. Kullanım [ `dotnet --list-runtimes` ](../tools/dotnet.md#options) makinenizde yüklü çalışma zamanları listesini görmek için. Aşağıdaki metni, Windows, macOS veya Linux için normal çıktı gösterilmektedir:

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

```console
C:\> dotnet --list-sdks
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

C:\> dotnet --list-runtimes
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

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

```console
$ dotnet --list-sdks
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]

$ dotnet --list-runtimes
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

# <a name="macostabmacos"></a>[macOS](#tab/macos)

```console
$ dotnet --list-sdks
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]

$ dotnet --list-runtimes
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

***

## <a name="uninstalling-net-core"></a>.NET Core kaldırma

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

.NET core kullanan Windows **Program Ekle/Kaldır** SDK ve .NET Core çalışma zamanı sürümleri kaldırılmaya iletişim. Aşağıdaki şekil gösterir **Program Ekle/Kaldır** çeşitli sürümleri yüklü SDK ve .NET çalışma zamanı ile iletişim.

![.NET Core kaldırmak için Program Ekle / Kaldır](./media/remove-runtime-sdk-versions/programs-and-features.png)

İstediğiniz makinenizden kaldırmak ve tüm sürümlerini seçin **kaldırma**.

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

Linux üzerinde .NET Core (SDK'sı veya çalışma zamanı) kaldırmak için daha fazla seçenek vardır. En iyi yolu, .NET Core kaldırmak, .NET Core yüklemek için kullanılan eylem yansıtma sağlamaktır. Özellikleri, seçtiğiniz dağıtım ve yükleme yöntemi bağlıdır.

> [!IMPORTANT]
> Red Hat yüklemelerinde başvurun [Red Hat Başlarken Kılavuzu](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) yükleme ve .NET Core kaldırma hakkında bilgi.

.NET Core 2.1 ile başlayarak, bir paket Yöneticisi'ni kullanarak yükseltme sırasında .NET Core SDK'yı kaldırmak için gerek yoktur. Paket Yöneticisi `update` veya `refresh` komutları otomatik olarak yeni bir sürüme başarılı yüklenmesinden sonra eski sürümü kaldırın.

Bir paket Yöneticisi'ni kullanarak .NET Core yüklü değilse, .NET SDK'sı veya çalışma zamanı'nı kaldırmak için aynı paket yöneticisini kullanın. .NET core yüklemeleri, en popüler paket yöneticileri destekler. Ortamınızda kesin sözdizimi için dağıtımınıza ait Paket Yöneticisi için belgelere bakın:

- [apt-get(8)](https://linux.die.net/man/8/apt-get) Ubuntu dahil olmak üzere Debian tabanlı sistemlerden tarafından kullanılır.
- [yum(8)](https://linux.die.net/man/8/yum) Fedora, CentOS ve Oracle Linux kullanılır.
- [zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) openSUSE ve SUSE Linux Enterprise sistem (SLES) kullanılır.
- [dnf(8)](https://dnf.readthedocs.io/latest/command_ref.html) Fedora üzerinde kullanılır.

Hemen hemen tüm durumlarda, bir paket kaldırmak için komutu olan `remove`.

Paket adı çoğu paket yöneticileri için .NET Core SDK'sı yüklemesi `dotnet-sdk`takip eden sürüm numarası. 2.1.300 sürümü ve .NET Core SDK sürümüyle başlayarak `2.1` çalışma zamanını, yalnızca birincil ve ikincil sürüm numaraları gereklidir: Örneğin, .NET Core SDK'sı sürüm 2.1.300 paketi olarak başvurulabilir `dotnet-sdk-2.1`. Önceki sürümler gerektiren tüm sürüm dizesini: Örneğin, `dotnet-sdk-2.1.200` .NET Core SDK'sını 2.1.200 sürümü için gerekli olacaktır.

Paket adı yalnızca çalışma zamanını ve SDK yüklü olduğu makineler için olduğundan `dotnet-runtime-<version>` .NET Core çalışma zamanı ve `aspnetcore-runtime-<version>` tüm çalışma zamanı yığını için.

.NET core yüklemeleri 2.0 önce konak uygulama kaldırmamanız, SDK'sı Paket Yöneticisi'ni kullanarak kaldırdığınızda. Kullanarak `apt-get`, komut:

```bash
apt-get remove dotnet-host
```

Hiçbir sürüm unutmayın iliştirilmiş `dotnet-host`.

Bir tarball kullanarak yüklediyseniz, .NET Core el ile gerçekleştirilen yöntemi kullanarak kaldırmanız gerekir.

Çalışma zamanları ve SDK'ları ayrı olarak, bu sürümü içeren dizine kaldırarak kaldırır. Örneğin, 1.0.1 kaldırmak için SDK ve çalışma zamanı, kullandığınız şu bash komutlarını:

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

SDK ve çalışma zamanı için üst dizinlerin çıktıda listelenen `dotnet --list-sdks` ve `dotnet --list-runtimes` önceki tabloda gösterildiği gibi komutu.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Mac bilgisayarlarda, SDK ve çalışma zamanları ayrı olarak, bu sürümü içeren dizine kaldırarak kaldırmanız gerekir. Örneğin, 1.0.1 kaldırmak için SDK ve çalışma zamanı, kullandığınız şu bash komutlarını:

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

SDK ve çalışma zamanı için üst dizinlerin çıktıda listelenen `dotnet --list-sdks` ve `dotnet --list-runtimes` önceki tabloda gösterildiği gibi komutu.

---
