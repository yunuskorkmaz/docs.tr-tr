---
description: ': ICorPublishAppDomainEnum:: Next yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8e8255aa2326c6f0678132f5735d6cdf504dcbd0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721729"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="9164a-103">ICorPublishAppDomainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9164a-103">ICorPublishAppDomainEnum::Next Method</span></span>

<span data-ttu-id="9164a-104">Geçerli konumdan başlayarak, işlemde mevcut olan uygulama etki alanı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="9164a-104">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9164a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9164a-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9164a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9164a-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="9164a-107">'ndaki Alınacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="9164a-107">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="9164a-108">dışı Her biri bir uygulama etki alanını temsil eden [ICorPublishAppDomain](icorpublishappdomain-interface.md) nesneleri dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9164a-108">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9164a-109">dışı Aslında döndürülen uygulama etki alanlarının sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9164a-109">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="9164a-110">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="9164a-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9164a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9164a-111">Requirements</span></span>  

 <span data-ttu-id="9164a-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9164a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9164a-113">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="9164a-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9164a-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9164a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9164a-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9164a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9164a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9164a-116">See also</span></span>

- [<span data-ttu-id="9164a-117">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9164a-117">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
