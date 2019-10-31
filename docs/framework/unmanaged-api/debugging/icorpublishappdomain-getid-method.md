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
ms.openlocfilehash: 33a72d9aea09f808d42d1a17a7ec5640d20d7c79
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140380"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="a3cb1-102">ICorPublishAppDomain::GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3cb1-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="a3cb1-103">Bu [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)için benzersiz tanımlayıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="a3cb1-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3cb1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3cb1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3cb1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3cb1-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="a3cb1-106">dışı Uygulama etki alanının tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a3cb1-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3cb1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3cb1-107">Remarks</span></span>  
 <span data-ttu-id="a3cb1-108">Tanımlayıcı yalnızca kapsayan işlemin kapsamında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="a3cb1-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3cb1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3cb1-109">Requirements</span></span>  
 <span data-ttu-id="a3cb1-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3cb1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3cb1-111">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="a3cb1-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a3cb1-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a3cb1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3cb1-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3cb1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3cb1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3cb1-114">See also</span></span>

- [<span data-ttu-id="a3cb1-115">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3cb1-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
