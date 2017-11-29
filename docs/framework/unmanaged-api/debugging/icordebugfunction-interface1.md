---
title: ICorDebugFunction Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction
helpviewer_keywords: ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 327ef9f74e94e3b1b20e78eb6a833038b5bfe16d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction-interface1"></a>ICorDebugFunction Interface1
Yönetilen bir işlevi veya yöntemi temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|Bu işlev, başında bir kesme noktası oluşturur.|  
|[GetClass yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|Bu işlev bir üyesidir sınıfı temsil eden bir Icordebugclass nesnesi alır.|  
|[GetCurrentVersionNumber yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|Bu işleve yapılan en son düzenleme sürüm numarasını alır.|  
|[Getılcode yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|Bu işlev için Microsoft Ara dili (MSIL) kodu alır.|  
|[GetLocalVarSigToken yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Meta verileri, bu tarafından temsil edilen işlevinin yerel değişken imzası için belirteç alır `ICorDebugFunction` örneği.|  
|[GetModule yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Bu işlevin tanımlı olduğu modülü alır.|  
|[GetNativeCode yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Bu işlev için yerel kodu alır.|  
|[GetToken yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Meta verileri bu işlev için belirteç alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugFunction` Arabirimi genel tür parametreleri olan bir işlevi temsil etmiyor. Örneğin, bir `ICorDebugFunction` örneği temsil eden `Func<T>` ama `Func<string>`. Çağrı [Icordebugılframe2::enumeratetypeparameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) genel tür parametreleri alınamıyor.  
  
 Bir yöntemin meta veri simgesi arasındaki ilişkiyi `mdMethodDef`ve bir yöntemin `ICorDebugFunction` Düzenle ve devam et izin verilip işlev bağlı nesne bağlıdır:  
  
-   Düzenle ve devam et izin verilmez, işlev arasında bire bir ilişki var. `ICorDebugFunction` nesne ve `mdMethodDef` belirteci. Diğer bir deyişle, işlev varsa `ICorDebugFunction` nesne ve bir `mdMethodDef` belirteci.  
  
-   Düzenle ve devam et izin veriliyorsa işlev arasında çoktan bire bir ilişki var. `ICorDebugFunction` nesne ve `mdMethodDef` belirteci. Diğer bir deyişle, birçok örneklerini işlevi olabilir `ICorDebugFunction`, bir işlev her sürümü, ancak yalnızca bir `mdMethodDef` belirteci.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
