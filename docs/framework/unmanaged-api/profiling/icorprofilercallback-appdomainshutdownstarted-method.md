---
title: 'ICorProfilerCallback:: AppDomainShutdownStarted Yöntemi'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
ms.openlocfilehash: 1b973cdeaffbec0dad1f2d082c44e8001647fdcc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500461"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a>ICorProfilerCallback:: AppDomainShutdownStarted Yöntemi
Profil Oluşturucu bir uygulama etki alanının bir işlemden kaldırılmakta olduğunu bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a>Parametreler

- `appDomainId`

  \[' de], uygulamanın derlemelerinin depolandığı etki alanını tanımlar.

## <a name="remarks"></a>Açıklamalar  
 Değeri, `appDomainId` Yöntem çağrıldıktan sonra herhangi bir bilgi isteği için geçerli değildir `AppDomainShutdownStarted` ; Bu, profil oluşturucunun bu uygulama etki alanı hakkında bilgi almak için en son şansınız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
