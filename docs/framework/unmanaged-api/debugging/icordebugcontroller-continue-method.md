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
ms.openlocfilehash: 529a65285203ac831e1bcab9dc1bea69ac28a282
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412571"
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue Yöntemi
Yönetilen iş parçacığı yürütülmesi için bir çağrı sonra sürdürür [Stop yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `fIsOutOfBand`  
 [in] Kümesine `true` bir bant dışı olayından; etmeden, aksi takdirde kümesine `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 `Continue` Çağrı sonra işlemine devam `ICorDebugController::Stop` yöntemi.  
  
 Karışık mod hata ayıklaması yaparken çağırmayın `Continue` Win32'olay iş parçacığı sürece bir bant dışı olayından devam ediliyor.  
  
 Bir *bant dışı olay* yönetilen bir olay ya da normal bir yönetilmeyen olay hata ayıklayıcı sırasında işlem yönetilen durumu ile etkileşimi destekler. Bu durumda, hata ayıklayıcısı alıyor [Icordebugunmanagedcallback::debugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) geri çağırmayı kendi `fOutOfBand` parametre kümesine `false`.  
  
 Bir *bant dışı olay* sırasında işleminin yönetilen durumunu etkileşim olduğu imkansız işlem olayı nedeniyle durdurulurken bir yönetilmeyen olaydır. Bu durumda, hata ayıklayıcısı alıyor `ICorDebugUnmanagedCallback::DebugEvent` geri çağırmayı kendi `fOutOfBand` parametre kümesine `true`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
