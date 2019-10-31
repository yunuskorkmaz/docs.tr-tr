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
ms.openlocfilehash: 805f9a5d1f2590a06bfa929c152bdfd13900531a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134276"
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach Yöntemi
Geçerli makine ve çalışma zamanı yapılandırması bağlamında yeni bir işlemin başlatılıp başlatılmayacağını veya belirtilen mevcut işleme iliştirilip mümkün olup olmadığını belirten bir HRESULT döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwProcessId`  
 'ndaki Mevcut bir işlemin KIMLIĞI.  
  
 `win32DebuggingEnabled`  
 'ndaki Win32 hata ayıklaması etkinken başlatmayı planlıyorsanız veya Win32 hata ayıklaması etkin olarak eklemek istiyorsanız `true` geçirin; Aksi takdirde, `false`geçirin.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Hata ayıklama Hizmetleri yeni bir işlem başlatma veya belirli bir işleme ekleme işleminin mümkün olduğunu tespit ederseniz, geçerli makine ve çalışma zamanı yapılandırmasıyla ilgili bilgiler verilir. Olası HRESULT değerleri şunlardır:  
  
- S_OK  
  
- CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
- CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
- CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem yalnızca bilgilendirme amaçlıdır. Arabirim, `CanLaunchOrAttach`tarafından döndürülen değerden bağımsız olarak, bir işlemden başlatma veya ekleme işlemini durdurmayacak.  
  
 Win32 hata ayıklaması etkinleştirilmiş veya Win32 hata ayıklama özelliği etkinken birlikte başlatmayı planlıyorsanız, `win32DebuggingEnabled`için `true` geçirin. `CanLaunchOrAttach` tarafından döndürülen HRESULT, bu seçeneği kullanırsanız farklılık gösterebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
