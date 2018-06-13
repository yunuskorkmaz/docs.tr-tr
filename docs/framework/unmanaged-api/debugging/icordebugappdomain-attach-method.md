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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a290ca162e5ab71b4184d166bcd00f1d0217cb94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402502"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="010ea-102">ICorDebugAppDomain::Attach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="010ea-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="010ea-103">Hata ayıklayıcı uygulama etki alanına ekler.</span><span class="sxs-lookup"><span data-stu-id="010ea-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="010ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="010ea-104">Syntax</span></span>  
  
```  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="010ea-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="010ea-105">Remarks</span></span>  
 <span data-ttu-id="010ea-106">Hata ayıklayıcı olayları almaya ve uygulama etki alanı, hata ayıklamayı etkinleştirmek için uygulama etki bağlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="010ea-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="010ea-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="010ea-107">Requirements</span></span>  
 <span data-ttu-id="010ea-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="010ea-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="010ea-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="010ea-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="010ea-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="010ea-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="010ea-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="010ea-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
