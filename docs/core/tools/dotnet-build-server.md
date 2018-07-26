---
title: DotNet yapı sunucu command - .NET Core CLI
description: Dotnet yapı sunucu komut, bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.
author: mairaw
ms.author: mairaw
ms.date: 07/02/2018
ms.openlocfilehash: 1c59c85f246b79c7e2552f704db5b4f076f9b502
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404339"
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

`shutdown`

Dotnet başlatılan yapı sunucularını kapatır. Varsayılan olarak, tüm sunucuların kapatılır.

## <a name="options"></a>Seçenekler

`-h|--help`

Komut için kısa bir Yardım yazdırır.

`--msbuild`

Yapı sunucusunda MSBuild kapatır.

`--razor`

Yapı sunucusunda Razor kapatır.

`--vbcscompiler`

Kapatan VB / C# Derleyici sunucusu derleme.
