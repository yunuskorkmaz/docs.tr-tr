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
ms.openlocfilehash: 9ffddb8242b6627239a99bd9223b98762910b831
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753242"
---
# <a name="icordebugeval2createvaluefortype-method"></a>ICorDebugEval2::CreateValueForType Yöntemi
Bir işaretçi için yeni bir Icordebugvalue belirtilen türe ait bir başlangıç değeri sıfır ya da null ile alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pType`  
 [in] İşaretçi Icordebugtype nesnenin türünü temsil eder.  
  
 `ppValue`  
 [out] İşaretçi adresine bir `ICorDebugValue` değerini temsil eden nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 `CreateValueForType` genelleştirir [Icordebugeval::createvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) rasgele nesne türünü belirtmenize olanak tanıyarak dahil olmak üzere oluşturulmuş türleri gibi `List<int>`. Bu yöntemin tek amacı, bir işlev değerlendirmesi için geçirilen değer oluşturmaktır.  
  
 Türü, bir sınıf veya değer türü olması gerekir. Bu yöntem, değerler dizisi veya dize değerleri oluşturmak için kullanamazsınız.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
