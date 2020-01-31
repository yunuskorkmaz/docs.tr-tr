---
title: ICorProfilerCallback2::FinalizeableObjectQueued Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.FinalizeableObjectQueued
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type:
- apiref
ms.openlocfilehash: b9093f920a8c14247bc51471da3682c7e500afa4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865811"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a>ICorProfilerCallback2::FinalizeableObjectQueued Yöntemi
Kod Profilcisi, sonlandırıcısı olan bir nesnenin `Finalize` yönteminin yürütülmesi için Sonlandırıcı iş parçacığına sıraya alınmış olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a>Parametreler  
 `finalizerFlags`  
 'ndaki Sonlandırıcının yönlerini açıklayan [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) numaralandırması değeri.  
  
 `objectID`  
 'ndaki Kuyruğa alınmış nesnenin KIMLIĞI.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 Arabirimi](icorprofilercallback2-interface.md)
