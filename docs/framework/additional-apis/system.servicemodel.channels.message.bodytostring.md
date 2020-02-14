---
title: Message. BodyToString yöntemi (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 9f1f852c0bd82299fd40afe66a5f90cd7c0335cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215499"
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
