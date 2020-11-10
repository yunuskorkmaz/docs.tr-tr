---
title: 'NETSDK1022: yinelenen öğeler dahil edildi.'
description: Varsayılan eklemeleri temel alarak yinelenen öğe iletisini çözümleme.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: 46c3d7d451e7c9e5b456b6e4e45054c3a4844386
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445805"
---
# <a name="netsdk1022-duplicate-items-were-included"></a>NETSDK1022: yinelenen öğeler dahil edildi.

**Bu makale şu şekilde geçerlidir:** ✔️ .NET 2.1.100 SDK ve sonraki sürümleri

Visual Studio 15,3 ' den başlayarak, .NET SDK varsayılan olarak proje dizinindeki öğeleri otomatik olarak içerir.  Bu `Compile` , ve `Content` hedeflerini içerir.  Bu, proje dosyanızı büyük ölçüde temizler ve sahip olduğunuz karmaşıklığı azaltır.

Doğru özelliği yanlış olarak ayarlayarak önceki davranışa döndürebilirsiniz.

Öğeler için örnek `Compile` :

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
