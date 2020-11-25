---
title: ICorDebugEval2::NewParameterizedObjectNoConstructor Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
ms.openlocfilehash: 796c6aa4c42a037fe612b4b1ee5267a678cf5224
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729648"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="19df2-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19df2-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>

<span data-ttu-id="19df2-103">Bir Oluşturucu yöntemini çağırmayı denemeden, belirtilen sınıfın yeni parametreli tür nesnesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="19df2-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19df2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="19df2-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19df2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="19df2-105">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="19df2-106">'ndaki Örnek oluşturulacak nesnenin sınıfını temsil eden ICorDebugClass nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="19df2-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="19df2-107">'ndaki Geçirilen tür bağımsız değişkenlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="19df2-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="19df2-108">'ndaki Her biri, örneklendiği nesnenin tür bağımsız değişkenini temsil eden bir ICorDebugType nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="19df2-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19df2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19df2-109">Remarks</span></span>  

 <span data-ttu-id="19df2-110">`NewParameterizedObjectNoConstructor`Yanlış sayıda tür bağımsız değişkeni ya da yanlış tür bağımsız değişken türleri geçirilirse yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="19df2-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19df2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19df2-111">Requirements</span></span>  

 <span data-ttu-id="19df2-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19df2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19df2-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="19df2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19df2-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="19df2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19df2-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19df2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
