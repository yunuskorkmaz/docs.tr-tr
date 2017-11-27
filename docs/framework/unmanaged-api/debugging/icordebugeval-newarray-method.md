---
title: "ICorDebugEval::NewArray Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewArray
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db9b5f7241e2be53cfbc2c6cea3da1b0182c3eb6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray Yöntemi
Belirtilen öğe türü ve boyutları yeni bir dizi ayırır.  
  
 Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır. Kullanım [Icordebugeval2::newparameterizedarray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `elementType`  
 [in] Dizi öğesi türünü belirtir CorElementType numaralandırması değeri.  
  
 `pElementClass`  
 [in] Bir işaretçi bir Icordebugclass nesnesine öğe sınıfı belirtir. Bu değer öğe türü basit tür ise null olabilir.  
  
 `rank`  
 [in] Dizi boyutları sayısı. .NET Framework 2.0 Bu değerin 1 olması gerekir.  
  
 `dims`  
 [in] Her boyutun dizisinin bayt cinsinden boyutu.  
  
 `lowBounds`  
 [in] İsteğe bağlı. Dizinin her boyutu alt sınırı. Bu değer belirtilmezse, bir alt sınırı sıfır her boyut için kabul edilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Dizi her zaman iş parçacığı şu anda yürütülmekte uygulama etki alanında oluşturulur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 1.1, 1.0
