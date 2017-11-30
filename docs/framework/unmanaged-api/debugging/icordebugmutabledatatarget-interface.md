---
title: ICorDebugMutableDataTarget arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef1c0b7a56f6bd1f7e87650b72dfe8b1411ef7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatarget-interface"></a>ICorDebugMutableDataTarget arabirimi
Genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) değişebilir veri hedefleri desteklemek için arabirim.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ContinueStatusChanged yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|Belirtilen iş parçacığı üzerinde bekleyen hata ayıklama olayı devamlılık durumunu değiştirir.|  
|[SetThreadContext yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|Bir iş parçacığı bağlamının (kayıt değerlerini) ayarlar.|  
|[WriteVirtual yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|Bellek, hedef işlem adres alanı yazar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu uzantı [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) arabirimi hata ayıklama (örneğin, Canlı bozucu hata ayıklama gerçekleştirmek için) hedef işlem değiştirmek istediğiniz araçları tarafından uygulanabilir.  
  
 Bu yöntemlerin tümü, bir çekirdek denetleme tabanlı hata ayıklama işlev bu arabirimini uygulayan değil veya bu yöntemlere çağrılar başarısız kayıp olduğunu herkese açık isteğe bağlıdır.  Herhangi bir hata `HRESULT` bu yöntemleri olarak kullanıma yayılır `HRESULT` Icordebug yöntemi çağrısından.  
  
 Tek bir Icordebug yöntemi çağrısı içinde birden çok mutations neden olabilir ve mutations işlemsel olarak uygulanır ilgili hiçbir mekanizması sağlamaya yönelik olduğunu unutmayın (tümü veya hiçbiri işlemini).  Bunun anlamı başkalarının (aynı Icordebug çağrısı) başarıyla tamamlandıktan sonra bir mutation başarısız olursa, hedef işlem tutarsız bir durumda kalabilir ve hata ayıklama güvenilir olmayan bir duruma gelebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
