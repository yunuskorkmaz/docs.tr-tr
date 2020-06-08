---
title: ICorProfilerCallback::ExceptionSearchFilterEnter Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type:
- apiref
ms.openlocfilehash: 304b8da670786851a70e38e6623d44b1bde71a04
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500240"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a>ICorProfilerCallback::ExceptionSearchFilterEnter Yöntemi
Profil oluşturucuyu, özel durum işlemenin arama aşamasının Kullanıcı tanımlı bir özel durum filtresi yürütmeye başladığını bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a>Parametreler

- `functionId`

  \[içinde] filtreyi içeren işlevin KIMLIĞI.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ExceptionSearchFilterLeave Yöntemi](icorprofilercallback-exceptionsearchfilterleave-method.md)
