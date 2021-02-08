---
description: 'Daha fazla bilgi edinin: ICorDebugThread3 Interface'
title: ICorDebugThread3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 88c668f1e08d0843f26d231937c85d80e03bee6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800974"
---
# <a name="icordebugthread3-interface"></a>ICorDebugThread3 Arabirimi

[Icordebugstackyürüme](icordebugstackwalk-interface.md) ve ilgili arabirimlere giriş noktası sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateStackWalk Yöntemi](icordebugthread3-createstackwalk-method.md)|Yığınını aşağı doğru bırakmak istediğiniz iş parçacığı için [ıcordebugstackyürüme](icordebugstackwalk-interface.md) nesnesi oluşturur.|  
|[GetActiveInternalFrames Yöntemi](icordebugthread3-getactiveinternalframes-method.md)|Yığında iç çerçeveler ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) nesneleri) dizisini döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorDebugThread3` , ICorDebugThread arabirimine yönelik mantıksal bir uzantıdır.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
