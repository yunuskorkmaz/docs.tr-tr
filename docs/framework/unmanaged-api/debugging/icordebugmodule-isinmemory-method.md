---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugModule:: IsInMemory Yöntemi'
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
ms.openlocfilehash: 41454ede15e1d45775af8fb0ab7a6b571d9c0e41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660095"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="cb503-103">ICorDebugModule::IsInMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb503-103">ICorDebugModule::IsInMemory Method</span></span>

<span data-ttu-id="cb503-104">Bu modülün yalnızca bellekte mevcut olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="cb503-104">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb503-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb503-105">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb503-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb503-106">Parameters</span></span>  

 `pInMemory`  
 <span data-ttu-id="cb503-107">[out] `true` Bu modül yalnızca bellekte mevcutsa; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="cb503-107">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb503-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cb503-108">Remarks</span></span>  

 <span data-ttu-id="cb503-109">Ortak dil çalışma zamanı (CLR), modüllerin ham akışlarının yüklenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="cb503-109">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="cb503-110">Bu tür modüller *bellek içi modüller* olarak adlandırılır ve diskte bulunmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb503-110">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb503-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb503-111">Requirements</span></span>  

 <span data-ttu-id="cb503-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb503-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb503-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cb503-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb503-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cb503-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb503-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb503-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb503-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb503-116">See also</span></span>
