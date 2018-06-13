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
ms.openlocfilehash: 94ba2b0cf7d88104eaadd434732edf3c1d4060e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422707"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a>ICorDebugProcess2::SetDesiredNGENCompilerFlags Yöntemi
Sırada, görüntü geçerli işlemine yüklemek çalışma zamanı için önceden derlenmiş görüntüsündeki gömülü gerekir bayrakları ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pdwFlags`  
 [in] Değerini [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) derleyici bayrakları belirtir numaralandırması önceden derlenmiş doğru görüntüyü seçmek için kullanılır.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetDesiredNGENCompilerFlags` Yöntemi önceden derlenmiş bir görüntüde gömülü gerekir ve böylece çalışma zamanı bu işlemine bu görüntüyü yükler bayrakları belirtir. Bu yöntem tarafından ayarlanan bayraklar yalnızca doğru önceden derlenmiş görüntüyü seçmek için kullanılır. Çalışma zamanı Microsoft Ara dili (MSIL) görüntüsü ve tam zamanında (JIT) derleyici böyle bir görüntü varsa, bunun yerine yükler. Bu durumda, hata ayıklayıcı hala kullanmalısınız [Icordebugmodule2::setjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) yöntemi JIT derleme için istediğiniz gibi bayraklarını ayarlayın.  
  
 Bir görüntü yüklenir, ancak bazı JIT derleme (görüntü genel türler içeriyorsa olacağı durum) bu görüntü için gerçekleşmesi gerekir tarafından belirtilen derleyici bayrakları `SetDesiredNGENCompilerFlags` yöntemi ek JIT derleme uygulanacaktır.  
  
 `SetDesiredNGENCompilerFlags` Yöntemi çağrılır, sırasında [Icordebugmanagedcallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma. Arama girişiminde `SetDesiredNGENCompilerFlags` yöntemi daha sonra başarısız olur. Ya da olan bayrakları ayarlamaya çalışır Ayrıca, tanımlanan `CorDebugJITCompilerFlags` numaralandırma veya belirli bir işlemi için yasal değil misiniz başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
