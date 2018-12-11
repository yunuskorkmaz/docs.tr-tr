---
title: DotNet yapı sunucu komutu
description: Dotnet yapı sunucu komut, bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.
ms.date: 12/04/2018
ms.openlocfilehash: 7f78a0cae6e3297f3084754dc56b0da4eac38caf
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169670"
---
# <a name="dotnet-build-server"></a>DotNet yapı sunucu

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Ad

`dotnet build-server` -Bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.

## <a name="synopsis"></a>Özeti

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Komutlar

* **`shutdown`**

  Dotnet başlatılan yapı sunucularını kapatır. Varsayılan olarak, tüm sunucuların kapatılır.

## <a name="options"></a>Seçenekler

* **`-h|--help`**

  Komut için kısa bir Yardım yazdırır.

* **`--msbuild`**

  Yapı sunucusunda MSBuild kapatır.

* **`--razor`**

  Yapı sunucusunda Razor kapatır.

* **`--vbcscompiler`**

  Kapatan VB / C# Derleyici sunucusu derleme.