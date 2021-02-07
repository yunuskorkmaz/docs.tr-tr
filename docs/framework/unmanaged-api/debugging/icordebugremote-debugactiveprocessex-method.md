---
description: ': ICorDebugRemote::D ebugActiveProcessEx yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ccbde152e59146bd852a5a0a2f991d10333fa9d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717907"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>ICorDebugRemote::DebugActiveProcessEx Yöntemi

Hata ayıklayıcı altındaki uzak makinede bir işlem başlatır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pRemoteTarget`  
 'ndaki [ICorDebugRemoteTarget arabirimine](icordebugremotetarget-interface.md)yönelik işaretçi. Bu parametre, işlemin üzerinde çalıştığı makineyi tespit etmek için kullanılır.  
  
 `id`  
 'ndaki Hata ayıklayıcının eklendiği işlemin KIMLIĞI.  
  
 `win32Attach`  
 [in] `true` hata ayıklayıcının işlem için Win32 hata ayıklayıcısı olarak davranması ve yönetilmeyen geri çağırmaları dağıtımı gerekiyorsa; Aksi takdirde, `false` .  
  
 `ppProcess`  
 dışı Hata ayıklayıcının eklendiği işlemi temsil eden bir "ICorDebugProcess" nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  

 S_OK  
 Uzak makinedeki işleme başarıyla eklendi.  
  
 E_FAIL (veya diğer E_ dönüş kodları)  
 Uzak makinedeki işleme iliştirilemiyor.  
  
## <a name="remarks"></a>Açıklamalar  

 Karışık modda hata ayıklama Silverlight 'ta desteklenmez.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 4,5, 4, 3,5 SP1  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRemote Arabirimi](icordebugremote-interface.md)
- [ICorDebug Arabirimi](icordebug-interface.md)

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
