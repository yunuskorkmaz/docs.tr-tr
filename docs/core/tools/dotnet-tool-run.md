---
title: dotnet aracı çalıştırma komutu
description: Dotnet araç çalıştırma komutu yerel bir aracı çağırır.
ms.date: 02/14/2020
ms.openlocfilehash: a088cd0b7f4bba014234a8189a42a63aa6d88f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847852"
---
# <a name="dotnet-tool-run"></a>dotnet tool run

**Bu makale şu şekilde dir:** ✔️ .NET Core 3.0 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet tool run`- Yerel bir aracı çağırır.

## <a name="synopsis"></a>Özet

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run <-h|--help>
```

## <a name="description"></a>Açıklama

Komut, `dotnet tool run` geçerli dizinin kapsamı içinde olan araç bildirimi dosyalarını arar. Belirtilen araca bir başvuru bulduğunda, aracı çalıştırZ. Daha fazla bilgi için yerel [bir aracı Çağır'a](global-tools.md#invoke-a-local-tool)bakın.

## <a name="arguments"></a>Bağımsız Değişkenler

- **`COMMAND_NAME`**

  Çalıştırılabilmek için aracın komut adı.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="example"></a>Örnek

- **`dotnet tool run dotnetsay`**

  `dotnetsay` Yerel aracı çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Çekirdek araçları](global-tools.md)
- [Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın](local-tools-how-to-use.md)
