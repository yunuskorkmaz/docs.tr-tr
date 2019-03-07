---
title: ICorDebugEval2::NewParameterizedArray Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c639204fa207774b0e362f1ba8fe71937494ae2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487709"
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="7a1d3-102">ICorDebugEval2::NewParameterizedArray Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a1d3-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="7a1d3-103">Belirtilen öğe türü ve boyut yeni bir dizi ayırır.</span><span class="sxs-lookup"><span data-stu-id="7a1d3-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a1d3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7a1d3-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a1d3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7a1d3-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="7a1d3-106">[in] Bir dizide depolanan öğenin türünü temsil eden bir Icordebugtype nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7a1d3-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="7a1d3-107">[in] Dizinin boyut sayısı.</span><span class="sxs-lookup"><span data-stu-id="7a1d3-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="7a1d3-108">.NET Framework sürüm 2. 0'da, bu değeri 1 olmalı.</span><span class="sxs-lookup"><span data-stu-id="7a1d3-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="7a1d3-109">[in] Dizinin her boyutunun bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="7a1d3-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="7a1d3-110">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="7a1d3-110">[in] Optional.</span></span> <span data-ttu-id="7a1d3-111">Dizinin her boyutunun alt sınırı.</span><span class="sxs-lookup"><span data-stu-id="7a1d3-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="7a1d3-112">Bu değer belirtilmezse, her boyut için alt sınırı sıfır varsayılır.</span><span class="sxs-lookup"><span data-stu-id="7a1d3-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a1d3-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a1d3-113">Remarks</span></span>  
 <span data-ttu-id="7a1d3-114">Dizinin öğeleri, genel bir türün örneklerinin olabilir.</span><span class="sxs-lookup"><span data-stu-id="7a1d3-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="7a1d3-115">Dizinin her zaman iş parçacığı şu anda çalıştığı uygulama etki alanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7a1d3-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="7a1d3-116">.NET Framework 2.0, değerini `rank` 1 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7a1d3-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a1d3-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a1d3-117">Requirements</span></span>  
 <span data-ttu-id="7a1d3-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a1d3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a1d3-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a1d3-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a1d3-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a1d3-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a1d3-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a1d3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
