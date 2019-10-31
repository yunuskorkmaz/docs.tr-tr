---
title: ICorDebugModule::IsInMemory Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
ms.openlocfilehash: 1384acff4ea3d1aa820b065cd2c56f649f0cbdbb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127920"
---
# <a name="icordebugmoduleisinmemory-method"></a>ICorDebugModule::IsInMemory Yöntemi
Bu modülün yalnızca bellekte mevcut olup olmadığını gösteren bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pInMemory`  
 [out] Bu modül yalnızca bellekte mevcutsa `true`; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR), modüllerin ham akışlarının yüklenmesini destekler. Bu tür modüller *bellek içi modüller* olarak adlandırılır ve diskte bulunmamaktadır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
