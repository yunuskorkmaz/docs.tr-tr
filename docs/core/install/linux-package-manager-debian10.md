---
title: .NET Core 'u detem 10-Package Manager 'a (.NET Core) yükler
description: .NET Core SDK ve çalışma zamanını de, 10 ' da yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 1280758e7ea9300d83fa01532f3b051c6e1c0c67
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451075"
---
# <a name="debian-10-package-manager---install-net-core"></a>Detem 10 Package Manager-.NET Core 'ı yükler

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Bu makalede, bir paket yöneticisinin .NET Core 'u de, 10 ' da yüklemek için nasıl kullanılacağı açıklanır. Çalışma zamanını yüklüyorsanız, hem .NET Core 'u hem de ASP.NET Core çalışma zamanlarını içerdiğinden [ASP.NET Core çalışma zamanını](#install-the-aspnet-core-runtime)yüklemenizi öneririz.

## <a name="register-microsoft-key-and-feed"></a>Microsoft anahtar ve akışını Kaydet

.NET yüklemeden önce şunları yapmanız gerekir:

- Microsoft anahtarını kaydetme
- Ürün deposunu kaydetme
- Gerekli bağımlılıkları yükler

Bu, makine başına yalnızca bir kez yapılmalıdır.

Bir Terminal açın ve aşağıdaki komutları çalıştırın.

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a>.NET Core SDK 'i yükler

Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core çalışma zamanını yükler

Yükleme için kullanılabilen ürünleri güncelleştirin, sonra ASP.NET çalışma zamanını yükleme. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a>.NET Core çalışma zamanını yükler

Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a>Diğer sürümleri nasıl yüklenir

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
