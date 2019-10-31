---
title: ICorDebugRegisterSet Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
ms.openlocfilehash: 1ea0274adc12f3a99df0422bfc0b5180f0ef5596
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131385"
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet Arabirimi
Şu anda kod yürüten bilgisayarda kullanılabilir olan yazmaçların kümesini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetRegisters Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.|  
|[GetRegistersAvailable Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|Şu anda bu `ICorDebugRegisterSet` yazmaçların kullanılabildiğini belirten bir bit maskesi alır.|  
|[GetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|Geçerli iş parçacığının bağlamını alır.|  
|[SetRegisters Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|.NET Framework sürüm 2,0 için uygulanmadı.|  
|[SetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|.NET Framework 2,0 için uygulanmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugRegisterSet` arabirimi yalnızca 32 bitlik kayıtları destekler. Daha fazla kayıt gerektiren IA-64 gibi platformlarda [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) arabirimini kullanın.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugRegisterSet2 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
