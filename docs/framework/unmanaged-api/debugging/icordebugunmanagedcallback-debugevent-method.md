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
ms.openlocfilehash: 24c316ea6bab11fb55e8e0fc1dc9832a312dbc6a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397191"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>ICorDebugUnmanagedCallback::DebugEvent Yöntemi
Hata ayıklayıcıyı yerel bir olayın harekete geçirildiğinde bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pDebugEvent`  
 'ndaki Yerel olaya yönelik bir işaretçi.  
  
 `fOutOfBand`  
 [in] `true` yönetilmeyen bir olay oluştuktan sonra yönetilen işlem durumu ile etkileşim varsa, hata ayıklayıcı [ICorDebugController:: Continue](icordebugcontroller-continue-method.md); Aksi takdirde, `false` .  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklanmakta olan iş parçacığı bir Win32 iş parçacığı ise, Win32 hata ayıklama arabiriminin herhangi bir üyesini kullanmayın. `ICorDebugController::Continue`Yalnızca bir Win32 iş parçacığı üzerinde ve yalnızca bant dışı bir olayı geçmiş olduğunda çağırabilirsiniz.  
  
 `DebugEvent`Geri çağırmalar, geri aramalar için standart kuralları uygulamaz. `DebugEvent`' İ çağırdığınızda, işlem ham, işletim sistemi-hata ayıklama durdurulmuş durumda olur. İşlem eşitlenmez. Yönetilen kod hakkında bilgi isteklerini karşılamak için gerektiğinde otomatik olarak eşitlenmiş duruma girer, bu da diğer iç içe çağrılar ile sonuçlanabilir `DebugEvent` .  
  
 İşleme devam etmeden önce bir özel durum olayını yok saymak için [ICorDebugProcess:: ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) ' i çağırın. Bu yöntemin çağrılması devam isteğinde DBG_EXCEPTION_NOT_HANDLED yerine DBG_CONTINUE gönderir ve bant dışı kesme noktalarını ve tek adımlı özel durumları otomatik olarak temizler. Bant dışı olaylar herhangi bir zamanda, hata ayıklamakta olan uygulama durdurulduğunda ve bekleyen bant içi bir olay zaten mevcut olduğunda bile gelebilir.  
  
 .NET Framework sürüm 2,0 ' de, hata ayıklayıcı hemen bir bant dışı kesme noktası olayını geçmiş olarak devam etmelidir. Hata ayıklayıcı, kesme noktaları eklemek ve kaldırmak için [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) ve [ICorDebugProcess2:: ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) yöntemlerini kullanıyor olmalıdır. Bu yöntemler, tüm bant dışı kesme noktalarını otomatik olarak atlar. Bu nedenle, gönderilen tek bant dışı kesme noktaları, bir Win32 işlevine çağrı gibi, zaten yönerge akışında olan ham kesme noktaları olmalıdır `DebugBreak` . `ICorDebugProcess::ClearCurrentException` [ICorDebugProcess:: GetThreadContext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess:: SetThreadContext](icordebugprocess-setthreadcontext-method.md)veya [hata ayıklama API](index.md)'sinin başka bir üyesini kullanmayı denemeyin.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugUnmanagedCallback Arabirimi](icordebugunmanagedcallback-interface.md)
