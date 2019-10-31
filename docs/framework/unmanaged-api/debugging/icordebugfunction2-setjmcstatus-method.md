---
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
ms.openlocfilehash: 758364b2d63343e464b727d5a1c1817533a6acea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137791"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="aa039-102">ICorDebugFunction2::SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aa039-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="aa039-103">Yalnızca kendi kodum Adımlama için bu ICorDebugFunction2 tarafından temsil edilen işlevi işaretler.</span><span class="sxs-lookup"><span data-stu-id="aa039-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa039-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa039-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa039-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aa039-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="aa039-106">'ndaki İşlevi Kullanıcı kodu olarak işaretlemek için `true` olarak ayarlayın; Aksi takdirde, `false`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="aa039-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="aa039-107">Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="aa039-107">Return Values</span></span>  
  
|<span data-ttu-id="aa039-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa039-108">HRESULT</span></span>|<span data-ttu-id="aa039-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa039-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="aa039-110">İşlev başarıyla işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="aa039-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="aa039-111">İşlev, hata ayıklanamadığından Kullanıcı kodu olarak işaretlenemedi.</span><span class="sxs-lookup"><span data-stu-id="aa039-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa039-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa039-112">Remarks</span></span>  
 <span data-ttu-id="aa039-113">Bir Yalnızca kendi kodum Stepper, Kullanıcı olmayan kodu atlar.</span><span class="sxs-lookup"><span data-stu-id="aa039-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="aa039-114">Kullanıcı kodu hata ayıklanabilir kodunun bir alt kümesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa039-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa039-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa039-115">Requirements</span></span>  
 <span data-ttu-id="aa039-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa039-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa039-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aa039-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa039-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="aa039-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa039-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa039-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
