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
ms.openlocfilehash: 8cb95fad4394e2ce9b7f922e720071d8c4434edb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125586"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode Arabirimi

Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|Belirtilen uzaklığa bir kesme noktası oluşturur.|  
|[GetAddress Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|Bu `ICorDebugCode` temsil ettiği kod segmentinin göreli sanal adresini (RVA) alır.|  
|[GetCode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|Ayrıştırılmış derleme için biçimlendirilen, belirtilen işlevin tüm kodunu alır. Bu yöntem kullanım dışıdır; Bunun yerine [ICorDebugCode2:: Getcodeöbekleri](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) kullanın.|  
|[GetEnCRemapSequencePoints Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|Uygulanmadı.|  
|[GetFunction Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|Bu `ICorDebugCode`ilişkili "ICorDebugFunction" öğesini alır.|  
|[GetILToNativeMapping Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|MSIL uzaklıklarından yerel uzaklıklardan eşlemeleri temsil eden "COR_DEBUG_IL_TO_NATIVE_MAP" örneklerinin bir dizisini alır.|  
|[GetSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|Bu `ICorDebugCode`temsil edilen ikili kodun boyutunu bayt cinsinden alır.|  
|[GetVersionNumber Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|Bu `ICorDebugCode` gösterdiği kodun sürümünü tanımlayan tek tabanlı sayıyı alır.|  
|[IsIL Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|Bu `ICorDebugCode` MSIL 'de derlenmiş olup olmadığını gösteren bir değer alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugCode` MSIL veya yerel kod temsil edebilir. MSIL kodunu temsil eden bir "ICorDebugFunction" nesnesi, kendisiyle ilişkilendirilmiş sıfır ya da bir `ICorDebugCode` nesnesine sahip olabilir. Yerel kodu temsil eden bir "ICorDebugFunction" nesnesi kendisiyle ilişkilendirilmiş herhangi bir sayıda `ICorDebugCode` nesnesine sahip olabilir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugCode3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
