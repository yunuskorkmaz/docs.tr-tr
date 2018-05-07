---
title: Global.JSON başvurusu
description: .NET Core Araçları sürüm ayarını verir global.json dosyası için şema bakın.
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.openlocfilehash: 7479774c7b9cdda233cf32d791c16e7fc6d733a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
