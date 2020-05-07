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
ms.openlocfilehash: 354df02b27e87550ba602fe102352455c227441b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859681"
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
 'ndaki `true` Win32 hata ayıklaması etkinken başlatmayı planlıyorsanız veya Win32 hata ayıklaması etkinleştirilmiş olarak eklemek istiyorsanız geçirin; Aksi takdirde, `false`Pass.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Hata ayıklama Hizmetleri, yeni bir işlem başlatmayı veya belirli bir işleme eklemeyi saptarken, geçerli makine ve çalışma zamanı yapılandırmasıyla ilgili bilgiler verildiğinde S_OK. Olası HRESULT değerleri şunlardır:  
  
- S_OK  
  
- CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
- CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
- CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem yalnızca bilgilendirme amaçlıdır. Arabirim, tarafından `CanLaunchOrAttach`döndürülen değerden bağımsız olarak, bir işleme veya ekleme işlemini durdurmayacak.  
  
 Win32 hata ayıklaması etkinleştirilmiş veya Win32 hata ayıklaması etkinken birlikte başlatmaya çalışırsanız, için `true` `win32DebuggingEnabled`geçiş yapın. Tarafından `CanLaunchOrAttach` döndürülen HRESULT, bu seçeneği kullanırsanız farklılık gösterebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](icordebug-interface.md)
