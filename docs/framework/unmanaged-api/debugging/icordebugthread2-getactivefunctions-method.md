---
title: ICorDebugThread2::GetActiveFunctions Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ecd9446f642011b21f784019f583f49e3a70433a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="7bf1b-102">ICorDebugThread2::GetActiveFunctions Metodu</span><span class="sxs-lookup"><span data-stu-id="7bf1b-102">ICorDebugThread2::GetActiveFunctions Method</span></span>
<span data-ttu-id="7bf1b-103">Etkin işlevi hakkında bilgi her bu iş parçacığının çerçeveleri alır.</span><span class="sxs-lookup"><span data-stu-id="7bf1b-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bf1b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7bf1b-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7bf1b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7bf1b-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="7bf1b-106">[in] Boyutunu `pFunctions` dizi.</span><span class="sxs-lookup"><span data-stu-id="7bf1b-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="7bf1b-107">[out] Döndürülen nesne sayısı için bir işaretçi `pFunctions` dizi.</span><span class="sxs-lookup"><span data-stu-id="7bf1b-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="7bf1b-108">Döndürülen nesne sayısı yığında yönetilen çerçeveler sayısına eşit olur.</span><span class="sxs-lookup"><span data-stu-id="7bf1b-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="7bf1b-109">[içinde out] Her biri bu iş parçacığının çerçeveleri etkin işlevleri hakkında bilgi içeren bir dizi cor_actıve_functıon nesneleri.</span><span class="sxs-lookup"><span data-stu-id="7bf1b-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="7bf1b-110">İlk öğe yaprak çerçeve ve yığın kökünde vb. geri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7bf1b-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bf1b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bf1b-111">Remarks</span></span>  
 <span data-ttu-id="7bf1b-112">Varsa `pFunctions` giriş, null `GetActiveFunctions` yalnızca olduğundan yığınındaki işlevler sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7bf1b-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="7bf1b-113">Diğer bir deyişle, `pFunctions` giriş, null `GetActiveFunctions` bir değer döndürür yalnızca `pcFunctions`.</span><span class="sxs-lookup"><span data-stu-id="7bf1b-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="7bf1b-114">`GetActiveFunctions` Yöntemi bir iyileştirme yığın izlemesi çerçevelere gelen aynı bilgi alma yöneliktir ve yalnızca Icordebugılframe nesne için tam yığın izlemesinde beklendiğinden çerçevelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7bf1b-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bf1b-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7bf1b-115">Requirements</span></span>  
 <span data-ttu-id="7bf1b-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bf1b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bf1b-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7bf1b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bf1b-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bf1b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bf1b-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bf1b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
