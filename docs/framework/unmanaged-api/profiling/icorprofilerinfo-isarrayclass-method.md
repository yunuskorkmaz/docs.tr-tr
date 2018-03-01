---
title: "ICorProfilerInfo::IsArrayClass Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a1063aea795d73ebaad0803abb7e555e1bb8b7e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfoisarrayclass-method"></a>ICorProfilerInfo::IsArrayClass Yöntemi
Belirtilen sınıf bir dizi sınıf olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `classId`  
 [in] İncelenmesi için sınıf kimliği.  
  
 `pBaseElemType`  
 [out] Dizi öğeleri türünü gösterir CorElementType numaralandırması değerini gösteren bir işaretçi.  
  
 `pBaseClassId`  
 [out] Dizi öğeleri, kullanılabilir olduğunda sınıf kimliği için bir işaretçi.  
  
 `pcRank`  
 [out] Dizi derecesini (diğer bir deyişle, Boyutlar sayısı) belirten bir tamsayı gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirtilen sınıf bir dizi sınıf ise `IsArrayClass` yöntemi S_OK HRESULT ve null olmayan çıktı parametreleri için değerleri döndürür. Aksi takdirde, S_FALSE döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
