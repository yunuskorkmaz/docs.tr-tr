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
ms.openlocfilehash: 9ae5c16f9f508511e4a15b2eae2c28d68238f1d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415899"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="cb813-102">ICorDebugModule::IsInMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb813-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="cb813-103">Bu modül yalnızca bellekte var olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="cb813-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb813-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb813-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb813-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb813-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="cb813-106">[out] `true` bellek; yalnızca bu modül varsa, aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="cb813-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb813-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb813-107">Remarks</span></span>  
 <span data-ttu-id="cb813-108">Ortak dil çalışma zamanı (CLR) ham bayt akışları modüllerden yüklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="cb813-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="cb813-109">Bu tür modülleri adlı *bellek içi modülleri* ve disk üzerinde mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="cb813-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb813-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb813-110">Requirements</span></span>  
 <span data-ttu-id="cb813-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb813-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb813-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb813-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb813-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb813-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb813-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb813-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb813-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb813-115">See Also</span></span>  
    
 
