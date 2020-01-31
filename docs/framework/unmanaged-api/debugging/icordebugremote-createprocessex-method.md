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
ms.openlocfilehash: cfec84483d387630623f77c176c668171303dd0f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791984"
---
# <a name="icordebugremotecreateprocessex-method"></a>ICorDebugRemote::CreateProcessEx Yöntemi
Hata ayıklayıcı altındaki uzak makinede bir işlem başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
  
## <a name="parameters"></a>Parametreler  
 `pRemoteTarget`  
 'ndaki [ICorDebugRemoteTarget arabirimine](icordebugremotetarget-interface.md)yönelik işaretçi. İşlemin başlatılacağı uzak makineyi tespit etmek için kullanılır.  
  
 `lpApplicationName`  
 'ndaki Başlatılan işlem tarafından yürütülecek modülü belirten, null ile sonlandırılmış bir dize işaretçisi. Modül, çağıran işlemin güvenlik bağlamında yürütülür.  
  
 `lpCommandLine`  
 'ndaki Başlatılan işlem tarafından yürütülecek komut satırını belirten, null ile sonlandırılmış bir dize işaretçisi.  
  
 `lpProcessAttributes`  
 'ndaki Uzaktan hata ayıklama için kullanılmıyor.  
  
 `lpThreadAttributes`  
 'ndaki Uzaktan hata ayıklama için kullanılmıyor.  
  
 `bInheritHandles`  
 'ndaki Uzaktan hata ayıklama için kullanılmıyor.  
  
 `dwCreationFlags`  
 'ndaki Uzaktan hata ayıklama için kullanılmıyor.  
  
 `lpEnvironment`  
 'ndaki Yeni işlem için ortam bloğunun işaretçisi.  
  
 `lpCurrentDirectory`  
 'ndaki İşlem için geçerli dizinin tam yolunu belirten, null ile sonlandırılmış bir dize işaretçisi. Bu parametre null ise, yeni işlem çağıran işlemle aynı geçerli sürücü ve dizine sahip olur.  
  
 `lpStartupInfo`  
 'ndaki Uzaktan hata ayıklama için kullanılmıyor.  
  
 `lpProcessInformation`  
 'ndaki Uzaktan hata ayıklama için kullanılmıyor.  
  
 `debuggingFlags`  
 'ndaki Uzaktan hata ayıklama için kullanılmıyor.  
  
 `ppProcess`  
 dışı İşlemi temsil eden "ICorDebugProcess Interface" nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 S_OK  
 İşlem uzak makinede başarıyla başlatıldı ve hata ayıklama için bir "ICorDebugProcess Interface" döndürdü.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Uzak makinede işlem başlatılamıyor ve hata ayıklama için bir "ICorDebugProcess Interface" döndürün.  
  
## <a name="remarks"></a>Açıklamalar  
 Karışık modda hata ayıklama Silverlight 'ta desteklenmez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 4,5, 4, 3,5 SP1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRemote Arabirimi](icordebugremote-interface.md)
- [ICorDebug Arabirimi](icordebug-interface.md)

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
