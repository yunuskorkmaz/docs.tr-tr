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
ms.openlocfilehash: 9a676989bdc6866f85fabe3e15b1e6b7b8b5a9a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000720"
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