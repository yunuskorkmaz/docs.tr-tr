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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168395"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="99283-102">ICorDebugArrayValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99283-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="99283-103">Bir tek boyutlu veya çok boyutlu diziyi temsil eden Icordebugheapvalue öğesinin.</span><span class="sxs-lookup"><span data-stu-id="99283-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99283-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="99283-104">Methods</span></span>  
  
|<span data-ttu-id="99283-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="99283-105">Method</span></span>|<span data-ttu-id="99283-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99283-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99283-107">GetBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99283-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="99283-108">Dizideki her boyutun temel dizini alır.</span><span class="sxs-lookup"><span data-stu-id="99283-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="99283-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99283-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="99283-110">Dizideki öğelerin toplam sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="99283-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="99283-111">GetDimensions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99283-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="99283-112">Dizinin boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="99283-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="99283-113">GetElement Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99283-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="99283-114">Belirtilen öğe dizideki temsil eden bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="99283-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="99283-115">GetElementAtPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99283-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="99283-116">Verilen konumunda dizinin sıfır tabanlı, tek boyutlu bir dizi olarak davranılması öğesini alır.</span><span class="sxs-lookup"><span data-stu-id="99283-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="99283-117">GetElementType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99283-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="99283-118">Dizideki öğelerin basit türünü alır.</span><span class="sxs-lookup"><span data-stu-id="99283-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="99283-119">GetRank Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99283-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="99283-120">Dizinin boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="99283-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="99283-121">HasBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99283-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="99283-122">Bir dizi temel dizinleri olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="99283-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99283-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99283-123">Remarks</span></span>  
 <span data-ttu-id="99283-124">`ICorDebugArrayValue` tek boyutlu ve çok boyutlu diziler destekler.</span><span class="sxs-lookup"><span data-stu-id="99283-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99283-125">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="99283-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99283-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99283-126">Requirements</span></span>  
 <span data-ttu-id="99283-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99283-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99283-128">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99283-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99283-129">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99283-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99283-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99283-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99283-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99283-131">See also</span></span>

- [<span data-ttu-id="99283-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="99283-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
