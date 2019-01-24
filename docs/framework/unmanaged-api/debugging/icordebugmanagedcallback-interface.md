---
title: ICorDebugManagedCallback Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback
helpviewer_keywords:
- ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: b47f1d61-c7dc-4196-b926-0b08c94f7041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 516485d39f1e18a3b82886ed08cd0344c16236dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640543"
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback Arabirimi
Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Break Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|Hata ayıklayıcı bildirir, bir <xref:System.Reflection.Emit.OpCodes.Break> yönerge kodu stream'de yürütülür.|  
|[Breakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|Hata ayıklayıcı bir kesme oluştuğunda size bildirir.|  
|[BreakpointSetError Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|Hata ayıklayıcı ortak dil çalışma zamanı (CLR) doğru bir şekilde bir işlev yalnızca derlenmiş zamanında (JIT) şeklindeydi ayarlanan bir kesme noktası bağlayamadı olduğunu bildirir.|  
|[ControlCTrap Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|Hata ayıklayıcı, CTRL + C ayıklanan işlemin yakalanır bildirir.|  
|[CreateAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|Hata ayıklayıcı, bir uygulama etki alanı oluşturulduğunu bildirir.|  
|[CreateProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|Bir işleme eklenmiş veya için ilk kez başlatıldığında, hata ayıklayıcı size bildirir.|  
|[CreateThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|Hata ayıklayıcı, yönetilen bir kodu yürüten bir iş parçacığı başlatıldı bildirir.|  
|[DebuggerError Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|CLR bir olaydan işlemeye çalışırken bir hata oluştu, hata ayıklayıcı bildirir.|  
|[EditAndContinueRemap Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|Kullanım dışı. Hata ayıklayıcı remap olay IDE'ye gönderildiğini bildirir.|  
|[EvalComplete Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|Hata ayıklayıcı, bir değerlendirme tamamlandığını bildirir.|  
|[EvalException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|Hata ayıklayıcı, bir değerlendirme işlenmeyen bir özel durum ile sonlandırıldı bildirir.|  
|[Exception Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|Hata ayıklayıcı, yönetilen koddan bir özel durum olduğunu bildirir.|  
|[ExitAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|Hata ayıklayıcı, bir uygulama etki alanı çıkıldı bildirir.|  
|[ExitProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|Hata ayıklayıcı bir işlemden çıkıldı bildirir.|  
|[ExitThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|Hata ayıklayıcı, yönetilen kod yürütülmekte olan bir iş parçacığı çıkıldı bildirir.|  
|[LoadAssembly Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|Hata ayıklayıcı bir CLR derlemesi başarıyla yüklenmiş olduğunu bildirir.|  
|[LoadClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|Hata ayıklayıcı, bir sınıf yüklenmemiş olduğunu bildirir.|  
|[LoadModule Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|Hata ayıklayıcı bir CLR modülünü başarılı bir şekilde yüklenmemiş olduğunu bildirir.|  
|[LogMessage Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|Hata ayıklayıcı, yönetilen CLR iş parçacığı bir yöntem çağırdı olduğunu bildirir <xref:System.Diagnostics.EventLog> günlüğe bir olay için sınıf.|  
|[LogSwitch Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|Hata ayıklayıcı, yönetilen CLR iş parçacığı bir yöntem çağırdı olduğunu bildirir <xref:System.Diagnostics.Switch> sınıfı oluşturmak, değiştirmek veya bir hata ayıklama izleme anahtarı silin.|  
|[NameChange Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|Hata ayıklayıcı, bir uygulama etki alanı veya iş parçacığı adı değiştiğini bildirir.|  
|[StepComplete Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|Hata ayıklayıcı, bir adım tamamlandığını bildirir.|  
|[UnloadAssembly Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|Hata ayıklayıcı bir CLR derlemesi kaldırıldı bildirir.|  
|[UnloadClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|Hata ayıklayıcı, bir sınıf boşaltılıyor bildirir.|  
|[UnloadModule Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|Hata ayıklayıcı bir CLR modülünü (DLL) kaldırıldı bildirir.|  
|[UpdateModuleSymbols Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|Hata ayıklayıcı bir CLR modüle ilişkin simgeleri değiştiğini bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm geri çağırmaları aynı iş parçacığında adlı, seri ve eşitlenmiş durumda işlemine çağrılır.  
  
 Her geri çağırma çağırmalı [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yürütme devam etmek için. Varsa `ICorDebugController::Continue` geri döndürür, işlem durdurulmuş kalır ve daha fazla olay geri dönüşleri kadar meydana gelir önce çağrılmaz `ICorDebugController::Continue` çağrılır.  
  
 Bir hata ayıklayıcı uygulamalıdır [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) .NET Framework sürüm 2.0 uygulamaları hata ayıklaması. Örneği `ICorDebugManagedCallback` veya `ICorDebugManagedCallback2` için geri çağırma nesnesi olarak geçirilen [Icordebug::setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
