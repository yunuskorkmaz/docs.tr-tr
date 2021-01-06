---
title: DotNet-sos Tanılama aracı-.NET CLı
description: Windows ve Linux 'ta yerel hata ayıklayıcıları ile kullanılan SOS hata ayıklayıcı uzantısını yönetmek için DotNet-sos CLı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: 09e8228c47bdc632bccf3c9ad2296d55fe420060
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97765013"
---
# <a name="sos-installer-dotnet-sos"></a>SOS yükleyicisi (DotNet-sos)

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="install"></a>Yükleme

İndirmek ve yüklemek için iki yol vardır `dotnet-sos` :

- **DotNet genel aracı:**

  NuGet paketinin en son sürümünü yüklemek için `dotnet-sos` [](https://www.nuget.org/packages/dotnet-sos) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:

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

`dotnet-sos`Genel araç, [sos hata ayıklayıcı uzantısını](sos-debugging-extension.md)yüklüyor. Bu uzantı, lldb ve WinDbg gibi yerel hata ayıklayıcılarından yönetilen .NET Core durumunu incelemenizi sağlar.

> [!NOTE]
> Aracı aracılığıyla SOS yükleme `dotnet-sos` yalnızca Linux veya macOS 'ta gereklidir.  Ayrıca, daha eski hata ayıklama araçları kullanıyorsanız Windows 'da da gerekli olabilir. [Windows hata ayıklayıcının](/windows-hardware/drivers/debugger/debugger-download-tools) son sürümleri (>= 10.0.18317.1001 of WinDbg veya CDB) Microsoft uzantı galerisinden otomatik olarak yük sos.  

## <a name="options"></a>Seçenekler

- **`--version`**

  Sürüm bilgilerini görüntüler.

- **`-h|--help`**

  Komut satırı yardımını gösterir.

## <a name="dotnet-sos-install"></a>DotNet-sos yüklemesi

.NET Core işlemlerinde hata ayıklamak için [SOS uzantısını](sos-debugging-extension.md) yerel olarak kurar. MacOS ve Linux 'ta, uzantısının lldb başlatması sırasında otomatik olarak yüklenmesi için *. lldbinit* dosyası güncelleştirilecektir. Windows 'a eski hata ayıklama araçlarıyla SOS yüklüyorsanız (sürüm 10.0.18317.1001 ' den önce), hata ayıklayıcıda çalıştırarak, uzantıyı WinDbg veya CDB 'ye el ile yüklemeniz gerekir `.load %USERPROFILE%\.dotnet\sos\sos.dll` .

### <a name="synopsis"></a>Özeti

```console
dotnet-sos install [--architecture <arch>]
```

### <a name="options"></a>Seçenekler

- **`--architecture <arch>`**

  Yüklenecek SOS ikililerinin işlemci mimarisini belirtir. Varsayılan olarak, `dotnet-sos` konak makinenin mimarisini yükleme. DotNet konak mimarisinden farklı bir mimariye SOS yüklemek istediğinizde bu seçeneği kullanın. Örneğin, bir Arm64 ana bilgisayardan Arm32 ikili dosyaları çalıştırıyorsanız, ile SOS 'i yüklemeniz gerekir `dotnet-sos install --architecture Arm` .

  Aşağıdaki mimariler mevcuttur:

  - `Arm`
  - `Arm64`
  - `X86`
  - `X64`

## <a name="dotnet-sos-uninstall"></a>DotNet-sos kaldır

[SOS uzantısını](sos-debugging-extension.md) kaldırır ve Linux ve MacOS 'ta, lldb yapılandırmasından kaldırır.

### <a name="synopsis"></a>Özeti

```console
dotnet-sos uninstall
```
