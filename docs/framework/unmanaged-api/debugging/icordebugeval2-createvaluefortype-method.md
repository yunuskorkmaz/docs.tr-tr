---
title: ICorDebugEval2::CreateValueForType Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 683457c249915708becadaeda9dec265666e2023
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412113"
---
# <a name="icordebugeval2createvaluefortype-method"></a>ICorDebugEval2::CreateValueForType Yöntemi
Bir işaretçi belirtilen türe ait yeni Icordebugvalue için sıfır ya da null bir başlangıç değeriyle birlikte alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pType`  
 [in] İşaretçi Icordebugtype nesneye türünü temsil eder.  
  
 `ppValue`  
 [out] İşaretçi adresine bir `ICorDebugValue` değerini temsil eden nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 `CreateValueForType` genelleştirir [Icordebugeval::createvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) rasgele nesne türünü belirtmenize olanak tanıyarak dahil olmak üzere oluşturulan türleri gibi `List<int>`. Tek amacı, bu yöntem, bir işlev değerlendirmesi için geçirilen değer oluşturmaktır.  
  
 Türün bir sınıf veya bir değer türü olmalıdır. Bu yöntem, dizi değerlerini veya dize değerlerini oluşturmak için kullanamazsınız.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
