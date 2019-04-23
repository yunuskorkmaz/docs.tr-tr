---
title: CorDebugSetContextFlag Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugSetContextFlag
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugSetContextFlag
helpviewer_keywords:
- CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5754968511f7b2db48f60b99748f10f5d27e8d21
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115693"
---
# <a name="cordebugsetcontextflag-enumeration"></a>CorDebugSetContextFlag Numaralandırması
Bağlam etkin olup olmadığını belirtir (veya yaprak) çerçevesi yığın üzerinde veya başka bir çerçeveden geriye doğru izleme tarafından hesaplanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|SET_CONTEXT_FLAG_ACTIVE_FRAME|İş parçacığının etkin bağlam bağlamdır.|  
|SET_CONTEXT_FLAG_UNWIND_FRAME|Bağlamı başka bir çerçeveden geriye doğru izleme hesaplandıktan.|  
  
## <a name="remarks"></a>Açıklamalar  
 `CorDebugSetContextFlag` tarafından kullanılan değerleri sağlar [Icordebugstackwalk::setcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
