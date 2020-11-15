---
title: DotNet aracı Run komutu
description: DotNet aracı Run komutu, yerel bir araç çağırır.
ms.date: 02/14/2020
ms.openlocfilehash: 116ecb61748a0ca70ed385b279b11b939748f4a8
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634161"
---
# <a name="dotnet-tool-run"></a>dotnet tool run

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet tool run` -Yerel bir araç çağırır.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run -h|--help
```

## <a name="description"></a>Açıklama

`dotnet tool run`Komutu, geçerli dizinin kapsamındaki araç bildirim dosyalarını arar. Belirtilen araca bir başvuru bulduğunda, aracı çalıştırır. Daha fazla bilgi için bkz. [yerel bir araç çağırma](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Arguments

- **`COMMAND_NAME`**

  Çalıştırılacak aracın komut adı.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="example"></a>Örnek

- **`dotnet tool run dotnetsay`**

  `dotnetsay`Yerel Aracı çalıştırır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET araçları](global-tools.md)
- [Öğretici: .NET CLı kullanarak .NET yerel aracını yükleyip kullanma](local-tools-how-to-use.md)
