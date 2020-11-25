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
ms.openlocfilehash: 1e159cacd297d56d63e512643ec4d3fe0c3709c0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694408"
---
# <a name="icoreclrdebugtargetfreememory-method"></a><span data-ttu-id="c8654-102">ICoreClrDebugTarget::FreeMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8654-102">ICoreClrDebugTarget::FreeMemory Method</span></span>

<span data-ttu-id="c8654-103">[ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) ve [ıreclrdebugtarget:: enumçalışma](icoreclrdebugtarget-enumruntimes-method.md) yöntemleri tarafından ayrılan belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="c8654-103">Frees the memory allocated by the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) and [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8654-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c8654-104">Syntax</span></span>  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8654-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8654-105">Parameters</span></span>  

 `pMemory`  
 <span data-ttu-id="c8654-106">'ndaki [ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) veya [ıreclrdebugtarget:: enumbir](icoreclrdebugtarget-enumruntimes-method.md) yöntemi tarafından döndürülen diziye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c8654-106">[in] A pointer to the array that is returned by either the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) or the [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8654-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8654-107">Requirements</span></span>  

 <span data-ttu-id="c8654-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8654-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8654-109">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="c8654-109">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="c8654-110">**Kitaplık:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="c8654-110">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="c8654-111">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c8654-111">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8654-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8654-112">See also</span></span>

- [<span data-ttu-id="c8654-113">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8654-113">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
