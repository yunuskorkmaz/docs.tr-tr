---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugEval2:: NewParameterizedArray Yöntemi'
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
ms.openlocfilehash: 0ce8582328013ad02357361f05efb55ade8780e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693752"
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="9093a-103">ICorDebugEval2::NewParameterizedArray Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9093a-103">ICorDebugEval2::NewParameterizedArray Method</span></span>

<span data-ttu-id="9093a-104">Belirtilen öğe türü ve boyutlarının yeni bir dizisini ayırır.</span><span class="sxs-lookup"><span data-stu-id="9093a-104">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9093a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9093a-105">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9093a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9093a-106">Parameters</span></span>  

 `pElementType`  
 <span data-ttu-id="9093a-107">'ndaki Dizide depolanan öğe türünü temsil eden ICorDebugType nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9093a-107">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="9093a-108">'ndaki Dizinin boyut sayısı.</span><span class="sxs-lookup"><span data-stu-id="9093a-108">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="9093a-109">.NET Framework sürüm 2,0 ' de, bu değer 1 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9093a-109">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="9093a-110">'ndaki Dizinin her boyutunun bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="9093a-110">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="9093a-111">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="9093a-111">[in] Optional.</span></span> <span data-ttu-id="9093a-112">Dizi boyutunun alt sınırı.</span><span class="sxs-lookup"><span data-stu-id="9093a-112">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="9093a-113">Bu değer atlanırsa, her bir boyut için sıfırdan daha düşük bir sınır varsayılır.</span><span class="sxs-lookup"><span data-stu-id="9093a-113">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9093a-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9093a-114">Remarks</span></span>  

 <span data-ttu-id="9093a-115">Dizinin öğeleri, genel bir türün örnekleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="9093a-115">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="9093a-116">Dizi, iş parçacığının çalışmakta olduğu uygulama etki alanında her zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9093a-116">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="9093a-117">.NET Framework 2,0 ' de, değeri 1 olmalıdır `rank` .</span><span class="sxs-lookup"><span data-stu-id="9093a-117">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9093a-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9093a-118">Requirements</span></span>  

 <span data-ttu-id="9093a-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9093a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9093a-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9093a-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9093a-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9093a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9093a-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9093a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
