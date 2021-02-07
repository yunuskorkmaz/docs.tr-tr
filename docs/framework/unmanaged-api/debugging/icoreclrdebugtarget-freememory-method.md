---
description: 'Şu konuda daha fazla bilgi edinin: ICoreClrDebugTarget:: FreeMemory yöntemi'
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
ms.openlocfilehash: 9572e0c3df1fdd064e78ba170d39c1415c68dc85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690008"
---
# <a name="icoreclrdebugtargetfreememory-method"></a><span data-ttu-id="a90e1-103">ICoreClrDebugTarget::FreeMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a90e1-103">ICoreClrDebugTarget::FreeMemory Method</span></span>

<span data-ttu-id="a90e1-104">[ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) ve [ıreclrdebugtarget:: enumçalışma](icoreclrdebugtarget-enumruntimes-method.md) yöntemleri tarafından ayrılan belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="a90e1-104">Frees the memory allocated by the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) and [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a90e1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a90e1-105">Syntax</span></span>  
  
```cpp  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a90e1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a90e1-106">Parameters</span></span>  

 `pMemory`  
 <span data-ttu-id="a90e1-107">'ndaki [ICoreClrDebugTarget:: EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) veya [ıreclrdebugtarget:: enumbir](icoreclrdebugtarget-enumruntimes-method.md) yöntemi tarafından döndürülen diziye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a90e1-107">[in] A pointer to the array that is returned by either the [ICoreClrDebugTarget::EnumProcesses](icoreclrdebugtarget-enumprocesses-method.md) or the [ICoreClrDebugTarget::EnumRuntimes](icoreclrdebugtarget-enumruntimes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a90e1-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a90e1-108">Requirements</span></span>  

 <span data-ttu-id="a90e1-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a90e1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a90e1-110">**Üst bilgi:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="a90e1-110">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="a90e1-111">**Kitaplık:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="a90e1-111">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="a90e1-112">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="a90e1-112">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a90e1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a90e1-113">See also</span></span>

- [<span data-ttu-id="a90e1-114">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a90e1-114">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
