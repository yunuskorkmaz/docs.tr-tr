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
ms.openlocfilehash: 9b9a301714ea60b4e3220eb75721e56e39bd9659
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139936"
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="b05a2-102">ICorDebugThread2::GetActiveFunctions Metodu</span><span class="sxs-lookup"><span data-stu-id="b05a2-102">ICorDebugThread2::GetActiveFunctions Method</span></span>
<span data-ttu-id="b05a2-103">Bu iş parçacığı çerçevelerinin her birinde etkin işlev hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="b05a2-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b05a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b05a2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b05a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b05a2-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="b05a2-106">'ndaki `pFunctions` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="b05a2-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="b05a2-107">dışı `pFunctions` dizisinde döndürülen nesne sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b05a2-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="b05a2-108">Döndürülen nesne sayısı, yığındaki yönetilen çerçeve sayısına eşit olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b05a2-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="b05a2-109">[in, out] Her biri bu iş parçacığı çerçevelerinin etkin işlevleri hakkında bilgi içeren bir COR_ACTIVE_FUNCTION nesneleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="b05a2-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="b05a2-110">İlk öğe yaprak çerçeve için kullanılacaktır ve bu nedenle yığının köküne geri dönün.</span><span class="sxs-lookup"><span data-stu-id="b05a2-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b05a2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b05a2-111">Remarks</span></span>  
 <span data-ttu-id="b05a2-112">`pFunctions` girişte null ise, `GetActiveFunctions` yalnızca yığında olan işlevlerin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b05a2-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="b05a2-113">Diğer bir deyişle, `pFunctions` girişte null ise, `GetActiveFunctions` yalnızca `pcFunctions`bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="b05a2-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="b05a2-114">`GetActiveFunctions` yöntemi, bir yığın izlemesinde çerçevelerden aynı bilgileri elde etmek için en iyi duruma getirme amaçlıdır ve yalnızca tam yığın izlemesinde bir ICorDebugILFrame nesnesine sahip olacak çerçeveleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b05a2-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b05a2-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b05a2-115">Requirements</span></span>  
 <span data-ttu-id="b05a2-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b05a2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b05a2-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b05a2-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b05a2-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b05a2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b05a2-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b05a2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
