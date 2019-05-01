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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 257011562a9ea687ef70b842c6d47219283e158e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988045"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule Arabirimi

Bir yürütülebilir dosya ya da bir dinamik bağlantı kitaplığı (DLL) bir ortak dil çalışma zamanı (CLR) modülü temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|Henüz uygulanmadı.|  
|[EnableClassLoadCallbacks Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|Belirler olmadığını [Icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [Icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları bu modül için çağrılır.|  
|[EnableJITDebugging Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|Just-ın-time (JIT) derleyicinin bu modül içindeki yöntemler için hata ayıklama bilgilerini korur olup olmadığını belirler.|  
|[GetAssembly Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|Bu modül için derlemeyi içeren alır.|  
|[GetBaseAddress Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|Modül temel adresini alır.|  
|[GetClassFromToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|Icordebugclass meta verileri alır.|  
|[GetEditAndContinueSnapshot Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|Kullanım dışı.|  
|[GetFunctionFromRVA Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|Henüz uygulanmadı.|  
|[GetFunctionFromToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|Metaveri belirteci tarafından belirtilen işlevi alır.|  
|[GetGlobalVariableValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|Belirtilen genel değişkeni için değer nesnesi alır.|  
|[GetMetaDataInterface Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|Modül meta verilerini incelemek için kullanılan bir meta veri arabirim işaretçisi alır.|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|Modül dosya adını alır.|  
|[GetProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|Bu modül için içeren işlemi alır.|  
|[GetSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|Modül boyutu bayt cinsinden alır.|  
|[GetToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|Bu modül için tablo girişi için belirteç alır.|  
|[IsDynamic Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|Modülü dinamik olup olmadığını belirtir.|  
|[IsInMemory Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|Bu modül yalnızca bellekte mevcut olup olmadığını gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
