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
ms.openlocfilehash: 39ce3e8329c4ff32b55341127f68a800246677df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995221"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a>ICorDebugManagedCallback::LoadClass Yöntemi
Hata ayıklayıcı, bir sınıf yüklenmemiş olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 [in] Sınıf yüklenmiş olan uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.  
  
 `c`  
 [in] Bu sınıfın temsil ettiği bir Icordebugclass nesneye bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Sınıf yükleme sınıfı içeren modül için yalnızca etkinleştirildiyse, bu geri çağırma gerçekleşir. Sınıf yükleme, dinamik modüller için her zaman etkindir.  
  
 `LoadClass` Dinamik modüller yeni oluşturulan sınıflardaki kesme noktaları bağlamak için uygun bir saat geri çağırma sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UnloadClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
