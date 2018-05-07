---
title: ICorDebugMutableDataTarget arabirimi
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 677db647320ff4014b791502b7ac1b261378c8dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmutabledatatarget-interface"></a>ICorDebugMutableDataTarget arabirimi
Genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) değişebilir veri hedefleri desteklemek için arabirim.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ContinueStatusChanged Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|Belirtilen iş parçacığı üzerinde bekleyen hata ayıklama olayı devamlılık durumunu değiştirir.|  
|[SetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|Bir iş parçacığı bağlamının (kayıt değerlerini) ayarlar.|  
|[WriteVirtual Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|Bellek, hedef işlem adres alanı yazar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu uzantı [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) arabirimi hata ayıklama (örneğin, Canlı bozucu hata ayıklama gerçekleştirmek için) hedef işlem değiştirmek istediğiniz araçları tarafından uygulanabilir.  
  
 Bu yöntemlerin tümü, bir çekirdek denetleme tabanlı hata ayıklama işlev bu arabirimini uygulayan değil veya bu yöntemlere çağrılar başarısız kayıp olduğunu herkese açık isteğe bağlıdır.  Herhangi bir hata `HRESULT` bu yöntemleri olarak kullanıma yayılır `HRESULT` Icordebug yöntemi çağrısından.  
  
 Tek bir Icordebug yöntemi çağrısı içinde birden çok mutations neden olabilir ve mutations işlemsel olarak uygulanır ilgili hiçbir mekanizması sağlamaya yönelik olduğunu unutmayın (tümü veya hiçbiri işlemini).  Bunun anlamı başkalarının (aynı Icordebug çağrısı) başarıyla tamamlandıktan sonra bir mutation başarısız olursa, hedef işlem tutarsız bir durumda kalabilir ve hata ayıklama güvenilir olmayan bir duruma gelebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
