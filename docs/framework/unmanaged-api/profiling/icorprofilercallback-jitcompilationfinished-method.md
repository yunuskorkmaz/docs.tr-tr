---
title: ICorProfilerCallback::JITCompilationFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
ms.openlocfilehash: 0da67f0d4be779cc21481d03a21209620289888e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500071"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a>ICorProfilerCallback::JITCompilationFinished Yöntemi
Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi derlemeyi tamamladığını bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametreler

- `functionId`

  \[içinde] derlenen işlevin KIMLIĞI.

- `hrStatus`

  \[' de] derlemenin başarılı olup olmadığını gösteren bir değer.

- `fIsSafeToBlock`

  \[' de] bir profil oluşturucunun, engelleme çalışma zamanının işlemini etkilemesini isteyip olmayacağını gösteren bir değer. Bu değer, `true` engelleme çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesini, aksi takdirde, `false` .

  Bir değeri `true` çalışma zamanına zarar verse de, profil oluşturma sonuçlarını çarpıtmasına neden olabilir.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [JITCompilationStarted Yöntemi](icorprofilercallback-jitcompilationstarted-method.md)
