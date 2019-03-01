---
title: ICorDebugCode Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ca47eb5508907297a78dba1ab2b0a6d2b8ece0d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976934"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode Arabirimi

Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|Belirtilen uzaklıkta bir kesme noktası oluşturur.|  
|[GetAddress Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|Kod kesiminin göreli sanal adres (RVA) alır bu `ICorDebugCode` temsil eder.|  
|[GetCode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|Ayrıştırma için biçimlendirilmiş belirtilen işlevi tüm kod alır. Bu yöntem kullanım dışı; kullanma [Icordebugcode2::getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) yerine.|  
|[GetEnCRemapSequencePoints Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|Henüz uygulanmadı.|  
|[GetFunction Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|"Bu ile ilişkili ICorDebugFunction" alır `ICorDebugCode`.|  
|[GetILToNativeMapping Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|Eşlemeleri için yerel uzaklıklar MSIL uzaklıkları temsil eden "Cor_debug_ıl_to_natıve_map" örneklerinin bir dizisini alır.|  
|[GetSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|Bu tarafından temsil edilen ikili kod bayt cinsinden boyutunu alır `ICorDebugCode`.|  
|[GetVersionNumber Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|Kod sürümünü tanımlayan bir tabanlı sayısını alır, bu `ICorDebugCode` temsil eder.|  
|[IsIL Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|Belirten bir değer alır olup bu `ICorDebugCode` MSIL derlenmiş.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugCode` MSIL veya yerel kod temsil edebilir. MSIL kodunu temsil eden bir "ICorDebugFunction" nesne sıfır veya bir olabilir `ICorDebugCode` ilişkili nesneleri. Yerel kod temsil eden bir "ICorDebugFunction" nesne herhangi bir sayıda olabilir `ICorDebugCode` ilişkili nesneleri.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugCode3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
