---
title: ICorDebugFunction Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae65c59efe1d925b5e058e8664d1e093fdfec875
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917200"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction Arabirimi

Yönetilen bir işlevi veya yöntemi temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|Bu işlevin başlangıcında bir kesme noktası oluşturur.|  
|[GetClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|Bu işlevin üyesi olduğu sınıfı temsil eden bir ICorDebugClass nesnesi alır.|  
|[GetCurrentVersionNumber Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|Bu işlevde yapılan en son düzenlemenin sürüm numarasını alır.|  
|[GetILCode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|Bu işlev için Microsoft ara dili (MSIL) kodunu alır.|  
|[GetLocalVarSigToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Bu `ICorDebugFunction` örnekle temsil edilen işlevin yerel değişken imzası için meta veri belirtecini alır.|  
|[GetModule Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Bu işlevin tanımlandığı modülü alır.|  
|[GetNativeCode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Bu işlev için yerel kodu alır.|  
|[GetToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Bu işlev için meta veri belirtecini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Arabirim `ICorDebugFunction` , genel tür parametrelerine sahip bir işlevi temsil etmiyor. Örneğin, bir `ICorDebugFunction` örnek temsil eder `Func<T>` ancak değil `Func<string>`. Genel tür parametrelerini almak için [ICorDebugILFrame2:: EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) çağırın.  
  
 Yöntemin meta veri belirteci, `mdMethodDef`ve `ICorDebugFunction` yöntemin nesnesi arasındaki ilişki, işlevde Düzenle ve devam et iznine sahip olup olmadığına bağlıdır:  
  
- İşlevde Düzenle ve devam et izin verilmiyorsa, `ICorDebugFunction` nesne `mdMethodDef` ve belirteç arasında bire bir ilişki bulunur. Diğer bir deyişle, işlevde bir `ICorDebugFunction` nesne ve bir `mdMethodDef` belirteç vardır.  
  
- İşlevde Düzenle ve devam et izni varsa, `ICorDebugFunction` nesne `mdMethodDef` ve belirteç arasında çoktan bire bir ilişki bulunur. Diğer bir deyişle, işlev işlevin her sürümü için bir `ICorDebugFunction`tane olmak üzere birçok örneğine, ancak yalnızca bir `mdMethodDef` belirtece sahip olabilir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı**  Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
