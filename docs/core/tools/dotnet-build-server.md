---
title: DotNet Build-Server komutu
description: DotNet Build-Server komutu, bir derleme tarafından başlatılan sunucularla etkileşime girer.
ms.date: 04/24/2019
ms.openlocfilehash: 1c6c6dcdb53d779426daf5daa470d2ad0470a7a1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523021"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Bu makale şu şekilde geçerlidir: ✓** .net Core 2,1 SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a>Name

`dotnet build-server`-bir derleme tarafından başlatılan sunucularla etkileşime girer.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Komutlar

- **`shutdown`**

  DotNet 'ten başlatılan yapı sunucularını kapatır. Varsayılan olarak, tüm sunucular kapanır.

## <a name="options"></a>Seçenekler

- **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

- **`--msbuild`**

  MSBuild yapı sunucusunu kapatır.

- **`--razor`**

  Razor derleme sunucusunu kapatır.

- **`--vbcscompiler`**

  VB/C# derleyici yapı sunucusunu kapatır.
