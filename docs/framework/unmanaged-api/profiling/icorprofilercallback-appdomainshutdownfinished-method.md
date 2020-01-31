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
ms.openlocfilehash: 0851ac33a2bac4fcf727cf09e5225f6b83481b50
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866682"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a>ICorProfilerCallback::AppDomainShutdownFinished Yöntemi
Profil oluşturucuyu bir uygulama etki alanının bir işlemden kaldırılmış olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Parametreler

- `appDomainId`

  \[içinde], uygulamanın derlemelerinin depolandığı etki alanını tanımlar.

- `hrStatus`

  \[) uygulama etki alanının başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.

## <a name="remarks"></a>Açıklamalar  
 `appDomainId` değeri, [ICorProfilerCallback:: AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) yöntemi döndürüldüğünden bir bilgi isteği için geçerli değildir.  
  
 Uygulama etki alanını kaldırma işleminin bazı bölümleri `AppDomainCreationFinished` geri çağrısından sonra devam edebilir. `hrStatus` HRESULT hatası, bir hatayı gösterir. Ancak `hrStatus` başarılı bir HRESULT, yalnızca uygulama etki alanını kaldırmayı ilk bölümünün başarılı olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
