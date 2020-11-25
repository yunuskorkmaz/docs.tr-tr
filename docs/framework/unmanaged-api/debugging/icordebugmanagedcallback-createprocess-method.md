---
title: ICorDebugManagedCallback::CreateProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type:
- apiref
ms.openlocfilehash: cd24e672c65769586dc618c21503dbb344566974
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731819"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a>ICorDebugManagedCallback::CreateProcess Yöntemi

Bir işlem ilk kez eklendiğinde veya başlatıldığında hata ayıklayıcıya bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pProcess`  
 'ndaki Eklenmiş veya başlatılan işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu yöntem, ortak dil çalışma zamanı başlatılana kadar çağrılmaz. [ICorDebug](icordebug-interface.md) yöntemlerinin çoğu geri aramadan önce CORDBG_E_NOTREADY döndürür `CreateProcess` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
