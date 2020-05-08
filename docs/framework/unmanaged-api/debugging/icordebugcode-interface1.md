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
ms.openlocfilehash: 3736627e7f42ad9db6699c31a0a618e993eef770
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893465"
---
# <a name="icordebugcode-interface"></a>ICorDebugCode Arabirimi

Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](icordebugcode-createbreakpoint-method.md)|Belirtilen uzaklığa bir kesme noktası oluşturur.|  
|[GetAddress Yöntemi](icordebugcode-getaddress-method.md)|Bu `ICorDebugCode` temsil eden kod kesiminin göreli sanal ADRESINI (RVA) alır.|  
|[GetCode Yöntemi](icordebugcode-getcode-method.md)|Ayrıştırılmış derleme için biçimlendirilen, belirtilen işlevin tüm kodunu alır. Bu yöntem kullanım dışıdır; Bunun yerine [ICorDebugCode2:: Getcodeöbekleri](icordebugcode2-getcodechunks-method.md) kullanın.|  
|[GetEnCRemapSequencePoints Yöntemi](icordebugcode-getencremapsequencepoints-method.md)|Uygulanmaz.|  
|[GetFunction Yöntemi](icordebugcode-getfunction-method.md)|Bu `ICorDebugCode`ile Ilişkili "ICorDebugFunction" öğesini alır.|  
|[GetILToNativeMapping Yöntemi](icordebugcode-getiltonativemapping-method.md)|MSIL uzaklıklarından yerel uzaklıklardan eşlemeleri temsil eden "COR_DEBUG_IL_TO_NATIVE_MAP" örneklerinin bir dizisini alır.|  
|[GetSize Yöntemi](icordebugcode-getsize-method.md)|Bu `ICorDebugCode`tarafından temsil edilen ikili kodun boyutunu bayt cinsinden alır.|  
|[GetVersionNumber Metodu](icordebugcode-getversionnumber-method.md)|Bu `ICorDebugCode` temsil eden kodun sürümünü tanımlayan tek tabanlı sayıyı alır.|  
|[IsIL Yöntemi](icordebugcode-isil-method.md)|Bu `ICorDebugCode` değerin MSIL 'de derlenip derlenmediğini gösteren bir değer alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugCode`MSIL veya yerel kod temsil edebilir. MSIL kodunu temsil eden bir "ICorDebugFunction" nesnesinin, kendisiyle ilişkilendirilmiş sıfır veya bir `ICorDebugCode` nesnesi olabilir. Yerel kodu temsil eden bir "ICorDebugFunction" nesnesi kendisiyle ilişkilendirilmiş herhangi bir sayıda `ICorDebugCode` nesne içerebilir.  
  
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
