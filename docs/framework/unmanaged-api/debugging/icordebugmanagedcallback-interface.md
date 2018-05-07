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
ms.openlocfilehash: 6c879af682e2d54ed3ae1e9821c0bd85b5cac27d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback Arabirimi
Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Break Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|Hata ayıklayıcı bildirir, bir <xref:System.Reflection.Emit.OpCodes.Break> yönerge kodu akışında gerçekleştirilir.|  
|[Breakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|Bir kesme noktası karşılaştı, hata ayıklayıcı size bildirir.|  
|[BreakpointSetError Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|Hata ayıklayıcı ortak dil çalışma zamanı (CLR) doğru sadece derlenmiş zamanında (JIT) bir işlevi olan önce bu ayarlanan bir kesme noktası bağlayamadı olduğunu bildirir.|  
|[ControlCTrap Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|Hata ayıklayıcı CTRL + C ayıklanacak işleminde yakalanır bildirir.|  
|[CreateAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|Hata ayıklayıcı uygulama etki alanı oluşturulduğunu size bildirir.|  
|[CreateProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|Bir işlem bağlı veya için ilk kez başlatıldığında, hata ayıklayıcı size bildirir.|  
|[CreateThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|Hata ayıklayıcı bir iş parçacığı yönetilen kod yürütmeyi başlattı bildirir.|  
|[DebuggerError Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|Bir CLR olayından işlemeye çalışırken bir hata oluştu hata ayıklayıcı bildirir.|  
|[EditAndContinueRemap Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|Kullanım dışı. Hata ayıklayıcı eşleme olay IDE gönderildi bildirir.|  
|[EvalComplete Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|Hata ayıklayıcı değerlendirme tamamlandığını bildirir.|  
|[EvalException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|Hata ayıklayıcı işlenmeyen bir özel durum ile bir değerlendirme sonlandırıldı bildirir.|  
|[Exception Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|Hata ayıklayıcı yönetilen koddan bir özel durum olduğunu bildirir.|  
|[ExitAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|Hata ayıklayıcı uygulama etki alanı yaptı bildirir.|  
|[ExitProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|Hata ayıklayıcı işlem yaptı bildirir.|  
|[ExitThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|Hata ayıklayıcı yönetilen kod yürütülmekte olan bir iş parçacığı yaptı bildirir.|  
|[LoadAssembly Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|Hata ayıklayıcı CLR derlemesinde başarıyla yüklendi olduğunu bildirir.|  
|[LoadClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|Hata ayıklayıcı bir sınıf yüklü olduğunu bildirir.|  
|[LoadModule Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|Hata ayıklayıcı CLR modülü başarıyla yüklendi bildirir.|  
|[LogMessage Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|Hata ayıklayıcı yönetilen CLR iş parçacığı bir yöntem çağırdı olduğunu bildirir <xref:System.Diagnostics.EventLog> sınıfı bir olayı günlüğe kaydedin.|  
|[LogSwitch Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|Hata ayıklayıcı yönetilen CLR iş parçacığı bir yöntem çağırdı olduğunu bildirir <xref:System.Diagnostics.Switch> sınıfı oluşturmak, değiştirmek veya bir hata ayıklama izleme anahtarı silin.|  
|[NameChange Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|Hata ayıklayıcı uygulama etki alanı veya iş parçacığı adı değiştiğini bildirir.|  
|[StepComplete Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|Hata ayıklayıcı bir adım tamamlandığını bildirir.|  
|[UnloadAssembly Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|Hata ayıklayıcı CLR derlemesinde kaldırıldı bildirir.|  
|[UnloadClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|Hata ayıklayıcı bir sınıf yüklenmemiş olduğunu bildirir.|  
|[UnloadModule Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|Hata ayıklayıcı CLR Modülü (DLL) kaldırıldı bildirir.|  
|[UpdateModuleSymbols Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|Hata ayıklayıcı CLR modülü simgelerini değişmiş bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm geri aramalar iş parçacığında adlı, serileştirilen ve eşitlenmiş durumda işlemine çağrılır.  
  
 Her geri çağırma çağırmalı [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yürütme devam etmek için. Varsa `ICorDebugController::Continue` geri döndürür, işlem durdurulmuş kalır ve daha fazla hiçbir olay geri aramalar kadar ortaya çıkar önce çağrılmaz `ICorDebugController::Continue` olarak adlandırılır.  
  
 Bir hata ayıklayıcısı uygulamalıdır [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) .NET Framework sürüm 2.0 uygulamalarında hata ayıklama durumunda. Örneği `ICorDebugManagedCallback` veya `ICorDebugManagedCallback2` geri çağırma nesnesi olarak geçirilen [Icordebug::setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
