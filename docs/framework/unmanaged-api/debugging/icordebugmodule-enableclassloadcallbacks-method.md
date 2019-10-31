---
title: ICorDebugModule::EnableClassLoadCallbacks Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
ms.openlocfilehash: c18ed781d44c873b4cd1957bf0102a4ce0cccad4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139214"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a>ICorDebugModule::EnableClassLoadCallbacks Yöntemi
Bu modül için [ICorDebugManagedCallback:: LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [ICorDebugManagedCallback:: UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları çağrılıp çağrılmayacağını denetler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bClassLoadCallbacks`  
 'ndaki Ortak dil çalışma zamanını (CLR), ilişkili olayları gerçekleştiğinde `ICorDebugManagedCallback::LoadClass` ve `ICorDebugManagedCallback::UnloadClass` yöntemlerini çağırmak üzere etkinleştirmek için bu değeri `true` olarak ayarlayın.  
  
 Dinamik olmayan modüller için varsayılan değer `false`. Değer her zaman dinamik modüller için `true` ve değiştirilemez.  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugManagedCallback::LoadClass` ve `ICorDebugManagedCallback::UnloadClass` geri çağırmaları her zaman dinamik modüller için etkinleştirilmiştir ve devre dışı bırakılamaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
