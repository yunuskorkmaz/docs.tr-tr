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
ms.openlocfilehash: f7bfdcc3c8328d71146732fc4ba5664ebee9bea2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574878"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="d7748-102">ICorDebugModule::IsInMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7748-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="d7748-103">Bu modül yalnızca bellekte var olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d7748-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7748-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7748-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7748-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d7748-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="d7748-106">[out] `true` varsa bu modül bellekte yalnızca; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="d7748-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7748-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7748-107">Remarks</span></span>  
 <span data-ttu-id="d7748-108">Ortak dil çalışma zamanı (CLR), ham bayt akışlarında modüllerden yüklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="d7748-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="d7748-109">Bu modül çağrılır *bellek içi modülleri* ve disk üzerinde mevcut değildir.</span><span class="sxs-lookup"><span data-stu-id="d7748-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7748-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7748-110">Requirements</span></span>  
 <span data-ttu-id="d7748-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7748-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7748-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7748-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7748-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7748-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7748-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7748-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7748-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7748-115">See also</span></span>


