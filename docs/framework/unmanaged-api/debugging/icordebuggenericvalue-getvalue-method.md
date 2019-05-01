---
title: ICorDebugGenericValue::GetValue Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53db4dcb13303c9e7bdd77a46b3c9526364bac06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995651"
---
# <a name="icordebuggenericvaluegetvalue-method"></a>ICorDebugGenericValue::GetValue Metodu
Bu genel değerini belirtilen arabelleğe kopyalar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pTo`  
 [out] Bu Icordebuggenericvalue nesnesi tarafından temsil edilen değeri için bir işaretçi. Değer, bir basit türü veya başvuru türü (diğer bir deyişle, bir işaretçi) olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
