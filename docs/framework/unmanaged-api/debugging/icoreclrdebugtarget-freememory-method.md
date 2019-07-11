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
ms.openlocfilehash: e0d61092621a55c49509c8c4e4c81f1d064e0fdb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774376"
---
# <a name="icoreclrdebugtargetfreememory-method"></a><span data-ttu-id="effbe-102">ICoreClrDebugTarget::FreeMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="effbe-102">ICoreClrDebugTarget::FreeMemory Method</span></span>
<span data-ttu-id="effbe-103">Tarafından ayrılan bellek serbest bırakma [Icoreclrdebugtarget::enumprocesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) ve [Icoreclrdebugtarget::enumruntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="effbe-103">Frees the memory allocated by the [ICoreClrDebugTarget::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) and [ICoreClrDebugTarget::EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="effbe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="effbe-104">Syntax</span></span>  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a><span data-ttu-id="effbe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="effbe-105">Parameters</span></span>  
 `pMemory`  
 <span data-ttu-id="effbe-106">[in] Tarafından döndürülen dizisine bir işaretçi [Icoreclrdebugtarget::enumprocesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) veya [Icoreclrdebugtarget::enumruntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="effbe-106">[in] A pointer to the array that is returned by either the [ICoreClrDebugTarget::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) or the [ICoreClrDebugTarget::EnumRuntimes](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="effbe-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="effbe-107">Requirements</span></span>  
 <span data-ttu-id="effbe-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="effbe-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="effbe-109">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="effbe-109">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="effbe-110">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="effbe-110">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="effbe-111">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="effbe-111">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="effbe-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="effbe-112">See also</span></span>

- [<span data-ttu-id="effbe-113">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="effbe-113">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
