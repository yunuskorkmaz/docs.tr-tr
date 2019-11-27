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
ms.openlocfilehash: af881d23ff77f05dadbbc745b973979e35ebe9f7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447561"
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc Yöntemi

Yeni bir Microsoft ara dili (MSIL) işlev gövdesi için belirtilen miktarda bellek ayırmaya çalışır.

## <a name="syntax"></a>Sözdizimi

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a>Parametreler

`cb`\
'ndaki Yöntem gövdesi için ayrılacak bayt sayısı.

## <a name="remarks"></a>Açıklamalar

 Ayrılan bellek, bu ayırıcıyla ilişkili modülün temel adresinden büyük bir adreste başlayacaktır. Diğer bir deyişle, her ayırıcı belirli bir modül için oluşturulur ve temel adresinden pozitif bir uzaklığa bellek ayırmaya çalışır. `Alloc`, istenen bayt sayısını modülün temel adresinden daha büyük bir adrese ayıramazsa, kullanılabilir bellek alanı gerçek miktarına bakılmaksızın E_OUTOFMEMORY döndürür.

 `Alloc` yöntemi [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) yöntemiyle birlikte kullanılmalıdır.

## <a name="requirements"></a>Gereksinimler
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

 **Üst bilgi:** CorProf. IDL, CorProf. h

 **Kitaplık:** Corguid. lib

 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [IMethodMalloc Arabirimi](imethodmalloc-interface.md)
