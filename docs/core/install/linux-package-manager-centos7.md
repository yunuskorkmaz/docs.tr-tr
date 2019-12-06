---
title: CentOS 7-Package Manager-.NET Core 'a .NET Core 'u yükler
description: .NET Core SDK ve çalışma zamanını CentOS 7 ' de yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: cb65811d5cae5c747c2660b4b10486f3162b9f33
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836943"
---
# <a name="centos-7-package-manager---install-net-core"></a>CentOS 7 Paket Yöneticisi-.NET Core 'ı yükler

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Bu makalede, CentOS 7 ' ye .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır. Çalışma zamanını yüklüyorsanız, hem .NET Core 'u hem de ASP.NET Core çalışma zamanlarını içerdiğinden [ASP.NET Core çalışma zamanını](#install-the-aspnet-core-runtime)yüklemenizi öneririz.

## <a name="register-microsoft-key-and-feed"></a>Microsoft anahtarını ve akışını kaydetme

.NET yüklemeden önce şunları yapmanız gerekir:

- Microsoft anahtarını kaydetme
- Ürün deposunu kaydetme
- Gerekli bağımlılıkları yükler

Bu işlemin makine başına bir kez yapılması yeterlidir.

Bir Terminal açın ve aşağıdaki komutu çalıştırın.

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a>.NET Core SDK 'i yükler

Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme. Terminalinizde aşağıdaki komutu çalıştırın.

```bash
sudo yum install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core çalışma zamanını yükler

Yükleme için kullanılabilen ürünleri güncelleştirin, sonra ASP.NET çalışma zamanını yükleme. Terminalinizde aşağıdaki komutu çalıştırın.

```bash
sudo yum install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>.NET Core çalışma zamanını yükler

Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme. Terminalinizde aşağıdaki komutu çalıştırın.

```bash
sudo yum install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Diğer sürümleri nasıl yüklenir

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
