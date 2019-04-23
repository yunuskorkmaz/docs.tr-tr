---
title: ICorDebugRegisterSet::GetThreadContext Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fecbcff0fd124b94aeeecf82e23d9875c34ebb9b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091583"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a>ICorDebugRegisterSet::GetThreadContext Metodu
Geçerli iş parçacığı bağlamını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `contextSize`  
 [in] Bayt cinsinden boyutu, `context` dizisi.  
  
 `context`  
 [out içinde] Win32 oluşturan bir bayt dizisi `CONTEXT` geçerli platform için yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı Win32 yerine bu işlevi çağırmanız gerekir `GetThreadContext` işlev çünkü iş parçacığı burada onun içeriği geçici olarak değiştirildi "ele geçirilen" bir durumda olabilir. Döndürülen veriler bir Win32, `CONTEXT` geçerli platform için yapısı.  
  
 Yaprak olmayan çerçeveler için istemcileri hangi kayıtları kullanarak geçerli olduğunu denetlemeniz gerekir [Icordebugregisterset::getregistersavailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugRegisterSet Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
