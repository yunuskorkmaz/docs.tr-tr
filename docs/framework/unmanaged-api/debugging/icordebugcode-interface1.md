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
ms.openlocfilehash: 03cbc1a598ba6c0166f72ff404c239763956c996
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687612"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode Arabirimi

Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](icordebugcode-createbreakpoint-method.md)|Belirtilen uzaklığa bir kesme noktası oluşturur.|  
|[GetAddress Yöntemi](icordebugcode-getaddress-method.md)|Bu temsil eden kod kesiminin göreli sanal adresini (RVA) alır `ICorDebugCode` .|  
|[GetCode Yöntemi](icordebugcode-getcode-method.md)|Ayrıştırılmış derleme için biçimlendirilen, belirtilen işlevin tüm kodunu alır. Bu yöntem kullanım dışıdır; Bunun yerine [ICorDebugCode2:: Getcodeöbekleri](icordebugcode2-getcodechunks-method.md) kullanın.|  
|[GetEnCRemapSequencePoints Yöntemi](icordebugcode-getencremapsequencepoints-method.md)|Uygulanmaz.|  
|[GetFunction Yöntemi](icordebugcode-getfunction-method.md)|Bu ile ilişkili "ICorDebugFunction" öğesini alır `ICorDebugCode` .|  
|[GetILToNativeMapping Metodu](icordebugcode-getiltonativemapping-method.md)|MSIL uzaklıklarından yerel uzaklıklardan eşlemeleri temsil eden "COR_DEBUG_IL_TO_NATIVE_MAP" örneklerinin bir dizisini alır.|  
|[GetSize Yöntemi](icordebugcode-getsize-method.md)|Bu tarafından temsil edilen ikili kodun boyutunu bayt cinsinden alır `ICorDebugCode` .|  
|[GetVersionNumber Metodu](icordebugcode-getversionnumber-method.md)|Bu temsil eden kodun sürümünü tanımlayan tek tabanlı sayıyı alır `ICorDebugCode` .|  
|[IsIL Yöntemi](icordebugcode-isil-method.md)|Bu değerin `ICorDebugCode` MSIL 'de derlenip derlenmediğini gösteren bir değer alır.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorDebugCode` MSIL veya yerel kod temsil edebilir. MSIL kodunu temsil eden bir "ICorDebugFunction" nesnesinin, kendisiyle ilişkilendirilmiş sıfır veya bir `ICorDebugCode` nesnesi olabilir. Yerel kodu temsil eden bir "ICorDebugFunction" nesnesi kendisiyle ilişkilendirilmiş herhangi bir sayıda `ICorDebugCode` nesne içerebilir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugCode3 Arabirimi](icordebugcode3-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
