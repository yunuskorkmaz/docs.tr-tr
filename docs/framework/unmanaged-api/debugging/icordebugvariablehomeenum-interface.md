---
title: ICorDebugVariableHomeEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
ms.openlocfilehash: 74b3c7bed54f3735efbd5d2c56962d427518f71a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790942"
---
# <a name="icordebugvariablehomeenum-interface"></a>ICorDebugVariableHomeEnum Arabirimi
Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir Numaralandırıcı sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Next Yöntemi](icordebugvariablehomeenum-next-method.md)|Bir işlevdeki yerel değişkenler ve bağımsız değişkenler hakkında bilgi içeren, belirtilen [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği sayısını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugVariableHomeEnum` arabirimi ıcorı, Genum arabirimini uygular.  
  
 [ICorDebugCode4:: enumeratevariableevler](icordebugcode4-enumeratevariablehomes-method.md) yöntemi çağırarak [ıcordebugvariablehome](icordebugvariablehome-interface.md) örnekleriyle birlikte `ICorDebugVariableHomeEnum` bir örnek doldurulur. Koleksiyondaki her [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği, bir işlevdeki yerel bir değişkeni veya bağımsız değişkeni temsil eder. Koleksiyondaki [ıcordebugvariableana](icordebugvariablehome-interface.md) nesneleri [ıcordebugvariablehomeenum:: Next](icordebugvariablehomeenum-next-method.md) yöntemi çağırarak listelenebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugVariableHome Arabirimi](icordebugvariablehome-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
