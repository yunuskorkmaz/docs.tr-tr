---
title: DotNet-sos Tanılama aracı-.NET CLı
description: Windows ve Linux 'ta yerel hata ayıklayıcıları ile kullanılan SOS hata ayıklayıcı uzantısını yönetmek için DotNet-sos CLı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: 59512c42a778f68bb3cd092dc854dcc727fd2881
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825448"
---
# <a name="sos-installer-dotnet-sos"></a>SOS yükleyicisi (DotNet-sos)

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="install"></a>Yükleme

İndirmek ve yüklemek için iki yol vardır `dotnet-sos` :

- **DotNet genel aracı:**

  NuGet paketinin en son sürümünü yüklemek için `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:

  ```dotnetcli
  dotnet tool install --global dotnet-sos
  ```

- **Doğrudan indirme:**

  Platformunuzla eşleşen araç yürütülebilirini indirin:

  | İşletim Sistemi  | Platform |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [ARM](https://aka.ms/dotnet-sos/win-arm) \| [ARM-x64](https://aka.ms/dotnet-sos/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-sos/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-sos/linux-x64) \| [ARM](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64) |

## <a name="synopsis"></a>Özeti

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a>Açıklama

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
