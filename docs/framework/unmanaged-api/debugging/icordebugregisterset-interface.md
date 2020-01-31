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
ms.openlocfilehash: f435db28d5c85d576f69e7612841fc46ae142332
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792082"
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet Arabirimi
Şu anda kod yürüten bilgisayarda kullanılabilir olan yazmaçların kümesini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetRegisters Yöntemi](icordebugregisterset-getregisters-method.md)|Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.|  
|[GetRegistersAvailable Yöntemi](icordebugregisterset-getregistersavailable-method.md)|Şu anda bu `ICorDebugRegisterSet` yazmaçların kullanılabildiğini belirten bir bit maskesi alır.|  
|[GetThreadContext Yöntemi](icordebugregisterset-getthreadcontext-method.md)|Geçerli iş parçacığının bağlamını alır.|  
|[SetRegisters Yöntemi](icordebugregisterset-setregisters-method.md)|.NET Framework sürüm 2,0 için uygulanmadı.|  
|[SetThreadContext Yöntemi](icordebugregisterset-setthreadcontext-method.md)|.NET Framework 2,0 için uygulanmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugRegisterSet` arabirimi yalnızca 32 bitlik kayıtları destekler. Daha fazla kayıt gerektiren IA-64 gibi platformlarda [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) arabirimini kullanın.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [ICorDebugRegisterSet2 Arabirimi](icordebugregisterset2-interface.md)
