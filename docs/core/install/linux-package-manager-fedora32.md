---
title: .NET Core 'u Fedora 32-Package Manager-.NET Core 'a yükler
description: .NET Core SDK ve çalışma zamanını Fedora 32 ' ye yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 04/28/2020
ms.openlocfilehash: e5a69bf00e7e2969143e044aea4c9938fd5a610d
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624968"
---
# <a name="fedora-32-package-manager---install-net-core"></a>Fedora 32 Paket Yöneticisi-.NET Core 'ı yükler

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Bu makalede, Fedora 32 ' de .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

Fedora 32 ile başlayarak, .NET Core 3,1, Fedora 'daki varsayılan paket depolarında sunulmaktadır.

## <a name="install-the-net-core-sdk"></a>.NET Core SDK’sını yükleme

.NET Core SDK 'i yükler. Terminalinizde aşağıdaki komutu çalıştırın.

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core çalışma zamanını yükler

ASP.NET çalışma zamanını yükler. Terminalinizde aşağıdaki komutu çalıştırın.

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>.NET Core çalışma zamanını yükler

.NET Core çalışma zamanını yükler. Terminalinizde aşağıdaki komutu çalıştırın.

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Diğer sürümleri nasıl yüklenir

.NET Core 'un diğer sürümlerini yüklemek için [.NET Core SDK](sdk.md?pivots=os-linux#download-and-manually-install) veya [.NET Core çalışma zamanını](runtime.md?pivots=os-linux#download-and-manually-install)el ile yükleyebilirsiniz.
