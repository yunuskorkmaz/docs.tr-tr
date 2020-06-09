---
title: RHEL-.NET Core 'a .NET Core 'u yükler
description: RHEL üzerinde .NET Core SDK ve .NET Core çalışma zamanı yüklemesinin çeşitli yollarını gösterir.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 7ae55f881cd0c877cf1db24be7a4ee23320e21a8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603043"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-rhel"></a>RHEL üzerinde .NET Core SDK veya .NET Core çalışma zamanı yüklemesi

.NET Core, RHEL 'de desteklenir. Bu makalede, RHEL üzerinde .NET Core 'un nasıl yükleneceği açıklanır.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>Red Hat aboneliğinizi kaydetme

RHEL 'de Red Hat 'ten .NET Core yüklemek için, önce Red Hat abonelik Yöneticisi 'Ni kullanarak kaydolmanız gerekir. Bu, sisteminizde yapmadıysanız veya emin değilseniz, [.NET Core Için Red Hat ürün belgelerine](https://access.redhat.com/documentation/net_core/)bakın.

## <a name="supported-distributions"></a>Desteklenen dağıtımlar

Aşağıdaki tabloda, hem RHEL 7 hem de RHEL 8 üzerinde şu anda desteklenen .NET Core sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET Core sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya RHEL sürümüne ulaşıncaya kadar desteklenmeye devam eder.

- ✔️, RHEL veya .NET Core sürümünün hala desteklendiğini gösterir.
- A ❌ , RHEL veya .NET Core sürümünün bu RHEL sürümünde desteklenmediğini belirtir.
- Hem RHEL hem de bir .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| RHEL                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (yalnızca el ile yüklenir) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](#rhel-8-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [7](#rhel-7-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |

Aşağıdaki .NET Core sürümleri artık desteklenmemektedir. Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:

- 3.0
- 2,2
- 2.0

## <a name="how-to-install-other-versions"></a>Diğer sürümleri nasıl yüklenir

.NET Core 'un diğer sürümlerini yüklemek için gereken adımlarda [.NET Core Için Red Hat belgelerine](https://access.redhat.com/documentation/net_core/) bakın.

## <a name="rhel-8-"></a>RHEL 8 ✔️

.NET Core, RHEL 8 için AppStream depolarına dahildir.

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="rhel-7-"></a>RHEL 7 ✔️

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
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

Red hat, `rh-dotnet31-aspnetcore-runtime-3.1` diğer programları etkileyebileceğinden, kalıcı olarak etkinleştirilmesini önermez. Örneğin, `rh-dotnet31-aspnetcore-runtime-3.1` `libcurl` temel RHEL sürümünden farklı bir sürümünü içerir. Bu, farklı bir sürümü beklemediği programlarda sorunlara yol açabilir `libcurl` . `rh-dotnet31-aspnetcore-runtime-3.1`Kalıcı olarak etkinleştirmek istiyorsanız, _~/,bashrc_ dosyanıza şu satırı ekleyin.

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

ASP.NET Core çalışma zamanına alternatif olarak, ASP.NET Core desteği içermeyen .NET Core çalışma zamanı 'nı yükleyebilirsiniz: Yukarıdaki komutlarda ' yi ile değiştirin `rh-dotnet31-aspnetcore-runtime-3.1` `rh-dotnet31-dotnet-runtime-3.1` .

## <a name="snap"></a>Bileşenlerinden

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>Bağımlılıklar

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a>Komut dosyalı yüklemesi

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>El ile yüklemesi

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Sonraki adımlar

- [Öğretici: Visual Studio Code kullanarak .NET Core SDK bir konsol uygulaması oluşturma](../tutorials/with-visual-studio-code.md)
