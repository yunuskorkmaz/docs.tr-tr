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
ms.openlocfilehash: bd10af53d7803964ed6e699ce5328aa8a860216c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085014"
---
# <a name="icordebugevalisactive-method"></a><span data-ttu-id="ed3a7-102">ICorDebugEval::IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed3a7-102">ICorDebugEval::IsActive Method</span></span>
<span data-ttu-id="ed3a7-103">Bu ıcorınkıt Geval nesnesinin Şu anda çalışıp çalışmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="ed3a7-103">Gets a value that indicates whether this ICorDebugEval object is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed3a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed3a7-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed3a7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed3a7-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="ed3a7-106">dışı Bu değerlendirmenin etkin olup olmadığını gösteren bir değere yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ed3a7-106">[out] Pointer to a value that indicates whether this evaluation is active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed3a7-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed3a7-107">Requirements</span></span>  
 <span data-ttu-id="ed3a7-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed3a7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed3a7-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ed3a7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed3a7-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ed3a7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed3a7-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed3a7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
