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
ms.openlocfilehash: 76f56971223154d3ed966c272081049adf30de54
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500500"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a>ICorProfilerCallback::AppDomainCreationFinished Yöntemi
Profil oluşturucuyu bir uygulama etki alanının oluşturulduğunu bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a>Parametreler

- `appDomainId`

  \[' de], oluşturulan etki alanını tanımlar.

- `hrStatus`

  \[içinde] uygulama etki alanının oluşturulmasını başarıyla tamamlanıp tamamlanmadığını gösteren bir HRESULT.

## <a name="remarks"></a>Açıklamalar  
 Uygulama KIMLIĞI, yöntem çağrılana kadar herhangi bir bilgi isteği için geçerli değildir `AppDomainCreationFinished` .  
  
 Uygulama etki alanını yüklemenin bazı bölümleri geri aramadan sonra devam edebilir `AppDomainCreationFinished` . ' De HRESULT hatası, `hrStatus` bir hatayı gösterir. Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca uygulama etki alanı oluşturmanın ilk bölümünün başarılı olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
