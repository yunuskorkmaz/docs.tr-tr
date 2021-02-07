---
description: ': IAssemblyCacheItem:: COMMIT yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: bd73bb9099090089e52d52009cfef309b33adc53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760866"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="5faa1-103">IAssemblyCacheItem::Commit Metodu</span><span class="sxs-lookup"><span data-stu-id="5faa1-103">IAssemblyCacheItem::Commit Method</span></span>

<span data-ttu-id="5faa1-104">Önbelleğe alınmış derleme başvurusunu belleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5faa1-104">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5faa1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5faa1-105">Syntax</span></span>  
  
```cpp  
HRESULT Commit (  
    [in] DWORD dwFlags,
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5faa1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5faa1-106">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="5faa1-107">'ndaki Fusion. IDL içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="5faa1-107">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="5faa1-108">[Out, isteğe bağlı] İşlemin sonucunu gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="5faa1-108">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5faa1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5faa1-109">Requirements</span></span>  

 <span data-ttu-id="5faa1-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5faa1-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5faa1-111">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="5faa1-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5faa1-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5faa1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5faa1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5faa1-113">See also</span></span>

- [<span data-ttu-id="5faa1-114">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5faa1-114">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
