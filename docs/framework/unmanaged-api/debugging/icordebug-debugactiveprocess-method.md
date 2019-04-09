---
title: ICorDebug::DebugActiveProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b880358ed0d7bce4896217bc07c6ef6268d62962
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076282"
---
# <a name="icordebugdebugactiveprocess-method"></a>ICorDebug::DebugActiveProcess Yöntemi
Hata ayıklayıcı, varolan bir sürece ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `id`  
 [in] Hata ayıklayıcı eklenmiş olduğu işlem kimliği.  
  
 `win32Attach`  
 [in] Ayarlanmış bir Boole değeri `true` hata ayıklayıcı Win32 hata ayıklayıcı işlemi gibi davranır ve yönetilmeyen geri çağırmaları; gönderme, aksi takdirde, `false`.  
  
 `ppProcess`  
 [out] Hata ayıklayıcı eklendikten işlemini temsil eden bir "ICorDebugProcess" nesnenin adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Birlikte çalışma hata ayıklama gibi IA-64 tabanlı ve AMD64 tabanlı platformlarda, Win9x ve x86 olmayan platformda desteklenmiyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
