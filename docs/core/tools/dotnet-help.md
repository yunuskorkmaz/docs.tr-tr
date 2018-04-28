---
title: DotNet Yardım komut - .NET Core CLI
description: Belirtilen komut için çevrimiçi belgeleri ayrıntılı dotnet Yardım komut gösterir.
author: mairaw
ms.author: mairaw
ms.date: 08/17/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 189eeea87babbce16751c5875f62c990ebecc10a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-help-reference"></a>DotNet Yardım başvurusu

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>Ad

`dotnet help` -Gösterir, belirtilen komutu için çevrimiçi belgeleri daha ayrıntılı.

## <a name="synopsis"></a>Özet

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>Açıklama

`dotnet help` Komutu docs.microsoft.com belirtilen komut hakkında daha ayrıntılı bilgi için ayarlama başvuru sayfası açılır.

## <a name="arguments"></a>Arguments

`COMMAND_NAME`

.NET Core CLI komut adı. Geçerli CLI komutlarının bir listesi için bkz: [CLI komutları](index.md#cli-commands).

## <a name="options"></a>Seçenekler

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

## <a name="examples"></a>Örnekler

Belgeleri sayfasını açar [dotnet yeni](dotnet-new.md) komutu:

`dotnet help new`
