---
title: ICorDebugModule::IsInMemory Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d79a8b0c3c56ffe2b8f57ec26f5942ee0d681194
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187596"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="d8ecf-102">ICorDebugModule::IsInMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8ecf-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="d8ecf-103">Bu modül yalnızca bellekte var olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d8ecf-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8ecf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8ecf-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8ecf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8ecf-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="d8ecf-106">[out] `true` varsa bu modül bellekte yalnızca; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="d8ecf-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8ecf-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8ecf-107">Remarks</span></span>  
 <span data-ttu-id="d8ecf-108">Ortak dil çalışma zamanı (CLR), ham bayt akışlarında modüllerden yüklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="d8ecf-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="d8ecf-109">Bu modül çağrılır *bellek içi modülleri* ve disk üzerinde mevcut değildir.</span><span class="sxs-lookup"><span data-stu-id="d8ecf-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ecf-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8ecf-110">Requirements</span></span>  
 <span data-ttu-id="d8ecf-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ecf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ecf-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8ecf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8ecf-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8ecf-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d8ecf-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d8ecf-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d8ecf-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8ecf-115">See also</span></span>
