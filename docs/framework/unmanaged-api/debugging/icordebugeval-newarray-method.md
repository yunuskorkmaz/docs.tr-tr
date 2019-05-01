---
title: ICorDebugEval::NewArray Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1abe307e3b9fa607912f98e456a11176eb17c56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934764"
---
# <a name="icordebugevalnewarray-method"></a><span data-ttu-id="e3585-102">ICorDebugEval::NewArray Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3585-102">ICorDebugEval::NewArray Method</span></span>
<span data-ttu-id="e3585-103">Belirtilen öğe türü ve boyut yeni bir dizi ayırır.</span><span class="sxs-lookup"><span data-stu-id="e3585-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
 <span data-ttu-id="e3585-104">Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e3585-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="e3585-105">Kullanım [Icordebugeval2::newparameterizedarray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) yerine.</span><span class="sxs-lookup"><span data-stu-id="e3585-105">Use [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3585-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3585-106">Syntax</span></span>  
  
```  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3585-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e3585-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="e3585-108">[in] Dizinin öğe türü belirtir CorElementType sabit listesi değeri.</span><span class="sxs-lookup"><span data-stu-id="e3585-108">[in] A value of the CorElementType enumeration that specifies the element type of the array.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="e3585-109">[in] Öğe sınıfı belirten Icordebugclass nesnesine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e3585-109">[in] A pointer to a ICorDebugClass object that specifies the class of the element.</span></span> <span data-ttu-id="e3585-110">Bu değer, öğe türü basit bir tür ise null olabilir.</span><span class="sxs-lookup"><span data-stu-id="e3585-110">This value may be null if the element type is a primitive type.</span></span>  
  
 `rank`  
 <span data-ttu-id="e3585-111">[in] Dizinin boyut sayısı.</span><span class="sxs-lookup"><span data-stu-id="e3585-111">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="e3585-112">.NET Framework 2.0 sürümünde, bu değeri 1 olmalı.</span><span class="sxs-lookup"><span data-stu-id="e3585-112">In the .NET Framework 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="e3585-113">[in] Dizinin her boyutunun bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="e3585-113">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="e3585-114">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e3585-114">[in] Optional.</span></span> <span data-ttu-id="e3585-115">Dizinin her boyutunun alt sınırı.</span><span class="sxs-lookup"><span data-stu-id="e3585-115">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="e3585-116">Bu değer belirtilmezse, her boyut için alt sınırı sıfır varsayılır.</span><span class="sxs-lookup"><span data-stu-id="e3585-116">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3585-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3585-117">Remarks</span></span>  
 <span data-ttu-id="e3585-118">Dizinin her zaman iş parçacığı gerçekleştirmektedir uygulama etki alanında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e3585-118">The array is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3585-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3585-119">Requirements</span></span>  
 <span data-ttu-id="e3585-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3585-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3585-121">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3585-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3585-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3585-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3585-123">**.NET framework sürümleri:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="e3585-123">**.NET Framework Versions:** 1.1, 1.0</span></span>
