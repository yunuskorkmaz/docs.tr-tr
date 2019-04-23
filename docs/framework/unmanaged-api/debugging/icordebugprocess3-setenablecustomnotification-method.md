---
title: ICorDebugProcess3::SetEnableCustomNotification Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8c8725bf21aefa3abf5fc41366d8f983bd686b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175753"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>ICorDebugProcess3::SetEnableCustomNotification Yöntemi
Sağlar ve belirtilen türün özel hata ayıklayıcı bildirimlerini devre dışı bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pClass`  
 [in] Özel hata ayıklayıcı bildirimlerini belirten türü.  
  
 `fEnable`  
 [in] `true` ; özel hata ayıklayıcı bildirimlerini etkinleştirmek için `false` bildirimlerini devre dışı. Varsayılan değer `false` şeklindedir.  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman `fEnable` ayarlanır `true`, çağrılar <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> yöntemi tetikleyici bir [Icordebugmanagedcallback3::customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) geri çağırma. Bildirimleri varsayılan olarak devre dışıdır; Bu nedenle, hata ayıklayıcı bildiği ve işlemek istediği herhangi bir bildirim türü belirtmeniz gerekir. Çünkü [Icordebugclass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) sınıfı uygulama etki alanına göre kapsamlı, hata ayıklayıcı çağırmalıdır `SetEnableCustomNotification` tüm işlem bildirimi almak istiyorsa, işlemdeki her bir uygulama etki alanı.  
  
 İle başlayarak [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], yalnızca desteklenen bildirim iş parçacıkları arası bağımlılık bildirimi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
