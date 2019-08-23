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
ms.openlocfilehash: 99bd3e9ae1faec1b71933681fadf4816b4789c98
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952217"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="f2300-102">ICorDebugArrayValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2300-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="f2300-103">Tek boyutlu veya çok boyutlu bir diziyi temsil eden ICorDebugHeapValue öğesinin alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f2300-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f2300-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f2300-104">Methods</span></span>  
  
|<span data-ttu-id="f2300-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f2300-105">Method</span></span>|<span data-ttu-id="f2300-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2300-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f2300-107">GetBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2300-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="f2300-108">Dizideki her boyutun temel dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="f2300-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="f2300-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2300-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="f2300-110">Dizideki toplam öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="f2300-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="f2300-111">GetDimensions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2300-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="f2300-112">Dizinin boyutlarını alır.</span><span class="sxs-lookup"><span data-stu-id="f2300-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="f2300-113">GetElement Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2300-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="f2300-114">Dizide verilen öğeyi temsil eden bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f2300-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="f2300-115">GetElementAtPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2300-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="f2300-116">Diziyi sıfır tabanlı, tek boyutlu bir dizi olarak düşünerek belirtilen konumdaki öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="f2300-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="f2300-117">GetElementType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2300-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="f2300-118">Dizideki öğelerin basit türünü alır.</span><span class="sxs-lookup"><span data-stu-id="f2300-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="f2300-119">GetRank Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2300-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="f2300-120">Dizideki boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="f2300-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="f2300-121">HasBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2300-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="f2300-122">Dizinin temel dizinlere sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="f2300-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2300-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2300-123">Remarks</span></span>  
 <span data-ttu-id="f2300-124">`ICorDebugArrayValue`hem tek boyutlu hem çok boyutlu dizileri destekler.</span><span class="sxs-lookup"><span data-stu-id="f2300-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2300-125">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="f2300-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2300-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2300-126">Requirements</span></span>  
 <span data-ttu-id="f2300-127">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2300-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2300-128">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f2300-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2300-129">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f2300-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2300-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2300-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2300-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2300-131">See also</span></span>

- [<span data-ttu-id="f2300-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f2300-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
