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
ms.openlocfilehash: 940810288b72be0d4dfc5366176663c22c369ebb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712385"
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet Arabirimi

Şu anda kod yürüten bilgisayarda kullanılabilir olan yazmaçların kümesini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetRegisters Metodu](icordebugregisterset-getregisters-method.md)|Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.|  
|[GetRegistersAvailable Yöntemi](icordebugregisterset-getregistersavailable-method.md)|Bu, içindeki yazmaçların Şu anda kullanılabilir olduğunu gösteren bir bit maskesi alır `ICorDebugRegisterSet` .|  
|[GetThreadContext Yöntemi](icordebugregisterset-getthreadcontext-method.md)|Geçerli iş parçacığının bağlamını alır.|  
|[SetRegisters Yöntemi](icordebugregisterset-setregisters-method.md)|.NET Framework sürüm 2,0 için uygulanmadı.|  
|[SetThreadContext Yöntemi](icordebugregisterset-setthreadcontext-method.md)|.NET Framework 2,0 için uygulanmadı.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorDebugRegisterSet`Arabirim yalnızca 32 bitlik kayıtları destekler. Daha fazla kayıt gerektiren IA-64 gibi platformlarda [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) arabirimini kullanın.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [ICorDebugRegisterSet2 Arabirimi](icordebugregisterset2-interface.md)
