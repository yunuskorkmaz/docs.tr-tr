---
title: Icordebugnativeframe Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame
helpviewer_keywords: ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 63d631dec00e63d6ee383cd36d79382a529d9ddb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframe-interface1"></a>Icordebugnativeframe Interface1
Yerel çerçeveler için kullanılan Icordebugframe, özelleştirilmiş bir uygulaması.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Cansetıp yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|Yönerge işaretçisi belirtilen uzaklık konuma yerel kodda ayarlamak güvenli olup olmadığını belirten bir değer alır.|  
|[Getıp yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|Yığın çerçeve uzaklığı yerel kod içine alır.|  
|[GetLocalDoubleRegisterValue yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Bir işaretçi bir bağımsız değişken veya yerel bir çerçeve iki bellek kayıtlarında depolanan yerel değişken değerini temsil eden bir Icordebugvalue alır.|  
|[GetLocalMemoryRegisterValue yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|Bir işaretçi alır bir `ICorDebugValue` biri düşük BITS belirtilen kayıt defterinde depolanır ve yüksek bit belirtilen bellek adresinde depolanan yerel bir değişkenin değerini temsil eder.|  
|[GetLocalMemoryValue yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|Bir işaretçi alır bir `ICorDebugValue` belirtilen bellek adresinde depolanan yerel bir değişkenin değerini temsil eder.|  
|[GetLocalRegisterMemoryValue yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Bir işaretçi alır bir `ICorDebugValue` biri yüksek bit belirtilen kayıt defterinde depolanır ve düşük BITS belirtilen bellek adresinde depolanan yerel bir değişkenin değerini temsil eder|  
|[GetLocalRegisterValue yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|Bir işaretçi alır bir `ICorDebugValue` bağımsız değişken veya belirtilen yerel kayıt defterinde depolanan yerel bir değişken değerini temsil eder.|  
|[GetRegisterSet yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|Bir işaretçi alır bir [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) temsil eden bu ayarla kayıt `ICorDebugNativeFrame`.|  
|[SetIP yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|Yönerge işaretçisi yerel kodda belirtilen uzaklık konumunu ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
