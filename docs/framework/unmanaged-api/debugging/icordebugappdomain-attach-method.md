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
ms.openlocfilehash: 92cc6c3ce15d8391a43ff130a82476a4363ff5bd
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895309"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="f7663-102">ICorDebugAppDomain::Attach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7663-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="f7663-103">Hata ayıklayıcıyı uygulama etki alanına iliştirir.</span><span class="sxs-lookup"><span data-stu-id="f7663-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7663-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7663-104">Syntax</span></span>  
  
```cpp  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f7663-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7663-105">Remarks</span></span>  
 <span data-ttu-id="f7663-106">Hata ayıklayıcı, olayları almak ve uygulama etki alanında hata ayıklamayı etkinleştirmek için uygulama etki alanına iliştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="f7663-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7663-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7663-107">Requirements</span></span>  
 <span data-ttu-id="f7663-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7663-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7663-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f7663-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7663-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f7663-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7663-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7663-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
