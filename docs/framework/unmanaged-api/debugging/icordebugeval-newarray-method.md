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
ms.openlocfilehash: ef6cbe2cef3c52d9a4b47ff77e8aeb5159e89c76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729765"
---
# <a name="icordebugevalnewarray-method"></a><span data-ttu-id="c4712-102">ICorDebugEval::NewArray Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4712-102">ICorDebugEval::NewArray Method</span></span>

<span data-ttu-id="c4712-103">Belirtilen öğe türü ve boyutlarının yeni bir dizisini ayırır.</span><span class="sxs-lookup"><span data-stu-id="c4712-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
 <span data-ttu-id="c4712-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="c4712-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c4712-105">Bunun yerine [ICorDebugEval2:: NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4712-105">Use [ICorDebugEval2::NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4712-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c4712-106">Syntax</span></span>  
  
```cpp  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4712-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4712-107">Parameters</span></span>  

 `elementType`  
 <span data-ttu-id="c4712-108">'ndaki Dizinin öğe türünü belirten CorElementType numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="c4712-108">[in] A value of the CorElementType enumeration that specifies the element type of the array.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="c4712-109">'ndaki Öğesinin sınıfını belirten ICorDebugClass nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c4712-109">[in] A pointer to a ICorDebugClass object that specifies the class of the element.</span></span> <span data-ttu-id="c4712-110">Öğe türü basit bir tür ise bu değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="c4712-110">This value may be null if the element type is a primitive type.</span></span>  
  
 `rank`  
 <span data-ttu-id="c4712-111">'ndaki Dizinin boyut sayısı.</span><span class="sxs-lookup"><span data-stu-id="c4712-111">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="c4712-112">.NET Framework 2,0 ' de, bu değer 1 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4712-112">In the .NET Framework 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="c4712-113">'ndaki Dizinin her boyutunun bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="c4712-113">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="c4712-114">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="c4712-114">[in] Optional.</span></span> <span data-ttu-id="c4712-115">Dizi boyutunun alt sınırı.</span><span class="sxs-lookup"><span data-stu-id="c4712-115">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="c4712-116">Bu değer atlanırsa, her bir boyut için sıfırdan daha düşük bir sınır varsayılır.</span><span class="sxs-lookup"><span data-stu-id="c4712-116">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4712-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4712-117">Remarks</span></span>  

 <span data-ttu-id="c4712-118">Dizi, iş parçacığının Şu anda yürütüldüğü uygulama etki alanında her zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c4712-118">The array is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4712-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4712-119">Requirements</span></span>  

 <span data-ttu-id="c4712-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4712-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4712-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c4712-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4712-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c4712-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4712-123">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="c4712-123">**.NET Framework Versions:** 1.1, 1.0</span></span>
