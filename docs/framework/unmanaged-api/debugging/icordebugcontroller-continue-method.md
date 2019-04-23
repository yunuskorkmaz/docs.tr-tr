---
title: ICorDebugController::Continue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7eacffe5769bc77ab626f6adbc99db1137da565f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59146815"
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue Yöntemi
Yönetilen iş parçacıklarının yürütülmesini çağrısı yapıldıktan sonra sürdürür [Stop yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fIsOutOfBand`  
 [in] Kümesine `true` ; bir bant dışı olay devam etmesini, aksi takdirde, kümesine `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 `Continue` işlem çağrısı yapıldıktan sonra devam eder `ICorDebugController::Stop` yöntemi.  
  
 Karışık mod hata ayıklaması yaparken çağırmayın `Continue` Win32'olay iş parçacığı sürece bir bant dışı olay devam ediyoruz.  
  
 Bir *bant dışı olay* yönetilen bir olay ya da hata ayıklayıcı sırasında işlem yönetilen durumu ile etkileşimi destekleyen normal yönetilmeyen bir olay. Bu durumda, hata ayıklayıcısı alıyor [Icordebugunmanagedcallback::debugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) geri çağırmayı kendi `fOutOfBand` parametresini `false`.  
  
 Bir *bant dışı olay* sırasında işlem yönetilen durumu ile etkileşimi olan imkansız olay nedeniyle işlem durdurulurken bir yönetilmeyen olaydır. Bu durumda, hata ayıklayıcısı alıyor `ICorDebugUnmanagedCallback::DebugEvent` geri çağırmayı kendi `fOutOfBand` parametresini `true`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
