---
title: DotNet yapı sunucu komutu
description: Dotnet yapı sunucu komut, bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.
ms.date: 12/04/2018
ms.openlocfilehash: 7f78a0cae6e3297f3084754dc56b0da4eac38caf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665318"
---
# <a name="dotnet-build-server"></a>DotNet yapı sunucu

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Ad

`dotnet build-server` -Bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.

## <a name="synopsis"></a>Synopsis

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