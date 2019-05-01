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
ms.openlocfilehash: ed13f78d5a1f6d54b12c86613715f4878a521bfa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993973"
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="de89a-102">ICorDebugThread2::GetActiveFunctions Metodu</span><span class="sxs-lookup"><span data-stu-id="de89a-102">ICorDebugThread2::GetActiveFunctions Method</span></span>
<span data-ttu-id="de89a-103">Bu bu iş parçacığının çerçevede etkin işlevi hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="de89a-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de89a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de89a-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de89a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="de89a-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="de89a-106">[in] Boyutu `pFunctions` dizisi.</span><span class="sxs-lookup"><span data-stu-id="de89a-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="de89a-107">[out] Döndürülen nesne sayısı için bir işaretçi `pFunctions` dizisi.</span><span class="sxs-lookup"><span data-stu-id="de89a-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="de89a-108">Döndürülen nesne sayısını yığın üzerinde yönetilen çerçeve sayısı eşit olacaktır.</span><span class="sxs-lookup"><span data-stu-id="de89a-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="de89a-109">[out içinde] Bir dizi cor_actıve_functıon nesnelerin her biri bu iş parçacığının çerçeveler etkin işlevler hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="de89a-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="de89a-110">İlk öğeyi yaprak çerçeve ve yığın kökünün vb. geri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="de89a-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de89a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de89a-111">Remarks</span></span>  
 <span data-ttu-id="de89a-112">Varsa `pFunctions` girişte, null `GetActiveFunctions` yalnızca yığında olan işlev sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="de89a-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="de89a-113">Diğer bir deyişle, `pFunctions` girişte, null `GetActiveFunctions` bir değer döndürür. yalnızca `pcFunctions`.</span><span class="sxs-lookup"><span data-stu-id="de89a-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="de89a-114">`GetActiveFunctions` Yöntemi bir iyileştirme bir yığın izlemesi çerçevelerde aynı bilgileri almaya oluşturulmuştur ve yalnızca bir Icordebugılframe nesne için tam bir yığın izlemeyle uygulamanızda zorunda kalacaktır çerçevelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="de89a-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de89a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="de89a-115">Requirements</span></span>  
 <span data-ttu-id="de89a-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de89a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de89a-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de89a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de89a-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de89a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de89a-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de89a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
