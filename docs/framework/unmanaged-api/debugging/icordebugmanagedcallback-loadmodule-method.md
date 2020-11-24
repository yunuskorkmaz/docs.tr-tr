---
title: ICorDebugManagedCallback::LoadModule Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
ms.openlocfilehash: 698a5cb88884febc4dfb3b916c00df20c1a77819
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679656"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a>ICorDebugManagedCallback::LoadModule Yöntemi

Bir ortak dil çalışma zamanı (CLR) modülünün başarıyla yüklendiğini hata ayıklayıcıya bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pAppDomain`  
 'ndaki Modülün yüklendiği uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.  
  
 `pModule`  
 'ndaki CLR modülünü temsil eden ICorDebugModule nesnesine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `LoadModule`Geri çağırma, modülün meta verilerini incelemek, Just-In-Time (JIT) derleyici bayraklarını ayarlamak ya da modül için sınıf yükleme geri çağırmaları etkinleştirmek veya devre dışı bırakmak için uygun bir zaman sağlar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UnloadModule Yöntemi](icordebugmanagedcallback-unloadmodule-method.md)
- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
