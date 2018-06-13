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
ms.openlocfilehash: ac3c6698e4ca127257b7682f1f55acd663375280
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423734"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="e02e2-102">ICorPublishAppDomainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e02e2-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="e02e2-103">Geçerli konumdan başlayarak işleminde, şu anda mevcut uygulama etki alanları belirtilen sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="e02e2-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e02e2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e02e2-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e02e2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e02e2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e02e2-106">[in] Alınacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="e02e2-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="e02e2-107">[out] Dizi için bir işaretçi alınan [Icorpublishappdomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) nesneleri, her biri uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e02e2-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="e02e2-108">[out] Uygulama etki alanları sayısı işaretçisine gerçekte döndürdü.</span><span class="sxs-lookup"><span data-stu-id="e02e2-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="e02e2-109">Bu değer null ise `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="e02e2-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e02e2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e02e2-110">Requirements</span></span>  
 <span data-ttu-id="e02e2-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e02e2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e02e2-112">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="e02e2-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e02e2-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e02e2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e02e2-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e02e2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e02e2-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e02e2-115">See Also</span></span>  
 [<span data-ttu-id="e02e2-116">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e02e2-116">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)
