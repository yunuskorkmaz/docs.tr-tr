---
title: ICorProfilerInfo::GetThreadContext Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
ms.openlocfilehash: 45ae164e79f077549a1d685aa060484240546a10
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497965"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a>ICorProfilerInfo::GetThreadContext Metodu
Belirtilen iş parçacığıyla Şu anda ilişkili olan bağlam Kimliğini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a>Parametreler  
 `threadId`  
 'ndaki İş parçacığının KIMLIĞI.  
  
 `pContextId`  
 dışı Şu anda belirtilen iş parçacığıyla ilişkilendirilen bağlam KIMLIĞINE yönelik bir işaretçi. İş parçacığında şu anda ilişkili bir bağlam yoksa, bu işlev CORPROF_E_DATAINCOMPLETE döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
