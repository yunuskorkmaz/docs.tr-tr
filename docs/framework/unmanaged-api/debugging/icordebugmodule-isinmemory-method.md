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
ms.openlocfilehash: 637cac67e73d38aca0fdc5eaeae5405c4a859aa3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709823"
---
# <a name="icordebugmoduleisinmemory-method"></a>ICorDebugModule::IsInMemory Yöntemi

Bu modülün yalnızca bellekte mevcut olup olmadığını gösteren bir değer alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pInMemory`  
 [out] `true` Bu modül yalnızca bellekte mevcutsa; Aksi takdirde, `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 Ortak dil çalışma zamanı (CLR), modüllerin ham akışlarının yüklenmesini destekler. Bu tür modüller *bellek içi modüller* olarak adlandırılır ve diskte bulunmamaktadır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
