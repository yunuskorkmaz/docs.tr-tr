---
title: Exception. PrepForRemoting yöntemi (sistem)
author: mairaw
ms.author: mairaw
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 057390d64f70d3cb8eba7d4b29b94570fdca77e3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72405034"
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
> @No__t-0 yöntemi dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** <xref:System>

**Bütünleştirilmiş kod:** mscorlib. dll (mscorlib. dll içinde)

**.NET Framework sürümleri:** 1,0 sürümünden itibaren kullanılabilir.
