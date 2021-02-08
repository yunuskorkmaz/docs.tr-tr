---
description: ': MemoryStream. ınternalgetoriginandlength yöntemi hakkında daha fazla bilgi edinin'
title: MemoryStream. ınternalgetoriginandlength yöntemi (System.IO)
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 4232852c0835a43454f36271a43062e1240297a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802547"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a>MemoryStream.InternalGetOriginAndLength yöntemi

Bellek akışının iç başlangıç değerlerini ve uzunluğunu alır.

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a>Parametreler

- `origin` <xref:System.Int32>\
  Bu yöntem döndüğünde, yeni bir nesne oluşturulurken belirtilen bayt dizisinin boşluğu <xref:System.IO.MemoryStream> . Bayt dizisi tarafından oluşturulduysa 0 içerir <xref:System.IO.MemoryStream> .

- `length` <xref:System.Int32>\
  Bu yöntem döndüğünde, bellek akışı içindeki bayt sayısı.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `MemoryStream.InternalGetOriginAndLength`Yöntemi iç yöntemidir ve doğrudan kodunuzda kullanılması amaçlıyordu.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.IO>

**Bütünleştirilmiş kod:** mscorlib.dll (mscorlib.dll)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
