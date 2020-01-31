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
ms.openlocfilehash: 4b24b3dfe6a931866acd7eba966811071ff39ea5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788935"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode Arabirimi

Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](icordebugcode-createbreakpoint-method.md)|Belirtilen uzaklığa bir kesme noktası oluşturur.|  
|[GetAddress Yöntemi](icordebugcode-getaddress-method.md)|Bu `ICorDebugCode` temsil ettiği kod segmentinin göreli sanal adresini (RVA) alır.|  
|[GetCode Yöntemi](icordebugcode-getcode-method.md)|Ayrıştırılmış derleme için biçimlendirilen, belirtilen işlevin tüm kodunu alır. Bu yöntem kullanım dışıdır; Bunun yerine [ICorDebugCode2:: Getcodeöbekleri](icordebugcode2-getcodechunks-method.md) kullanın.|  
|[GetEnCRemapSequencePoints Yöntemi](icordebugcode-getencremapsequencepoints-method.md)|Uygulanmadı.|  
|[GetFunction Yöntemi](icordebugcode-getfunction-method.md)|Bu `ICorDebugCode`ilişkili "ICorDebugFunction" öğesini alır.|  
|[GetILToNativeMapping Yöntemi](icordebugcode-getiltonativemapping-method.md)|MSIL uzaklıklarından yerel uzaklıklardan eşlemeleri temsil eden "COR_DEBUG_IL_TO_NATIVE_MAP" örneklerinin bir dizisini alır.|  
|[GetSize Yöntemi](icordebugcode-getsize-method.md)|Bu `ICorDebugCode`temsil edilen ikili kodun boyutunu bayt cinsinden alır.|  
|[GetVersionNumber Yöntemi](icordebugcode-getversionnumber-method.md)|Bu `ICorDebugCode` gösterdiği kodun sürümünü tanımlayan tek tabanlı sayıyı alır.|  
|[IsIL Yöntemi](icordebugcode-isil-method.md)|Bu `ICorDebugCode` MSIL 'de derlenmiş olup olmadığını gösteren bir değer alır.|  
  
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

- [ICorDebugCode3 Arabirimi](icordebugcode3-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
