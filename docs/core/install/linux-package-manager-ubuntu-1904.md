---
title: Ubuntu 19,04 paket yöneticisi 'ne .NET Core 'u yükler-.NET Core
description: Ubuntu 19,04 ' de .NET Core SDK ve çalışma zamanı yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 98ceb0ae7f3fbd99c4be412fd1e19928793c348f
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836894"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a>Ubuntu 19,04 paket yöneticisi-.NET Core 'ı yükler

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Bu makalede, Ubuntu 19,04 ' de .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır. Çalışma zamanını yüklüyorsanız, hem .NET Core 'u hem de ASP.NET Core çalışma zamanlarını içerdiğinden [ASP.NET Core çalışma zamanını](#install-the-aspnet-core-runtime)yüklemenizi öneririz.

## <a name="register-microsoft-key-and-feed"></a>Microsoft anahtarını ve akışını kaydetme

.NET yüklemeden önce şunları yapmanız gerekir:

- Microsoft anahtarını kaydetme
- Ürün deposunu kaydetme
- Gerekli bağımlılıkları yükler

Bu işlemin makine başına bir kez yapılması yeterlidir.

Bir Terminal açın ve aşağıdaki komutları çalıştırın.

```bash
wget -q https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a>.NET Core SDK 'i yükler

Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> **DotNet-SDK-3,1**' i bulamıyor gibi bir hata iletisi alırsanız, bkz. [Paket Yöneticisi sorunlarını giderme](#troubleshoot-the-package-manager) bölümü.

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core çalışma zamanını yükler

Yükleme için kullanılabilen ürünleri güncelleştirin, ardından ASP.NET Core çalışma zamanını yüklemeniz gerekir. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> Bir hata iletisi alırsanız, **aspnetcore-Runtime-3,1 paketini bulamazsanız**, bkz. [Package Manager sorunlarını giderme](#troubleshoot-the-package-manager) bölümü.

## <a name="install-the-net-core-runtime"></a>.NET Core çalışma zamanını yükler

Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> **DotNet-Runtime-3,1 bulunamadı**hatasıyla benzer bir hata iletisi alırsanız, [Paket Yöneticisi sorunlarını giderme](#troubleshoot-the-package-manager) bölümüne bakın.

## <a name="how-to-install-other-versions"></a>Diğer sürümleri nasıl yüklenir

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Paket yöneticisinin sorunlarını giderme

**{.NET Core Package} paketi bulunamadı**hatasıyla benzer bir hata iletisi alırsanız aşağıdaki komutları çalıştırın.

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

Bu işe yaramazsa, aşağıdaki komutlarla el ile yüklemeyi çalıştırabilirsiniz.

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```
