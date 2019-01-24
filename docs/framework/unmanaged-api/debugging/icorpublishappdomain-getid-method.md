---
title: ICorPublishAppDomain::GetID Metodu
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
ms.openlocfilehash: 8a18e079f84d8adf2cc6f9bd22b35eb1445eaaf3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585022"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="ec655-102">ICorPublishAppDomain::GetID Metodu</span><span class="sxs-lookup"><span data-stu-id="ec655-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="ec655-103">Bu benzersiz tanımlayıcısını alır [Icorpublishappdomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ec655-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec655-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec655-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ec655-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ec655-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="ec655-106">[out] Uygulama etki alanı tanımlayıcısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ec655-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec655-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec655-107">Remarks</span></span>  
 <span data-ttu-id="ec655-108">Yalnızca içeren işlem kapsamında benzersiz tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="ec655-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec655-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ec655-109">Requirements</span></span>  
 <span data-ttu-id="ec655-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec655-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec655-111">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="ec655-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ec655-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec655-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec655-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec655-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec655-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec655-114">See also</span></span>
- [<span data-ttu-id="ec655-115">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ec655-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
