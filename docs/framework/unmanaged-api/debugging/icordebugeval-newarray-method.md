---
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
ms.openlocfilehash: ef6cbe2cef3c52d9a4b47ff77e8aeb5159e89c76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729765"
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray Yöntemi

Belirtilen öğe türü ve boyutlarının yeni bir dizisini ayırır.  
  
 Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor. Bunun yerine [ICorDebugEval2:: NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) kullanın.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
