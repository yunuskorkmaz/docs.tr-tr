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
ms.openlocfilehash: 360434fe6e08804d8c80c4ea36d585209cc6761a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137814"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="aefae-102">ICorDebugFunction2::GetJMCStatus Metodu</span><span class="sxs-lookup"><span data-stu-id="aefae-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="aefae-103">Bu ICorDebugFunction2 nesnesi tarafından temsil edilen işlevin Kullanıcı kodu olarak işaretlenip işaretlenmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="aefae-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aefae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aefae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aefae-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aefae-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="aefae-106">dışı Bu işlev kullanıcı kodu olarak işaretlenmişse `true`Boolean değere yönelik bir işaretçi; Aksi takdirde, değer `false`.</span><span class="sxs-lookup"><span data-stu-id="aefae-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aefae-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aefae-107">Remarks</span></span>  
 <span data-ttu-id="aefae-108">Bu `ICorDebugFunction2` tarafından temsil edilen işlevin ayıklanamayacağını belirlerseniz, `pbIsJustMyCode` her zaman `false`olur.</span><span class="sxs-lookup"><span data-stu-id="aefae-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aefae-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aefae-109">Requirements</span></span>  
 <span data-ttu-id="aefae-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aefae-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aefae-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aefae-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aefae-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="aefae-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aefae-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aefae-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
