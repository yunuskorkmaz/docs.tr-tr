---
title: ICorDebugEval::IsActive Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::IsActive method [.NET Framework debugging]
ms.assetid: bf2bba24-d278-43bd-b1c5-35680e748d3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d992ea86b3221af222bb01f1985fe277cea5a2c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480058"
---
# <a name="icordebugevalisactive-method"></a><span data-ttu-id="37f94-102">ICorDebugEval::IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37f94-102">ICorDebugEval::IsActive Method</span></span>
<span data-ttu-id="37f94-103">Bu Icordebugeval nesne yürütülmekte olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="37f94-103">Gets a value that indicates whether this ICorDebugEval object is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37f94-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37f94-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37f94-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="37f94-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="37f94-106">[out] Bu değerlendirme etkin olup olmadığını gösteren bir değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="37f94-106">[out] Pointer to a value that indicates whether this evaluation is active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37f94-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37f94-107">Requirements</span></span>  
 <span data-ttu-id="37f94-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37f94-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37f94-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37f94-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37f94-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37f94-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37f94-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37f94-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
