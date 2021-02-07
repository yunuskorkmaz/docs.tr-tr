---
description: ': ICorPublishAppDomain:: GetID Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b3de19c053b5fcce2af5e0036ee6174b01700aac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721846"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="c695a-103">ICorPublishAppDomain::GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c695a-103">ICorPublishAppDomain::GetID Method</span></span>

<span data-ttu-id="c695a-104">Bu [ICorPublishAppDomain](icorpublishappdomain-interface.md)için benzersiz tanımlayıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="c695a-104">Gets the unique identifier for this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c695a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c695a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c695a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c695a-106">Parameters</span></span>  

 `puId`  
 <span data-ttu-id="c695a-107">dışı Uygulama etki alanının tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c695a-107">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c695a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c695a-108">Remarks</span></span>  

 <span data-ttu-id="c695a-109">Tanımlayıcı yalnızca kapsayan işlemin kapsamında benzersizdir.</span><span class="sxs-lookup"><span data-stu-id="c695a-109">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c695a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c695a-110">Requirements</span></span>  

 <span data-ttu-id="c695a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c695a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c695a-112">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="c695a-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c695a-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c695a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c695a-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c695a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c695a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c695a-115">See also</span></span>

- [<span data-ttu-id="c695a-116">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c695a-116">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
