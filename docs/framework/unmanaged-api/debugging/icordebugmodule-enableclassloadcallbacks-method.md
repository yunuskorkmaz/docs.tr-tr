---
description: ': ICorDebugModule:: EnableClassLoadCallbacks Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 16516cceae9a10288f8660fa69d8e0c018953777
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801091"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a>ICorDebugModule::EnableClassLoadCallbacks Yöntemi

Bu modül için [ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) ve [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları çağrılıp çağrılmayacağını denetler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `bClassLoadCallbacks`  
 'ndaki `true` Ortak dil çalışma zamanını (CLR), `ICorDebugManagedCallback::LoadClass` ilişkili olayları gerçekleştiğinde ve yöntemlerini çağırmak üzere etkinleştirmek için bu değeri olarak ayarlayın `ICorDebugManagedCallback::UnloadClass` .  
  
 Varsayılan değer, `false` dinamik olmayan modüller içindir. Değer her zaman `true` Dinamik modüller için ve değiştirilemez.  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorDebugManagedCallback::LoadClass`Ve `ICorDebugManagedCallback::UnloadClass` geri çağırmaları her zaman dinamik modüller için etkindir ve devre dışı bırakılamaz.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
