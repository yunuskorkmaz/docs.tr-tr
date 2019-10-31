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
ms.openlocfilehash: eb2b1e218314be01898ce90c4378fb713f9bf6ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137858"
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
|[GetLocalVarSigToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Bu `ICorDebugFunction` örneğiyle temsil edilen işlevin yerel değişken imzası için meta veri belirtecini alır.|  
|[GetModule Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Bu işlevin tanımlandığı modülü alır.|  
|[GetNativeCode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Bu işlev için yerel kodu alır.|  
|[GetToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Bu işlev için meta veri belirtecini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugFunction` arabirimi, genel tür parametrelerine sahip bir işlevi temsil etmiyor. Örneğin, bir `ICorDebugFunction` örneği `Func<T>` temsil eder ancak `Func<string>`değil. Genel tür parametrelerini almak için [ICorDebugILFrame2:: EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) çağırın.  
  
 Yöntemin meta veri belirteci, `mdMethodDef`ve yöntemin `ICorDebugFunction` nesnesi arasındaki ilişki, işlevde Düzenle ve devam et iznine sahip olup olmadığına bağlıdır:  
  
- İşlevde Düzenle ve devam et izin verilmiyorsa, `ICorDebugFunction` nesnesi ve `mdMethodDef` belirteci arasında bire bir ilişki bulunur. Diğer bir deyişle, işlevinin bir `ICorDebugFunction` nesnesi ve bir `mdMethodDef` belirteci vardır.  
  
- İşlevde Düzenle ve devam et ' e izin veriliyorsa, `ICorDebugFunction` nesnesi ve `mdMethodDef` belirteci arasında çoktan bire bir ilişki bulunur. Diğer bir deyişle, işlevi işlevin her sürümü için bir tane olmak üzere birden çok `ICorDebugFunction`örneğine sahip olabilir, ancak yalnızca bir `mdMethodDef` belirteci olabilir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:**  Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
