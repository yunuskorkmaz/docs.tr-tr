---
title: ICorDebugFunction2::GetJMCStatus Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d23a0a489cfe13201b7798920feb3528db3b0709
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494616"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="af021-102">ICorDebugFunction2::GetJMCStatus Metodu</span><span class="sxs-lookup"><span data-stu-id="af021-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="af021-103">Bu Icordebugfunction2 nesnesi tarafından temsil edilen işlevi kullanıcı kodu işaretlenmiş olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="af021-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af021-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af021-104">Syntax</span></span>  
  
```  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af021-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af021-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="af021-106">[out] Boolean bir değer için bir işaretçi `true`, bu işlev, kullanıcı kodu işaretlenmiş; Aksi takdirde, değeri `false`.</span><span class="sxs-lookup"><span data-stu-id="af021-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af021-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af021-107">Remarks</span></span>  
 <span data-ttu-id="af021-108">İşlev bu tarafından temsil edilen varsa `ICorDebugFunction2` ayıklanamıyor, `pbIsJustMyCode` her zaman `false`.</span><span class="sxs-lookup"><span data-stu-id="af021-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af021-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af021-109">Requirements</span></span>  
 <span data-ttu-id="af021-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af021-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af021-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af021-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af021-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af021-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af021-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af021-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
