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
ms.openlocfilehash: 6f5cbb7c0b4e3ce6d66d30e812008fc3419d7d7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429098"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="2d440-102">IAssemblyCacheItem::Commit Metodu</span><span class="sxs-lookup"><span data-stu-id="2d440-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="2d440-103">Bellek için önbelleğe alınmış derleme başvurusu kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2d440-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d440-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d440-104">Syntax</span></span>  
  
```  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d440-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d440-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="2d440-106">[in] Fusion.idl içinde tanımlı bayrak.</span><span class="sxs-lookup"><span data-stu-id="2d440-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="2d440-107">[out, isteğe bağlı] İşlemin sonucunu gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="2d440-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d440-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d440-108">Requirements</span></span>  
 <span data-ttu-id="2d440-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d440-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d440-110">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2d440-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2d440-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d440-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d440-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d440-112">See Also</span></span>  
 [<span data-ttu-id="2d440-113">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d440-113">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
