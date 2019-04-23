---
title: ICorDebugValue3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 300d2263c076c9028340863e2f7a3fa27a36ef9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221983"
---
# <a name="icordebugvalue3-interface"></a>ICorDebugValue3 Arabirimi
2 GB'den daha büyük diziler için destek sağlamak için "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetSize64 Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|Bu bayt cinsinden boyutunu alır `ICorDebugValue3` nesne.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Icordebugvalue::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) yöntemi 2.147.483.647 bayt 0'dan aralıkları bir nesne boyutu döndürür. İçinde [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], dizi boyutu 2 GB aşabilir. `ICorDebugValue3` Arabirimi bu dizileri boyutunu belirlemek etkinleştirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
