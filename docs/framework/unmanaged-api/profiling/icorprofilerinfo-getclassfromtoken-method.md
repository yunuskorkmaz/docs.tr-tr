---
title: ICorProfilerInfo::GetClassFromToken Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 335c25316b34f79b8d02eea5a7dd4ed7994fc754
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780173"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a>ICorProfilerInfo::GetClassFromToken Metodu
Meta veri belirteci verilen sınıfı Kimliğini alır. Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor. Kullanım [Icorprofilerınfo2::getclassfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleID`  
 [in] Sınıfı içeren modül kimliği.  
  
 `typeDef`  
 [in] Bir `mdTypeDef` sınıfına başvuran meta veri belirteci.  
  
 `cTypeArgs`  
 [out] Sınıf kimliği için bir işaretçi  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem artık kullanılmıyor; Bunun yerine, `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` tüm türleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 1.0, 1.1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
