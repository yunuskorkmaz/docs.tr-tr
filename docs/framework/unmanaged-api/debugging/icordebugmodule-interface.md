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
ms.openlocfilehash: 105e56f2508eabbb6876a09d35e6abfbfc08950b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212249"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule Arabirimi

Yürütülebilir bir dosya veya dinamik bağlantı kitaplığı (DLL) olan bir ortak dil çalışma zamanı (CLR) modülünü temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](icordebugmodule-createbreakpoint-method.md)|Uygulanmaz.|  
|[EnableClassLoadCallbacks Yöntemi](icordebugmodule-enableclassloadcallbacks-method.md)|Bu modül için [ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) ve [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) geri çağırmaları çağrılıp çağrılmayacağını belirler.|  
|[EnableJITDebugging Yöntemi](icordebugmodule-enablejitdebugging-method.md)|Just-In-Time (JıT) derleyicisinin Bu modüldeki yöntemler için hata ayıklama bilgilerini koruyamayacağını belirler.|  
|[GetAssembly Yöntemi](icordebugmodule-getassembly-method.md)|Bu modülün kapsayan derlemesini alır.|  
|[GetBaseAddress Yöntemi](icordebugmodule-getbaseaddress-method.md)|Modülün temel adresini alır.|  
|[GetClassFromToken Yöntemi](icordebugmodule-getclassfromtoken-method.md)|Meta verilerden ICorDebugClass alır.|  
|[GetEditAndContinueSnapshot Yöntemi](icordebugmodule-geteditandcontinuesnapshot-method.md)|Kullanım dışı.|  
|[GetFunctionFromRVA Yöntemi](icordebugmodule-getfunctionfromrva-method.md)|Uygulanmaz.|  
|[GetFunctionFromToken Yöntemi](icordebugmodule-getfunctionfromtoken-method.md)|Meta veri belirteci tarafından belirtilen işlevi alır.|  
|[GetGlobalVariableValue Yöntemi](icordebugmodule-getglobalvariablevalue-method.md)|Belirtilen genel değişken için bir değer nesnesi alır.|  
|[GetMetaDataInterface Yöntemi](icordebugmodule-getmetadatainterface-method.md)|Modülün meta verilerini incelemek için kullanılabilecek bir meta veri arabirim işaretçisi alır.|  
|[GetName Yöntemi](icordebugmodule-getname-method.md)|Modülün dosya adını alır.|  
|[GetProcess Yöntemi](icordebugmodule-getprocess-method.md)|Bu modül için kapsayan işlemi alır.|  
|[GetSize Yöntemi](icordebugmodule-getsize-method.md)|Modülün boyutunu bayt cinsinden alır.|  
|[GetToken Metodu](icordebugmodule-gettoken-method.md)|Bu modül için tablo girişi belirtecini alır.|  
|[IsDynamic Yöntemi](icordebugmodule-isdynamic-method.md)|Modülün Dinamik olup olmadığını gösterir.|  
|[IsInMemory Yöntemi](icordebugmodule-isinmemory-method.md)|Bu modülün yalnızca bellekte bulunup bulunmadığını gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](icordebug-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
