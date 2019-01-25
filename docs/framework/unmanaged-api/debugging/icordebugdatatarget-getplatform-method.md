---
title: ICorDebugDataTarget::GetPlatform Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bc91a90320967e625aab63fa17ae88ab284ea38
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689136"
---
# <a name="icordebugdatatargetgetplatform-method"></a>ICorDebugDataTarget::GetPlatform Metodu
İşlemci mimarisi ve hedef işlem üzerinde çalıştığı işletim sistemi dahil olmak üzere platform hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pTargetPlatform`  
 [out] Bir işaretçi bir [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) hedef platform açıklayan sabit listesi.  
  
## <a name="remarks"></a>Açıklamalar  
 `CorDebugPlatformEnum` Numaralandırma dönüş değeri tarafından kullanılan [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) arabirimi, işaretçi boyutu, adres alanı düzeni, kayıt kümesi, yönerge biçimi, içerik düzeni, hedef işlemin ayrıntılarını belirlemek için ve çağırma kuralları.  
  
 `pTargetPlatform` Değeri, gerçek donanım kullanımda belirtmek yerine hedef için benzetilmiş bir platforma başvurabilir. Örneğin, Windows (WOW) ortamında Windows 64-bit Windows işletim sistemi sürümünde çalışan bir işlemin kullanmalıdır `CORDB_PLATFORM_WINDOWS_X86` değerini [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) sabit listesi.  
  
 Bu yöntem başarılı olması gerekir. Başarısız olursa, hedef platform kullanılamaz. Yöntemi, aşağıdaki nedenlerden dolayı başarısız olabilir:  
  
-   Hedef benzetilip benzetilmediğini platformu kullanılamıyor.  
  
-   Gerçek donanım hedef platformda kullanılamaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorDebugDataTarget Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
