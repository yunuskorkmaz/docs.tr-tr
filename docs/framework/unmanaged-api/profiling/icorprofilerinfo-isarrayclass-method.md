---
title: ICorProfilerInfo::IsArrayClass Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c131c5531d52f5ee81c70bddb67e8bc6071f39e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599675"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>ICorProfilerInfo::IsArrayClass Yöntemi
Array sınıfı belirtilen sınıf olup olmadığını belirler.  
  
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
 [in] İncelenecek sınıfın Kimliğidir.  
  
 `pBaseElemType`  
 [out] Dizi öğelerin türünü belirten CorElementType sabit değeri için bir işaretçi.  
  
 `pBaseClassId`  
 [out] Kullanılabilir olduğunda, dizi öğelerinin sınıf kimliği için bir işaretçi.  
  
 `pcRank`  
 [out] (Diğer bir deyişle, boyut sayısı) dizi boyut sayısını belirten bir tamsayı işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir dizi sınıfı belirtilen sınıf ise `IsArrayClass` yöntemi bir S_OK HRESULT ve null olmayan çıkış parametreleri için değerleri döndürür. Aksi takdirde S_FALSE döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
