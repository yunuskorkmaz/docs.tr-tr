---
title: Message. BodyToString yöntemi (System. ServiceModel. Channels)
author: mairaw
ms.author: mairaw
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 7b0b56bfda1c0c37f43f95e9684d3b4042c1b97c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451208"
---
# <a name="messagebodytostring-method"></a>Message. BodyToString yöntemi

<xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> yöntemini çağırarak ileti gövdesini bir dizeye dönüştürür.

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a>Parametreler

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  İleti gövdesini bir dizeye dönüştürmek için kullanılan yazıcı.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `Message.BodyToString` yöntemi dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.ServiceModel.Channels>

**Bütünleştirilmiş kod:** System. ServiceModel. dll

**.NET Framework sürümleri:** 3,0 sürümünden itibaren kullanılabilir.
