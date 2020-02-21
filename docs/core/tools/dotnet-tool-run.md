---
title: DotNet aracı Run komutu
description: DotNet aracı Run komutu, yerel bir araç çağırır.
ms.date: 02/14/2020
ms.openlocfilehash: 05b21c0f5ea86f4b99b220f556c61bf83f464114
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543882"
---
# <a name="dotnet-tool-run"></a>DotNet aracı çalıştırması

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri

## <a name="name"></a>Adı

`dotnet tool run`-yerel bir araç çağırır.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet tool run <COMMAND NAME> 
dotnet tool run <-h|--help>
```

## <a name="description"></a>Açıklama

`dotnet tool run` komutu, geçerli dizinin kapsamındaki araç bildirimi dosyalarını arar. Belirtilen araca bir başvuru bulduğunda, aracı çalıştırır. Daha fazla bilgi için bkz. [yerel bir araç çağırma](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Bağımsız Değişkenler

- **`COMMAND_NAME`**

  Çalıştırılacak aracın komut adı.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

## <a name="example"></a>Örnek

- **`dotnet tool run dotnetsay`**

  `dotnetsay` yerel aracını çalıştırır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core araçları](global-tools.md)
