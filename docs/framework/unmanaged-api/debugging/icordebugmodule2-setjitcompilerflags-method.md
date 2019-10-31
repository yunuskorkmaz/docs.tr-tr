---
title: ICorDebugModule2::SetJITCompilerFlags Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
ms.openlocfilehash: 2358cee1b3a9aa50fb1f0e61d558f164a39aa86c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137357"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags Yöntemi
Bu ICorDebugModule2 'ın tam zamanında (JıT) derlemesini denetleyen bayrakları ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwFlags`  
 'ndaki [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  
 `dwFlags` değeri geçersizse, `SetJITCompilerFlags` yöntemi başarısız olur.  
  
 `SetJITCompilerFlags` yöntemi yalnızca bu modül için [ICorDebugManagedCallback:: LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) geri çağırması içinden çağrılabilir. `ICorDebugManagedCallback::LoadModule` geri çağırma işlemi teslim edildikten sonra bu aramayı çağırma girişimleri başarısız olur.  
  
 Düzenle ve devam et, 64-bit veya Win9x platformlarında desteklenmez. Bu nedenle, bu iki platformda `SetJITCompilerFlags` yöntemini `dwFlags`CORDEBUG_JIT_ENABLE_ENC bayrağı ayarlanmış olarak çağırırsanız, `SetJITCompilerFlags` yöntemi ve [ICorDebugModule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)gibi Düzenle ve devam et 'e özgü tüm yöntemler başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
