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
ms.openlocfilehash: 41ac0b29ade2f78b893df72e8a17624373f6dd78
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792789"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame Arabirimi

Yerel çerçeveler için kullanılan ICorDebugFrame 'in özelleştirilmiş bir uygulaması.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CanSetIP Yöntemi](icordebugnativeframe-cansetip-method.md)|Yerel koddaki belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını gösteren bir değer alır.|  
|[GetIP Yöntemi](icordebugnativeframe-getip-method.md)|Yığın çerçevesinin sapmasını yerel koda alır.|  
|[GetLocalDoubleRegisterValue Yöntemi](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Bir bağımsız değişkenin veya yerel bir karenin iki bellek kaydı içinde depolanan yerel değişkenin değerini temsil eden bir ICorDebugValue için bir işaretçi alır.|  
|[GetLocalMemoryRegisterValue Yöntemi](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|, Düşük bitlerin belirtilen kasada depolandığı ve yüksek bitlerin belirtilen bellek adresinde depolandığı bir yerel değişkenin değerini temsil eden bir `ICorDebugValue` için bir işaretçi alır.|  
|[GetLocalMemoryValue Yöntemi](icordebugnativeframe-getlocalmemoryvalue-method.md)|Belirtilen bellek adresinde depolanan yerel bir değişkenin değerini temsil eden bir `ICorDebugValue` için bir işaretçi alır.|  
|[GetLocalRegisterMemoryValue Yöntemi](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Yüksek bitlerin belirtilen kasada depolandığı ve düşük bitlerin belirtilen bellek adresinde depolandığı bir yerel değişkenin değerini temsil eden bir `ICorDebugValue` için bir işaretçi alır|  
|[GetLocalRegisterValue Yöntemi](icordebugnativeframe-getlocalregistervalue-method.md)|Bir bağımsız değişkenin veya belirtilen yerel kasada depolanan yerel değişkenin değerini temsil eden bir `ICorDebugValue` için bir işaretçi alır.|  
|[GetRegisterSet Yöntemi](icordebugnativeframe-getregisterset-method.md)|Bu `ICorDebugNativeFrame`için yazmaç kümesini temsil eden bir [ICorDebugRegisterSet](icordebugregisterset-interface.md) için bir işaretçi alır.|  
|[SetIP Yöntemi](icordebugnativeframe-setip-method.md)|Yönerge işaretçisini yerel kodda belirtilen konum konumunu ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
