---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugClass2:: SetJMCStatus yöntemi'
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
ms.openlocfilehash: 28859522052fd9587dc3890eb4137929dbdc6763
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711485"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="54cef-103">ICorDebugClass2::SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54cef-103">ICorDebugClass2::SetJMCStatus Method</span></span>

<span data-ttu-id="54cef-104">Sınıfının her yöntemi için, yöntemin Kullanıcı tanımlı kod olup olmadığını belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="54cef-104">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54cef-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54cef-105">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54cef-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54cef-106">Parameters</span></span>  

 `bIsJustMyCode`  
 <span data-ttu-id="54cef-107">'ndaki `true` Metodun Kullanıcı tanımlı kod olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="54cef-107">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54cef-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54cef-108">Remarks</span></span>  

 <span data-ttu-id="54cef-109">Just-Code (JMC) Stepper, Kullanıcı tanımlı olmayan kodu atlar.</span><span class="sxs-lookup"><span data-stu-id="54cef-109">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="54cef-110">Kullanıcı tanımlı kodun bir hata ayıklanabilir kodu alt kümesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="54cef-110">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="54cef-111">`SetJMCStatus` Tüm diğer yöntemler için değeri başarıyla ayarlasa bile, herhangi bir yöntem için değeri ayarlayamazsa, bir S_FALSE HRESULT değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="54cef-111">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54cef-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54cef-112">Requirements</span></span>  

 <span data-ttu-id="54cef-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54cef-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54cef-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="54cef-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54cef-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="54cef-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54cef-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54cef-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
