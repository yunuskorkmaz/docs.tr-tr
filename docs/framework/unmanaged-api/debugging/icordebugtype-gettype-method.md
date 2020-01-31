---
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
ms.openlocfilehash: 25ffbf73fbefbb3c584450283c3080dfc11ee598
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791248"
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType Metodu
Bu ICorDebugType tarafından temsil edilen ortak dil çalışma zamanı (CLR) <xref:System.Type> yerel türünü açıklayan bir CorElementType değeri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ty`  
 dışı Bu `ICorDebugType` temsil eden CLR <xref:System.Type> belirten `CorElementType` numaralandırması değerine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `ty` değeri ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE ise, [ICorDebugType:: GetClass](icordebugtype-getclass-method.md) yöntemi, genel bir türün örneklenmemiş türünü almak için çağrılabilir; Aksi takdirde, `ICorDebugType::GetClass`çağırmayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
