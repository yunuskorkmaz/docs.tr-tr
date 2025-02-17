---
description: ': ICorDebugType:: GetType yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugType::GetType Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
ms.openlocfilehash: 922791e51855badfb1fd548e08953a2f660f971a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658223"
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType Metodu

Bu ICorDebugType tarafından temsil edilen ortak dil çalışma zamanının (CLR) yerel türünü açıklayan bir CorElementType değeri alır <xref:System.Type> .  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `ty`  
 dışı `CorElementType` Numaralandırmadaki, bu temsil eden clr 'yi gösteren bir değer işaretçisi <xref:System.Type> `ICorDebugType` .  
  
## <a name="remarks"></a>Açıklamalar  

 Değeri `ty` element_type_class ya da element_type_valuetype ise, [ICorDebugType:: GetClass](icordebugtype-getclass-method.md) yöntemi, genel bir türün örneklenmemiş türünü almak için çağrılabilir; Aksi takdirde, çağırmayın `ICorDebugType::GetClass` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
