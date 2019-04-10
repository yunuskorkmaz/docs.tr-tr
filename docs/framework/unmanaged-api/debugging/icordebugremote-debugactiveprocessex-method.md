---
title: ICorDebugRemote::DebugActiveProcessEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45b919d90454c9424cadb1d4dfc3b0dfb09e5053
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209456"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>ICorDebugRemote::DebugActiveProcessEx Yöntemi
Hata ayıklayıcısı altında uzak bir makinede bir işlem başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pRemoteTarget`  
 [in] İşaretçi bir [Icordebugremotetarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Bu parametre, işlem üzerinde çalıştığı makinenin belirlemek için kullanılır.  
  
 `id`  
 [in] Hata ayıklayıcı eklenmiş olduğu işlem kimliği.  
  
 `win32Attach`  
 [in] `true` hata ayıklayıcı Win32 hata ayıklayıcı işlemi gibi davranır ve gönderme yönetilmeyen geri çağırmaları; Aksi takdirde, `false`.  
  
 `ppProcess`  
 [out] Hata ayıklayıcı eklendikten işlemini temsil eden bir "ICorDebugProcess" nesnenin adresi için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 İşlem uzak makinede başarıyla kullanıma açıldı.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Uzak makinede işlemine iliştirilemiyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Silverlight'ta, karma mod hata ayıklaması desteklenmiyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRemote Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
