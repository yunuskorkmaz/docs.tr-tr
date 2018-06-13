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
ms.openlocfilehash: 6f4947a9b6c0e3fd87ee474111f143d273c1d7b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422801"
---
# <a name="icordebugregisterset2-interface"></a>ICorDebugRegisterSet2 Arabirimi
Yeteneklerini genişletir [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) 64 taneden fazla kayıtları olan donanım platformları için arabirim.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetRegisters Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|Her kayıt değerini (kod şu anda yürütülmekte bilgisayarda) alır bit maskesi kullanılarak belirtilir.|  
|[GetRegistersAvailable Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|Bir bit eşlem kullanılabilir yazmaçlar sağlayan bir bayt dizisi alır.|  
|[SetRegisters Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|.NET Framework sürüm 2.0 uygulanmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugRegisterSet Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
