---
title: ICorDebugManagedCallback2::MDANotification Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15addd0b35c43945f643386f8983fc14c9312bae
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492341"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification Yöntemi
Kod yürütmeyi ayıklanmakta olan uygulamada yönetilen hata ayıklama Yardımcısı (MDA) karşılaştı bildirim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pController`  
 [in] Bir işlem sunan Icordebugcontroller arabirimi veya MDA gerçekleştiği uygulama etki alanı için bir işaretçi.  
  
 Her zaman bir bulguyu arabirimi sorgulayabilirsiniz ancak bir hata ayıklayıcı bir işlem veya bir uygulama etki alanı denetleyicisi olup olmadığı hakkında varsayımlar yapmamalısınız.  
  
 `pThread`  
 [in] Yönetilen iş parçacığı hata ayıklama olayın gerçekleştiği kullanıma sunan bir Icordebugthread arabirimi için bir işaretçi.  
  
 MDA yönetilmeyen üzerinde oluştuysa iş parçacığı, değerini `pThread` null olacaktır.  
  
 İşletim sistemi (OS) iş parçacığı kimliği MDA nesnenin kendisini almanız gerekir.  
  
 `pMDA`  
 [in] Bir işaretçi bir [Icordebugmda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) MDA bilgileri kullanıma sunan arabirim.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir MDA buluşsal bir uyarıdır ve arama dışında herhangi bir açık hata ayıklayıcı eylem gerektirmeyen [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) ayıklanmakta olan uygulamanın yürütülmesini sürdürmek için.  
  
 Ortak dil çalışma zamanı (CLR) Mda'leri tetiklenir ve herhangi belirli MDA herhangi bir noktada hangi verilerin bulunduğu belirleyebilirsiniz. Bu nedenle, hata ayıklayıcıları belirli MDA desenleri gerektiren herhangi bir işlevsellik tasarlanmamış.  
  
 Mda'leri kuyruğa alınır ve kısa süre içinde MDA karşılaşıldıktan sonra gönderilir. Çalışma zamanı bu karşılaştığında MDA tetikleme yerine MDA tetikleme için güvenli bir noktadan ulaşana kadar beklenecek gerektiriyorsa Bu durum gerçekleşebilir. Ayrıca, çalışma zamanı sıraya alınan geri çağırmalar (bir "ekleme" olay işleme benzer) tek bir kümedeki Mda'leri birkaç yangın anlamına gelir.  
  
 Başvuru için hata ayıklayıcı serbest bırakmalısınız bir `ICorDebugMDA` döndürme hemen sonra örnek `MDANotification` bir MDA tarafından kullanılan belleği geri dönüştürmek CLR izin vermek için geri çağırma. Birçok Mda'leri tetikleme, örneği serbest performansını artırabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
