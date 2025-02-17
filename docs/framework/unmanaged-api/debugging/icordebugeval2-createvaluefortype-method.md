---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugEval2:: CreateValueForType yöntemi'
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
ms.openlocfilehash: 2a8cd129d6194a4870817eb64b79606c395cb055
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693921"
---
# <a name="icordebugeval2createvaluefortype-method"></a>ICorDebugEval2::CreateValueForType Yöntemi

Belirtilen türdeki yeni bir ICorDebugValue değeri, sıfır veya null değeri olan bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pType`  
 'ndaki Türü temsil eden ICorDebugType nesnesine yönelik işaretçi.  
  
 `ppValue`  
 dışı `ICorDebugValue` Değeri temsil eden bir nesnenin adresine yönelik işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 `CreateValueForType` gibi oluşturulmuş türler de dahil olmak üzere, rastgele bir nesne türü belirtmenize izin vererek [ıcorınkıx Geval:: CreateValue](icordebugeval-createvalue-method.md) öğesini genelleştirir `List<int>` . Bu yöntemin tek amacı, bir işlev değerlendirmesine geçirilebilecek bir değer üretmesidir.  
  
 Tür bir sınıf veya değer türü olmalıdır. Dizi değerleri veya dize değerleri oluşturmak için bu yöntemi kullanamazsınız.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
