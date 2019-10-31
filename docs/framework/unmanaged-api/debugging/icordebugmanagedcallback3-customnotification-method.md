---
title: ICorDebugManagedCallback3::CustomNotification Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
ms.openlocfilehash: 83192fd2d24e740ab470988531db823b34df4494
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131433"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a>ICorDebugManagedCallback3::CustomNotification Yöntemi
Özel bir hata ayıklayıcı bildiriminin yapıldığını gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pThread`  
 'ndaki Bildirimi oluşturan iş parçacığına yönelik bir işaretçi.  
  
 `pAppDomain`  
 'ndaki Bildirimi oluşturan iş parçacığını içeren uygulama etki alanına yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 [ICorDebugThread4:: GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) yöntemine sonraki bir çağrı, <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> metoduna geçirilen iş parçacığı nesnesini alır. İş parçacığı nesnesinin türü, [ICorDebugProcess3:: SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) yöntemi çağırarak önceden etkinleştirilmiş olmalıdır. Hata ayıklayıcı, iş parçacığı nesnesi alanlarından türe özgü parametreleri okuyabilir ve yanıtları alanlara depolayabilirler.  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) arabirimi, bildirim türleri veya içerikleri üzerinde hiçbir ilke vermez ve bildirimlerin semantiği, hata ayıklayıcılar, uygulamalar ve .NET Framework arasındaki bir anlaşmada yer alır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugManagedCallback3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
