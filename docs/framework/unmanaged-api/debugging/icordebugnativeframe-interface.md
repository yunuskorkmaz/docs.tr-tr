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
ms.openlocfilehash: dd87745a29514a2f9f05aa142baae4e05d4b4a7b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206606"
---
# <a name="icordebugnativeframe-interface"></a>ICorDebugNativeFrame Arabirimi

Yerel çerçeveler için kullanılan ICorDebugFrame 'in özelleştirilmiş bir uygulaması.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CanSetIP Yöntemi](icordebugnativeframe-cansetip-method.md)|Yerel koddaki belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını gösteren bir değer alır.|  
|[GetIP Yöntemi](icordebugnativeframe-getip-method.md)|Yığın çerçevesinin sapmasını yerel koda alır.|  
|[GetLocalDoubleRegisterValue Yöntemi](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|Bir bağımsız değişkenin veya yerel bir karenin iki bellek kaydı içinde depolanan yerel değişkenin değerini temsil eden bir ICorDebugValue için bir işaretçi alır.|  
|[GetLocalMemoryRegisterValue Yöntemi](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|`ICorDebugValue`, Düşük bitlerin belirtilen kasada depolandığı ve yüksek bitlerin belirtilen bellek adresinde depolandığı yerel bir değişkenin değerini temsil eden bir işaretçi alır.|  
|[GetLocalMemoryValue Yöntemi](icordebugnativeframe-getlocalmemoryvalue-method.md)|`ICorDebugValue`Belirtilen bellek adresinde depolanan yerel bir değişkenin değerini temsil eden bir işaretçisi alır.|  
|[GetLocalRegisterMemoryValue Yöntemi](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|Bir `ICorDebugValue` yerel değişkenin değerini temsil eden bir işaretçi alır, bu, yüksek bitlerin belirtilen kasada depolandığı ve düşük bitlerin belirtilen bellek adresinde depolandığı bir.|  
|[GetLocalRegisterValue Yöntemi](icordebugnativeframe-getlocalregistervalue-method.md)|Bir `ICorDebugValue` bağımsız değişkenin veya belirtilen yerel kasada depolanan yerel değişkenin değerini temsil eden bir işaretçi alır.|  
|[GetRegisterSet Metodu](icordebugnativeframe-getregisterset-method.md)|Bu için yazmaç kümesini temsil eden bir [ICorDebugRegisterSet](icordebugregisterset-interface.md) için bir işaretçi alır `ICorDebugNativeFrame` .|  
|[SetIP Yöntemi](icordebugnativeframe-setip-method.md)|Yönerge işaretçisini yerel kodda belirtilen konum konumunu ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
