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
ms.openlocfilehash: 9d589bfc3093d03d87acb47ade0fc6c972bcd335
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976115"
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="5fcbb-102">ICorDebugEval2::NewParameterizedArray Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5fcbb-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="5fcbb-103">Belirtilen öğe türü ve boyutlarının yeni bir dizisini ayırır.</span><span class="sxs-lookup"><span data-stu-id="5fcbb-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fcbb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fcbb-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fcbb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5fcbb-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="5fcbb-106">'ndaki Dizide depolanan öğe türünü temsil eden ICorDebugType nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5fcbb-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="5fcbb-107">'ndaki Dizinin boyut sayısı.</span><span class="sxs-lookup"><span data-stu-id="5fcbb-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="5fcbb-108">.NET Framework sürüm 2,0 ' de, bu değer 1 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fcbb-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="5fcbb-109">'ndaki Dizinin her boyutunun bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="5fcbb-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="5fcbb-110">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="5fcbb-110">[in] Optional.</span></span> <span data-ttu-id="5fcbb-111">Dizi boyutunun alt sınırı.</span><span class="sxs-lookup"><span data-stu-id="5fcbb-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="5fcbb-112">Bu değer atlanırsa, her bir boyut için sıfırdan daha düşük bir sınır varsayılır.</span><span class="sxs-lookup"><span data-stu-id="5fcbb-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fcbb-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5fcbb-113">Remarks</span></span>  
 <span data-ttu-id="5fcbb-114">Dizinin öğeleri, genel bir türün örnekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="5fcbb-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="5fcbb-115">Dizi, iş parçacığının çalışmakta olduğu uygulama etki alanında her zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5fcbb-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="5fcbb-116">.NET Framework 2,0 ' de, değeri `rank` 1 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fcbb-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fcbb-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5fcbb-117">Requirements</span></span>  
 <span data-ttu-id="5fcbb-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fcbb-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fcbb-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5fcbb-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fcbb-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5fcbb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fcbb-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fcbb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
