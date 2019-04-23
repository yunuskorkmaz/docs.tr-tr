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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3757eee4c013ccf4f0f6d21ef64a92a5ffd70f19
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074319"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="054cc-102">IAssemblyCacheItem::Commit Metodu</span><span class="sxs-lookup"><span data-stu-id="054cc-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="054cc-103">Bellek için önbelleğe alınan derleme başvurusu kaydeder.</span><span class="sxs-lookup"><span data-stu-id="054cc-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="054cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="054cc-104">Syntax</span></span>  
  
```  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="054cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="054cc-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="054cc-106">[in] Fusion.idl içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="054cc-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="054cc-107">[out, isteğe bağlı] İşlemin sonucunu gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="054cc-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="054cc-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="054cc-108">Requirements</span></span>  
 <span data-ttu-id="054cc-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="054cc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="054cc-110">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="054cc-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="054cc-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="054cc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="054cc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="054cc-112">See also</span></span>

- [<span data-ttu-id="054cc-113">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="054cc-113">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
