---
title: ICorProfilerInfo::GetThreadInfo Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f68565977551a54244f3caf6a0250f67005a6ecf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452888"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a>ICorProfilerInfo::GetThreadInfo Metodu
Geçerli Win32 iş parçacığı kimliği için belirtilen iş parçacığı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `threadId`  
 [in] Win32 geçerli kimliği edinmek için iş parçacığı kimliği  
  
 `pdwWin32ThreadId`  
 [out] Belirtilen iş parçacığının geçerli Win32 iş parçacığı için bir işaretçi kimliği  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
