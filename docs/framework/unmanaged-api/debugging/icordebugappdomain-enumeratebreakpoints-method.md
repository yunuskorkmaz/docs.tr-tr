---
title: "ICorDebugAppDomain::EnumerateBreakpoints Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAppDomain.EnumerateBreakpoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints method [.NET Framework debugging]
- EnumerateBreakpoints method [.NET Framework debugging]
ms.assetid: 206069c5-25cb-4794-9d69-67c5aa7ed0af
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2363b3159bef4453eb3eeb910d3d304806c56e6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="0bc3e-102">ICorDebugAppDomain::EnumerateBreakpoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0bc3e-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="0bc3e-103">Bir numaralandırıcı uygulama etki alanı için tüm etkin kesme noktalarını alır.</span><span class="sxs-lookup"><span data-stu-id="0bc3e-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bc3e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0bc3e-104">Syntax</span></span>  
  
```  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0bc3e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0bc3e-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="0bc3e-106">[out] Uygulama etki alanındaki tüm etkin kesme noktaları için Numaralandırıcı bir Icordebugbreakpointenum nesne adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0bc3e-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bc3e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0bc3e-107">Remarks</span></span>  
 <span data-ttu-id="0bc3e-108">Numaralayıcı kesme noktaları işlevi kesme noktaları ve veri kesme noktaları da dahil olmak üzere, tüm türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0bc3e-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bc3e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0bc3e-109">Requirements</span></span>  
 <span data-ttu-id="0bc3e-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bc3e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bc3e-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0bc3e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bc3e-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bc3e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bc3e-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bc3e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
