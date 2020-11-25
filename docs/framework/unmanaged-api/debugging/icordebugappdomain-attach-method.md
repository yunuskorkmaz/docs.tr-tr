---
title: ICorDebugAppDomain::Attach Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.Attach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type:
- apiref
ms.openlocfilehash: d133cacb611a1c7bd03d7653f46c2e5fb1acc043
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723356"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="c0b64-102">ICorDebugAppDomain::Attach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0b64-102">ICorDebugAppDomain::Attach Method</span></span>

<span data-ttu-id="c0b64-103">Hata ayıklayıcıyı uygulama etki alanına iliştirir.</span><span class="sxs-lookup"><span data-stu-id="c0b64-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0b64-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c0b64-104">Syntax</span></span>  
  
```cpp  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c0b64-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0b64-105">Remarks</span></span>  

 <span data-ttu-id="c0b64-106">Hata ayıklayıcı, olayları almak ve uygulama etki alanında hata ayıklamayı etkinleştirmek için uygulama etki alanına iliştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c0b64-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0b64-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0b64-107">Requirements</span></span>  

 <span data-ttu-id="c0b64-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0b64-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0b64-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c0b64-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0b64-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c0b64-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0b64-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0b64-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
