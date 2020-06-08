---
title: ICorProfilerCallback::ExceptionSearchCatcherFound Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
ms.openlocfilehash: 70c03d34bdf9bd315994b2bfa09631efac2565ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500227"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a>ICorProfilerCallback::ExceptionSearchCatcherFound Yöntemi
Profil oluşturucuya özel durum işlemenin arama aşamasının oluşturulan özel durum için bir işleyici bulunduğunu bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a>Parametreler

- `functionId`

  \[' de] özel durum işleyicisini içeren işlevin KIMLIĞI.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
