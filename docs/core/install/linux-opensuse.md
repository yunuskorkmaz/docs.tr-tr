---
title: OpenSUSE-.NET üzerine .NET 'i yükler
description: OpenSUSE üzerinde .NET SDK ve .NET çalışma zamanı yüklemek için çeşitli yollar gösterir.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: d238054a217a7295594db856d5497982572af377
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873958"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-opensuse"></a>OpenSUSE 'e .NET SDK veya .NET çalışma zamanı yüklemesi

.NET, openSUSE 'de desteklenir. Bu makalede, openSUSE 'ta .NET 'in nasıl yükleneceği açıklanır.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a>Desteklenen dağıtımlar

Aşağıdaki tabloda, openSUSE 15 üzerinde şu anda desteklenen .NET sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya openSUSE sürümü artık desteklenene kadar desteklenmeye devam eder.

- ✔️, openSUSE veya .NET sürümünün hala desteklendiğini gösterir.
- Bir ❌ , openSUSE veya .NET sürümünün bu openSUSE sürümünde desteklenmediğini belirtir.
- Hem openSUSE hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| openSUSE                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](#opensuse-15-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |

Aşağıdaki .NET sürümleri artık desteklenmemektedir. Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:

- 3.0
- 2,2
- 2.0

## <a name="remove-preview-versions"></a>Önizleme sürümlerini Kaldır

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="opensuse-15-"></a>openSUSE 15 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="how-to-install-other-versions"></a>Diğer sürümleri nasıl yüklenir

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Paket yöneticisinin sorunlarını giderme

Bu bölüm, .NET yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.

### <a name="unable-to-find-package"></a>Paket bulunamadı

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a>Getirilemedi

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a>Bağımlılıklar

Bir paket yöneticisi ile yüklediğinizde, bu kitaplıklar sizin için yüklenir. Ancak, .NET 'i el ile veya bağımsız bir uygulama yayımladığınızda, bu kitaplıkların yüklü olduğundan emin olmanız gerekir:

- krb5
- libıu
- libopenssl1_0_0

Hedef çalışma zamanı ortamının OpenSSL sürümü 1,1 veya daha yeniyse, **COMPAT-openssl10** yüklemeniz gerekir.

Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).

*System. Drawing. Common* derlemesini kullanan .NET uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:

- [libgdiplus (sürüm 6.0.1 veya üzeri)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > En son bir *libgdiplus* sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz. Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.

## <a name="next-steps"></a>Sonraki adımlar

- [.NET CLı için sekme tamamlamayı etkinleştirme](../tools/enable-tab-autocomplete.md)
- [Öğretici: Visual Studio Code kullanarak .NET SDK ile bir konsol uygulaması oluşturma](../tutorials/with-visual-studio-code.md)
