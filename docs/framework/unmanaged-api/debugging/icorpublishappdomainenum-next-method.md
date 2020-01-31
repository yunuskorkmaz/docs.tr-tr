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
ms.openlocfilehash: c8866e98be0dd064138acdf5e0f6fb9c339fb3d2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790642"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="c59b1-102">ICorPublishAppDomainEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c59b1-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="c59b1-103">Geçerli konumdan başlayarak, işlemde mevcut olan uygulama etki alanı sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c59b1-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c59b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c59b1-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c59b1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c59b1-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c59b1-106">'ndaki Alınacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="c59b1-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="c59b1-107">dışı Her biri bir uygulama etki alanını temsil eden [ICorPublishAppDomain](icorpublishappdomain-interface.md) nesneleri dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c59b1-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c59b1-108">dışı Aslında döndürülen uygulama etki alanlarının sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c59b1-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="c59b1-109">`celt` bir tane ise bu değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="c59b1-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c59b1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c59b1-110">Requirements</span></span>  
 <span data-ttu-id="c59b1-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c59b1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c59b1-112">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="c59b1-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c59b1-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c59b1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c59b1-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c59b1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c59b1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c59b1-115">See also</span></span>

- [<span data-ttu-id="c59b1-116">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c59b1-116">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)
