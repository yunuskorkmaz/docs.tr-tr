---
title: 'NETSDK1022: yinelenen öğeler dahil edildi.'
description: Varsayılan eklemeleri temel alarak yinelenen öğe iletisini çözümleme.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: c2bdbbb5503e5e4f6e6826f95f5a2cb08c908ceb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717882"
---
# <a name="netsdk1022-duplicate-items-were-included"></a>NETSDK1022: yinelenen öğeler dahil edildi.

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2.1.100 SDK ve sonraki sürümleri

Visual Studio 2017/MSBuild sürüm 15,3 ' den başlayarak, .NET SDK varsayılan olarak proje dizinindeki öğeleri otomatik olarak ekler.  Bu `Compile` , ve `Content` hedeflerini içerir.  Bu, proje dosyanızı büyük ölçüde temizler ve sahip olduğunuz karmaşıklığı azaltır.

Doğru özelliği yanlış olarak ayarlayarak önceki davranışa döndürebilirsiniz.

Öğeler için örnek `Compile` :

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
