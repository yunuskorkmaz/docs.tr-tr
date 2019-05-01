---
title: ICorProfilerInfo4::GetObjectSize2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15829e08a755b91ff91ca939b92a5a87bd377e8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000681"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a>ICorProfilerInfo4::GetObjectSize2 Yöntemi
Belirtilen nesnenin boyutunu döndürür. Değiştirir [Icorprofilerınfo::getobjectsize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md) ne de ifade edilebilir daha büyük nesnelerin boyutunu raporlama yöntemi bir `ULONG`.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a>Parametreler  
 `objectId`  
 [in] Nesnenin kimliği.  
  
 `pcSize`  
 [out] Nesnenin boyutu, bayt için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Aynı türden farklı nesneler genellikle aynı boyuta sahip. Ancak, diziler veya dizeler gibi bazı türleri her nesne için başka bir boyutu olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
