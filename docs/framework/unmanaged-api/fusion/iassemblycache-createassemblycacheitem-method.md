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
ms.openlocfilehash: e3e50538bde8fe3509b49e3dbcb031875e6863e5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127113"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="d9128-102">IAssemblyCache::CreateAssemblyCacheItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9128-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="d9128-103">Yeni bir [IAssemblyCacheItem](iassemblycacheitem-interface.md) nesnesine bir başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="d9128-103">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9128-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9128-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9128-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9128-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="d9128-106">'ndaki Fusion. IDL içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="d9128-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="d9128-107">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="d9128-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="d9128-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="d9128-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="d9128-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="d9128-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="d9128-110">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d9128-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d9128-111">`pvReserved`, null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9128-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="d9128-112">dışı Döndürülen `IAssemblyCacheItem` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d9128-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="d9128-113">[ın, isteğe bağlı] Uncanonicalized, virgülle ayrılmış `name=value` çiftleri.</span><span class="sxs-lookup"><span data-stu-id="d9128-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9128-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9128-114">Requirements</span></span>  
 <span data-ttu-id="d9128-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9128-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9128-116">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="d9128-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d9128-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9128-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9128-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9128-118">See also</span></span>

- [<span data-ttu-id="d9128-119">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9128-119">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="d9128-120">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9128-120">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
