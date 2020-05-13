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
ms.openlocfilehash: f73919634ba15dfd16694676d1389875fc2d79bc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210195"
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
 `dwFlags`Değer geçersizse, `SetJITCompilerFlags` Yöntem başarısız olur.  
  
 `SetJITCompilerFlags`Yöntemi yalnızca bu modül Için [ICorDebugManagedCallback:: LoadModule](icordebugmanagedcallback-loadmodule-method.md) geri çağırması içinden çağrılabilir. Geri çağırma işlemi geri alındıktan sonra çağrı denemeleri `ICorDebugManagedCallback::LoadModule` başarısız olur.  
  
 Düzenle ve devam et, 64-bit veya Win9x platformlarında desteklenmez. Bu nedenle, `SetJITCompilerFlags` yöntemi ' de ayarlanmış CORDEBUG_JIT_ENABLE_ENC bayrağı ile bu iki platformundan birine çağırırsanız `dwFlags` , `SetJITCompilerFlags` [ICorDebugModule2:: ApplyChanges](icordebugmodule2-applychanges-method.md)gibi, düzenleme ve devam etme yöntemine özgü Yöntem ve tüm yöntemler başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
