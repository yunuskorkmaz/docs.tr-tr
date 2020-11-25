---
title: .NET 'i Fedora-.NET üzerine yükler
description: Fedora üzerinde .NET SDK ve .NET çalışma zamanı yüklemenin çeşitli yollarını gösterir.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: f7422941af7e39d69d286a0f79920b025c1bf9c0
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031910"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a>.NET SDK veya .NET çalışma zamanını Fedora 'ya yükler

.NET, Fedora 'da desteklenir. Bu makalede, Fedora 'da .NET yüklemesi açıklanmaktadır. Bir Fedora sürümü destek dışı kaldığında, .NET artık bu sürümde desteklenmemektedir. Ancak, bu yönergeler desteklenmese de bu sürümler üzerinde çalışan .NET almanıza yardımcı olabilir.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>Desteklenen dağıtımlar

Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen Fedora sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ya da [Fedora sürümü yaşam sonuna](https://fedoraproject.org/wiki/End_of_life)ulaşana kadar desteklenmeye devam eder.

- ✔️, Fedora veya .NET sürümünün hala desteklendiğini gösterir.
- Bir ❌ , Fedora veya .NET sürümünün bu Fedora sürümünde desteklenmediğini belirtir.
- Hem Fedora hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| Fedora               | .NET Core 2.1 | .NET Core 3,1 | .NET 5,0 |
|----------------------|---------------|---------------|----------|
| ✔️ [33](#fedora-33-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [32](#fedora-32-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌[31](#fedora-31-) | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌[30](#fedora-30-) | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌[29](#fedora-29-) | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌[28](#fedora-28-) | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |
| ❌[27](#fedora-27-) | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |

Aşağıdaki .NET sürümleri artık desteklenmemektedir. Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:

- 3,0
- 2.2
- 2,0

## <a name="remove-preview-versions"></a>Önizleme sürümlerini Kaldır

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a>Diğer sürümleri nasıl yüklenir

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-33-"></a>Fedora 33 ✔️

> [!TIP]
> .NET Core 3,1, Fedora 33 için varsayılan paket depolarında kullanılabilir. .NET Core 3,1 yüklemek için, veya gibi `dnf install` uygun Paketle komutunu kullanın `aspnetcore-runtime-3.1` `dotnet-sdk-3.1` . .NET 5,0 henüz varsayılan paket depolarında kullanılabilir değildir.

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/33/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-32-"></a>Fedora 32 ✔️

> [!TIP]
> .NET Core 3,1, Fedora 32 için varsayılan paket depolarında kullanılabilir. .NET Core 3,1 yüklemek için, veya gibi `dnf install` uygun Paketle komutunu kullanın `aspnetcore-runtime-3.1` `dotnet-sdk-3.1` . .NET 5,0 henüz varsayılan paket depolarında kullanılabilir değildir.

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/32/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-31-"></a>Fedora 31 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a>Fedora 30 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a>Fedora 29 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a>Fedora 28 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a>Fedora 27 ❌

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a>Paket yöneticisinin sorunlarını giderme

Bu bölüm, .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.

### <a name="unable-to-find-package"></a>Paket bulunamadı

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a>Getirilemedi

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

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
