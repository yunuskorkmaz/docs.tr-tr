---
title: ICorDebugManagedCallback::LoadClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1d920a97338bba3e90ec8f0c440f6dd2a93e722
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416211"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a>ICorDebugManagedCallback::LoadClass Yöntemi
Hata ayıklayıcı bir sınıf yüklü olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] Bir işaretçi Icordebugappdomain nesneye sınıfı yüklenmiş olan uygulama etki alanını temsil eder.  
  
 `c`  
 [in] Bir işaretçi Icordebugclass nesneye sınıfı temsil eder.  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca sınıfı yükleme sınıfı içeren modülü için etkinleştirilmişse bu geri çağırma oluşur. Sınıf yükleme dinamik modülleri için her zaman etkindir.  
  
 `LoadClass` Geri çağırma dinamik modüllerdeki yeni oluşturulan sınıflar kesme noktaları bağlamak için uygun bir saat sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UnloadClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)  
 [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
