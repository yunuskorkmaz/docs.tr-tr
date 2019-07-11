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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67959b2ebbfb62b47a1b2a770e278d043fc66d21
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754924"
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="e7e4a-102">ICorDebugFunction2::SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7e4a-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="e7e4a-103">Yalnızca benim kodum bu Icordebugfunction2 tarafından temsil edilen işlevi işaretler Adımlama.</span><span class="sxs-lookup"><span data-stu-id="e7e4a-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7e4a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7e4a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7e4a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7e4a-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="e7e4a-106">[in] Kümesine `true` işlevi kullanıcı kodu; olarak işaretlemek için Aksi takdirde, kümesine `false`.</span><span class="sxs-lookup"><span data-stu-id="e7e4a-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="e7e4a-107">Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="e7e4a-107">Return Values</span></span>  
  
|<span data-ttu-id="e7e4a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7e4a-108">HRESULT</span></span>|<span data-ttu-id="e7e4a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7e4a-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e7e4a-110">İşlev başarıyla işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="e7e4a-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="e7e4a-111">İşlevi, hata ayıklaması yapamazsınız çünkü kullanıcı kodu işaretlenemez.</span><span class="sxs-lookup"><span data-stu-id="e7e4a-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7e4a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7e4a-112">Remarks</span></span>  
 <span data-ttu-id="e7e4a-113">Yalnızca kendi kodum Adımlayıcı kullanıcı olmayan kod atlar.</span><span class="sxs-lookup"><span data-stu-id="e7e4a-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="e7e4a-114">Kullanıcı kodu hata ayıklaması yapılabilir kod bir alt kümesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7e4a-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7e4a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7e4a-115">Requirements</span></span>  
 <span data-ttu-id="e7e4a-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7e4a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7e4a-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7e4a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7e4a-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7e4a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7e4a-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7e4a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
