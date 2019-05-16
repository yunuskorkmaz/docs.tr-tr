---
title: DotNet yapı sunucu komutu
description: Dotnet yapı sunucu komut, bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.
ms.date: 04/24/2019
ms.openlocfilehash: fa663bc045e8abfc3375a0226be7d16331b49740
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632093"
---
# <a name="dotnet-build-server"></a>DotNet yapı sunucu

**Bu makale için geçerlidir: ✓** .NET Core 2.1 SDK ve sonraki sürümler

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

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
