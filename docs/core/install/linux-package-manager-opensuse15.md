---
title: OpenSUSE 15-Package Manager-.NET Core 'a .NET Core 'u yükler
description: OpenSUSE 15 üzerinde .NET Core SDK ve çalışma zamanı yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/26/2019
ms.openlocfilehash: cba07bafc32cc71a1cdaec08902284e105af4776
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740675"
---
# <a name="opensuse-15-package-manager---install-net-core"></a>openSUSE 15 Paket Yöneticisi-.NET Core 'ı yükler

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Bu makalede, openSUSE 15 ' te .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır. Çalışma zamanını yüklüyorsanız, hem .NET Core 'u hem de ASP.NET Core çalışma zamanlarını içerdiğinden [ASP.NET Core çalışma zamanını](#install-the-aspnet-core-runtime)yüklemenizi öneririz.

## <a name="register-microsoft-key-and-feed"></a>Microsoft anahtarını ve akışını kaydetme

.NET yüklemeden önce şunları yapmanız gerekir:

- Microsoft anahtarını kaydettirin.
- Ürün deposunu kaydedin.
- Gerekli bağımlılıkları yükler.

Bu işlemin makine başına tek bir kez yapılması yeterlidir.

Bir Terminal açın ve aşağıdaki komutları çalıştırın.

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget -q https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="dependency-error-with-net-core-31"></a>.NET Core 3,1 ile bağımlılık hatası

OpenSUSE için .NET Core 3,1 paket akışında **krb5** bağımlılığıyla ilgili bir sorun vardır. .NET Core 3,1 veya ASP.NET Core 3,1 ' ü yüklemeden önce doğru bağımlılıkları yüklemek için aşağıdaki komutu kullanın.

```bash
sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
```

## <a name="install-the-net-core-sdk"></a>.NET Core SDK 'i yükler

Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme. Terminalinizde aşağıdaki komutu çalıştırın.

```bash
sudo zypper install dotnet-sdk-3.1
```

> [!IMPORTANT]
> OpenSUSE için .NET Core 3,1 paket akışında **krb5** bağımlılığıyla ilgili bir sorun vardır. Doğru bağımlılıkları yüklemek için aşağıdaki komutu kullanın, ardından .NET Core 3,1 SDK 'sını yükler.
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core çalışma zamanını yükler

Yükleme için kullanılabilen ürünleri güncelleştirin, sonra ASP.NET çalışma zamanını yükleme. Terminalinizde aşağıdaki komutu çalıştırın.

```bash
sudo zypper install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> OpenSUSE için .NET Core 3,1 paket akışında **krb5** bağımlılığıyla ilgili bir sorun vardır. Doğru bağımlılıkları yüklemek için aşağıdaki komutu kullanın ve ardından ASP.NET Core 3,1 çalışma zamanını yüklemelisiniz.
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-net-core-runtime"></a>.NET Core çalışma zamanını yükler

Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme. Terminalinizde aşağıdaki komutu çalıştırın.

```bash
sudo zypper install dotnet-runtime-3.1
```

> [!IMPORTANT]
> OpenSUSE için .NET Core 3,1 paket akışında **krb5** bağımlılığıyla ilgili bir sorun vardır. Doğru bağımlılıkları yüklemek için aşağıdaki komutu kullanın, ardından .NET Core 3,1 çalışma zamanını yükler.
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="how-to-install-other-versions"></a>Diğer sürümleri nasıl yüklenir

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
