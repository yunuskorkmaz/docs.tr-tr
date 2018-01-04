---
title: "Global.JSON başvurusu"
description: ".NET Core Araçları sürüm ayarını verir global.json dosyası için şema bakın."
keywords: .NET, .NET core
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
ms.workload: dotnetcore
ms.openlocfilehash: c7e64995ed00a6b2df1b7e1dfa43c6bea5cf4535
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
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
