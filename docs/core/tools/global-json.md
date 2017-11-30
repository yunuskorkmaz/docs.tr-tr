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
ms.openlocfilehash: ffa97164736fc7f3edc450682d23bdf499b6eb34
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
