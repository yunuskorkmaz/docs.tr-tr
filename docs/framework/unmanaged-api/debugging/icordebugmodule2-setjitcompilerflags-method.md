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
ms.openlocfilehash: c71ccbc62ea026a55a7e84f6925a78850594a813
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942525"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a>ICorDebugModule2::SetJITCompilerFlags Yöntemi
Bu Icordebugmodule2 just-in-time (JIT) derlenmesi denetleyen bayraklar ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwFlags`  
 [in] Bitsel bir birleşimi [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) sabit listesi değerleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa `dwFlags` değeri geçersiz `SetJITCompilerFlags` yöntemi başarısız olur.  
  
 `SetJITCompilerFlags` Yöntemi yalnızca içinde çağrılabilir [Icordebugmanagedcallback::LoadModule](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md) bu modül için geri çağırma. Bundan sonra çağırma girişiminde `ICorDebugManagedCallback::LoadModule` geri çağırma, teslim başarısız.  
  
 Düzenle ve devam et desteklenmez 64-bit veya Win9x platformlar. Bu nedenle, eğer `SetJITCompilerFlags` yöntemi bu iki platform kümesinde CORDEBUG_JIT_ENABLE_ENC bayrağıyla birini `dwFlags`, `SetJITCompilerFlags` yöntemi ve belirli tüm yöntemler, Düzenle ve devam et, gibi [Icordebugmodule2:: ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md), başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
