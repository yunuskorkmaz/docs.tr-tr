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
ms.openlocfilehash: b28e457ea0b51d320581c0fbe36574698081ea36
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792956"
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
 'ndaki [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırma değerlerinin bit düzeyinde birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  
 `dwFlags` değeri geçersizse, `SetJITCompilerFlags` yöntemi başarısız olur.  
  
 `SetJITCompilerFlags` yöntemi yalnızca bu modül için [ICorDebugManagedCallback:: LoadModule](icordebugmanagedcallback-loadmodule-method.md) geri çağırması içinden çağrılabilir. `ICorDebugManagedCallback::LoadModule` geri çağırma işlemi teslim edildikten sonra bu aramayı çağırma girişimleri başarısız olur.  
  
 Düzenle ve devam et, 64-bit veya Win9x platformlarında desteklenmez. Bu nedenle, bu iki platformda `SetJITCompilerFlags` yöntemini `dwFlags`CORDEBUG_JIT_ENABLE_ENC bayrağıyla ayarlarsanız çağırırsanız, `SetJITCompilerFlags` yöntemi ve [ICorDebugModule2:: ApplyChanges](icordebugmodule2-applychanges-method.md)gibi Düzenle ve devam et 'e özgü tüm yöntemler başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
