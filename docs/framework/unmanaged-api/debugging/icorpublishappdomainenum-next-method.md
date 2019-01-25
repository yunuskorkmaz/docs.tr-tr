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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1492c9eac9d647c2b71c47cf758265152783d991
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54673889"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="f203c-102">ICorPublishAppDomainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f203c-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="f203c-103">İşleminde, geçerli konumdan başlayarak belirtilen sayıda şu anda mevcut uygulama etki alanları alır.</span><span class="sxs-lookup"><span data-stu-id="f203c-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f203c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f203c-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f203c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f203c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f203c-106">[in] Alınacak öğelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="f203c-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="f203c-107">[out] Bir işaretçi dizisinin işaretçisi alınan [Icorpublishappdomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) her biri bir uygulama etki alanı temsil eden nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f203c-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f203c-108">[out] Gerçekte döndürülen uygulama etki alanı sayısı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f203c-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="f203c-109">Bu değer null olabilir, `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="f203c-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f203c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f203c-110">Requirements</span></span>  
 <span data-ttu-id="f203c-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f203c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f203c-112">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f203c-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f203c-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f203c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f203c-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f203c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f203c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f203c-115">See also</span></span>
- [<span data-ttu-id="f203c-116">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f203c-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
