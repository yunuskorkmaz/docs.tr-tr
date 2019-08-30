---
title: DotNet Build-Server komutu
description: DotNet Build-Server komutu, bir derleme tarafından başlatılan sunucularla etkileşime girer.
ms.date: 04/24/2019
ms.openlocfilehash: b2dfd5f317466f18d9246bd1fb281a92c42f6d9d
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168105"
---
# <a name="dotnet-build-server"></a>dotnet build-server

**Bu makale şu şekilde geçerlidir: ✓** .net Core 2,1 SDK ve sonraki sürümleri

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a>Ad

`dotnet build-server`-Bir derleme tarafından başlatılan sunucularla etkileşime girer.

## <a name="synopsis"></a>Özeti

```console
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
