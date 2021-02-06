---
description: 'Daha fazla bilgi edinin: ICorDebugHeapSegmentEnum Interface'
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
ms.openlocfilehash: 614bae0ea5e3eb7816fdeec23a0dc7aa6e44801d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660888"
---
# <a name="icordebugheapsegmentenum-interface"></a>ICorDebugHeapSegmentEnum Arabirimi

Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar. Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next Yöntemi](icordebugheapsegmentenum-next-method.md)|Yönetilen yığının bölgeleri hakkında bilgi içeren [cor_segment](cor-segment-structure.md) örneklerinin belirtilen sayısını alır.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorDebugHeapSegmentEnum`Arabirim ıcorı, Genum arabirimini uygular.  
  
 `ICorDebugHeapSegmentEnum` [ICorDebugProcess5:: Enumerateheapregion](icordebugprocess5-enumerateheapregions-method.md) yöntemi çağırarak bir örnek [cor_segment](cor-segment-structure.md) örneklerle doldurulur. Koleksiyondaki [cor_segment](cor-segment-structure.md) nesneleri [ICorDebugHeapSegmentEnum:: Next](icordebugheapsegmentenum-next-method.md) yöntemi çağırarak Numaralandırılabilir.  
  
 Bir `ICorDebugHeapSegmentEnum` koleksiyon nesnesi, yönetilen nesneler içerebilen tüm bellek bölgelerini numaralandırır, ancak yönetilen nesnelerin gerçekten bu bölgelerde yer aldığı garanti etmez. Boş veya ayrılmış bellek bölgeleri hakkında bilgi içerebilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
