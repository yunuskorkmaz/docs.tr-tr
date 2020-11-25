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
ms.openlocfilehash: ab331145a8147e8830cb9b158a1975bc748c7cce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716869"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="38abb-102">ICorPublishAppDomain::GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38abb-102">ICorPublishAppDomain::GetID Method</span></span>

<span data-ttu-id="38abb-103">Bu [ICorPublishAppDomain](icorpublishappdomain-interface.md)için benzersiz tanımlayıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="38abb-103">Gets the unique identifier for this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38abb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="38abb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38abb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38abb-105">Parameters</span></span>  

 `puId`  
 <span data-ttu-id="38abb-106">dışı Uygulama etki alanının tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="38abb-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38abb-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38abb-107">Remarks</span></span>  

 <span data-ttu-id="38abb-108">Tanımlayıcı yalnızca kapsayan işlemin kapsamında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="38abb-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38abb-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38abb-109">Requirements</span></span>  

 <span data-ttu-id="38abb-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38abb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38abb-111">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="38abb-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="38abb-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="38abb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38abb-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38abb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38abb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38abb-114">See also</span></span>

- [<span data-ttu-id="38abb-115">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38abb-115">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
