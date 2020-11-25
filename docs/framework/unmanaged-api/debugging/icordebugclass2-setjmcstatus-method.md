---
title: ICorDebugClass2::SetJMCStatus Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
ms.openlocfilehash: 1db2c9b5e65ae150f05242172f5ea16db433bbb5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717831"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="e5ade-102">ICorDebugClass2::SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5ade-102">ICorDebugClass2::SetJMCStatus Method</span></span>

<span data-ttu-id="e5ade-103">Sınıfının her yöntemi için, yöntemin Kullanıcı tanımlı kod olup olmadığını belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e5ade-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5ade-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e5ade-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5ade-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5ade-105">Parameters</span></span>  

 `bIsJustMyCode`  
 <span data-ttu-id="e5ade-106">'ndaki `true` Metodun Kullanıcı tanımlı kod olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="e5ade-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5ade-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5ade-107">Remarks</span></span>  

 <span data-ttu-id="e5ade-108">Just-Code (JMC) Stepper, Kullanıcı tanımlı olmayan kodu atlar.</span><span class="sxs-lookup"><span data-stu-id="e5ade-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="e5ade-109">Kullanıcı tanımlı kodun bir hata ayıklanabilir kodu alt kümesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5ade-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="e5ade-110">`SetJMCStatus` Tüm diğer yöntemler için değeri başarıyla ayarlasa bile, herhangi bir yöntem için değeri ayarlayamazsa, bir S_FALSE HRESULT değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e5ade-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5ade-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5ade-111">Requirements</span></span>  

 <span data-ttu-id="e5ade-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5ade-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5ade-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e5ade-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5ade-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e5ade-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5ade-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5ade-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
