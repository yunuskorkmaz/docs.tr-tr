---
title: ICorDebugThread2::GetActiveFunctions Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7ed7787f0302826cab67664780177f05e551199
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421112"
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="a571f-102">ICorDebugThread2::GetActiveFunctions Metodu</span><span class="sxs-lookup"><span data-stu-id="a571f-102">ICorDebugThread2::GetActiveFunctions Method</span></span>
<span data-ttu-id="a571f-103">Etkin işlevi hakkında bilgi her bu iş parçacığının çerçeveleri alır.</span><span class="sxs-lookup"><span data-stu-id="a571f-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a571f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a571f-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a571f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a571f-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="a571f-106">[in] Boyutunu `pFunctions` dizi.</span><span class="sxs-lookup"><span data-stu-id="a571f-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="a571f-107">[out] Döndürülen nesne sayısı için bir işaretçi `pFunctions` dizi.</span><span class="sxs-lookup"><span data-stu-id="a571f-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="a571f-108">Döndürülen nesne sayısı yığında yönetilen çerçeveler sayısına eşit olur.</span><span class="sxs-lookup"><span data-stu-id="a571f-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="a571f-109">[içinde out] Her biri bu iş parçacığının çerçeveleri etkin işlevleri hakkında bilgi içeren bir dizi cor_actıve_functıon nesneleri.</span><span class="sxs-lookup"><span data-stu-id="a571f-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="a571f-110">İlk öğe yaprak çerçeve ve yığın kökünde vb. geri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a571f-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a571f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a571f-111">Remarks</span></span>  
 <span data-ttu-id="a571f-112">Varsa `pFunctions` giriş, null `GetActiveFunctions` yalnızca olduğundan yığınındaki işlevler sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="a571f-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="a571f-113">Diğer bir deyişle, `pFunctions` giriş, null `GetActiveFunctions` bir değer döndürür yalnızca `pcFunctions`.</span><span class="sxs-lookup"><span data-stu-id="a571f-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="a571f-114">`GetActiveFunctions` Yöntemi bir iyileştirme yığın izlemesi çerçevelere gelen aynı bilgi alma yöneliktir ve yalnızca Icordebugılframe nesne için tam yığın izlemesinde beklendiğinden çerçevelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a571f-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a571f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a571f-115">Requirements</span></span>  
 <span data-ttu-id="a571f-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a571f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a571f-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a571f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a571f-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a571f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a571f-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a571f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
