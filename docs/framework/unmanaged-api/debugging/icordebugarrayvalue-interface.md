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
ms.openlocfilehash: 0944f3379c18cba56ab65fe40a5b94a64d8a8991
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778197"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="2179b-102">ICorDebugArrayValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2179b-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="2179b-103">Tek boyutlu veya çok boyutlu bir diziyi temsil eden ICorDebugHeapValue öğesinin alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2179b-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2179b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2179b-104">Methods</span></span>  
  
|<span data-ttu-id="2179b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2179b-105">Method</span></span>|<span data-ttu-id="2179b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2179b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2179b-107">GetBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2179b-107">GetBaseIndicies Method</span></span>](icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="2179b-108">Dizideki her boyutun temel dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="2179b-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="2179b-109">GetCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2179b-109">GetCount Method</span></span>](icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="2179b-110">Dizideki toplam öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="2179b-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="2179b-111">GetDimensions Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2179b-111">GetDimensions Method</span></span>](icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="2179b-112">Dizinin boyutlarını alır.</span><span class="sxs-lookup"><span data-stu-id="2179b-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="2179b-113">GetElement Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2179b-113">GetElement Method</span></span>](icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="2179b-114">Dizide verilen öğeyi temsil eden bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="2179b-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="2179b-115">GetElementAtPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2179b-115">GetElementAtPosition Method</span></span>](icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="2179b-116">Diziyi sıfır tabanlı, tek boyutlu bir dizi olarak düşünerek belirtilen konumdaki öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="2179b-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="2179b-117">GetElementType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2179b-117">GetElementType Method</span></span>](icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="2179b-118">Dizideki öğelerin basit türünü alır.</span><span class="sxs-lookup"><span data-stu-id="2179b-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="2179b-119">GetRank Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2179b-119">GetRank Method</span></span>](icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="2179b-120">Dizideki boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="2179b-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="2179b-121">HasBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2179b-121">HasBaseIndicies Method</span></span>](icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="2179b-122">Dizinin temel dizinlere sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="2179b-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2179b-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2179b-123">Remarks</span></span>  
 <span data-ttu-id="2179b-124">`ICorDebugArrayValue` hem tek boyutlu hem çok boyutlu dizileri destekler.</span><span class="sxs-lookup"><span data-stu-id="2179b-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2179b-125">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="2179b-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2179b-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2179b-126">Requirements</span></span>  
 <span data-ttu-id="2179b-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2179b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2179b-128">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2179b-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2179b-129">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2179b-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2179b-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2179b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2179b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2179b-131">See also</span></span>

- [<span data-ttu-id="2179b-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2179b-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
