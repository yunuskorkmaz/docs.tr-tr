---
title: ICoreClrDebugTarget::FreeMemory Yöntemi
ms.date: 03/30/2017
api_name:
- ICoreDebugTarget.FreeMemory
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a3448512cb486419e524df012fcd1b8fcf639f1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466381"
---
# <a name="icoreclrdebugtargetfreememory-method"></a><span data-ttu-id="c2b41-102">ICoreClrDebugTarget::FreeMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2b41-102">ICoreClrDebugTarget::FreeMemory Method</span></span>
<span data-ttu-id="c2b41-103">Tarafından ayrılan bellek serbest bırakma [Icoreclrdebugtarget::enumprocesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) ve [Icoreclrdebugtarget::enumruntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="c2b41-103">Frees the memory allocated by the [ICoreClrDebugTarget::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) and [ICoreClrDebugTarget::EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2b41-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2b41-104">Syntax</span></span>  
  
```  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2b41-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2b41-105">Parameters</span></span>  
 `pMemory`  
 <span data-ttu-id="c2b41-106">[in] Tarafından döndürülen dizisine bir işaretçi [Icoreclrdebugtarget::enumprocesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) veya [Icoreclrdebugtarget::enumruntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2b41-106">[in] A pointer to the array that is returned by either the [ICoreClrDebugTarget::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) or the [ICoreClrDebugTarget::EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2b41-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2b41-107">Requirements</span></span>  
 <span data-ttu-id="c2b41-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2b41-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2b41-109">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="c2b41-109">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="c2b41-110">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="c2b41-110">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="c2b41-111">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="c2b41-111">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2b41-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2b41-112">See also</span></span>
- [<span data-ttu-id="c2b41-113">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c2b41-113">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
