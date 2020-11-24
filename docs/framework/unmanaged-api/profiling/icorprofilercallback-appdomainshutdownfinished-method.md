---
title: ICorProfilerCallback::AppDomainShutdownFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
ms.openlocfilehash: ddb2d6eeb75a118a12f681b354f6feccd1231c64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685397"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a>ICorProfilerCallback::AppDomainShutdownFinished Yöntemi

Profil oluşturucuyu bir uygulama etki alanının bir işlemden kaldırılmış olduğunu bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Parametreler

- `appDomainId`

  \[' de], uygulamanın derlemelerinin depolandığı etki alanını tanımlar.

- `hrStatus`

  \[içinde] uygulama etki alanının başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.

## <a name="remarks"></a>Açıklamalar  

 Değeri, `appDomainId` [ICorProfilerCallback:: AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) yönteminin döndürdüğü bir bilgi isteği için geçerli değildir.  
  
 Uygulama etki alanını kaldırma işleminin bazı bölümleri geri aramadan sonra devam edebilir `AppDomainCreationFinished` . ' De HRESULT hatası, `hrStatus` bir hatayı gösterir. Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca uygulama etki alanını kaldırmayı ilk bölümünün başarılı olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
