---
title: ICorDebugRemote::CreateProcessEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06bdc3605d981acad68a97901627f361da4061c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423325"
---
# <a name="icordebugremotecreateprocessex-method"></a>ICorDebugRemote::CreateProcessEx Yöntemi
Hata ayıklayıcı altında uzaktaki bir makinede bir işlem başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRemoteTarget`  
 [in] İşaretçi bir [Icordebugremotetarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). İşlem başlatılacak uzak makine belirlemek için kullanılır.  
  
 `lpApplicationName`  
 [in] İşaretçi null ile sonlandırılmış dizeye başlatılan işlem tarafından yürütülecek Modülü belirtir. Modül çağırma işlemi güvenlik bağlamında çalıştırılır.  
  
 `lpCommandLine`  
 [in] İşaretçi null ile sonlandırılmış dizeye başlatılan işlem tarafından yürütülecek komut satırını belirtir.  
  
 `lpProcessAttributes`  
 [in] Uzaktan hata ayıklama için kullanılmıyor.  
  
 `lpThreadAttributes`  
 [in] Uzaktan hata ayıklama için kullanılmıyor.  
  
 `bInheritHandles`  
 [in] Uzaktan hata ayıklama için kullanılmıyor.  
  
 `dwCreationFlags`  
 [in] Uzaktan hata ayıklama için kullanılmıyor.  
  
 `lpEnvironment`  
 [in] Yeni işlem için bir ortam bloğu işaretçi.  
  
 `lpCurrentDirectory`  
 [in] İşaretçi null ile sonlandırılmış dizeye işlemi için geçerli dizin tam yolunu belirtir. Bu parametre null ise, yeni işlem çağırma işlemi aynı geçerli sürücü ve dizine sahip.  
  
 `lpStartupInfo`  
 [in] Uzaktan hata ayıklama için kullanılmıyor.  
  
 `lpProcessInformation`  
 [in] Uzaktan hata ayıklama için kullanılmıyor.  
  
 `debuggingFlags`  
 [in] Uzaktan hata ayıklama için kullanılmıyor.  
  
 `ppProcess`  
 [out] İşlemi temsil eden bir "Icordebugprocess arabirimi" nesnesi adresini gösteren bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 Hata ayıklama için uzak makineye ve döndürülen bir "Icordebugprocess arabirimi" işlem başarıyla başlattı.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Uzak makinedeki işlemi başlatmak ve hata ayıklama için "Icordebugprocess arabirimi" dönmek oluşturulamıyor.  
  
## <a name="remarks"></a>Açıklamalar  
 Karışık mod hata ayıklaması Silverlight'ta desteklenmez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugRemote Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
