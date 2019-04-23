---
title: ICorPublishAppDomain::GetID Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a2038af5d6ef46ad7cc661603e99b2f3dd67a9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215930"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="3d9d3-102">ICorPublishAppDomain::GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d9d3-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="3d9d3-103">Bu benzersiz tanımlayıcısını alır [Icorpublishappdomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="3d9d3-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d9d3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d9d3-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d9d3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d9d3-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="3d9d3-106">[out] Uygulama etki alanı tanımlayıcısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3d9d3-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d9d3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d9d3-107">Remarks</span></span>  
 <span data-ttu-id="3d9d3-108">Yalnızca içeren işlem kapsamında benzersiz tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="3d9d3-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d9d3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d9d3-109">Requirements</span></span>  
 <span data-ttu-id="3d9d3-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d9d3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d9d3-111">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="3d9d3-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3d9d3-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d9d3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d9d3-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d9d3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d9d3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d9d3-114">See also</span></span>

- [<span data-ttu-id="3d9d3-115">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d9d3-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
