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
ms.openlocfilehash: 28b9fb5a25981e5e37a5f1bbb797baeac45e0028
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793571"
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
 Hata ayıklama Hizmetleri, yeni bir işlem başlatmayı veya belirli bir işleme eklemeyi saptarken, geçerli makine ve çalışma zamanı yapılandırmasıyla ilgili bilgiler verildiğinde S_OK. Olası HRESULT değerleri şunlardır:  
  
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

- [ICorDebug Arabirimi](icordebug-interface.md)
