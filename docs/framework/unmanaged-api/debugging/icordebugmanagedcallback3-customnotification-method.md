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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 098e140b7bffb7798a37b1881f2cb2ced36bcf1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416491"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a>ICorDebugManagedCallback3::CustomNotification Yöntemi
Bir özel hata ayıklayıcı bildirim yükseltildiğinde gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pThread`  
 [in] Bildirim gerçekleştirilen iş parçacığı için bir işaretçi.  
  
 `pAppDomain`  
 [in] Bildirim gerçekleştirilen iş parçacığı içeren uygulama etki alanı için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla tamamlandı.|  
  
## <a name="exceptions"></a>Özel Durumlar  
  
## <a name="remarks"></a>Açıklamalar  
 Sonraki çağrı [Icordebugthread4::getcurrentcustomdebuggernotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) yöntemi alır geçirilmedi iş parçacığı nesnesi <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> yöntemi. İş parçacığı nesnenin türü daha önce çağırarak etkinleştirilmiş olmalıdır [Icordebugprocess3::setenablecustomnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) yöntemi. Hata ayıklayıcı türüne özgü parametreler iş parçacığı nesnesi alanlardan okuyabilir ve yanıtları alanlarına depolayabilirsiniz.  
  
 [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) arabirimi bildirimleri veya içeriklerini türleri üzerinde hiçbir ilke uygular ve bildirimleri semantiği kesinlikle hata ayıklayıcıları, uygulamaları ve .NET Framework arasında bir sözleşme şunlardır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugManagedCallback3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
