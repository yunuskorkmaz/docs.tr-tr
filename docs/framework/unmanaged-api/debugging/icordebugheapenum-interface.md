---
title: ICorDebugHeapEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapEnum
helpviewer_keywords: ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbc97aec2fc9758df17767188c6b4d044b5016fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapenum-interface"></a>ICorDebugHeapEnum Arabirimi
Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar. Bu arabirim Icordebugenum arabirimi sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|Belirtilen sayıda alır [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) yönetilen yığında nesneler hakkında bilgi içeren örnekleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugHeapEnum` Arabirimini uygulayan Icordebugenum arabirimi.  
  
 Bir `ICorDebugHeapEnum` örneği ile doldurulur [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) çağırarak örnekleri [Icordebugprocess5::enumerateheap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) yöntemi. Her [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) öbek canlı bir nesnede veya herhangi bir nesne tarafından kökü değil, ancak henüz atık toplayıcısı tarafından toplanan değil bir nesne koleksiyonundaki örneği temsil eder. [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) koleksiyonundaki nesneleri numaralandırılan çağırarak [Icordebugheapenum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
