---
title: "ICorDebugFunction2::SetJMCStatus Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 315e036481f0454bf68b2da9e496c441ee843ba2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="e188d-102">ICorDebugFunction2::SetJMCStatus Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e188d-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="e188d-103">Sadece kendi kodumu bu Icordebugfunction2 tarafından temsil edilen işlevi işaretler atlama.</span><span class="sxs-lookup"><span data-stu-id="e188d-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e188d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e188d-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e188d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e188d-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="e188d-106">[in] Kümesine `true` işlevi kullanıcı kodu; olarak işaretlemek için Aksi takdirde kümesine `false`.</span><span class="sxs-lookup"><span data-stu-id="e188d-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="e188d-107">Dönüş Değerleri</span><span class="sxs-lookup"><span data-stu-id="e188d-107">Return Values</span></span>  
  
|<span data-ttu-id="e188d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e188d-108">HRESULT</span></span>|<span data-ttu-id="e188d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e188d-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e188d-110">İşlev başarıyla işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="e188d-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="e188d-111">Hata ayıklaması yapılamıyor çünkü işlev kullanıcı kodu olarak işaretlenemez.</span><span class="sxs-lookup"><span data-stu-id="e188d-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e188d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e188d-112">Remarks</span></span>  
 <span data-ttu-id="e188d-113">Sadece kendi kodumu Adımlayıcı kullanıcı olmayan kod atlar.</span><span class="sxs-lookup"><span data-stu-id="e188d-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="e188d-114">Kullanıcı kodu bir alt kümesini debuggable kodu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e188d-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e188d-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e188d-115">Requirements</span></span>  
 <span data-ttu-id="e188d-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e188d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e188d-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e188d-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e188d-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e188d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e188d-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e188d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
