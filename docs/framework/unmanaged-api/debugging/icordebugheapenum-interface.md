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
ms.openlocfilehash: bed2871c46712490bc4b0520fa1ab8023dbab5cf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794435"
---
# <a name="icordebugheapenum-interface"></a>ICorDebugHeapEnum Arabirimi
Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar. Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next Yöntemi](icordebugheapenum-next-method.md)|Yönetilen yığında nesneler hakkında bilgi içeren [cor_heapobject](cor-heapobject-structure.md) örneklerinin belirtilen sayısını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugHeapEnum` arabirimi ıcorı, Genum arabirimini uygular.  
  
 [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md) yöntemi çağırarak bir `ICorDebugHeapEnum` örneği [cor_heapobject](cor-heapobject-structure.md) örneklerle doldurulur. Koleksiyondaki her bir [cor_heapobject](cor-heapobject-structure.md) örneği, yığında canlı bir nesneyi veya herhangi bir nesne tarafından kök olmayan ancak henüz atık toplayıcı tarafından toplanmayan bir nesneyi temsil eder. Koleksiyondaki [cor_heapobject](cor-heapobject-structure.md) nesneleri [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) yöntemi çağırarak Numaralandırılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
