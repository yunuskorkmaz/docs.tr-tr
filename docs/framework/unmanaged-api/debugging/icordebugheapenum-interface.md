---
title: ICorDebugHeapEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
ms.openlocfilehash: e8d1948a7d0ff23410ba8670628424a4067fb47d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138494"
---
# <a name="icordebugheapenum-interface"></a>ICorDebugHeapEnum Arabirimi
Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar. Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|Yönetilen yığında nesneler hakkında bilgi içeren, belirtilen [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örnek sayısını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugHeapEnum` arabirimi ıcorı, Genum arabirimini uygular.  
  
 `ICorDebugHeapEnum` örneği, [ICorDebugProcess5:: EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) yöntemi çağırarak [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örnekleriyle doldurulur. Koleksiyondaki her bir [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örneği, yığında canlı bir nesneyi veya herhangi bir nesne tarafından kök olmayan ancak henüz atık toplayıcı tarafından toplanmayan bir nesneyi temsil eder. Koleksiyondaki [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) nesneleri [ICorDebugHeapEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) yöntemi çağırarak Numaralandırılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
