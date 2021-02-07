---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugFunction2:: SetJMCStatus yöntemi'
title: ICorDebugFunction2::SetJMCStatus Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
ms.openlocfilehash: d2df9d47808b0220a91bd344e7600f8d16eccdb4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692197"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="03a0c-103">ICorDebugFunction2::SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03a0c-103">ICorDebugFunction2::SetJMCStatus Method</span></span>

<span data-ttu-id="03a0c-104">Yalnızca kendi kodum Adımlama için bu ICorDebugFunction2 tarafından temsil edilen işlevi işaretler.</span><span class="sxs-lookup"><span data-stu-id="03a0c-104">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03a0c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03a0c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03a0c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03a0c-106">Parameters</span></span>  

 `bIsJustMyCode`  
 <span data-ttu-id="03a0c-107">'ndaki `true` İşlevi Kullanıcı kodu olarak işaretlemek için olarak ayarlayın; Aksi takdirde, olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="03a0c-107">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="03a0c-108">Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="03a0c-108">Return Values</span></span>  
  
|<span data-ttu-id="03a0c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03a0c-109">HRESULT</span></span>|<span data-ttu-id="03a0c-110">Description</span><span class="sxs-lookup"><span data-stu-id="03a0c-110">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="03a0c-111">İşlev başarıyla işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="03a0c-111">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="03a0c-112">İşlev, hata ayıklanamadığından Kullanıcı kodu olarak işaretlenemedi.</span><span class="sxs-lookup"><span data-stu-id="03a0c-112">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03a0c-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03a0c-113">Remarks</span></span>  

 <span data-ttu-id="03a0c-114">Bir Yalnızca kendi kodum Stepper, Kullanıcı olmayan kodu atlar.</span><span class="sxs-lookup"><span data-stu-id="03a0c-114">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="03a0c-115">Kullanıcı kodu hata ayıklanabilir kodunun bir alt kümesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03a0c-115">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03a0c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03a0c-116">Requirements</span></span>  

 <span data-ttu-id="03a0c-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03a0c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03a0c-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="03a0c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03a0c-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="03a0c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03a0c-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03a0c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
