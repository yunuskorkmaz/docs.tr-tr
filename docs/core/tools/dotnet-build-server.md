---
title: DotNet Build-Server komutu
description: DotNet Build-Server komutu, bir derleme tarafından başlatılan sunucularla etkileşime girer.
ms.date: 04/24/2019
ms.openlocfilehash: 89d1aba104e2cb07b46766a3768eed68d85a7aa7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117768"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Bu makale şu şekilde geçerlidir: ✓** .net Core 2,1 SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a>Ad

`dotnet build-server`-Bir derleme tarafından başlatılan sunucularla etkileşime girer.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Komutlar

* **`shutdown`**

  DotNet 'ten başlatılan yapı sunucularını kapatır. Varsayılan olarak, tüm sunucular kapanır.

## <a name="options"></a>Seçenekler

* **`-h|--help`**

  Komut için kısa bir yardım yazdırır.

* **`--msbuild`**

  MSBuild yapı sunucusunu kapatır.

* **`--razor`**

  Razor derleme sunucusunu kapatır.

* **`--vbcscompiler`**

  VB/C# derleyici yapı sunucusunu kapatır.
