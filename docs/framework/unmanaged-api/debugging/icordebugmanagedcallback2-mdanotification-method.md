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
ms.openlocfilehash: ab3819d5c33f090fda1ca9c3dccb5d08ab8f84cc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131454"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification Yöntemi
Kod yürütmenin ayıklanmakta olan uygulamada yönetilen hata ayıklama Yardımcısı (MDA) ile karşılaştığından bildirim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pController`  
 'ndaki ICorDebugController arabirimine, MDA 'ın üzerinde oluştuğu işlem veya uygulama etki alanını sunan bir işaretçi.  
  
 Hata ayıklayıcı, denetleyicinin bir işlem veya uygulama etki alanı olup olmadığı konusunda herhangi bir varsayımda bulunmamalıdır, ancak her zaman bir belirleme yapmak üzere arabirimi sorgulayabilir.  
  
 `pThread`  
 'ndaki Hata ayıklama olayının gerçekleştiği yönetilen iş parçacığını sunan ICorDebugThread arabirimine yönelik bir işaretçi.  
  
 Bir yönetilmeyen iş parçacığında MDA oluştuysa, `pThread` değeri null olur.  
  
 MDA nesnesinden işletim sistemi (OS) iş parçacığı KIMLIĞI almalısınız.  
  
 `pMDA`  
 'ndaki MDA bilgisini sunan bir [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) arabirimine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir MDA, buluşsal bir uyarıdır ve [ICorDebugController::](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) ' i çağırmak dışında herhangi bir açık hata ayıklayıcı eylemi gerektirmez ve hata ayıklanmakta olan uygulamanın yürütülmesini sürdürmek Için devam edin.  
  
 Ortak dil çalışma zamanı (CLR) hangi Mdaların tetikleyeceğini ve hangi herhangi bir MDA hangi verilerin herhangi bir noktada olduğunu tespit edebilir. Bu nedenle, hata ayıklayıcılar, belirli MDA desenleri gerektiren herhangi bir işlev derlenmemelidir.  
  
 MDAs 'ler kuyruğa alınmış ve kısa bir süre sonra da tetiklenebilir. Bunun nedeni, çalışma zamanının mda ' ı tetiklemenin bir güvenli noktaya ulaşıncaya kadar beklemesi gerekir. Ayrıca, çalışma zamanının tek bir sıraya alınmış geri çağırmalar kümesinde ("iliştirme" olay işlemine benzer) çok sayıda MDAs tetikleneceği anlamına gelir.  
  
 Hata ayıklayıcı, CLR 'nin bir MDA tarafından tüketilen belleği geri dönüştürmesini sağlamak için `MDANotification` geri çağrısından geri dönmeden hemen sonra bir `ICorDebugMDA` örneğine başvuruyu serbest bırakmalıdır. Birçok MDAs tetikleme durumunda örneği serbest bırakmak performansı iyileştirebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
