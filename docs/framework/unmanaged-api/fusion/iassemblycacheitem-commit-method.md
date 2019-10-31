---
title: IAssemblyCacheItem::Commit Metodu
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.Commit
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::Commit
helpviewer_keywords:
- IAssemblyCacheItem::Commit method [.NET Framework fusion]
- Commit method, IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: c2321f17-f46f-4815-ae41-b28678753613
topic_type:
- apiref
ms.openlocfilehash: 5de522c00da76e7c01369c706cb7f9e2bdad4b3b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134510"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="1f86a-102">IAssemblyCacheItem::Commit Metodu</span><span class="sxs-lookup"><span data-stu-id="1f86a-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="1f86a-103">Önbelleğe alınmış derleme başvurusunu belleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1f86a-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f86a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f86a-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f86a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f86a-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="1f86a-106">'ndaki Fusion. IDL içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="1f86a-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="1f86a-107">[Out, isteğe bağlı] İşlemin sonucunu gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="1f86a-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f86a-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f86a-108">Requirements</span></span>  
 <span data-ttu-id="1f86a-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f86a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f86a-110">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="1f86a-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1f86a-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f86a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f86a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f86a-112">See also</span></span>

- [<span data-ttu-id="1f86a-113">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f86a-113">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
