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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d79a8b0c3c56ffe2b8f57ec26f5942ee0d681194
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187596"
---
# <a name="icordebugmoduleisinmemory-method"></a>ICorDebugModule::IsInMemory Yöntemi
Bu modül yalnızca bellekte var olup olmadığını belirten bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pInMemory`  
 [out] `true` varsa bu modül bellekte yalnızca; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Ortak dil çalışma zamanı (CLR), ham bayt akışlarında modüllerden yüklenmesini destekler. Bu modül çağrılır *bellek içi modülleri* ve disk üzerinde mevcut değildir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
