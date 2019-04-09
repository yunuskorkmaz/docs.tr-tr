---
title: ICorDebugArrayValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67fd1a9174b04e42b53f2b866a1dfdd504362aa9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168395"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="a8d72-102">ICorDebugArrayValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8d72-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="a8d72-103">Bir tek boyutlu veya çok boyutlu diziyi temsil eden Icordebugheapvalue öğesinin.</span><span class="sxs-lookup"><span data-stu-id="a8d72-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8d72-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a8d72-104">Methods</span></span>  
  
|<span data-ttu-id="a8d72-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a8d72-105">Method</span></span>|<span data-ttu-id="a8d72-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8d72-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8d72-107">GetBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8d72-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="a8d72-108">Dizideki her boyutun temel dizini alır.</span><span class="sxs-lookup"><span data-stu-id="a8d72-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="a8d72-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8d72-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="a8d72-110">Dizideki öğelerin toplam sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a8d72-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="a8d72-111">GetDimensions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8d72-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="a8d72-112">Dizinin boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a8d72-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="a8d72-113">GetElement Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8d72-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="a8d72-114">Belirtilen öğe dizideki temsil eden bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="a8d72-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="a8d72-115">GetElementAtPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8d72-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="a8d72-116">Verilen konumunda dizinin sıfır tabanlı, tek boyutlu bir dizi olarak davranılması öğesini alır.</span><span class="sxs-lookup"><span data-stu-id="a8d72-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="a8d72-117">GetElementType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8d72-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="a8d72-118">Dizideki öğelerin basit türünü alır.</span><span class="sxs-lookup"><span data-stu-id="a8d72-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="a8d72-119">GetRank Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8d72-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="a8d72-120">Dizinin boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="a8d72-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="a8d72-121">HasBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8d72-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="a8d72-122">Bir dizi temel dizinleri olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a8d72-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8d72-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8d72-123">Remarks</span></span>  
 `ICorDebugArrayValue` <span data-ttu-id="a8d72-124">tek boyutlu ve çok boyutlu diziler destekler.</span><span class="sxs-lookup"><span data-stu-id="a8d72-124">supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8d72-125">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a8d72-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8d72-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8d72-126">Requirements</span></span>  
 <span data-ttu-id="a8d72-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8d72-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8d72-128">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8d72-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8d72-129">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8d72-129">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a8d72-130">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="a8d72-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a8d72-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8d72-131">See also</span></span>

- [<span data-ttu-id="a8d72-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a8d72-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
