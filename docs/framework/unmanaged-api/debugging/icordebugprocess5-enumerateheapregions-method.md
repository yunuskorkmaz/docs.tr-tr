---
title: ICorDebugProcess5::EnumerateHeapRegions Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9340977c55c54b9a4683115000293d1c98dfcf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767463"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a>ICorDebugProcess5::EnumerateHeapRegions Yöntemi
Yönetilen yığının bellek aralığı için bir numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppRegions`  
 [out] Adresine bir işaretçi bir [Icordebugheapsegmentenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) nesneler yönetilen yığında bulunan bellek aralığı için bir numaralandırıcı arabirimi nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağırmadan önce `ICorDebugProcess5::EnumerateHeapRegions` yöntemini çağırmalıdır [Icordebugprocess5::getgcheapınformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) yöntemi ve değerini incelemek `areGCStructuresValid` alan döndürülen [cor_heapınfo](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) nesnenin numaralandırılabilir çöp toplama yığınındaki geçerli durumda olduğundan emin olun. Ayrıca, `ICorDebugProcess5::EnumerateHeapRegions` yöntemi döndürür `E_FAIL` çok erken işlem yaşam süresi içinde eklerseniz, önce bellek bölgeleri oluşturulur.  
  
 Bu yöntem, yönetilen nesneleri içerebilir tüm bellek bölümlerinin numaralandırmak için garanti edilir, ancak yönetilen nesneleri aslında bu bölgelerde bulunan garantilemez. [Icordebugheapsegmentenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) koleksiyon nesnesi boş veya ayrılmış bellek bölümlerinin içerebilir.  
  
 [Icordebugheapsegmentenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) arabirimi nesnedir listeleme olanak tanıyan Icordebugenum arabirimden türetilmiş standart bir numaralandırıcı [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) nesneleri. Her [COR_SEGMENT](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) nesne kesiminin nesneleri nesil yanı sıra belirli bir kesim bellek aralığı hakkında bilgi sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess5 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
