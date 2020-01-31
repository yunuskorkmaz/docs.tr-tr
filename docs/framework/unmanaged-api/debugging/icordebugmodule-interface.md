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
ms.openlocfilehash: c573e6b768aee1e8b681dcf2e828dc24d409025b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793009"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule Arabirimi

Yürütülebilir bir dosya veya dinamik bağlantı kitaplığı (DLL) olan bir ortak dil çalışma zamanı (CLR) modülünü temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](icordebugmodule-createbreakpoint-method.md)|Uygulanmadı.|  
|[EnableClassLoadCallbacks Yöntemi](icordebugmodule-enableclassloadcallbacks-method.md)|Bu modül için [ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) ve [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları çağrılıp çağrılmayacağını belirler.|  
|[EnableJITDebugging Yöntemi](icordebugmodule-enablejitdebugging-method.md)|Just-In-Time (JıT) derleyicisinin Bu modüldeki yöntemler için hata ayıklama bilgilerini koruyamayacağını belirler.|  
|[GetAssembly Yöntemi](icordebugmodule-getassembly-method.md)|Bu modülün kapsayan derlemesini alır.|  
|[GetBaseAddress Yöntemi](icordebugmodule-getbaseaddress-method.md)|Modülün temel adresini alır.|  
|[GetClassFromToken Yöntemi](icordebugmodule-getclassfromtoken-method.md)|Meta verilerden ICorDebugClass alır.|  
|[GetEditAndContinueSnapshot Yöntemi](icordebugmodule-geteditandcontinuesnapshot-method.md)|Kullanım dışı.|  
|[GetFunctionFromRVA Yöntemi](icordebugmodule-getfunctionfromrva-method.md)|Uygulanmadı.|  
|[GetFunctionFromToken Yöntemi](icordebugmodule-getfunctionfromtoken-method.md)|Meta veri belirteci tarafından belirtilen işlevi alır.|  
|[GetGlobalVariableValue Yöntemi](icordebugmodule-getglobalvariablevalue-method.md)|Belirtilen genel değişken için bir değer nesnesi alır.|  
|[GetMetaDataInterface Yöntemi](icordebugmodule-getmetadatainterface-method.md)|Modülün meta verilerini incelemek için kullanılabilecek bir meta veri arabirim işaretçisi alır.|  
|[GetName Yöntemi](icordebugmodule-getname-method.md)|Modülün dosya adını alır.|  
|[GetProcess Yöntemi](icordebugmodule-getprocess-method.md)|Bu modül için kapsayan işlemi alır.|  
|[GetSize Yöntemi](icordebugmodule-getsize-method.md)|Modülün boyutunu bayt cinsinden alır.|  
|[GetToken Yöntemi](icordebugmodule-gettoken-method.md)|Bu modül için tablo girişi belirtecini alır.|  
|[IsDynamic Yöntemi](icordebugmodule-isdynamic-method.md)|Modülün Dinamik olup olmadığını gösterir.|  
|[IsInMemory Yöntemi](icordebugmodule-isinmemory-method.md)|Bu modülün yalnızca bellekte bulunup bulunmadığını gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](icordebug-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
