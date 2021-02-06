---
description: ': ICorDebugType:: GetClass yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 2e8d68fbc8909599ca649ba0e226cc84af820939
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658353"
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
 dışı `ICorDebugClass` Örneklenmiş genel türü temsil eden bir arabirimin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `GetClass` yalnızca belirli koşullar altında çağrılabilir. Çağrılmadan önce [ICorDebugType:: GetType](icordebugtype-gettype-method.md) çağırın `GetClass` . `ICorDebugType::GetType`Element_type_class veya element_type_valuetype bir CorElementType değeri döndürürse, `GetClass` genel bir türün örneklenmemiş türünü almak için çağrılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
