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
ms.openlocfilehash: 9a33b90bf39103756ab4fd07157739633997fb61
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788392"
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback Arabirimi
Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Break Yöntemi](icordebugmanagedcallback-break-method.md)|Kod akışındaki bir <xref:System.Reflection.Emit.OpCodes.Break> yönerge yürütüldüğünde hata ayıklayıcıya bildirir.|  
|[Breakpoint Yöntemi](icordebugmanagedcallback-breakpoint-method.md)|Bir kesme noktasıyla karşılaşıldığında hata ayıklayıcıya bildirir.|  
|[BreakpointSetError Yöntemi](icordebugmanagedcallback-breakpointseterror-method.md)|Hata ayıklayıcısını, ortak dil çalışma zamanının (CLR), bir işlev tam zamanında (JıT) derlenmesinden önce ayarlanmış bir kesme noktasını doğru bir şekilde bağlamadığı hakkında bilgilendirir.|  
|[ControlCTrap Yöntemi](icordebugmanagedcallback-controlctrap-method.md)|Hata ayıklayıcıya CTRL + C 'nin hata ayıklamakta olan işlemde yakalandığını bildirir.|  
|[CreateAppDomain Yöntemi](icordebugmanagedcallback-createappdomain-method.md)|Hata ayıklayıcıya bir uygulama etki alanının oluşturulduğunu bildirir.|  
|[CreateProcess Yöntemi](icordebugmanagedcallback-createprocess-method.md)|Bir işlem ilk kez eklendiğinde veya başlatıldığında hata ayıklayıcıya bildirir.|  
|[CreateThread Yöntemi](icordebugmanagedcallback-createthread-method.md)|Hata ayıklayıcıya bir iş parçacığının yönetilen kodu yürütmeye başlatıldığını bildirir.|  
|[DebuggerError Yöntemi](icordebugmanagedcallback-debuggererror-method.md)|Hata ayıklayıcıya CLR 'den bir olayı işlemeye çalışırken bir hata oluştuğunu bildirir.|  
|[EditAndContinueRemap Yöntemi](icordebugmanagedcallback-editandcontinueremap-method.md)|Kullanım dışı. Hata ayıklayıcıya bir yeniden eşleme olayının IDE 'ye gönderildiğini bildirir.|  
|[EvalComplete Yöntemi](icordebugmanagedcallback-evalcomplete-method.md)|Hata ayıklayıcıya bir değerlendirmenin tamamlandığını bildirir.|  
|[EvalException Yöntemi](icordebugmanagedcallback-evalexception-method.md)|Hata ayıklayıcıya bir değerlendirmenin işlenmeyen bir özel durumla sonlandırıldığını bildirir.|  
|[Exception Yöntemi](icordebugmanagedcallback-exception-method.md)|Hata ayıklayıcıya yönetilen koddan bir özel durum gerçekleştiğini bildirir.|  
|[ExitAppDomain Yöntemi](icordebugmanagedcallback-exitappdomain-method.md)|Hata ayıklayıcıya bir uygulama etki alanının çıkış olduğunu bildirir.|  
|[ExitProcess Yöntemi](icordebugmanagedcallback-exitprocess-method.md)|Hata ayıklayıcıya bir işlemin çıkış olduğunu bildirir.|  
|[ExitThread Yöntemi](icordebugmanagedcallback-exitthread-method.md)|Hata ayıklayıcıya yönetilen kodu yürüten bir iş parçacığının çıkış olduğunu bildirir.|  
|[LoadAssembly Yöntemi](icordebugmanagedcallback-loadassembly-method.md)|Hata ayıklayıcıya bir CLR derlemesinin başarıyla yüklendiğini bildirir.|  
|[LoadClass Yöntemi](icordebugmanagedcallback-loadclass-method.md)|Bir sınıfın yüklendiğini hata ayıklayıcıya bildirir.|  
|[LoadModule Yöntemi](icordebugmanagedcallback-loadmodule-method.md)|Hata ayıklayıcıya bir CLR modülünün başarıyla yüklendiğini bildirir.|  
|[LogMessage Yöntemi](icordebugmanagedcallback-logmessage-method.md)|Hata ayıklayıcıyı bir CLR Managed iş parçacığının, bir olayı günlüğe kaydetmek için <xref:System.Diagnostics.EventLog> sınıfında bir yöntemi çağırdığını bildirir.|  
|[LogSwitch Yöntemi](icordebugmanagedcallback-logswitch-method.md)|Hata ayıklayıcıyı bir CLR Managed iş parçacığının bir hata ayıklama/izleme anahtarı oluşturmak, değiştirmek veya silmek için <xref:System.Diagnostics.Switch> sınıfında bir yöntemi çağırdığını bildirir.|  
|[NameChange Yöntemi](icordebugmanagedcallback-namechange-method.md)|Hata ayıklayıcıya bir uygulama etki alanı veya iş parçacığının adının değiştiğini bildirir.|  
|[StepComplete Yöntemi](icordebugmanagedcallback-stepcomplete-method.md)|Hata ayıklayıcıyı bir adımın tamamlandığını bildirir.|  
|[UnloadAssembly Yöntemi](icordebugmanagedcallback-unloadassembly-method.md)|Hata ayıklayıcıya bir CLR derlemesinin kaldırılmış olduğunu bildirir.|  
|[UnloadClass Yöntemi](icordebugmanagedcallback-unloadclass-method.md)|Hata ayıklayıcıya bir sınıfın bellekten kaldırılmakta olduğunu bildirir.|  
|[UnloadModule Yöntemi](icordebugmanagedcallback-unloadmodule-method.md)|Hata ayıklayıcıya bir CLR modülü (DLL) kaldırılmış olduğunu bildirir.|  
|[UpdateModuleSymbols Yöntemi](icordebugmanagedcallback-updatemodulesymbols-method.md)|Hata ayıklayıcıya bir CLR modülünün sembolleri değiştiğini bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tüm geri çağrılar aynı iş parçacığında çağrılır ve eşitlenmiş durumda işlemle birlikte çağırılır.  
  
 Her geri çağırma uygulaması [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) ' i çağırmalıdır ve yürütmeyi sürdürmelidir. Geri çağırma işlemi geri alınmadan önce `ICorDebugController::Continue` çağrılmamışsa, işlem durdurulmuş olarak kalır ve `ICorDebugController::Continue` çağrılana kadar başka olay geri çağırmaları gerçekleşmeyecektir.  
  
 Hata ayıklayıcı, sürüm 2,0 uygulamaları .NET Framework hata ayıklaması durumunda [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) uygulamalıdır. Bir `ICorDebugManagedCallback` veya `ICorDebugManagedCallback2` örneği [ICorDebug:: SetManagedHandler](icordebug-setmanagedhandler-method.md)öğesine geri çağırma nesnesi olarak geçirilir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](icordebug-interface.md)
- [ICorDebugManagedCallback2 Arabirimi](icordebugmanagedcallback2-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
