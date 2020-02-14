---
title: Exception. PrepForRemoting yöntemi (sistem)
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: ce1c24578690a1643b7f5af0e44eaae95ed7b0a2
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214894"
---
# <a name="exceptionprepforremoting-method"></a>Exception.PrepForRemoting Metodu

Özel durum istemci çağrı sitesinde yeniden oluşturulmadan önce iletiye ekleyerek sunucu tarafı yığın izlemesini korur.

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>Döndürür

<xref:System.Exception>  
Bu <xref:System.Exception> örneği.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `Exception.PrepForRemoting` yöntemi dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System>

**Bütünleştirilmiş kod:** mscorlib. dll (mscorlib. dll içinde)

**.NET Framework sürümleri:** 1,0 sürümünden itibaren kullanılabilir.
