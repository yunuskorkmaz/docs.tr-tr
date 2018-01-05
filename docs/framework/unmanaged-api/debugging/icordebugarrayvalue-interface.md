---
title: Icordebugarrayvalue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue interface
helpviewer_keywords: ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35169f0dd2ca71400d3aebddf9d5e2ae6b72be07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvalue-interface1"></a><span data-ttu-id="a0d91-102">Icordebugarrayvalue Interface1</span><span class="sxs-lookup"><span data-stu-id="a0d91-102">ICorDebugArrayValue Interface1</span></span>
<span data-ttu-id="a0d91-103">Tek boyutlu veya çok boyutlu bir array temsil eden Icordebugheapvalue sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="a0d91-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0d91-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a0d91-104">Methods</span></span>  
  
|<span data-ttu-id="a0d91-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a0d91-105">Method</span></span>|<span data-ttu-id="a0d91-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0d91-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0d91-107">GetBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0d91-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="a0d91-108">Dizideki her boyut temel dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="a0d91-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="a0d91-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0d91-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="a0d91-110">Dizideki öğeler toplam sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a0d91-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="a0d91-111">GetDimensions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0d91-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="a0d91-112">Dizi boyutları alır.</span><span class="sxs-lookup"><span data-stu-id="a0d91-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="a0d91-113">GetElement Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0d91-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="a0d91-114">Dizideki verilen öğe temsil eden bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="a0d91-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="a0d91-115">GetElementAtPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0d91-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="a0d91-116">Verilen konumunda dizinin sıfır tabanlı, tek boyutlu bir dizi olarak davranma öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="a0d91-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="a0d91-117">GetElementType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0d91-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="a0d91-118">Dizideki öğeleri basit türünü alır.</span><span class="sxs-lookup"><span data-stu-id="a0d91-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="a0d91-119">GetRank Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0d91-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="a0d91-120">Dizideki boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a0d91-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="a0d91-121">HasBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a0d91-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="a0d91-122">Dizi temel dizinleri olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a0d91-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0d91-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a0d91-123">Remarks</span></span>  
 <span data-ttu-id="a0d91-124">`ICorDebugArrayValue`tek boyutlu ve çok boyutlu diziler destekler.</span><span class="sxs-lookup"><span data-stu-id="a0d91-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0d91-125">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a0d91-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0d91-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a0d91-126">Requirements</span></span>  
 <span data-ttu-id="a0d91-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0d91-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0d91-128">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0d91-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0d91-129">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0d91-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0d91-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0d91-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d91-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0d91-131">See Also</span></span>  
 [<span data-ttu-id="a0d91-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a0d91-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
