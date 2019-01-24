---
title: ICorDebugController::IsRunning Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.IsRunning
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::IsRunning
helpviewer_keywords:
- IsRunning method [.NET Framework debugging]
- ICorDebugController::IsRunning method [.NET Framework debugging]
ms.assetid: b33ff059-40c4-4dfe-9cb2-21bfed2de0b0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd54792e37523ea5bf0c2e7a4082ee00c30d00ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496302"
---
# <a name="icordebugcontrollerisrunning-method"></a>ICorDebugController::IsRunning Yöntemi
İşlemdeki iş parçacıkları şu anda özgürce çalışıp çalışmadığını gösteren bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsRunning (  
    [out] BOOL *pbRunning  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pbRunning`  
 [out] Bir değer için bir işaretçi `true` serbestçe; Aksi takdirde, işlemdeki iş parçacıkları çalıştırıyorsanız, `false`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

