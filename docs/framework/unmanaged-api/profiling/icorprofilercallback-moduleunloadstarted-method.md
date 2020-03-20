---
title: ICorProfilerCallback::ModuleUnloadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
ms.openlocfilehash: fcfdddbd5316c098754ea7b0d4714b050c64fe55
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175154"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a>ICorProfilerCallback::ModuleUnloadStarted Yöntemi
Profiloluşturucuya bir modülün boşaltıldığını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleId`  
 [içinde] Boşaltılan modülün kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Yöntem döndükten sonra `moduleId` `ModuleUnloadStarted` bir bilgi isteği için değeri geçerli değildir — bu, profiloluşturucunun bu modül hakkında bilgi almak için son şansıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorProf.idl, CorProf.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ModuleUnloadFinished Yöntemi](icorprofilercallback-moduleunloadfinished-method.md)
