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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66bd56a332dc34fd35f3129256cc0e3d6c5d4508
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636695"
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc Yöntemi

Yeni bir Microsoft Ara dili (MSIL) işlev gövdesi için belirtilen miktarda bellek ayırmaya çalışır.

## <a name="syntax"></a>Sözdizimi

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a>Parametreler

`cb`\
[in] Yöntem gövdesi için ayrılacak bayt sayısı.

## <a name="remarks"></a>Açıklamalar

 Ayrılan bellek bu ayırıcı ile ilişkili olan modülün taban adresi daha büyük bir adresten başlar. Diğer bir deyişle, her ayırıcı için belirli bir modülün oluşturulur ve kendi temel adres bir pozitif uzaklığında bellek dener. Varsa `Alloc` modülü temel adresini büyük bir adresteki bayt istenen sayıda başarısız E_OUTOFMEMORY, gerçek kullanılabilir bellek alanı miktarından bağımsız olarak döndürür.

 `Alloc` Yöntemi ile birlikte kullanılması gerekir [Icorprofilerınfo::setılfunctionbody](icorprofilerinfo-setilfunctionbody-method.md) yöntemi.

## <a name="requirements"></a>Gereksinimler
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

 **Üst bilgi:** CorProf.idl, CorProf.h

 **Kitaplığı:** CorGuids.lib

 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [IMethodMalloc Arabirimi](imethodmalloc-interface.md)
