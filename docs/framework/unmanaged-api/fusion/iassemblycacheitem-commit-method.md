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
ms.openlocfilehash: 2b7c10e82aca2b2ece7ea4d7209c1f3c9a456434
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670413"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="a562a-102">IAssemblyCacheItem::Commit Metodu</span><span class="sxs-lookup"><span data-stu-id="a562a-102">IAssemblyCacheItem::Commit Method</span></span>

<span data-ttu-id="a562a-103">Önbelleğe alınmış derleme başvurusunu belleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a562a-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a562a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a562a-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit (  
    [in] DWORD dwFlags,
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a562a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a562a-105">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="a562a-106">'ndaki Fusion. IDL içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="a562a-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="a562a-107">[Out, isteğe bağlı] İşlemin sonucunu gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="a562a-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a562a-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a562a-108">Requirements</span></span>  

 <span data-ttu-id="a562a-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a562a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a562a-110">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a562a-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a562a-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a562a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a562a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a562a-112">See also</span></span>

- [<span data-ttu-id="a562a-113">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a562a-113">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
