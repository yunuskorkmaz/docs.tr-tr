---
title: DotNet-sos-.NET Core
description: DotNet-sos komut satırı aracını yükleme ve kullanma.
ms.date: 08/26/2020
ms.openlocfilehash: 3ce7ca79bbc2c72958d395e9d312e3001ec9fbf8
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598353"
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

## <a name="description"></a>Açıklama

`dotnet-sos`Küresel araç, Windows üzerinde WinDbg/CDB ve Linux ve MacOS 'ta lldb gibi yerel hata ayıklayıcılarından [yönetilen .NET Core durumunun incelemesinin](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) yapılmasına izin veren [sos hata ayıklayıcı uzantısını](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) da yüklüyor. Windows hata ayıklayıcı 'nın (>= sürüm 10.0.18317.1001) (WinDbg veya CDB) son sürümlerinin SOS 'yi Microsoft uzantı galerisinden otomatik olarak yükleytiğine, bu nedenle aracı aracılığıyla SOS 'in yüklenmesi `dotnet-sos` yalnızca Linux ve MacOS 'ta veya daha eski hata ayıklama araçları kullanılıyorsa Windows 'da gereklidir.

## <a name="options"></a>Seçenekler

- **`--version`**

  Sürüm bilgilerini görüntüler.

- **`-h|--help`**

  Komut satırı yardımını gösterir.

## <a name="dotnet-sos-install"></a>DotNet-sos yüklemesi

.NET Core işlemlerinde hata ayıklama kullanımı için [SOS uzantısını yerel olarak](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) kurar. MacOS ve Linux 'ta, uzantısının lldb başlatması sırasında otomatik olarak yüklenmesi için. lldbinit dosyası güncelleştirilecektir. Daha eski hata ayıklama araçları (< Version 10.0.18317.1001) ile Windows 'a SOS yüklüyorsanız, hata ayıklayıcıda çalıştırarak, uzantıyı WinDbg veya CDB 'de el ile yüklemeniz gerekir `.load %USERPROFILE%\.dotnet\sos\sos.dll` .

### <a name="synopsis"></a>Özeti

```console
dotnet-sos install
```

## <a name="dotnet-sos-uninstall"></a>DotNet-sos kaldır

[SOS uzantısını](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) kaldırır ve Linux veya MacOS 'ta ise lldb yapılandırmasından kaldırır.

### <a name="synopsis"></a>Özeti

```console
dotnet-sos uninstall
```
