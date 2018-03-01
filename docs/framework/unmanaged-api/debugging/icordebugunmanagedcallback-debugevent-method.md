---
title: "ICorDebugUnmanagedCallback::DebugEvent Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 49c3386fcda0bc731935ec9db7d029d0e619ef14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>ICorDebugUnmanagedCallback::DebugEvent Yöntemi
Hata ayıklayıcı yerel olay harekete olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pDebugEvent`  
 [in] Yerel olay için bir işaretçi.  
  
 `fOutOfBand`  
 [in] `true`, yönetilmeyen bir olay gerçekleşene kadar hata ayıklayıcı çağrıları yönetilen işlem durumu ile etkileşimi mümkün değildir, [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); Aksi halde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Ayıklanacak iş parçacığı bir Win32 iş parçacığı ise arabirimi hata ayıklama tüm üyeleri Win32 kullanmayın. Çağırabilirsiniz `ICorDebugController::Continue` yalnızca bir iş parçacığında Win32 ve yalnızca bir bant dışı olay etmeden.  
  
 `DebugEvent` Geri çağırma geri aramalar için standart kuralları izleyin değil. Çağırdığınızda `DebugEvent`işlemi ham olacaktır, işletim sistemi hata ayıklama durduruldu durumu. İşlem eşitlenmeyecek. Otomatik olarak diğer iç içe geçmiş sonuçlanabilir yönetilen kodu hakkında bilgi için istekleri karşılamak için gerekli olduğunda eşitlenmiş durumuna girer `DebugEvent` geri aramalar.  
  
 Çağrı [Icordebugprocess::clearcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) işleme işlemi devam etmeden önce bir özel durum olayı yoksay. Bu yöntemi çağırmadan DBG_EXCEPTION_NOT_HANDLED yerine DBG_CONTINUE devam isteği gönderir ve bant dışı kesme noktaları ve tek adımlı özel durumları otomatik olarak temizler. Bant dışı olayları herhangi bir zamanda bile ayıklanacak uygulama durdurulmuş görüntülendiğinde ve bekleyen bant dışı olaya zaten mevcut olduğunda gelebilir.  
  
 .NET Framework sürüm 2. 0'da, hata ayıklayıcı hemen bir bant dışı kesme noktası olay devam etmelidir. Hata ayıklayıcıyı kullanma [Icordebugprocess2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) ve [Icordebugprocess2::clearunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) yöntemleri eklemek ve kesme noktaları kaldırmak için. Bu yöntemler tüm bant dışı kesme noktaları otomatik olarak atlar. Bu nedenle, dağıtılan yalnızca-bant kesme noktaları Win32 çağrısı gibi yönerge akış zaten bulunan ham kesme noktaları olmalıdır `DebugBreak` işlevi. Kullanmaya çalışmayın `ICorDebugProcess::ClearCurrentException`, [Icordebugprocess::getthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [Icordebugprocess::setthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), veya diğer herhangi bir üyenin [hata ayıklama API'si](../../../../docs/framework/unmanaged-api/debugging/index.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugUnmanagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
