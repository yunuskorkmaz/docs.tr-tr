---
title: "ICorDebugManagedCallback2::MDANotification Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.MDANotification
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aeddab575f6667dbd27ab3474ae9c6e00dd05750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification Yöntemi
Kod yürütmeyi ayıklanacak uygulamasında yönetilen hata ayıklama Yardımcısı (MDA) karşılaştı bildirim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pController`  
 [in] Bir işlem sunan Icordebugcontroller arabirimi veya MDA oluştuğu uygulama etki alanı için bir işaretçi.  
  
 Her zaman bir belirlenmesi için arabirimi sorgulayabilirsiniz olsa da bir hata ayıklayıcısı bir işlem veya bir uygulama etki alanı denetleyici olup olmadığına dair varsayımlar yapmamalısınız.  
  
 `pThread`  
 [in] Hata ayıklama olayın oluştuğu yönetilen iş parçacığı kullanıma sunan bir Icordebugthread arabirimi için bir işaretçi.  
  
 MDA yönetilmeyen üzerinde oluştuysa iş parçacığı, değeri `pThread` null olur.  
  
 İşletim sistemi (OS) iş parçacığı kimliği MDA nesnesinin kendisi almanız gerekir.  
  
 `pMDA`  
 [in] Bir işaretçi bir [Icordebugmda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) MDA bilgi kullanıma sunan arabirim.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir MDA buluşsal bir uyarıdır ve arama dışında herhangi bir açık hata ayıklayıcı eylem gerektirmez [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) ayıklanacak uygulamanın yürütülmesini sürdürmek için.  
  
 Ortak dil çalışma zamanı (CLR) Mda'lar tetiklenir ve herhangi bir noktada verilen tüm MDA hangi verilerin bulunduğu belirleyebilirsiniz. Bu nedenle, hata ayıklayıcıları belirli MDA desenleri gerektiren herhangi bir işlevsellik oluşturup değil.  
  
 Mda'lar sıraya alındı ve kısa süre içinde MDA karşılaştı sonra gönderilir. Çalışma zamanı bu karşılaştığında MDA tetikleme yerine MDA tetikleme için güvenli bir noktası ulaşana kadar bekleyin gerekiyorsa, bu durum oluşabilir. Ayrıca, çalışma zamanı numarasında sıraya alınan geri aramalar ("Ekle" olay işlem için benzer) tek bir dizi Mda'lar yangın anlamına gelir.  
  
 Bir hata ayıklayıcısı referansı serbest bırakmalısınız bir `ICorDebugMDA` döndürme hemen sonra örneği `MDANotification` bir MDA tarafından tüketilen bellek geri dönüştürmek CLR izin vermek için geri çağırma. Birçok Mda'lar tetikleme varsa örnek serbest performansını artırabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Icordebugmanagedcallback2 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [Icordebugmanagedcallback arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
