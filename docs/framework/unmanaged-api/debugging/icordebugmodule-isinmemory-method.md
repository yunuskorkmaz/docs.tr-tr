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
ms.openlocfilehash: 637cac67e73d38aca0fdc5eaeae5405c4a859aa3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709823"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="a28bf-102">ICorDebugModule::IsInMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a28bf-102">ICorDebugModule::IsInMemory Method</span></span>

<span data-ttu-id="a28bf-103">Bu modülün yalnızca bellekte mevcut olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="a28bf-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a28bf-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a28bf-104">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a28bf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a28bf-105">Parameters</span></span>  

 `pInMemory`  
 <span data-ttu-id="a28bf-106">[out] `true` Bu modül yalnızca bellekte mevcutsa; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="a28bf-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a28bf-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a28bf-107">Remarks</span></span>  

 <span data-ttu-id="a28bf-108">Ortak dil çalışma zamanı (CLR), modüllerin ham akışlarının yüklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="a28bf-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="a28bf-109">Bu tür modüller *bellek içi modüller* olarak adlandırılır ve diskte bulunmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="a28bf-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a28bf-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a28bf-110">Requirements</span></span>  

 <span data-ttu-id="a28bf-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a28bf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a28bf-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a28bf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a28bf-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a28bf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a28bf-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a28bf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a28bf-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a28bf-115">See also</span></span>
