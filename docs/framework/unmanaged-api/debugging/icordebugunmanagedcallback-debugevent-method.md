---
title: ICorDebugUnmanagedCallback::DebugEvent Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ec45004f5dd87983187690a0a4feefb35b05e85
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748961"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>ICorDebugUnmanagedCallback::DebugEvent Yöntemi
Hata ayıklayıcı, yerel bir olay harekete bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pDebugEvent`  
 [in] Yerel olay için bir işaretçi.  
  
 `fOutOfBand`  
 [in] `true`yönetilmeyen bir olay gerçekleşene kadar hata ayıklayıcı çağrıları yönetilen işlem durumu etkileşim mümkün değildir, [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); Aksi takdirde `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Hatası ayıklanmakta olan iş parçacığı bir Win32 iş parçacığı, arabirimi hata ayıklama Win32 üyelerinin kullanmayın. Çağırabilirsiniz `ICorDebugController::Continue` Win32 iş parçacığı üzerinde yalnızca ve yalnızca bir bant dışı olay devam.  
  
 `DebugEvent` Geri çağırma geri çağırmaları standart kurallarını izleyin değil. Çağırdığınızda `DebugEvent`işlem ham olması, işletim sistemi hata ayıklama durumunu durduruldu. İşlem eşitlenmez. Eşitlenmiş durum iç içe geçmiş diğer sonuçlanabilir yönetilen kodu hakkında bilgi için isteklerini karşılamak için gerekli olduğunda otomatik olarak girer `DebugEvent` geri çağırmalar.  
  
 Çağrı [Icordebugprocess::clearcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) işlemi devam etmeden önce bir özel durum olayı yok saymak için işlem. Bu yöntemin çağrılması DBG_CONTINUE DBG_EXCEPTION_NOT_HANDLED yerine devam isteği gönderir ve bant dışı kesme noktaları ve tek adımlı özel durumları otomatik olarak temizler. Bant dışı olayları, hatta ayıklanan uygulamayı durdurulmuş göründüğünde ve bekleyen bir bant dışı olay zaten mevcut olduğunda herhangi bir zamanda gelebilir.  
  
 .NET Framework 2.0 sürümünde, hata ayıklayıcının hemen bir bant dışı kesme noktası olayı devam etmelidir. Hata ayıklayıcıyı kullanma [Icordebugprocess2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) ve [Icordebugprocess2::clearunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) eklemek ve kesme noktaları kaldırmak için yöntemleri. Bu yöntemlerin herhangi bir bant dışı kesme noktası otomatik olarak atlar. Bu nedenle, dağıtılan yalnızca-bant kesme noktaları yönerge stream'de bir çağrı Win32 gibi zaten olan ham kesme noktaları olmalıdır `DebugBreak` işlevi. Kullanmaya çalışmayın `ICorDebugProcess::ClearCurrentException`, [Icordebugprocess::getthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [Icordebugprocess::setthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), veya diğer herhangi bir üyesi [hata ayıklama API'si](../../../../docs/framework/unmanaged-api/debugging/index.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugUnmanagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
