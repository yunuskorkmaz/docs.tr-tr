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
ms.openlocfilehash: 6b7b6969c1f207decbf47217e98b7fee3aa9ce54
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213250"
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
|[GetLocalVarSigToken Metodu](icordebugfunction-getlocalvarsigtoken-method.md)|Bu örnekle temsil edilen işlevin yerel değişken imzası için meta veri belirtecini alır `ICorDebugFunction` .|  
|[GetModule Yöntemi](icordebugfunction-getmodule-method.md)|Bu işlevin tanımlandığı modülü alır.|  
|[GetNativeCode Yöntemi](icordebugfunction-getnativecode-method.md)|Bu işlev için yerel kodu alır.|  
|[GetToken Metodu](icordebugfunction-gettoken-method.md)|Bu işlev için meta veri belirtecini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugFunction`Arabirim, genel tür parametrelerine sahip bir işlevi temsil etmiyor. Örneğin, bir `ICorDebugFunction` örnek temsil eder `Func<T>` ancak değil `Func<string>` . Genel tür parametrelerini almak için [ICorDebugILFrame2:: EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) çağırın.  
  
 Yöntemin meta veri belirteci, `mdMethodDef` ve yöntemin nesnesi arasındaki ilişki, `ICorDebugFunction` işlevde Düzenle ve devam et iznine sahip olup olmadığına bağlıdır:  
  
- İşlevde Düzenle ve devam et izin verilmiyorsa, nesne ve belirteç arasında bire bir ilişki bulunur `ICorDebugFunction` `mdMethodDef` . Diğer bir deyişle, işlevde bir `ICorDebugFunction` nesne ve bir `mdMethodDef` belirteç vardır.  
  
- İşlevde Düzenle ve devam et izni varsa, nesne ve belirteç arasında çoktan bire bir ilişki bulunur `ICorDebugFunction` `mdMethodDef` . Diğer bir deyişle, işlev `ICorDebugFunction` işlevin her sürümü için bir tane olmak üzere birçok örneğine, ancak yalnızca bir belirtece sahip olabilir `mdMethodDef` .  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:**  Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
