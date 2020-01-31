---
title: ICorDebugMutableDataTarget Arabirimi
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: e4601c24194404f943c8de8f320bf704efcc553e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792852"
---
# <a name="icordebugmutabledatatarget-interface"></a>ICorDebugMutableDataTarget Arabirimi
[ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini, değişebilir veri hedeflerini destekleyecek şekilde genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ContinueStatusChanged Yöntemi](icordebugmutabledatatarget-continuestatuschanged-method.md)|Belirtilen iş parçacığında bekleyen hata ayıklama olayının devamlılık durumunu değiştirir.|  
|[SetThreadContext Yöntemi](icordebugmutabledatatarget-setthreadcontext-method.md)|Bir iş parçacığının bağlamını (kayıt değerlerini) ayarlar.|  
|[WriteVirtual Yöntemi](icordebugmutabledatatarget-writevirtual-method.md)|Belleği hedef işlem adres alanına yazar.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimine olan bu uzantı, hedef işlemi değiştirmek isteyen hata ayıklama araçlarıyla (örneğin, canlı bir hata ayıklama işlemi gerçekleştirmek için) uygulanabilir.  
  
 Bu yöntemlerin hepsi, bu arabirimi uygulamayarak veya bu yöntemlere yapılan çağrılar başarısız olmadan hiçbir çekirdek İnceleme tabanlı hata ayıklama işlevinin kaybedilmediğinden emin olmak için isteğe bağlıdır.  Bu yöntemlerden herhangi bir hata `HRESULT`, ICorDebug yöntemi çağrısından `HRESULT` olarak yayılır.  
  
 Tek bir ICorDebug yöntemi çağrısının birden çok mutasyonda neden olabileceğini ve ilgili mutasyonların işlem için (tümü-veya-hiçbiri) uygulanmasını sağlamak için hiçbir mekanizma olmadığını unutmayın.  Bu, diğerleri (aynı ICorDebug çağrısı için) başarılı olduktan sonra başarısız olursa, hedef işlem tutarsız bir durumda kalabilir ve hata ayıklama güvenilir hale gelebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
