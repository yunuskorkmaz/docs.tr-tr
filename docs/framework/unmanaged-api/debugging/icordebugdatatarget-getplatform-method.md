---
title: ICorDebugDataTarget::GetPlatform Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget.GetPlatform Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf2f852d0da36211e379a4068cccff9dfc656100
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatargetgetplatform-method"></a>ICorDebugDataTarget::GetPlatform Metodu
İşlemci mimarisi ve hedef işlemin çalıştığı işletim sistemi dahil olmak üzere bu platform hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pTargetPlatform`  
 [out] Bir işaretçi bir [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) hedef platformu açıklar numaralandırması.  
  
## <a name="remarks"></a>Açıklamalar  
 `CorDebugPlatformEnum` Numaralandırma dönüş değeri tarafından kullanılan [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) kendi işaretçi boyutu, adres alanı düzeni, kayıt kümesi, yönerge biçimi, içerik düzeni gibi hedef işleminin ayrıntılarını belirlemek için arabirimi ve çağırma kuralları.  
  
 `pTargetPlatform` Değeri gerçek donanım kullanımda belirtmek yerine hedef için benzetilmiş bir platform başvurabilir. Örneğin, Windows işletim sisteminin 64 bit sürümünde Windows (WOW) ortamında Windows çalıştıran bir işlem kullanması gereken `CORDB_PLATFORM_WINDOWS_X86` değerini [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) numaralandırması.  
  
 Bu yöntem başarılı olması gerekir. Başarısız olursa, hedef platformu kullanılamaz. Yöntemi, aşağıdaki nedenlerden dolayı başarısız olabilir:  
  
-   Hedef benzetilmiş platform kullanılamaz.  
  
-   Hedef platformu üzerinde gerçek donanım kullanılamaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icordebugdatatarget arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
