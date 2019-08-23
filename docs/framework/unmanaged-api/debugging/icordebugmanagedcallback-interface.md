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
ms.openlocfilehash: 25e40103a2925cbd2a181b8e39c3873e4d7c842c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940039"
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback Arabirimi
Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Break Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|Kod akışındaki bir <xref:System.Reflection.Emit.OpCodes.Break> yönerge yürütüldüğünde hata ayıklayıcıya bildirir.|  
|[Breakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|Bir kesme noktasıyla karşılaşıldığında hata ayıklayıcıya bildirir.|  
|[BreakpointSetError Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|Hata ayıklayıcısını, ortak dil çalışma zamanının (CLR), bir işlev tam zamanında (JıT) derlenmesinden önce ayarlanmış bir kesme noktasını doğru bir şekilde bağlamadığı hakkında bilgilendirir.|  
|[ControlCTrap Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|Hata ayıklayıcıya CTRL + C 'nin hata ayıklamakta olan işlemde yakalandığını bildirir.|  
|[CreateAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|Hata ayıklayıcıya bir uygulama etki alanının oluşturulduğunu bildirir.|  
|[CreateProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|Bir işlem ilk kez eklendiğinde veya başlatıldığında hata ayıklayıcıya bildirir.|  
|[CreateThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|Hata ayıklayıcıya bir iş parçacığının yönetilen kodu yürütmeye başlatıldığını bildirir.|  
|[DebuggerError Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|Hata ayıklayıcıya CLR 'den bir olayı işlemeye çalışırken bir hata oluştuğunu bildirir.|  
|[EditAndContinueRemap Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|Kullanım dışı. Hata ayıklayıcıya bir yeniden eşleme olayının IDE 'ye gönderildiğini bildirir.|  
|[EvalComplete Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|Hata ayıklayıcıya bir değerlendirmenin tamamlandığını bildirir.|  
|[EvalException Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|Hata ayıklayıcıya bir değerlendirmenin işlenmeyen bir özel durumla sonlandırıldığını bildirir.|  
|[Exception Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|Hata ayıklayıcıya yönetilen koddan bir özel durum gerçekleştiğini bildirir.|  
|[ExitAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|Hata ayıklayıcıya bir uygulama etki alanının çıkış olduğunu bildirir.|  
|[ExitProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|Hata ayıklayıcıya bir işlemin çıkış olduğunu bildirir.|  
|[ExitThread Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|Hata ayıklayıcıya yönetilen kodu yürüten bir iş parçacığının çıkış olduğunu bildirir.|  
|[LoadAssembly Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|Hata ayıklayıcıya bir CLR derlemesinin başarıyla yüklendiğini bildirir.|  
|[LoadClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|Bir sınıfın yüklendiğini hata ayıklayıcıya bildirir.|  
|[LoadModule Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|Hata ayıklayıcıya bir CLR modülünün başarıyla yüklendiğini bildirir.|  
|[LogMessage Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|Hata ayıklayıcıyı bir clr Managed iş parçacığının, bir olayı günlüğe kaydetmek için <xref:System.Diagnostics.EventLog> sınıfında bir yöntemi çağırdığını bildirir.|  
|[LogSwitch Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|Hata ayıklayıcıyı bir clr Managed iş parçacığının bir hata ayıklama/izleme anahtarı oluşturmak <xref:System.Diagnostics.Switch> , değiştirmek veya silmek için sınıfında bir yöntemi çağırdığını bildirir.|  
|[NameChange Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|Hata ayıklayıcıya bir uygulama etki alanı veya iş parçacığının adının değiştiğini bildirir.|  
|[StepComplete Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|Hata ayıklayıcıyı bir adımın tamamlandığını bildirir.|  
|[UnloadAssembly Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|Hata ayıklayıcıya bir CLR derlemesinin kaldırılmış olduğunu bildirir.|  
|[UnloadClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|Hata ayıklayıcıya bir sınıfın bellekten kaldırılmakta olduğunu bildirir.|  
|[UnloadModule Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|Hata ayıklayıcıya bir CLR modülü (DLL) kaldırılmış olduğunu bildirir.|  
|[UpdateModuleSymbols Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|Hata ayıklayıcıya bir CLR modülünün sembolleri değiştiğini bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm geri çağrılar aynı iş parçacığında çağrılır ve eşitlenmiş durumda işlemle birlikte çağırılır.  
  
 Her geri çağırma uygulaması [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) ' i çağırmalıdır ve yürütmeyi sürdürmelidir. Geri çağırma işlemi geri alınmadan önce çağrılmamışsa, işlem durdurulmuş olarak kalır ve çağrılana kadar `ICorDebugController::Continue` başka olay geri çağırmaları gerçekleşmeyecektir. `ICorDebugController::Continue`  
  
 Hata ayıklayıcı, sürüm 2,0 uygulamaları .NET Framework hata ayıklaması durumunda [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) uygulamalıdır. `ICorDebugManagedCallback` Veya`ICorDebugManagedCallback2` örneği [ICorDebug:: SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)öğesine geri çağırma nesnesi olarak geçirilir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
