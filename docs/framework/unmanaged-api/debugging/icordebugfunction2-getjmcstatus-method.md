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
ms.openlocfilehash: ed2364c7c47aed1430a86aeee3daabf6b94cbf3b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754483"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="518f1-102">ICorDebugFunction2::GetJMCStatus Metodu</span><span class="sxs-lookup"><span data-stu-id="518f1-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="518f1-103">Bu Icordebugfunction2 nesnesi tarafından temsil edilen işlevi kullanıcı kodu işaretlenmiş olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="518f1-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="518f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="518f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="518f1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="518f1-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="518f1-106">[out] Boolean bir değer için bir işaretçi `true`, bu işlev, kullanıcı kodu işaretlenmiş; Aksi takdirde, değeri `false`.</span><span class="sxs-lookup"><span data-stu-id="518f1-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="518f1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="518f1-107">Remarks</span></span>  
 <span data-ttu-id="518f1-108">İşlev bu tarafından temsil edilen varsa `ICorDebugFunction2` ayıklanamıyor, `pbIsJustMyCode` her zaman `false`.</span><span class="sxs-lookup"><span data-stu-id="518f1-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="518f1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="518f1-109">Requirements</span></span>  
 <span data-ttu-id="518f1-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="518f1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="518f1-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="518f1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="518f1-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="518f1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="518f1-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="518f1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
