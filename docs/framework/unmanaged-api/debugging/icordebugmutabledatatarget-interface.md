---
title: ICorDebugMutableDataTarget Arabirimi
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8b33b07e7c9f83f5874dea1455cd70dcc3206de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942434"
---
# <a name="icordebugmutabledatatarget-interface"></a>ICorDebugMutableDataTarget Arabirimi
Genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) değişebilir veri hedefleri desteklemek için arabirim.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ContinueStatusChanged Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|Belirtilen iş parçacığı üzerinde bekleyen hata ayıklama olayı için devamlılık durumu değişir.|  
|[SetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|Bir iş parçacığı bağlamı (yazmaç değerlerini) ayarlar.|  
|[WriteVirtual Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|Bellek, hedef işlemin adres alanına yazar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu uzantı için [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) arabirimi hata ayıklama (örneğin, Canlı bozucu hata ayıklama gerçekleştirmek için) hedef işlem değiştirmek istediğiniz araçları tarafından uygulanabilir.  
  
 Bu yöntemlerin tümü, hiçbir çekirdek denetleme tabanlı hata ayıklama işlevselliğini bu arabirimi uygulayan değil veya bu yöntemlere yapılan çağrılar başarısız kaybolmadığı algılama isteğe bağlıdır.  Herhangi bir hata `HRESULT` bu yöntemleri olarak kullanıma yayılır `HRESULT` Icordebug yöntem çağrısından.  
  
 Tek bir Icordebug yöntemi çağrısı birden çok mutations neden olabilir ve sağlamaya yönelik bir mekanizma bulunmamaktadır mutations işlemsel olarak uygulandığını ilgili not (tümü veya hiçbiri işlemini).  Başka bir deyişle, diğerleri (için aynı Icordebug çağrısı) başarıyla tamamlandıktan sonra bir Mutasyon başarısız olursa, hedef işlem tutarsız bir durumda kalabilir ve hata ayıklama güvenilir olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
