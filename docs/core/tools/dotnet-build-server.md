---
title: DotNet Build-Server komutu
description: DotNet Build-Server komutu, bir derleme tarafından başlatılan sunucularla etkileşime girer.
ms.date: 04/24/2019
ms.openlocfilehash: e77a4d9f49f555ac847bb13380380599eef881b1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734381"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

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
