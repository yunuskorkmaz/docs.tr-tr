---
title: ICorDebugRegisterSet2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da2759219901a4f49808300ea3b038b10ce2d032
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101178"
---
# <a name="icordebugregisterset2-interface"></a>ICorDebugRegisterSet2 Arabirimi
Yeteneklerini genişletir [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) 64'den fazla kayda sahip donanım platformları için arabirim.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetRegisters Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|Her kaydın değerini alır (şu anda kod yürüttüğünü bilgisayarda) bit maskesi kullanılarak belirtilir.|  
|[GetRegistersAvailable Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|Bir bit eşlem kullanılabilir kayıtlara sağlayan bayt dizisini alır.|  
|[SetRegisters Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|.NET Framework 2.0 sürümünde uygulanmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugRegisterSet Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
