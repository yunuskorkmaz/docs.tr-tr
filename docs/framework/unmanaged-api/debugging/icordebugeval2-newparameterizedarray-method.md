---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugEval2:: NewParameterizedArray Yöntemi'
title: ICorDebugEval2::NewParameterizedArray Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
ms.openlocfilehash: 0ce8582328013ad02357361f05efb55ade8780e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693752"
---
# <a name="icordebugeval2newparameterizedarray-method"></a>ICorDebugEval2::NewParameterizedArray Yöntemi

Belirtilen öğe türü ve boyutlarının yeni bir dizisini ayırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pElementType`  
 'ndaki Dizide depolanan öğe türünü temsil eden ICorDebugType nesnesine yönelik bir işaretçi.  
  
 `rank`  
 'ndaki Dizinin boyut sayısı. .NET Framework sürüm 2,0 ' de, bu değer 1 olmalıdır.  
  
 `dims`  
 'ndaki Dizinin her boyutunun bayt cinsinden boyutu.  
  
 `lowBounds`  
 'ndaki Seçim. Dizi boyutunun alt sınırı. Bu değer atlanırsa, her bir boyut için sıfırdan daha düşük bir sınır varsayılır.  
  
## <a name="remarks"></a>Açıklamalar  

 Dizinin öğeleri, genel bir türün örnekleri olabilir. Dizi, iş parçacığının çalışmakta olduğu uygulama etki alanında her zaman oluşturulur. .NET Framework 2,0 ' de, değeri 1 olmalıdır `rank` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
