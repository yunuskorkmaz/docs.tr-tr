---
title: ICorProfilerCallback::AppDomainCreationStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type:
- apiref
ms.openlocfilehash: fcebe65b7f39dd2849946e445a694ad5e9b1a65d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500487"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a>ICorProfilerCallback::AppDomainCreationStarted Yöntemi
Profil oluşturucuyu bir uygulama etki alanının oluşturulduğunu bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a>Parametreler

- `appDomainId`

  \[' de] oluşturulmakta olan etki alanını tanımlar.
  
## <a name="remarks"></a>Açıklamalar  
 ID, [ICorProfilerCallback:: AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) yöntemi çağrılana kadar herhangi bir bilgi isteği için geçerli değildir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
