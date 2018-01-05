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
ms.workload: dotnet
ms.openlocfilehash: a605276fac66e395d5663bacff727c235981a868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="ff887-102">ICorDebugEval2::NewParameterizedArray Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff887-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="ff887-103">Belirtilen öğe türü ve boyutları yeni bir dizi ayırır.</span><span class="sxs-lookup"><span data-stu-id="ff887-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff887-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff887-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff887-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff887-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="ff887-106">[in] Bir işaretçi Icordebugtype nesneye dizisinde depolanan öğenin türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ff887-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="ff887-107">[in] Dizi boyutları sayısı.</span><span class="sxs-lookup"><span data-stu-id="ff887-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="ff887-108">.NET Framework sürüm 2. 0'da, bu değerin 1 olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff887-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="ff887-109">[in] Her boyutun dizisinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ff887-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="ff887-110">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ff887-110">[in] Optional.</span></span> <span data-ttu-id="ff887-111">Dizinin her boyutu alt sınırı.</span><span class="sxs-lookup"><span data-stu-id="ff887-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="ff887-112">Bu değer belirtilmezse, bir alt sınırı sıfır her boyut için kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ff887-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff887-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff887-113">Remarks</span></span>  
 <span data-ttu-id="ff887-114">Dizideki öğeler genel bir tür örneklerini olabilir.</span><span class="sxs-lookup"><span data-stu-id="ff887-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="ff887-115">Dizi her zaman iş parçacığı çalışıyor uygulama etki alanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ff887-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="ff887-116">.NET Framework 2. 0 değeri, `rank` 1 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ff887-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff887-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff887-117">Requirements</span></span>  
 <span data-ttu-id="ff887-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff887-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff887-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff887-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff887-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff887-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff887-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff887-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
