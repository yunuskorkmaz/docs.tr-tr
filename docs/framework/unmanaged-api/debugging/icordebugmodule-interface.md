---
title: ICorDebugModule Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
ms.openlocfilehash: 971d6a6a2157c48dcb9105e9f523b1f077098479
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129482"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule Arabirimi

Yürütülebilir bir dosya veya dinamik bağlantı kitaplığı (DLL) olan bir ortak dil çalışma zamanı (CLR) modülünü temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|Uygulanmadı.|  
|[EnableClassLoadCallbacks Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|Bu modül için [ICorDebugManagedCallback:: LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [ICorDebugManagedCallback:: UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları çağrılıp çağrılmayacağını belirler.|  
|[EnableJITDebugging Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|Just-In-Time (JıT) derleyicisinin Bu modüldeki yöntemler için hata ayıklama bilgilerini koruyamayacağını belirler.|  
|[GetAssembly Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|Bu modülün kapsayan derlemesini alır.|  
|[GetBaseAddress Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|Modülün temel adresini alır.|  
|[GetClassFromToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|Meta verilerden ICorDebugClass alır.|  
|[GetEditAndContinueSnapshot Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|Kullanım dışı.|  
|[GetFunctionFromRVA Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|Uygulanmadı.|  
|[GetFunctionFromToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|Meta veri belirteci tarafından belirtilen işlevi alır.|  
|[GetGlobalVariableValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|Belirtilen genel değişken için bir değer nesnesi alır.|  
|[GetMetaDataInterface Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|Modülün meta verilerini incelemek için kullanılabilecek bir meta veri arabirim işaretçisi alır.|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|Modülün dosya adını alır.|  
|[GetProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|Bu modül için kapsayan işlemi alır.|  
|[GetSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|Modülün boyutunu bayt cinsinden alır.|  
|[GetToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|Bu modül için tablo girişi belirtecini alır.|  
|[IsDynamic Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|Modülün Dinamik olup olmadığını gösterir.|  
|[IsInMemory Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|Bu modülün yalnızca bellekte bulunup bulunmadığını gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
