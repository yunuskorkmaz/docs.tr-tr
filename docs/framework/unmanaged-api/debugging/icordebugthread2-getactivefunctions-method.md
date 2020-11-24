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
ms.openlocfilehash: 2d5674d6b5962ca539de02cda1e5658daed83622
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678759"
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="e6ac2-102">ICorDebugThread2::GetActiveFunctions Metodu</span><span class="sxs-lookup"><span data-stu-id="e6ac2-102">ICorDebugThread2::GetActiveFunctions Method</span></span>

<span data-ttu-id="e6ac2-103">Bu iş parçacığı çerçevelerinin her birinde etkin işlev hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="e6ac2-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6ac2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e6ac2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6ac2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6ac2-105">Parameters</span></span>  

 `cFunctions`  
 <span data-ttu-id="e6ac2-106">'ndaki `pFunctions` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="e6ac2-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="e6ac2-107">dışı Dizide döndürülen nesne sayısına yönelik bir işaretçi `pFunctions` .</span><span class="sxs-lookup"><span data-stu-id="e6ac2-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="e6ac2-108">Döndürülen nesne sayısı, yığındaki yönetilen çerçeve sayısına eşit olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e6ac2-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="e6ac2-109">[in, out] Her biri bu iş parçacığı çerçevelerinden etkin işlevlerle ilgili bilgiler içeren COR_ACTIVE_FUNCTION nesnelerden oluşan bir dizi.</span><span class="sxs-lookup"><span data-stu-id="e6ac2-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="e6ac2-110">İlk öğe yaprak çerçeve için kullanılacaktır ve bu nedenle yığının köküne geri dönün.</span><span class="sxs-lookup"><span data-stu-id="e6ac2-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6ac2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6ac2-111">Remarks</span></span>  

 <span data-ttu-id="e6ac2-112">`pFunctions`Girişte null ise, `GetActiveFunctions` yalnızca yığında olan işlev sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e6ac2-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="e6ac2-113">Yani, `pFunctions` girişte null ise, `GetActiveFunctions` yalnızca içinde bir değer döndürür `pcFunctions` .</span><span class="sxs-lookup"><span data-stu-id="e6ac2-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="e6ac2-114">`GetActiveFunctions`Yöntemi, bir yığın izlemesinde çerçevelerden aynı bilgileri elde etmek için en iyi duruma getirme amaçlıdır ve yalnızca tam yığın izlemesinde bir ICorDebugILFrame nesnesine sahip olacak çerçeveleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e6ac2-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6ac2-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6ac2-115">Requirements</span></span>  

 <span data-ttu-id="e6ac2-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6ac2-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6ac2-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e6ac2-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6ac2-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e6ac2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6ac2-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6ac2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
