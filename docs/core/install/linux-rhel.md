---
title: RHEL-.NET üzerinde .NET 'i yükler
description: RHEL üzerinde .NET SDK ve .NET çalışma zamanı yüklemek için çeşitli yollar gösterir.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 0b6138185bfd3e2f50c1b31e82779165715a5b6e
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851646"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a>RHEL üzerinde .NET SDK veya .NET çalışma zamanı 'nı yükler

.NET, RHEL 'de desteklenir. Bu makalede, RHEL 'de .NET 'in nasıl yükleneceği açıklanır.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>Red Hat aboneliğinizi kaydetme

RHEL 'de Red Hat 'ten .NET yüklemek için önce Red Hat abonelik Yöneticisi 'Ni kullanarak kaydolmanız gerekir. Bu, sisteminizde yapmadıysanız veya emin değilseniz, [.net Için Red Hat ürün belgelerine](https://access.redhat.com/documentation/net/5.0/)bakın.

## <a name="supported-distributions"></a>Desteklenen dağıtımlar

Aşağıdaki tabloda, hem RHEL 7 hem de RHEL 8 üzerinde şu anda desteklenen .NET sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya RHEL sürümü artık desteklenene kadar desteklenmeye devam eder.

- ✔️, RHEL veya .NET sürümünün hala desteklendiğini gösterir.
- A ❌ , RHEL veya .NET sürümünün bu RHEL sürümünde desteklenmediğini belirtir.
- Hem RHEL hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| RHEL                     | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](#rhel-8-)        | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [7](#rhel-7--net-50) | ✔️ 2,1        | ✔️ [3,1](#rhel-7--net-core-31)        | ✔️ [5,0](#rhel-7--net-50) |

Aşağıdaki .NET sürümleri artık desteklenmemektedir. Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:

- 3,0
- 2.2
- 2,0

## <a name="remove-preview-versions"></a>Önizleme sürümlerini Kaldır

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a>Diğer sürümleri nasıl yüklenir

.Net 'in diğer sürümlerini yüklemek için gereken adımlarda [.net Için Red Hat belgelerine](https://access.redhat.com/documentation/net/5.0/) başvurun.

## <a name="rhel-8-"></a>RHEL 8 ✔️

.NET, RHEL 8 için AppStream depolarına dahildir.

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7--net-50"></a>RHEL 7 ✔️ .NET 5,0

Aşağıdaki komut `scl-utils` paketini yüklüyor:

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a>SDK Yükleme

.NET SDK, .NET ile uygulama geliştirmenize olanak tanır. .NET SDK 'yı yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez. .NET SDK 'yı yüklemek için aşağıdaki komutları çalıştırın:

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50 -y
scl enable rh-dotnet50 bash
```

Red hat, `rh-dotnet50` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez. `rh-dotnet`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.

```bash
source scl_source enable rh-dotnet50
```

### <a name="install-the-runtime"></a>Çalışma zamanını yükler

.NET çalışma zamanı, .NET ile yapılan ve çalışma zamanını içermeyen uygulamaları çalıştırmanızı sağlar. Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50-aspnetcore-runtime-5.0 -y
scl enable rh-dotnet50 bash
```

Red hat, `rh-dotnet50` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez. `rh-dotnet50`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.

```bash
source scl_source enable rh-dotnet50
```

ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET çalışma zamanını yükleyebilirsiniz: Yukarıdaki komutlarda ' ı değiştirin `rh-dotnet50-aspnetcore-runtime-5.0` `rh-dotnet50-dotnet-runtime-5.0` .

## <a name="rhel-7--net-core-31"></a>RHEL 7 ✔️ .NET Core 3,1

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

Aşağıdaki komut `scl-utils` paketini yüklüyor:

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a>SDK Yükleme

.NET Core SDK .NET Core ile uygulama geliştirmenize olanak tanır. .NET Core SDK yüklerseniz, ilgili çalışma zamanını yüklemeniz gerekmez. .NET Core SDK yüklemek için aşağıdaki komutları çalıştırın:

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

Red hat, `rh-dotnet31` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez. Örneğin, `rh-dotnet31` `libcurl` temel RHEL sürümünden farklı bir sürümünü içerir. Bu, farklı bir sürümü beklemediği programlarda sorunlara yol açabilir `libcurl` . `rh-dotnet`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a>Çalışma zamanını yükler

.NET Core çalışma zamanı, .NET Core ile oluşturulmuş uygulamaları çalışma zamanını içermeyen uygulamalar çalıştırmanıza olanak tanır. Aşağıdaki komutlar, .NET Core için en uyumlu çalışma zamanı olan ASP.NET Core çalışma zamanını yükler. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

Red hat, `rh-dotnet31` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez. Örneğin, `rh-dotnet31` `libcurl` temel RHEL sürümünden farklı bir sürümünü içerir. Bu, farklı bir sürümü beklemediği programlarda sorunlara yol açabilir `libcurl` . `rh-dotnet31`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.

```bash
source scl_source enable rh-dotnet31
```

ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET Core çalışma zamanı 'nı yükleyebilirsiniz: Yukarıdaki komutlarda ' yi ile değiştirin `rh-dotnet31-aspnetcore-runtime-3.1` `rh-dotnet31-dotnet-runtime-3.1` .

## <a name="snap"></a>Bileşenlerinden

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>Bağımlılıklar

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a>Komut dosyalı yüklemesi

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>El ile yüklemesi

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Sonraki adımlar

- [Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma](../tutorials/with-visual-studio-code.md)
