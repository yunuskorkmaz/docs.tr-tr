---
description: ': ICorDebugType:: GetFirstTypeParameter metodu hakkında daha fazla bilgi edinin'
title: ICorDebugType::GetFirstTypeParameter Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
ms.openlocfilehash: 4c37217f34f80c916d618d88e4917eab794a1d90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658288"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a>ICorDebugType::GetFirstTypeParameter Yöntemi

<xref:System.Type>Bu tarafından temsil edilen türün ilk parametresini temsil eden bir ICorDebugType için bir arabirim işaretçisi alır `ICorDebugType` .  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `value`  
 dışı `ICorDebugType` İlk parametreyi temsil eden bir nesnenin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `GetFirstTypeParameter` , türle ilgili ek bilgilerin en çok, tek bir tür parametresine sahip olduğu durumlarda çağrılabilir. Özellikle, türü [ICorDebugType:: GetType](icordebugtype-gettype-method.md) yöntemiyle gösterildiği gibi bir ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF veya ELEMENT_TYPE_PTR ise kullanılabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
