---
title: 'NETSDK1022: yinelenen öğeler dahil edildi.'
description: Varsayılan eklemeleri temel alarak yinelenen öğe iletisini çözümleme.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: bc803f5316bf09c12c563f1a63b8385d1be4e9ce
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506642"
---
# <a name="netsdk1022-duplicate-items-were-included"></a>NETSDK1022: yinelenen öğeler dahil edildi.

**Bu makale şu şekilde geçerlidir:** ✔️ .NET 2.1.100 SDK ve sonraki sürümleri

Visual Studio 2017/MSBuild sürüm 15,3 ' den başlayarak, .NET SDK varsayılan olarak proje dizinindeki öğeleri otomatik olarak ekler.  Bu `Compile` , ve `Content` hedeflerini içerir.  Bu, proje dosyanızı büyük ölçüde temizler ve sahip olduğunuz karmaşıklığı azaltır.

Doğru özelliği yanlış olarak ayarlayarak önceki davranışa döndürebilirsiniz.

Öğeler için örnek `Compile` :

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
