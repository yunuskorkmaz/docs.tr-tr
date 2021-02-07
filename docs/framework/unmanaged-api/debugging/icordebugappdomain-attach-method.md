---
description: ': ICorDebugAppDomain:: Attach yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 94448937a735b30d0403a207992dae29920a93bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754283"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="6b002-103">ICorDebugAppDomain::Attach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6b002-103">ICorDebugAppDomain::Attach Method</span></span>

<span data-ttu-id="6b002-104">Hata ayıklayıcıyı uygulama etki alanına iliştirir.</span><span class="sxs-lookup"><span data-stu-id="6b002-104">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b002-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6b002-105">Syntax</span></span>  
  
```cpp  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6b002-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6b002-106">Remarks</span></span>  

 <span data-ttu-id="6b002-107">Hata ayıklayıcı, olayları almak ve uygulama etki alanında hata ayıklamayı etkinleştirmek için uygulama etki alanına iliştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6b002-107">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b002-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b002-108">Requirements</span></span>  

 <span data-ttu-id="6b002-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b002-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b002-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6b002-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b002-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6b002-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b002-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b002-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
