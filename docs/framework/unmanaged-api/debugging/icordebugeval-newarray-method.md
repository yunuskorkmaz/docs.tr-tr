---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgeval:: NewArray Yöntemi'
title: ICorDebugEval::NewArray Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type:
- apiref
ms.openlocfilehash: 1344a99450974369533b1c54b641c036fc64e3ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693986"
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray Yöntemi

Belirtilen öğe türü ve boyutlarının yeni bir dizisini ayırır.  
  
 Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor. Bunun yerine [ICorDebugEval2:: NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `elementType`  
 'ndaki Dizinin öğe türünü belirten CorElementType numaralandırması değeri.  
  
 `pElementClass`  
 'ndaki Öğesinin sınıfını belirten ICorDebugClass nesnesine yönelik bir işaretçi. Öğe türü basit bir tür ise bu değer null olabilir.  
  
 `rank`  
 'ndaki Dizinin boyut sayısı. .NET Framework 2,0 ' de, bu değer 1 olmalıdır.  
  
 `dims`  
 'ndaki Dizinin her boyutunun bayt cinsinden boyutu.  
  
 `lowBounds`  
 'ndaki Seçim. Dizi boyutunun alt sınırı. Bu değer atlanırsa, her bir boyut için sıfırdan daha düşük bir sınır varsayılır.  
  
## <a name="remarks"></a>Açıklamalar  

 Dizi, iş parçacığının Şu anda yürütüldüğü uygulama etki alanında her zaman oluşturulur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 1,1, 1,0
