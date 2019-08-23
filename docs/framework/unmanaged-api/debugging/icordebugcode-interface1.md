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
ms.openlocfilehash: 75cc8ea9d88dda42362f50b519864b1a78e1a64b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960788"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode Arabirimi

Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|Belirtilen uzaklığa bir kesme noktası oluşturur.|  
|[GetAddress Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|Bu `ICorDebugCode` temsil eden kod kesiminin göreli sanal adresini (RVA) alır.|  
|[GetCode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|Ayrıştırılmış derleme için biçimlendirilen, belirtilen işlevin tüm kodunu alır. Bu yöntem kullanım dışıdır; Bunun yerine [ICorDebugCode2:: Getcodeöbekleri](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) kullanın.|  
|[GetEnCRemapSequencePoints Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|Uygulanmadı.|  
|[GetFunction Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|Bu `ICorDebugCode`Ile Ilişkili "ICorDebugFunction" öğesini alır.|  
|[GetILToNativeMapping Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|MSIL uzaklıklarından yerel uzaklıklardan eşlemeleri temsil eden "COR_DEBUG_IL_TO_NATIVE_MAP" örneklerinin bir dizisini alır.|  
|[GetSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|Bu `ICorDebugCode`tarafından temsil edilen ikili kodun boyutunu bayt cinsinden alır.|  
|[GetVersionNumber Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|Bu `ICorDebugCode` temsil eden kodun sürümünü tanımlayan tek tabanlı sayıyı alır.|  
|[IsIL Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|Bu `ICorDebugCode` değerin MSIL 'de derlenip derlenmediğini gösteren bir değer alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugCode`MSIL veya yerel kod temsil edebilir. MSIL kodunu temsil eden bir "ICorDebugFunction" nesnesinin, kendisiyle ilişkilendirilmiş sıfır veya bir `ICorDebugCode` nesnesi olabilir. Yerel kodu temsil eden bir "ICorDebugFunction" nesnesi kendisiyle ilişkilendirilmiş herhangi bir sayıda `ICorDebugCode` nesne içerebilir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugCode3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
