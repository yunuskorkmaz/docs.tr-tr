---
title: IMethodMalloc::Alloc Yöntemi
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
ms.openlocfilehash: a82a2150f32b1b335da083ca235ed9d2966a0b6e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494208"
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc Yöntemi

Yeni bir Microsoft ara dili (MSIL) işlev gövdesi için belirtilen miktarda bellek ayırmaya çalışır.

## <a name="syntax"></a>Söz dizimi

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a>Parametreler

`cb`\
'ndaki Yöntem gövdesi için ayrılacak bayt sayısı.

## <a name="remarks"></a>Açıklamalar

 Ayrılan bellek, bu ayırıcıyla ilişkili modülün temel adresinden büyük bir adreste başlayacaktır. Diğer bir deyişle, her ayırıcı belirli bir modül için oluşturulur ve temel adresinden pozitif bir uzaklığa bellek ayırmaya çalışır. `Alloc`Modülün temel adresinden daha büyük bir adreste istenen bayt sayısını ayıramazsa, kullanılabilir bellek alanının gerçek miktarından bağımsız olarak e_outofmemory döndürür.

 `Alloc`Yöntemi [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) yöntemiyle birlikte kullanılmalıdır.

## <a name="requirements"></a>Gereksinimler
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

 **Üst bilgi:** CorProf. IDL, CorProf. h

 **Kitaplık:** Corguid. lib

 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [IMethodMalloc Arabirimi](imethodmalloc-interface.md)
