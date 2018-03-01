---
title: "ICorDebug::CanLaunchOrAttach Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 62ebdb178ef7aaa16bcc163e42662e1d69f1f6f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach Yöntemi
Yeni bir işlem başlatılıyor veya belirtilen varolan işlemine iliştirme geçerli makine ve çalışma zamanı yapılandırma bağlamında mümkün olup olmadığını belirten bir HRESULT döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwProcessId`  
 [in] Varolan bir işlemin kimliği.  
  
 `win32DebuggingEnabled`  
 [in] Geçirin `true` , Win32 hata ayıklama etkin durumdayken başlatmak plan veya etkin; tersi durumda, Win32 hata ayıklamaya eklemek için geçmesi durumunda `false`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Hata Ayıklama Hizmetleri yeni bir işlem başlatılıyor veya verilen işlemine iliştirme karar verirseniz S_OK geçerli makine ve çalışma zamanı yapılandırma hakkında bilgi verilir, mümkündür. Olası HRESULT değerleri şunlardır:  
  
-   S_OK  
  
-   CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
-   CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
-   CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem yalnızca bilgilendirme amaçlıdır. Arabirim, başlatmasını durdurmaz veya tarafından döndürülen değer bağımsız olarak bir işlem ekleme `CanLaunchOrAttach`.  
  
 Win32 hata ayıklama etkin durumdayken başlatın veya Win32 hata ayıklama etkin durumdayken bağlayın, geçirmek, düşünüyorsanız, `true` için `win32DebuggingEnabled`. Tarafından döndürülen HRESULT `CanLaunchOrAttach` bu seçeneği kullanırsanız, farklı olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
