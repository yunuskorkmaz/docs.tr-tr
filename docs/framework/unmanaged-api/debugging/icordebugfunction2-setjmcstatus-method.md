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
ms.openlocfilehash: 55f219b5b834f365b87440e69bfa7d2c4e519235
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696103"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="c98b1-102">ICorDebugFunction2::SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c98b1-102">ICorDebugFunction2::SetJMCStatus Method</span></span>

<span data-ttu-id="c98b1-103">Yalnızca kendi kodum Adımlama için bu ICorDebugFunction2 tarafından temsil edilen işlevi işaretler.</span><span class="sxs-lookup"><span data-stu-id="c98b1-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c98b1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c98b1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c98b1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c98b1-105">Parameters</span></span>  

 `bIsJustMyCode`  
 <span data-ttu-id="c98b1-106">'ndaki `true` İşlevi Kullanıcı kodu olarak işaretlemek için olarak ayarlayın; Aksi takdirde, olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="c98b1-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="c98b1-107">Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="c98b1-107">Return Values</span></span>  
  
|<span data-ttu-id="c98b1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c98b1-108">HRESULT</span></span>|<span data-ttu-id="c98b1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c98b1-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c98b1-110">İşlev başarıyla işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="c98b1-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="c98b1-111">İşlev, hata ayıklanamadığından Kullanıcı kodu olarak işaretlenemedi.</span><span class="sxs-lookup"><span data-stu-id="c98b1-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c98b1-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c98b1-112">Remarks</span></span>  

 <span data-ttu-id="c98b1-113">Bir Yalnızca kendi kodum Stepper, Kullanıcı olmayan kodu atlar.</span><span class="sxs-lookup"><span data-stu-id="c98b1-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="c98b1-114">Kullanıcı kodu hata ayıklanabilir kodunun bir alt kümesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c98b1-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c98b1-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c98b1-115">Requirements</span></span>  

 <span data-ttu-id="c98b1-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c98b1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c98b1-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c98b1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c98b1-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c98b1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c98b1-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c98b1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
