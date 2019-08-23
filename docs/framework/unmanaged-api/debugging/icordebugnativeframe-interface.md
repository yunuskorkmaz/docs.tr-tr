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
ms.openlocfilehash: c01346b42fff812f8358482ae0e8570c03ee9231
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912808"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame Arabirimi

Yerel çerçeveler için kullanılan ICorDebugFrame 'in özelleştirilmiş bir uygulaması.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CanSetIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|Yerel koddaki belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını gösteren bir değer alır.|  
|[GetIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|Yığın çerçevesinin sapmasını yerel koda alır.|  
|[GetLocalDoubleRegisterValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Bir bağımsız değişkenin veya yerel bir karenin iki bellek kaydı içinde depolanan yerel değişkenin değerini temsil eden bir ICorDebugValue için bir işaretçi alır.|  
|[GetLocalMemoryRegisterValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|, Düşük bitlerin belirtilen kasada `ICorDebugValue` depolandığı ve yüksek bitlerin belirtilen bellek adresinde depolandığı yerel bir değişkenin değerini temsil eden bir işaretçi alır.|  
|[GetLocalMemoryValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|Belirtilen bellek adresinde depolanan yerel `ICorDebugValue` bir değişkenin değerini temsil eden bir işaretçisi alır.|  
|[GetLocalRegisterMemoryValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Bir `ICorDebugValue` yerel değişkenin değerini temsil eden bir işaretçi alır, bu, yüksek bitlerin belirtilen kasada depolandığı ve düşük bitlerin belirtilen bellek adresinde depolandığı bir.|  
|[GetLocalRegisterValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|Bir bağımsız değişkenin veya belirtilen `ICorDebugValue` yerel kasada depolanan yerel değişkenin değerini temsil eden bir işaretçi alır.|  
|[GetRegisterSet Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|Bu`ICorDebugNativeFrame`için yazmaç kümesini temsil eden bir [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) için bir işaretçi alır.|  
|[SetIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|Yönerge işaretçisini yerel kodda belirtilen konum konumunu ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
