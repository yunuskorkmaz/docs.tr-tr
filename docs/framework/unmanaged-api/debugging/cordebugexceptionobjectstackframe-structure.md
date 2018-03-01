---
title: "CorDebugExceptionObjectStackFrame Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugExceptionObjectStackFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionObjectStackFrame
helpviewer_keywords:
- CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f2d3f0d0c17c0fdf8b772ba38ae97fd8e406be8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugexceptionobjectstackframe-structure"></a>CorDebugExceptionObjectStackFrame Yapısı
Bir özel durum nesnesi çerçeve bilgilerini temsil yığın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`pModule`|Geçerli çerçevenin Icordebugmodule nesnesine bir işaretçi.|  
|`ip`|Geçerli çerçevenin yönerge işaretçisi (EIP/RIP) değeri.|  
|`methodDef`|Geçerli çerçevenin yöntemi belirteci.|  
|`isLastForeignExceptionFrame`|Çerçeve bir yabancı özel son çerçevede olup olmadığını belirten bir değer.|  
  
## <a name="remarks"></a>Açıklamalar  
 Artık kullanımda olduğunda arayan Icordebugmodule nesnesine işaretçi serbest bırakmanız gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
