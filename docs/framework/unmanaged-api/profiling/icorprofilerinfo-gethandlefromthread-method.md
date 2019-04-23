---
title: ICorProfilerInfo::GetHandleFromThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fc26ad9b25ad243bf868d6ef3155360509e6483
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59185750"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a>ICorProfilerInfo::GetHandleFromThread Yöntemi
Bir iş parçacığının kimliği bir Win32 iş parçacığı tutamacı eşler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a>Parametreler  
 `threadId`  
 [in] Eşleştirilecek iş parçacığı kimliği.  
  
 `phThread`  
 [out] Bir Win32 iş parçacığı tutamacı işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu Win32 çağırmalıdır `DuplicateHandle` kullanmadan önce tutamacı işlevi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
