---
title: ICorDebugProcess2::SetDesiredNGENCompilerFlags Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3582ebf2acee02d49aabafb03604c84249c4ce13
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747379"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>ICorDebugProcess2::SetDesiredNGENCompilerFlags Yöntemi
Geçerli işleme bu görüntüyü yüklemek çalışma zamanı için sırayla önceden derlenmiş bir görüntüde gömülü gerekir bayraklarını ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pdwFlags`  
 [in] Değerini [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) derleyici bayraklarına belirten sabit listesi önceden derlenmiş doğru görüntüyü seçmek için kullanılır.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetDesiredNGENCompilerFlags` Yöntemi önceden derlenmiş bir görüntüde gömülü olması gerekir ve böylece çalışma zamanı bu işlemine o yansıma yükleyecek bayrakları belirtir. Bu yöntem tarafından ayarlanan bayraklar yalnızca önceden derlenmiş doğru görüntüyü seçmek için kullanılır. Çalışma zamanı Microsoft Ara dili (MSIL) görüntüsü ve just-ın-time (JIT) derleyici bu tür bir görüntü varsa, bunun yerine yükler. Bu durumda, hata ayıklayıcı hala kullanmalısınız [Icordebugmodule2::setjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) istenen JIT derlemesi için bayrakları ayarlamanızı yöntemi.  
  
 Görüntü yüklendi, ancak bazı JIT derleme bu görüntüyü (görüntü, genel türler içeriyorsa, olacaktır) yer almalıdır tarafından belirtilen derleyici bayraklarına `SetDesiredNGENCompilerFlags` yöntemi ek JIT derlemesi için uygulanır.  
  
 `SetDesiredNGENCompilerFlags` Sırasında metodu çağrılmalıdır [Icordebugmanagedcallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma. Arama girişiminde `SetDesiredNGENCompilerFlags` yöntemi daha sonra başarısız olur. Olan bayrakları ayarlamaya çalışır ayrıca tanımlanan `CorDebugJITCompilerFlags` numaralandırma veya verilen işlem için yasal değil misiniz başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
