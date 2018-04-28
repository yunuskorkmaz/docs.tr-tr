---
title: Global.JSON başvurusu
description: .NET Core Araçları sürüm ayarını verir global.json dosyası için şema bakın.
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: ac53a899e76c99527f2670d0a6bed3f8cc6ce31f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="globaljson-reference"></a>Global.JSON başvurusu

*Global.json* dosyasının aracılığıyla kullanılan .NET Core Araçları sürüm seçimine olanak tanır `sdk` özelliği.

.NET core CLI araçlarını (hangi mutlaka proje dizini ile aynı değil) geçerli çalışma dizini veya onun üst dizinlerden biri bu dosyada arayın.

## <a name="sdk"></a>SDK'sı
Tür: nesnesi

SDK hakkında bilgileri belirtir.

### <a name="version"></a>sürüm
Türü: dize

Kullanmak için SDK sürümü.

Örneğin:

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```
