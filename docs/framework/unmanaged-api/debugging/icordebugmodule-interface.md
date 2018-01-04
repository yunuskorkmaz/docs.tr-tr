---
title: Icordebugmodule Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule
helpviewer_keywords: ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59c24d8305e71aac01843155b86fb54fb1e1263d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule-interface1"></a>Icordebugmodule Interface1
Yürütülebilir bir dosyanın veya bir dinamik bağlantı kitaplığı (DLL) bir ortak dil çalışma zamanı (CLR) modülü temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|Henüz uygulanmadı.|  
|[EnableClassLoadCallbacks Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|Belirler olup olmadığını [Icordebugmanagedcallback::loadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) ve [Icordebugmanagedcallback::unloadclass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) geri aramalar, bu modül için çağrılır.|  
|[EnableJITDebugging Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|Tam zamanında (JIT) derleyici bu modül içinde yöntemleri için hata ayıklama bilgilerini korur olup olmadığını belirler.|  
|[GetAssembly Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|Bu modül için içeren derleme alır.|  
|[GetBaseAddress Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|Modülün taban adresi alır.|  
|[GetClassFromToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|Icordebugclass meta verilerini alır.|  
|[GetEditAndContinueSnapshot Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|Kullanım dışı.|  
|[GetFunctionFromRVA Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|Henüz uygulanmadı.|  
|[GetFunctionFromToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|Meta veri simgesi tarafından belirtilen işlevi alır.|  
|[GetGlobalVariableValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|Belirtilen genel değişkeni için bir değer nesnesi alır.|  
|[GetMetaDataInterface Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|Modül için meta verileri incelemek için kullanılan bir meta veri arabirim işaretçisi alır.|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|Modül dosyası adını alır.|  
|[GetProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|Bu modül için içeren işlem alır.|  
|[GetSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|Modül boyutunu bayt cinsinden alır.|  
|[GetToken Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|Bu modül için tablo girişi için belirteç alır.|  
|[IsDynamic Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|Modül dinamik olup olmadığını gösterir.|  
|[IsInMemory Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|Bu modül yalnızca bellekte var olup olmadığını gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
