---
title: "IMethodMalloc::Alloc Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc.Alloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ae0fa84c08cb8e366db36b6727a3058f24789801
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imethodmalloc arabirimi](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
