---
description: 'Bu konuda daha fazla bilgi edinin: ıcorı, Garrayvalue arabirimi'
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
ms.openlocfilehash: 2b91c910b9444b061b4a6bea715667bca6a4629c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722899"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="e40e6-103">ICorDebugArrayValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e40e6-103">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="e40e6-104">Tek boyutlu veya çok boyutlu bir diziyi temsil eden ICorDebugHeapValue öğesinin alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e40e6-104">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e40e6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e40e6-105">Methods</span></span>  
  
|<span data-ttu-id="e40e6-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e40e6-106">Method</span></span>|<span data-ttu-id="e40e6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e40e6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e40e6-108">GetBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e40e6-108">GetBaseIndicies Method</span></span>](icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="e40e6-109">Dizideki her boyutun temel dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="e40e6-109">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="e40e6-110">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e40e6-110">GetCount Method</span></span>](icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="e40e6-111">Dizideki toplam öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="e40e6-111">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="e40e6-112">GetDimensions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e40e6-112">GetDimensions Method</span></span>](icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="e40e6-113">Dizinin boyutlarını alır.</span><span class="sxs-lookup"><span data-stu-id="e40e6-113">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="e40e6-114">GetElement Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e40e6-114">GetElement Method</span></span>](icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="e40e6-115">Dizide verilen öğeyi temsil eden bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="e40e6-115">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="e40e6-116">GetElementAtPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e40e6-116">GetElementAtPosition Method</span></span>](icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="e40e6-117">Diziyi sıfır tabanlı, tek boyutlu bir dizi olarak düşünerek belirtilen konumdaki öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="e40e6-117">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="e40e6-118">GetElementType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e40e6-118">GetElementType Method</span></span>](icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="e40e6-119">Dizideki öğelerin basit türünü alır.</span><span class="sxs-lookup"><span data-stu-id="e40e6-119">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="e40e6-120">GetRank Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e40e6-120">GetRank Method</span></span>](icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="e40e6-121">Dizideki boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="e40e6-121">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="e40e6-122">HasBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e40e6-122">HasBaseIndicies Method</span></span>](icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="e40e6-123">Dizinin temel dizinlere sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="e40e6-123">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e40e6-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e40e6-124">Remarks</span></span>  

 <span data-ttu-id="e40e6-125">`ICorDebugArrayValue` hem tek boyutlu hem çok boyutlu dizileri destekler.</span><span class="sxs-lookup"><span data-stu-id="e40e6-125">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e40e6-126">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="e40e6-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e40e6-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e40e6-127">Requirements</span></span>  

 <span data-ttu-id="e40e6-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e40e6-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e40e6-129">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e40e6-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e40e6-130">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e40e6-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e40e6-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e40e6-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e40e6-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e40e6-132">See also</span></span>

- [<span data-ttu-id="e40e6-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e40e6-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
