---
title: "ICorDebugModule2::SetJITCompilerFlags Yöntemi"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cfc25e9ce15996360cd0e3c68805d3707b325f79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
