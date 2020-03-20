---
title: ICorProfilerCallback::AppDomainCreationFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
ms.openlocfilehash: 8b3f7712436c001e5cd44f214f6edb06390abd41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177078"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a>ICorProfilerCallback::AppDomainCreationFinished Yöntemi
Profil oluşturucuya bir uygulama etki alanı oluşturulduğunu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a>Parametreler

- `appDomainId`

  \[in] Oluşturulan etki alanını tanımlar.

- `hrStatus`

  \[in] Uygulama etki alanıoluşturmanın başarıyla tamamlanıp tamamlanmadığını gösteren bir HRESULT.

## <a name="remarks"></a>Açıklamalar  
 `AppDomainCreationFinished` Yöntem çağrılana kadar başvuru kimliği herhangi bir bilgi isteği için geçerli değildir.  
  
 Uygulama etki alanıyüklemenin bazı bölümleri `AppDomainCreationFinished` geri aramadan sonra da devam edebilir. Bir hata HRESULT bir hata `hrStatus` gösterir. Ancak, bir başarı `hrStatus` HRESULT yalnızca uygulama etki alanı oluşturma nın ilk bölümü başarılı olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorProf.idl, CorProf.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
