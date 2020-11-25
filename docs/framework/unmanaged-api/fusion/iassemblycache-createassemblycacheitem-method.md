---
title: IAssemblyCache::CreateAssemblyCacheItem Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
ms.openlocfilehash: b417377ea1d0746e563490d87cc9a988e857d943
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697046"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="ae5a1-102">IAssemblyCache::CreateAssemblyCacheItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae5a1-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>

<span data-ttu-id="ae5a1-103">Yeni bir [IAssemblyCacheItem](iassemblycacheitem-interface.md) nesnesine bir başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="ae5a1-103">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae5a1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ae5a1-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae5a1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae5a1-105">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="ae5a1-106">'ndaki Fusion. IDL içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="ae5a1-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="ae5a1-107">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="ae5a1-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="ae5a1-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="ae5a1-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="ae5a1-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="ae5a1-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="ae5a1-110">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ae5a1-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ae5a1-111">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ae5a1-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="ae5a1-112">dışı Döndürülen `IAssemblyCacheItem` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ae5a1-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="ae5a1-113">[ın, isteğe bağlı] Uncanonicalized, virgülle ayrılmış `name=value` çiftler.</span><span class="sxs-lookup"><span data-stu-id="ae5a1-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae5a1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae5a1-114">Requirements</span></span>  

 <span data-ttu-id="ae5a1-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae5a1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae5a1-116">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ae5a1-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ae5a1-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae5a1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae5a1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae5a1-118">See also</span></span>

- [<span data-ttu-id="ae5a1-119">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae5a1-119">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="ae5a1-120">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae5a1-120">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
