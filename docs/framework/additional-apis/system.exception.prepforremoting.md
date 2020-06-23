---
title: Exception. PrepForRemoting yöntemi (sistem)
description: .NET 'teki özel durumu gözden geçirin. Yöntemi, istemci sırasında özel durum yeniden oluşturulmadan önce iletiye sunucu tarafı yığın izlemesini ekler.
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 9ceb73499ae3bb308975e6db5b961bfe40165ba3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105256"
---
# <a name="exceptionprepforremoting-method"></a>Exception.PrepForRemoting Metodu

Özel durum istemci çağrı sitesinde yeniden oluşturulmadan önce iletiye ekleyerek sunucu tarafı yığın izlemesini korur.

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>Döndürülenler

<xref:System.Exception>  
Bu <xref:System.Exception> örnek.

## <a name="remarks"></a>Açıklamalar

> [!WARNING]
> `Exception.PrepForRemoting`Yöntemi iç yöntemidir ve doğrudan kodunuzda kullanılması amaçlıyordu.
>
> Microsoft, bu yöntemin herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System>

**Bütünleştirilmiş kod:** mscorlib.dll (mscorlib.dll)

**.NET Framework sürümleri:** 1,0 sürümünden itibaren kullanılabilir.
