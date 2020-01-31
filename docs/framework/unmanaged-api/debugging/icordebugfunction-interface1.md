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
ms.openlocfilehash: ba0e0b1b2bac785e28f41e09dda74841121a748d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794512"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction Arabirimi

Yönetilen bir işlevi veya yöntemi temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](icordebugfunction-createbreakpoint-method.md)|Bu işlevin başlangıcında bir kesme noktası oluşturur.|  
|[GetClass Yöntemi](icordebugfunction-getclass-method.md)|Bu işlevin üyesi olduğu sınıfı temsil eden bir ICorDebugClass nesnesi alır.|  
|[GetCurrentVersionNumber Yöntemi](icordebugfunction-getcurrentversionnumber-method.md)|Bu işlevde yapılan en son düzenlemenin sürüm numarasını alır.|  
|[GetILCode Yöntemi](icordebugfunction-getilcode-method.md)|Bu işlev için Microsoft ara dili (MSIL) kodunu alır.|  
|[GetLocalVarSigToken Yöntemi](icordebugfunction-getlocalvarsigtoken-method.md)|Bu `ICorDebugFunction` örneğiyle temsil edilen işlevin yerel değişken imzası için meta veri belirtecini alır.|  
|[GetModule Yöntemi](icordebugfunction-getmodule-method.md)|Bu işlevin tanımlandığı modülü alır.|  
|[GetNativeCode Yöntemi](icordebugfunction-getnativecode-method.md)|Bu işlev için yerel kodu alır.|  
|[GetToken Yöntemi](icordebugfunction-gettoken-method.md)|Bu işlev için meta veri belirtecini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugFunction` arabirimi, genel tür parametrelerine sahip bir işlevi temsil etmiyor. Örneğin, bir `ICorDebugFunction` örneği `Func<T>` temsil eder ancak `Func<string>`değil. Genel tür parametrelerini almak için [ICorDebugILFrame2:: EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) çağırın.  
  
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

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
