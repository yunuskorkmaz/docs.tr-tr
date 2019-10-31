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
ms.openlocfilehash: d23b695550c8444264934f7aca4fa185064e89c5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130734"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a>ICorDebugManagedCallback::LoadClass Yöntemi
Bir sınıfın yüklendiğini hata ayıklayıcıya bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pAppDomain`  
 'ndaki Sınıfın yüklendiği uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.  
  
 `c`  
 'ndaki Sınıfını temsil eden ICorDebugClass nesnesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu geri çağırma, yalnızca sınıf yüklemesi sınıfı içeren modül için etkinleştirildiyse oluşur. Sınıf yükleme her zaman dinamik modüller için etkindir.  
  
 `LoadClass` geri çağırması, kesme noktalarını dinamik modüllerde yeni oluşturulan sınıflara bağlamak için uygun bir zaman sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UnloadClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
