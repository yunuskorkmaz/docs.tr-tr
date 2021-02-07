---
description: ': IAssemblyCache:: CreateAssemblyCacheItem yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3377901d358bcf643ce0d30336c1c0cd8089e50c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760985"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="c101e-103">IAssemblyCache::CreateAssemblyCacheItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c101e-103">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>

<span data-ttu-id="c101e-104">Yeni bir [IAssemblyCacheItem](iassemblycacheitem-interface.md) nesnesine bir başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="c101e-104">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c101e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c101e-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c101e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c101e-106">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="c101e-107">'ndaki Fusion. IDL içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="c101e-107">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="c101e-108">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="c101e-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="c101e-109">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="c101e-109">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="c101e-110">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="c101e-110">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="c101e-111">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c101e-111">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="c101e-112">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c101e-112">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="c101e-113">dışı Döndürülen `IAssemblyCacheItem` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c101e-113">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="c101e-114">[ın, isteğe bağlı] Uncanonicalized, virgülle ayrılmış `name=value` çiftler.</span><span class="sxs-lookup"><span data-stu-id="c101e-114">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c101e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c101e-115">Requirements</span></span>  

 <span data-ttu-id="c101e-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c101e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c101e-117">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c101e-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c101e-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c101e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c101e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c101e-119">See also</span></span>

- [<span data-ttu-id="c101e-120">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c101e-120">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="c101e-121">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c101e-121">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
