---
title: ICorPublishAppDomainEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type:
- apiref
ms.openlocfilehash: 0553d8b07e3a16dc31474b5470ba2dd8ba365cb2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140507"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="3f793-102">ICorPublishAppDomainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f793-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="3f793-103">Geçerli konumdan başlayarak, işlemde mevcut olan uygulama etki alanı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="3f793-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f793-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f793-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f793-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f793-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3f793-106">'ndaki Alınacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="3f793-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="3f793-107">dışı Her biri bir uygulama etki alanını temsil eden [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) nesneleri dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f793-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3f793-108">dışı Aslında döndürülen uygulama etki alanlarının sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f793-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="3f793-109">`celt` bir tane ise bu değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f793-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f793-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f793-110">Requirements</span></span>  
 <span data-ttu-id="3f793-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f793-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f793-112">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="3f793-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3f793-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3f793-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f793-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f793-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f793-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f793-115">See also</span></span>

- [<span data-ttu-id="3f793-116">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f793-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
