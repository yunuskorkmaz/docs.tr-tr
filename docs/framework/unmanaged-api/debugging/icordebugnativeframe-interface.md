---
title: ICorDebugNativeFrame Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d59450540b680d6004c47fd646769e38c806024
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994623"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame Arabirimi

Yerel çerçevelere ilişkin kullanılan Icordebugframe öğesinin özelleşmiş uygulaması.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CanSetIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|Yerel kodda belirtilen uzaklık konuma yönerge işaretçisi ayarlama güvenli olup olmadığını gösteren bir değer alır.|  
|[GetIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|Yığın çerçeve uzaklığı yerel kod içine alır.|  
|[GetLocalDoubleRegisterValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Bir bağımsız değişken veya yerel değişken bir yerel çerçeve iki bellek yazmaçlarda depolanan değerini temsil eden bir Icordebugvalue için bir işaretçi alır.|  
|[GetLocalMemoryRegisterValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|Bir işaretçi alır bir `ICorDebugValue` biri düşük BITS belirtilen kayıt defterinde depolanır ve yüksek bit belirtilen bellek adresinde depolanan bir yerel değişkenin değerini temsil eder.|  
|[GetLocalMemoryValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|Bir işaretçi alır bir `ICorDebugValue` belirtilen bellek adresinde depolanan bir yerel değişkenin değerini temsil eder.|  
|[GetLocalRegisterMemoryValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Bir işaretçi alır bir `ICorDebugValue` biri yüksek bit belirtilen kayıt defterinde depolanır ve düşük BITS belirtilen bellek adresinde depolanan bir yerel değişkenin değerini temsil eder|  
|[GetLocalRegisterValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|Bir işaretçi alır bir `ICorDebugValue` bağımsız değişken ya da belirtilen yerel kayıt defterinde depolanan bir yerel değişken değerini temsil eder.|  
|[GetRegisterSet Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|Bir işaretçi alır bir [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) için bunu kayıt temsil eden `ICorDebugNativeFrame`.|  
|[SetIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|Yönerge işaretçisi yerel kodda uzaklık belirtilen konuma ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
