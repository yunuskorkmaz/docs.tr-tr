---
title: ICorProfilerCallback::FunctionUnloadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: 988843559e55cc4cacd2a40bb3e6ac51721e99b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175167"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a>ICorProfilerCallback::FunctionUnloadStarted Yöntemi
Profil oluşturucuya çalışma zamanının bir işlevi boşaltmaya başladığını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a>Parametreler

- `functionId`

  \[in] Boşaltılan işlevin kimliği.

## <a name="remarks"></a>Açıklamalar  
 Bu yöntem `functionId` arayana döndükten sonra parametrenin değeri artık geçerli değildir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorProf.idl, CorProf.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
