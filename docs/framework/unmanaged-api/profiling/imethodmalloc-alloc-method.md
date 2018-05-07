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
ms.openlocfilehash: 6d73fe16720248d541bac64a432bb6f35d6873b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc Yöntemi
Belirtilen bir bellek miktarı için yeni bir Microsoft Ara dili (MSIL) işlev gövdesi ayırmaya çalışır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
PVOID Alloc (  
    [in] ULONG   cb  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cb`  
 [in] Yöntem gövdesi için ayrılacak bayt sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Ayrılmış bellek taban adresi bu ayırıcısı ile ilişkili modülünün daha büyük bir adresindeki başlar. Diğer bir deyişle, her ayırıcısı için belirli bir modülü oluşturulur ve temel adresinden bellek pozitif uzaklığındaki dener. Varsa `Alloc` istenen modülü temel adresinden daha büyük bir adresindeki bayt sayısı ayrılamıyor başarısız kullanılabilir bellek alanı gerçek bakılmaksızın E_OUTOFMEMORY döndürür.  
  
 `Alloc` Yöntemi ile birlikte kullanılmalıdır [Icorprofilerınfo::setılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** WindSee [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMethodMalloc Arabirimi](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
