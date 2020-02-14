---
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
ms.openlocfilehash: d82b5080e9fbd5fc6603f1cddae996c75a06d3a3
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215468"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a>MemoryStream. ınternalgetoriginandlength yöntemi

Bellek akışının iç başlangıç değerlerini ve uzunluğunu alır.

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a>Parametreler

- `origin` <xref:System.Int32>\
  Bu yöntem, yeni bir <xref:System.IO.MemoryStream> nesnesi oluşturulurken belirtilen bayt dizisinin sapmasını döndürür. Bayt dizisi <xref:System.IO.MemoryStream>tarafından oluşturulduysa 0 içerir.

- `length` <xref:System.Int32>\
  Bu yöntem döndüğünde, bellek akışı içindeki bayt sayısı.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `MemoryStream.InternalGetOriginAndLength` yöntemi dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System.IO>

**Bütünleştirilmiş kod:** mscorlib. dll (mscorlib. dll içinde)

**.NET Framework sürümleri:** 2,0 sürümünden itibaren kullanılabilir.
