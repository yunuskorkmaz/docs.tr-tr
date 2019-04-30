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
ms.openlocfilehash: ca21911f3d16b79887b9d6d8185f8fab17651321
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672997"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction Arabirimi

Yönetilen bir işlevi veya yöntemi temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|Bu işlevin başında bir kesme noktası oluşturur.|  
|[GetClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|Bu işlev bir üyesi, sınıfın temsil ettiği bir Icordebugclass nesnesini alır.|  
|[GetCurrentVersionNumber Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|Bu işleve yapılan en son düzenleme sürüm numarasını alır.|  
|[GetILCode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|Bu işlev için Microsoft Ara dil (MSIL) kodu alır.|  
|[GetLocalVarSigToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Yerel değişken bu tarafından temsil edilen işlev imzası için meta veri belirteci alır `ICorDebugFunction` örneği.|  
|[GetModule Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Bu işlev tanımlandığı modül alır.|  
|[GetNativeCode Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Yerel kod için bu işlevi alır.|  
|[GetToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Meta veriler, bu işlev için belirteç alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugFunction` Arabirimi, genel tür parametreleri olan bir işlevi temsil etmiyor. Örneğin, bir `ICorDebugFunction` örneği gösterir `Func<T>` ama `Func<string>`. Çağrı [Icordebugılframe2::enumeratetypeparameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) genel tür parametreleri alınamıyor.  
  
 Bir yöntemin meta veri belirteci arasındaki ilişkiyi `mdMethodDef`ve bir yöntemin `ICorDebugFunction` Düzenle ve devam et izin verilip işlev üzerinde nesne bağlıdır:  
  
- Düzenle ve devam et izin verilmez, işlev arasında bire bir ilişki var. `ICorDebugFunction` nesne ve `mdMethodDef` belirteci. Diğer bir deyişle, bir işleve sahip `ICorDebugFunction` nesnesi ve bir `mdMethodDef` belirteci.  
  
- Düzenle ve devam et izin veriliyorsa işlev arasında çok bir ilişkinin var. `ICorDebugFunction` nesne ve `mdMethodDef` belirteci. İşlevin birçok örneğini diğer bir deyişle, olabilir `ICorDebugFunction`, işlevin her sürüm için ancak tek `mdMethodDef` belirteci.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:**  CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
