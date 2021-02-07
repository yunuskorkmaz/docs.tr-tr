---
description: 'Şu konuda daha fazla bilgi edinin: ICOR, Geval:: IsActive yöntemi'
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
ms.openlocfilehash: 2314814f8979f460063017ebdf46beb512417395
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694064"
---
# <a name="icordebugevalisactive-method"></a><span data-ttu-id="f6cc3-103">ICorDebugEval::IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6cc3-103">ICorDebugEval::IsActive Method</span></span>

<span data-ttu-id="f6cc3-104">Bu ıcorınkıt Geval nesnesinin Şu anda çalışıp çalışmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f6cc3-104">Gets a value that indicates whether this ICorDebugEval object is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6cc3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6cc3-105">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6cc3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f6cc3-106">Parameters</span></span>  

 `pbActive`  
 <span data-ttu-id="f6cc3-107">dışı Bu değerlendirmenin etkin olup olmadığını gösteren bir değere yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f6cc3-107">[out] Pointer to a value that indicates whether this evaluation is active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6cc3-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6cc3-108">Requirements</span></span>  

 <span data-ttu-id="f6cc3-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6cc3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6cc3-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f6cc3-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6cc3-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f6cc3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6cc3-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6cc3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
