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
ms.openlocfilehash: bf9ea40cc81be37499e6729006e7177a8000c000
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793292"
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
 'ndaki MDA bilgisini sunan bir [ICorDebugMDA](icordebugmda-interface.md) arabirimine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir MDA, buluşsal bir uyarıdır ve [ICorDebugController::](icordebugcontroller-continue-method.md) ' i çağırmak dışında herhangi bir açık hata ayıklayıcı eylemi gerektirmez ve hata ayıklanmakta olan uygulamanın yürütülmesini sürdürmek Için devam edin.  
  
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
- [ICorDebugManagedCallback2 Arabirimi](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
