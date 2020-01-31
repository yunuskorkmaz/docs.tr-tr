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
ms.openlocfilehash: 13ac5379992f4e768b09a03d31591143ba9bf627
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788718"
---
# <a name="icordebugevalnewarray-method"></a><span data-ttu-id="b1873-102">ICorDebugEval::NewArray Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1873-102">ICorDebugEval::NewArray Method</span></span>
<span data-ttu-id="b1873-103">Belirtilen öğe türü ve boyutlarının yeni bir dizisini ayırır.</span><span class="sxs-lookup"><span data-stu-id="b1873-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
 <span data-ttu-id="b1873-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="b1873-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="b1873-105">Bunun yerine [ICorDebugEval2:: NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="b1873-105">Use [ICorDebugEval2::NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1873-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1873-106">Syntax</span></span>  
  
```cpp  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1873-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1873-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="b1873-108">'ndaki Dizinin öğe türünü belirten CorElementType numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="b1873-108">[in] A value of the CorElementType enumeration that specifies the element type of the array.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="b1873-109">'ndaki Öğesinin sınıfını belirten ICorDebugClass nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b1873-109">[in] A pointer to a ICorDebugClass object that specifies the class of the element.</span></span> <span data-ttu-id="b1873-110">Öğe türü basit bir tür ise bu değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="b1873-110">This value may be null if the element type is a primitive type.</span></span>  
  
 `rank`  
 <span data-ttu-id="b1873-111">'ndaki Dizinin boyut sayısı.</span><span class="sxs-lookup"><span data-stu-id="b1873-111">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="b1873-112">.NET Framework 2,0 ' de, bu değer 1 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b1873-112">In the .NET Framework 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="b1873-113">'ndaki Dizinin her boyutunun bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b1873-113">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="b1873-114">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="b1873-114">[in] Optional.</span></span> <span data-ttu-id="b1873-115">Dizi boyutunun alt sınırı.</span><span class="sxs-lookup"><span data-stu-id="b1873-115">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="b1873-116">Bu değer atlanırsa, her bir boyut için sıfırdan daha düşük bir sınır varsayılır.</span><span class="sxs-lookup"><span data-stu-id="b1873-116">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1873-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1873-117">Remarks</span></span>  
 <span data-ttu-id="b1873-118">Dizi, iş parçacığının Şu anda yürütüldüğü uygulama etki alanında her zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b1873-118">The array is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1873-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1873-119">Requirements</span></span>  
 <span data-ttu-id="b1873-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1873-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1873-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b1873-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1873-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b1873-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1873-123">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="b1873-123">**.NET Framework Versions:** 1.1, 1.0</span></span>
