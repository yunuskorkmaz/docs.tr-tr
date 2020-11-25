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
ms.openlocfilehash: 00aff9ab4edbbebe4b924d335fa12f92e9840737
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693703"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="eb2de-102">ICorPublishAppDomainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb2de-102">ICorPublishAppDomainEnum::Next Method</span></span>

<span data-ttu-id="eb2de-103">Geçerli konumdan başlayarak, işlemde mevcut olan uygulama etki alanı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="eb2de-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb2de-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="eb2de-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb2de-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb2de-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="eb2de-106">'ndaki Alınacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="eb2de-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="eb2de-107">dışı Her biri bir uygulama etki alanını temsil eden [ICorPublishAppDomain](icorpublishappdomain-interface.md) nesneleri dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eb2de-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="eb2de-108">dışı Aslında döndürülen uygulama etki alanlarının sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eb2de-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="eb2de-109">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="eb2de-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb2de-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb2de-110">Requirements</span></span>  

 <span data-ttu-id="eb2de-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb2de-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb2de-112">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="eb2de-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="eb2de-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="eb2de-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb2de-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb2de-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2de-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb2de-115">See also</span></span>

- [<span data-ttu-id="eb2de-116">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb2de-116">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
