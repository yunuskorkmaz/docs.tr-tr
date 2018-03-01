---
title: "ICorDebugRemote::DebugActiveProcessEx Yöntemi"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 09bc98b477231eb1466300451585f4569aff222c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>ICorDebugRemote::DebugActiveProcessEx Yöntemi
Hata ayıklayıcı altında uzaktaki bir makinede bir işlem başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRemoteTarget`  
 [in] İşaretçi bir [Icordebugremotetarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Bu parametre, işlemin çalıştığı makine belirlemek için kullanılır.  
  
 `id`  
 [in] Hata ayıklayıcısı ekli olduğu işlemin kimliği.  
  
 `win32Attach`  
 [in] `true` hata ayıklayıcı işlem için Win32 hata ayıklayıcı olarak davranır ve yönetilmeyen geri çağırmaları; gönderme gerekir, aksi takdirde `false`.  
  
 `ppProcess`  
 [out] Hata ayıklayıcı eklenmiş olması işlemi temsil eden bir "ICorDebugProcess" nesnesinin adresi için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Uzak makinedeki işlemi başarıyla eklendi.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Uzak makinedeki işlem eklenemiyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Karışık mod hata ayıklaması Silverlight'ta desteklenmez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugRemote Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
