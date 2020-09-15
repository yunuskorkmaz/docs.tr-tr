---
title: DotNet-sos-.NET Core
description: DotNet-sos komut satırı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 08/26/2020
ms.openlocfilehash: ba83105718909038ca56129ed8a5063aeff12e89
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065090"
---
# <a name="sos-installer-dotnet-sos"></a>SOS yükleyicisi (DotNet-sos)

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="install-dotnet-sos"></a>DotNet 'yi yükler-sos

NuGet paketinin en son sürümünü yüklemek için `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:

```dotnetcli
dotnet tool install -g dotnet-sos
```

## <a name="synopsis"></a>Özeti

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a>Description

`dotnet-sos`Küresel araç, Windows üzerinde WinDbg/CDB ve Linux ve macOS 'ta lldb gibi yerel hata ayıklayıcılarından [yönetilen .NET Core durumunun incelemesinin](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) yapılmasına izin veren [sos hata ayıklayıcı uzantısını](../../framework/tools/sos-dll-sos-debugging-extension.md) da yüklüyor. Windows hata ayıklayıcının son sürümleri (>= WinDbg veya CDB 'nin 10.0.18317.1001 sürümü), SOS 'yi Microsoft uzantı Galerisi 'nden otomatik olarak yükler, bu nedenle aracı aracılığıyla SOS yüklemek `dotnet-sos` yalnızca Linux ve macOS 'ta veya daha eski hata ayıklama araçları kullanılıyorsa Windows 'ta gereklidir.

## <a name="options"></a>Seçenekler

- **`--version`**

  Sürüm bilgilerini görüntüler.

- **`-h|--help`**

  Komut satırı yardımını gösterir.

## <a name="dotnet-sos-install"></a>DotNet-sos yüklemesi

.NET Core işlemlerinde hata ayıklamak için [SOS uzantısını](../../framework/tools/sos-dll-sos-debugging-extension.md) yerel olarak kurar. MacOS ve Linux 'ta, uzantısının lldb başlatması sırasında otomatik olarak yüklenmesi için. lldbinit dosyası güncelleştirilecektir. Daha eski hata ayıklama araçları (< Version 10.0.18317.1001) ile Windows 'a SOS yüklüyorsanız, hata ayıklayıcıda çalıştırarak, uzantıyı WinDbg veya CDB 'de el ile yüklemeniz gerekir `.load %USERPROFILE%\.dotnet\sos\sos.dll` .

### <a name="synopsis"></a>Özeti

```console
dotnet-sos install
```

## <a name="dotnet-sos-uninstall"></a>DotNet-sos kaldır

[SOS uzantısını](../../framework/tools/sos-dll-sos-debugging-extension.md) kaldırır ve Linux veya MacOS 'ta ise lldb yapılandırmasından kaldırır.

### <a name="synopsis"></a>Özeti

```console
dotnet-sos uninstall
```
