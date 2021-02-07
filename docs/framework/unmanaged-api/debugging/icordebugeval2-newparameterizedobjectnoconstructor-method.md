---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugEval2:: NewParameterizedObjectNoConstructor yöntemi'
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
ms.openlocfilehash: 8300378facb38714b50d6507b19876b8721c6229
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693596"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="63705-103">ICorDebugEval2::NewParameterizedObjectNoConstructor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63705-103">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>

<span data-ttu-id="63705-104">Bir Oluşturucu yöntemini çağırmayı denemeden, belirtilen sınıfın yeni parametreli tür nesnesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="63705-104">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63705-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63705-105">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63705-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63705-106">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="63705-107">'ndaki Örnek oluşturulacak nesnenin sınıfını temsil eden ICorDebugClass nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="63705-107">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="63705-108">'ndaki Geçirilen tür bağımsız değişkenlerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="63705-108">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="63705-109">'ndaki Her biri, örneklendiği nesnenin tür bağımsız değişkenini temsil eden bir ICorDebugType nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="63705-109">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63705-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63705-110">Remarks</span></span>  

 <span data-ttu-id="63705-111">`NewParameterizedObjectNoConstructor`Yanlış sayıda tür bağımsız değişkeni ya da yanlış tür bağımsız değişken türleri geçirilirse yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="63705-111">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63705-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63705-112">Requirements</span></span>  

 <span data-ttu-id="63705-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63705-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63705-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="63705-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63705-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="63705-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63705-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63705-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
