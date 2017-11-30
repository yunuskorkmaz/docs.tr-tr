---
title: "ICorDebugEval2::NewParameterizedArray Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedArray
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf7f8fb0d3418f863f2cd1531dc32b7e64c2b8a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2newparameterizedarray-method"></a>ICorDebugEval2::NewParameterizedArray Yöntemi
Belirtilen öğe türü ve boyutları yeni bir dizi ayırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pElementType`  
 [in] Bir işaretçi Icordebugtype nesneye dizisinde depolanan öğenin türünü temsil eder.  
  
 `rank`  
 [in] Dizi boyutları sayısı. .NET Framework sürüm 2. 0'da, bu değerin 1 olması gerekir.  
  
 `dims`  
 [in] Her boyutun dizisinin bayt cinsinden boyutu.  
  
 `lowBounds`  
 [in] İsteğe bağlı. Dizinin her boyutu alt sınırı. Bu değer belirtilmezse, bir alt sınırı sıfır her boyut için kabul edilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Dizideki öğeler genel bir tür örneklerini olabilir. Dizi her zaman iş parçacığı çalışıyor uygulama etki alanında oluşturulur. .NET Framework 2. 0 değeri, `rank` 1 olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
