---
title: Ubuntu 18.04 paket yöneticisine .NET Core yükle - .NET Core
description: .NET Core SDK'yı ve çalışma süresini Ubuntu 18.04'e yüklemek için bir paket yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: e36116d357b8fcd5ced328a574e12c558dd9e2f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920684"
---
# <a name="ubuntu-1804-package-manager---install-net-core"></a>Ubuntu 18.04 Paket Yöneticisi - Install .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Bu makalede, Ubuntu 18.04'e .NET Core yüklemek için bir paket yöneticisinin nasıl kullanılacağı açıklanmaktadır. Çalışma süresini yüklüyorsanız, hem .NET Core hem de ASP.NET Core [çalışma sürelerini içerdiğinden, ASP.NET Core çalışma süresini](#install-the-aspnet-core-runtime)yüklemenizi öneririz.

## <a name="register-microsoft-key-and-feed"></a>Microsoft anahtarını ve akışını kaydetme

.NET'i yüklemeden önce şunları yapmanız gerekir:

- Microsoft anahtarını kaydedin.
- Ürün deposunu kaydedin.
- Gerekli bağımlılıkları yükleyin.

Bu işlemin makine başına tek bir kez yapılması yeterlidir.

Bir terminal açın ve aşağıdaki komutları çalıştırın.

```bash
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a>.NET Core SDK’sını yükleme

Yükleme için kullanılabilen ürünleri güncelleştirin ve sonra .NET Core SDK'yı yükleyin. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> **Paket dotnet-sdk-3.1'i bulamayınca**benzer bir hata iletisi alırsanız, [sorun giderme bölümüne](#troubleshoot-the-package-manager) bakın.

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core çalışma süresini yükleme

Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından ASP.NET Core çalışma süresini yükleyin. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> **Aspnetcore-runtime-3.1 paketini bulamayınca**benzer bir hata iletisi alırsanız, [Sorun Giderme Bölümü'ne](#troubleshoot-the-package-manager) bakın.

## <a name="install-the-net-core-runtime"></a>.NET Core çalışma süresini yükleme

Yükleme için kullanılabilen ürünleri güncelleştirin ve .NET Core çalışma süresini yükleyin. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> **Paket dotnet-runtime-3.1'i bulamayınca**benzer bir hata iletisi alırsanız, [sorun giderme bölümüne](#troubleshoot-the-package-manager) bakın.

## <a name="how-to-install-other-versions"></a>Diğer sürümler nasıl yüklenir?

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Paket yöneticisinin sorun giderme

Bu bölümde, .NET Core'u yüklemek için paket yöneticisini kullanırken karşılaşabileceğiniz sık karşılaşılan hatalar hakkında bilgi verilmektedir.

### <a name="unable-to-locate"></a>Bulunamıyor

**{.NET Core paketi} paketini bulamayıncabenzer**bir hata iletisi alırsanız, aşağıdaki komutları çalıştırın.

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

Bu işe yaramazsa, aşağıdaki komutları içeren bir el ile yükleme çalıştırabilirsiniz.

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/18.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a>Getirilemedi

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
