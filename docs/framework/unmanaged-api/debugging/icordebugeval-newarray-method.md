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
# <a name="icordebugevalnewarray-method"></a><span data-ttu-id="8d1d4-102">ICorDebugEval::NewArray Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d1d4-102">ICorDebugEval::NewArray Method</span></span>
<span data-ttu-id="8d1d4-103">Belirtilen öğe türü ve boyutları yeni bir dizi ayırır.</span><span class="sxs-lookup"><span data-stu-id="8d1d4-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
 <span data-ttu-id="8d1d4-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="8d1d4-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="8d1d4-105">Kullanım [Icordebugeval2::newparameterizedarray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="8d1d4-105">Use [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d1d4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d1d4-106">Syntax</span></span>  
  
```  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d1d4-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8d1d4-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="8d1d4-108">[in] Dizi öğesi türünü belirtir CorElementType numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="8d1d4-108">[in] A value of the CorElementType enumeration that specifies the element type of the array.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="8d1d4-109">[in] Bir işaretçi bir Icordebugclass nesnesine öğe sınıfı belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d1d4-109">[in] A pointer to a ICorDebugClass object that specifies the class of the element.</span></span> <span data-ttu-id="8d1d4-110">Bu değer öğe türü basit tür ise null olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d1d4-110">This value may be null if the element type is a primitive type.</span></span>  
  
 `rank`  
 <span data-ttu-id="8d1d4-111">[in] Dizi boyutları sayısı.</span><span class="sxs-lookup"><span data-stu-id="8d1d4-111">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="8d1d4-112">.NET Framework 2.0 Bu değerin 1 olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d1d4-112">In the .NET Framework 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="8d1d4-113">[in] Her boyutun dizisinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="8d1d4-113">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="8d1d4-114">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8d1d4-114">[in] Optional.</span></span> <span data-ttu-id="8d1d4-115">Dizinin her boyutu alt sınırı.</span><span class="sxs-lookup"><span data-stu-id="8d1d4-115">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="8d1d4-116">Bu değer belirtilmezse, bir alt sınırı sıfır her boyut için kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="8d1d4-116">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d1d4-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d1d4-117">Remarks</span></span>  
 <span data-ttu-id="8d1d4-118">Dizi her zaman iş parçacığı şu anda yürütülmekte uygulama etki alanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8d1d4-118">The array is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d1d4-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d1d4-119">Requirements</span></span>  
 <span data-ttu-id="8d1d4-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d1d4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d1d4-121">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d1d4-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d1d4-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d1d4-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d1d4-123">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="8d1d4-123">**.NET Framework Versions:** 1.1, 1.0</span></span>
