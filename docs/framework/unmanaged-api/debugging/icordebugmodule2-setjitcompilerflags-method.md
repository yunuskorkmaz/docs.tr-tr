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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e605859a3049abc0c17d9d6792ade78f4ad2bd78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417368"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags Yöntemi
Bu Icordebugmodule2 tam zamanında (JIT) derlenmesini denetim bayrakları ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwFlags`  
 [in] Bit düzeyinde bileşimini [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) numaralandırma değerleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `dwFlags` değeri geçersiz `SetJITCompilerFlags` yöntemi başarısız olur.  
  
 `SetJITCompilerFlags` Yöntemi yalnızca içinden çağrılamaz [Icordebugmanagedcallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) bu modül için geri çağırma. Bundan sonra arama girişiminde `ICorDebugManagedCallback::LoadModule` geri çağırma, teslim başarısız.  
  
 Düzenle ve devam et 64-bit veya desteklenmiyor Win9x platformlar üzerinde. Bu nedenle, çağırırsanız `SetJITCompilerFlags` CORDEBUG_JIT_ENABLE_ENC bayrağı ayarlanmış bu iki platform birini yöntemi `dwFlags`, `SetJITCompilerFlags` yöntemi ve tüm yöntemleri belirli Düzenle ve devam et, gibi [Icordebugmodule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
