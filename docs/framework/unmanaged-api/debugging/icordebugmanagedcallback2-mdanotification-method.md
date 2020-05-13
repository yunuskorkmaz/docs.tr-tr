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
ms.openlocfilehash: f850b3cd35fda8bd554b99e14553100008cb4eca
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208531"
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
  
 Bir yönetilmeyen iş parçacığında MDA oluştuysa, değeri `pThread` null olur.  
  
 MDA nesnesinden işletim sistemi (OS) iş parçacığı KIMLIĞI almalısınız.  
  
 `pMDA`  
 'ndaki MDA bilgisini sunan bir [ICorDebugMDA](icordebugmda-interface.md) arabirimine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir MDA, buluşsal bir uyarıdır ve [ICorDebugController::](icordebugcontroller-continue-method.md) ' i çağırmak dışında herhangi bir açık hata ayıklayıcı eylemi gerektirmez ve hata ayıklanmakta olan uygulamanın yürütülmesini sürdürmek Için devam edin.  
  
 Ortak dil çalışma zamanı (CLR) hangi Mdaların tetikleyeceğini ve hangi herhangi bir MDA hangi verilerin herhangi bir noktada olduğunu tespit edebilir. Bu nedenle, hata ayıklayıcılar, belirli MDA desenleri gerektiren herhangi bir işlev derlenmemelidir.  
  
 MDAs 'ler kuyruğa alınmış ve kısa bir süre sonra da tetiklenebilir. Bunun nedeni, çalışma zamanının mda ' ı tetiklemenin bir güvenli noktaya ulaşıncaya kadar beklemesi gerekir. Ayrıca, çalışma zamanının tek bir sıraya alınmış geri çağırmalar kümesinde ("iliştirme" olay işlemine benzer) çok sayıda MDAs tetikleneceği anlamına gelir.  
  
 Hata ayıklayıcı, `ICorDebugMDA` `MDANotification` clr 'nın bir mda tarafından tüketilen belleği geri dönüştürmesini sağlamak için geri aramadan dönmeden bir örneğe başvuruyu serbest bırakmalıdır. Birçok MDAs tetikleme durumunda örneği serbest bırakmak performansı iyileştirebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2 Arabirimi](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
