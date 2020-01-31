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
ms.openlocfilehash: 9b96c0a2eca543b9e01ccf92b271b1aa7003c5c9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781943"
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
  
 `DebugError` geri çağırması hata nedeniyle hata ayıklama Hizmetleri 'nin devre dışı bırakıldığını belirtir, bu nedenle hata ayıklayıcılar hata iletisini Kullanıcı için kullanılabilir hale getirir. [ICorDebugProcess:: GetID](icordebugprocess-getid-method.md) çağrısı güvenli olacak, ancak [ICorDebug:: Terminate](icordebug-terminate-method.md)dahil diğer tüm yöntemler çağrılmamalıdır. Hata ayıklayıcı, işlem sonlandırmakta olan işletim sistemi tesislerini kullanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
