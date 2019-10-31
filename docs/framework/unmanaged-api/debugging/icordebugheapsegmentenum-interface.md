---
title: ICorDebugHeapSegmentEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugHealRegionEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum
helpviewer_keywords:
- ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type:
- apiref
ms.openlocfilehash: e9679029cd54ac44832add9bc4f47f8c8e9a26a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138458"
---
# <a name="icordebugheapsegmentenum-interface"></a>ICorDebugHeapSegmentEnum Arabirimi
Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar. Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|Yönetilen yığının bölgeleri hakkında bilgi içeren, belirtilen [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örnek sayısını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugHeapSegmentEnum` arabirimi ıcorı, Genum arabirimini uygular.  
  
 `ICorDebugHeapSegmentEnum` örneği, [ICorDebugProcess5:: Enumerateheapregion](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) yöntemi çağırarak [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örnekleriyle doldurulur. Koleksiyondaki [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) nesneleri [ICorDebugHeapSegmentEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) yöntemi çağırarak listelenebilir.  
  
 `ICorDebugHeapSegmentEnum` bir koleksiyon nesnesi, yönetilen nesneler içerebilen tüm bellek bölgelerini numaralandırır, ancak yönetilen nesnelerin gerçekten bu bölgelerde yer aldığı garanti etmez. Boş veya ayrılmış bellek bölgeleri hakkında bilgi içerebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
