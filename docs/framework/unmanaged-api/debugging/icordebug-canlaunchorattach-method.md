---
title: ICorDebug::CanLaunchOrAttach Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0cf0065f1ed12ad3a37819b0a15d734a2b51ff5b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125612"
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach Yöntemi
Yeni bir işlem başlatılıyor veya belirtilen mevcut işleme iliştirdikten geçerli makine ve çalışma zamanı yapılandırma bağlamında mümkün olup olmadığını belirten bir HRESULT döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwProcessId`  
 [in] Var olan bir işlem kimliği.  
  
 `win32DebuggingEnabled`  
 [in] Geçirin `true` , Win32 ile hata ayıklama etkin oluşturmayı planlıyoruz veya Win32 hata ayıklamaya etkin; Aksi takdirde eklemek için geçirmek `false`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Hata Ayıklama Hizmetleri yeni bir işlem başlatılıyor veya belirtilen işleme iliştirdikten belirlerseniz S_OK geçerli makine ve çalışma zamanı yapılandırma hakkında bilgi verilen mümkündür. HRESULT olası değerler şunlardır:  
  
-   S_OK  
  
-   CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
-   CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
-   CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, yalnızca bilgilendirme amaçlıdır. Arabirimi, başlatılmasını durdurmaz ya da tarafından döndürülen değerinden bağımsız olarak bir işleme ekleme `CanLaunchOrAttach`.  
  
 Planlıyorsanız Win32 ile hata ayıklama etkin başlatma veya ekleme Win32 ile hata ayıklamayı etkin geçirmek `true` için `win32DebuggingEnabled`. Tarafından döndürülen HRESULT `CanLaunchOrAttach` bu seçeneği kullanırsanız farklı olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
