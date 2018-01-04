---
title: ICorDebugHeapSegmentEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHealRegionEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapSegmentEnum
helpviewer_keywords: ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b477631b5920401127d34b2304485bd32c3d78f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapsegmentenum-interface"></a>ICorDebugHeapSegmentEnum Arabirimi
Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar. Bu arabirim Icordebugenum arabirimi sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|Belirtilen sayıda alır [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Yönetilen yığın bölgeler hakkında bilgiler içeren örnekleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugHeapSegmentEnum` Arabirimini uygulayan Icordebugenum arabirimi.  
  
 Bir `ICorDebugHeapSegmentEnum` örneği ile doldurulur [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) çağırarak örnekleri [Icordebugprocess5::enumerateheapregions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) yöntemi. [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) koleksiyonundaki nesneleri numaralandırılan çağırarak [Icordebugheapsegmentenum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) yöntemi.  
  
 Bir `ICorDebugHeapSegmentEnum` koleksiyon nesnesi numaralandırır yönetilen nesneleri içerebilir tüm bellek bölgeler, ancak bunu yönetilen nesneler gerçekte bu bölgede bulunan garanti etmez. Boş veya ayrılmış bellek bölgeler hakkında bilgi içerebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
