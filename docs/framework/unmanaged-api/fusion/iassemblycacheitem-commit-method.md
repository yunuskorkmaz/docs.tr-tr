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
ms.openlocfilehash: f840438e175790a2b4c97302963b910f98dffb7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176571"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="ff584-102">IAssemblyCacheItem::Commit Metodu</span><span class="sxs-lookup"><span data-stu-id="ff584-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="ff584-103">Önbelleğe alınmış derleme başvuruyu belleğe adazıyor.</span><span class="sxs-lookup"><span data-stu-id="ff584-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff584-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff584-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit (  
    [in] DWORD dwFlags,
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff584-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff584-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="ff584-106">[içinde] Fusion.idl'de tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="ff584-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="ff584-107">[çıkış, isteğe bağlı] İşlemin sonucunu gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="ff584-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff584-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff584-108">Requirements</span></span>  
 <span data-ttu-id="ff584-109">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff584-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff584-110">**Üstbilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ff584-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ff584-111">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff584-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff584-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff584-112">See also</span></span>

- [<span data-ttu-id="ff584-113">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff584-113">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
