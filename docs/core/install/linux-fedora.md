---
title: .NET 'i Fedora-.NET üzerine yükler
description: Fedora üzerinde .NET SDK ve .NET çalışma zamanı yüklemenin çeşitli yollarını gösterir.
author: adegeo
ms.author: adegeo
ms.date: 02/17/2021
ms.openlocfilehash: efaad4788db2200b1a47f9b4ae2414730588c6ae
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255769"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a>.NET SDK veya .NET çalışma zamanını Fedora 'ya yükler

.NET, Fedora 'da desteklenir ve bu makalede, Fedora 'da .NET yüklemesi açıklanmaktadır. Bir Fedora sürümü destek dışı kaldığında, .NET artık bu sürümde desteklenmemektedir.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

Bir paket yöneticisi olmadan .NET yükleme hakkında daha fazla bilgi için aşağıdaki makalelerden birine bakın:

- [.NET SDK veya .NET çalışma zamanını yaslama ile birlikte yükler.](linux-snap.md)
- [.NET SDK veya .NET çalışma zamanını bir komut dosyası ile birlikte yükler.](linux-scripted-manual.md#scripted-install)
- [.NET SDK veya .NET çalışma zamanını el ile yükleyebilirsiniz.](linux-scripted-manual.md#manual-install)

## <a name="install-net-50"></a>.NET 5,0 'yi yükler

Fedora için varsayılan paket depolarında sunulan en son .NET sürümü .NET 5,0 ' dir.

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="install-net-core-31"></a>.NET Core 3,1 'yi yükler

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="supported-distributions"></a>Desteklenen dağıtımlar

Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen Fedora sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ya da [Fedora sürümü yaşam sonuna](https://fedoraproject.org/wiki/End_of_life)ulaşana kadar desteklenmeye devam eder.

- ✔️, Fedora veya .NET sürümünün hala desteklendiğini gösterir.
- Bir ❌ , Fedora veya .NET sürümünün bu Fedora sürümünde desteklenmediğini belirtir.
- Hem Fedora hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| .NET sürümü  | Fedora 33 ✔️ | 32 ✔️ | 31 ❌ | ila ❌ | , ❌ | 28.672 ❌ | döndürdü ❌ |
| ------------  | ---------: | --: | --: | --: | --: | --: | --: |
| .NET 5.0      | ✔️        | ✔️ | ❌|❌ |❌ |❌  |❌ |
| .NET Core 3.1 | ✔️        | ✔️ | ✔️|✔️ |✔️ |❌  |❌ |
| .NET Core 2.1 | ✔️        | ✔️ | ✔️|✔️ |✔️ |✔️  |✔️ |

Aşağıdaki .NET sürümleri artık desteklenmemektedir. Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:

- 3.0
- 2,2
- 2.0

## <a name="remove-preview-versions"></a>Önizleme sürümlerini Kaldır

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="dependencies"></a>Bağımlılıklar

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="install-on-older-distributions"></a>Daha eski dağıtımlarla yüklensin

Eski Fedora sürümleri, varsayılan paket depolarında .NET Core içermez. [ _DotNet-install.sh_ betiği](linux-scripted-manual.md#scripted-install)aracılığıyla .net 'i [Snap](linux-snap.md)Ile yükleyebilir veya .net yüklemek için Microsoft 'un deposunu kullanabilirsiniz:

01. Öncelikle, güvenilen anahtarlar listenize Microsoft imzalama anahtarını ekleyin.

    ```bash
    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    ```

02. Ardından, Microsoft paket deposunu ekleyin. Deponun kaynağı Fedora sürümünüzü temel alır.

    | Fedora sürümü | Paket deposu |
    | -------------- | ------- |
    | 31             | `https://packages.microsoft.com/config/fedora/31/prod.repo` |
    | 30             | `https://packages.microsoft.com/config/fedora/30/prod.repo` |
    | 29             | `https://packages.microsoft.com/config/fedora/29/prod.repo` |
    | 28             | `https://packages.microsoft.com/config/fedora/28/prod.repo` |
    | 27             | `https://packages.microsoft.com/config/fedora/27/prod.repo` |

    ```bash
    sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
    ```

[!INCLUDE [linux-dnf-install-31](./includes/linux-install-31-dnf.md)]

## <a name="how-to-install-other-versions"></a>Diğer sürümleri nasıl yüklenir

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Paket yöneticisinin sorunlarını giderme

Bu bölüm, .NET veya .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.

### <a name="unable-to-find-package"></a>Paket bulunamadı

Bir paket yöneticisi olmadan .NET yükleme hakkında daha fazla bilgi için aşağıdaki makalelerden birine bakın:

- [.NET SDK veya .NET çalışma zamanını yaslama ile birlikte yükler.](linux-snap.md)
- [.NET SDK veya .NET çalışma zamanını bir komut dosyası ile birlikte yükler.](linux-scripted-manual.md#scripted-install)
- [.NET SDK veya .NET çalışma zamanını el ile yükleyebilirsiniz.](linux-scripted-manual.md#manual-install)

### <a name="failed-to-fetch"></a>Getirilemedi

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="next-steps"></a>Sonraki adımlar

- [.NET CLı için sekme tamamlamayı etkinleştirme](../tools/enable-tab-autocomplete.md)
- [Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma](../tutorials/with-visual-studio-code.md)
