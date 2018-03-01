---
title: "ICorDebugModule::IsInMemory Yöntemi"
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
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 448458874c4de96503261bc0fe34fae160395c49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="c2b07-102">ICorDebugModule::IsInMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2b07-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="c2b07-103">Bu modül yalnızca bellekte var olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="c2b07-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2b07-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2b07-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2b07-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2b07-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="c2b07-106">[out] `true` bellek; yalnızca bu modül varsa, aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="c2b07-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2b07-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2b07-107">Remarks</span></span>  
 <span data-ttu-id="c2b07-108">Ortak dil çalışma zamanı (CLR) ham bayt akışları modüllerden yüklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="c2b07-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="c2b07-109">Bu tür modülleri adlı *bellek içi modülleri* ve disk üzerinde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="c2b07-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2b07-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2b07-110">Requirements</span></span>  
 <span data-ttu-id="c2b07-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2b07-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2b07-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2b07-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2b07-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2b07-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2b07-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2b07-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2b07-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2b07-115">See Also</span></span>  
    
 
