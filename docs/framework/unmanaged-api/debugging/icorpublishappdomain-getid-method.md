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
ms.openlocfilehash: 8d6e130981693268ae5c2cd615036b84ca8ed2d8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790692"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="ccb58-102">ICorPublishAppDomain::GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ccb58-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="ccb58-103">Bu [ICorPublishAppDomain](icorpublishappdomain-interface.md)için benzersiz tanımlayıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="ccb58-103">Gets the unique identifier for this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccb58-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccb58-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccb58-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ccb58-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="ccb58-106">dışı Uygulama etki alanının tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ccb58-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccb58-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ccb58-107">Remarks</span></span>  
 <span data-ttu-id="ccb58-108">Tanımlayıcı yalnızca kapsayan işlemin kapsamında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="ccb58-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccb58-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ccb58-109">Requirements</span></span>  
 <span data-ttu-id="ccb58-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccb58-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccb58-111">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="ccb58-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ccb58-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ccb58-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccb58-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccb58-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb58-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccb58-114">See also</span></span>

- [<span data-ttu-id="ccb58-115">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ccb58-115">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
