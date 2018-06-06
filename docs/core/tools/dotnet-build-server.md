---
title: DotNet yapı sunuculu command - .NET Core CLI
description: Dotnet yapı sunuculu bir yapı tarafından başlatılan sunucuları ile etkileşim kurar.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 929b8d74aa5f3f0ad73b108be8a5bf22f86e30d6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696260"
---
# <a name="dotnet-build"></a>DotNet derleme

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Ad

`dotnet build-server` -Bir yapı tarafından başlatılan sunucularıyla etkileşim kurar.

## <a name="synopsis"></a>Özet

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a>Komutlar

`shutdown`

Dotnet başlatılan yapı sunucuları kapatır. Varsayılan olarak, tüm sunucuların kapatılır.

## <a name="options"></a>Seçenekler

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

`--msbuild`

MSBuild kapatır sunucusu oluşturun.

`--razor`

Razor kapatır sunucusu oluşturun.

`--vbcscompiler`

VB kapatır / C# Derleyici build sunucu.
