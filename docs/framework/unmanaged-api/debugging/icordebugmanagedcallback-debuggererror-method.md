---
title: ICorDebugManagedCallback::DebuggerError Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.DebuggerError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type:
- apiref
ms.openlocfilehash: c03be2405e1ab0287a2921b6e2e293862c67a193
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137367"
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>ICorDebugManagedCallback::DebuggerError Yöntemi
Ortak dil çalışma zamanından (CLR) bir olayı işlemeye çalışırken hata ayıklayıcıya bir hata oluştuğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pProcess`  
 'ndaki Olayın gerçekleştiği işlemi temsil eden bir "ICorDebugProcess" nesnesine yönelik bir işaretçi.  
  
 `errorHR`  
 'ndaki Olay işleyicisinden döndürülen HRESULT değeri.  
  
 `errorCode`  
 'ndaki CLR hatasını belirten bir tamsayı.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlem, hatanın doğasına bağlı olarak doğrudan geçiş moduna yerleştirilebilecek.  
  
 `DebugError` geri çağırması hata nedeniyle hata ayıklama Hizmetleri 'nin devre dışı bırakıldığını belirtir, bu nedenle hata ayıklayıcılar hata iletisini Kullanıcı için kullanılabilir hale getirir. [ICorDebugProcess:: GetID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md) çağrısı güvenli olacak, ancak [ICorDebug:: Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)dahil diğer tüm yöntemler çağrılmamalıdır. Hata ayıklayıcı, işlem sonlandırmakta olan işletim sistemi tesislerini kullanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
