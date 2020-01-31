---
title: ICorDebugType::GetClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: d403a8bfba3599a60d8af72307590f5a569480dd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791290"
---
# <a name="icordebugtypegetclass-method"></a>ICorDebugType::GetClass Yöntemi
Örneklenmiş genel türü temsil eden bir ICorDebugClass için bir arabirim işaretçisi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppClass`  
 dışı Örneklenmemiş genel türü temsil eden `ICorDebugClass` arabiriminin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetClass`, yalnızca belirli koşullar altında çağrılabilir. `GetClass`çağrılmadan önce [ICorDebugType:: GetType](icordebugtype-gettype-method.md) çağırın. `ICorDebugType::GetType`, ELEMENT_TYPE_CLASS veya ELEMENT_TYPE_VALUETYPE olan bir CorElementType değeri döndürürse, bir genel türün örneklenmemiş türünü almak için `GetClass` çağrılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
