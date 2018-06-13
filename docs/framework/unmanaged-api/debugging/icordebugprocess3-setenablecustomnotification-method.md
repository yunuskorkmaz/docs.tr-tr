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
ms.openlocfilehash: 2a84061cff7cc5dbdeba1e0e66396e04a8f345cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423162"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>ICorDebugProcess3::SetEnableCustomNotification Yöntemi
Belirtilen türün özel hata ayıklayıcı bildirimleri devre dışı bırakır ve sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pClass`  
 [in] Özel hata ayıklayıcı bildirimleri belirtir türü.  
  
 `fEnable`  
 [in] `true` özel hata ayıklayıcı bildirimlerini; etkinleştirmek için `false` bildirimleri devre dışı bırakmak için. Varsayılan değer `false` şeklindedir.  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman `fEnable` ayarlanır `true`, çağrılar <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> yöntemi tetikleyici bir [Icordebugmanagedcallback3::customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) geri çağırma. Bildirimler, varsayılan olarak devre dışıdır; Bu nedenle, hata ayıklayıcı bildiği ve işlemek istediği her bildirim türünü belirtmeniz gerekir. Çünkü [Icordebugclass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) sınıfı uygulama etki alanı tarafından kapsamlı, hata ayıklayıcı çağırmalısınız `SetEnableCustomNotification` sürecinin tamamı bildirim almak istiyorsa, işlemdeki her uygulama etki alanı için.  
  
 İle başlayarak [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], yalnızca desteklenen bildirim iş parçacıkları arası bağımlılık bildirimi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugProcess3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
