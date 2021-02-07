---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgeval:: NewArray Yöntemi'
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
ms.openlocfilehash: 1344a99450974369533b1c54b641c036fc64e3ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693986"
---
# <a name="icordebugevalnewarray-method"></a><span data-ttu-id="a2448-103">ICorDebugEval::NewArray Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2448-103">ICorDebugEval::NewArray Method</span></span>

<span data-ttu-id="a2448-104">Belirtilen öğe türü ve boyutlarının yeni bir dizisini ayırır.</span><span class="sxs-lookup"><span data-stu-id="a2448-104">Allocates a new array of the specified element type and dimensions.</span></span>  
  
 <span data-ttu-id="a2448-105">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="a2448-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="a2448-106">Bunun yerine [ICorDebugEval2:: NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a2448-106">Use [ICorDebugEval2::NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2448-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2448-107">Syntax</span></span>  
  
```cpp  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2448-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2448-108">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="a2448-109">'ndaki Dizinin öğe türünü belirten CorElementType numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="a2448-109">[in] A value of the CorElementType enumeration that specifies the element type of the array.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="a2448-110">'ndaki Öğesinin sınıfını belirten ICorDebugClass nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a2448-110">[in] A pointer to a ICorDebugClass object that specifies the class of the element.</span></span> <span data-ttu-id="a2448-111">Öğe türü basit bir tür ise bu değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="a2448-111">This value may be null if the element type is a primitive type.</span></span>  
  
 `rank`  
 <span data-ttu-id="a2448-112">'ndaki Dizinin boyut sayısı.</span><span class="sxs-lookup"><span data-stu-id="a2448-112">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="a2448-113">.NET Framework 2,0 ' de, bu değer 1 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a2448-113">In the .NET Framework 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="a2448-114">'ndaki Dizinin her boyutunun bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="a2448-114">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="a2448-115">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="a2448-115">[in] Optional.</span></span> <span data-ttu-id="a2448-116">Dizi boyutunun alt sınırı.</span><span class="sxs-lookup"><span data-stu-id="a2448-116">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="a2448-117">Bu değer atlanırsa, her bir boyut için sıfırdan daha düşük bir sınır varsayılır.</span><span class="sxs-lookup"><span data-stu-id="a2448-117">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2448-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2448-118">Remarks</span></span>  

 <span data-ttu-id="a2448-119">Dizi, iş parçacığının Şu anda yürütüldüğü uygulama etki alanında her zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a2448-119">The array is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2448-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2448-120">Requirements</span></span>  

 <span data-ttu-id="a2448-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2448-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2448-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a2448-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2448-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a2448-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2448-124">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="a2448-124">**.NET Framework Versions:** 1.1, 1.0</span></span>
