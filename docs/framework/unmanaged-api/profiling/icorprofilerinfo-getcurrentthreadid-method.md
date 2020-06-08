---
title: ICorProfilerInfo::GetCurrentThreadID Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
ms.openlocfilehash: fa0fe827300a86a906a254292434e2a56ebb4a47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498407"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a>ICorProfilerInfo::GetCurrentThreadID Metodu
Yönetilen bir iş parçacığı ise, geçerli iş parçacığının KIMLIĞINI alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pThreadId`  
 dışı Yönetilen iş parçacığının döndürülen KIMLIĞINE yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Geçerli iş parçacığı bir iç çalışma zamanı iş parçacığı veya diğer yönetilmeyen iş parçacığıdır, `GetCurrentThreadID` hresult olarak CORPROF_E_NOT_MANAGED_THREAD döndürür ve parametre döndürülen değeri `pThreadId` null olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
