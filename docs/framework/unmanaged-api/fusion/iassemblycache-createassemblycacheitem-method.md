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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 215eb3a508a746230d36fdda3e8ba992287be62c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796823"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="2b824-102">IAssemblyCache::CreateAssemblyCacheItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b824-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="2b824-103">Yeni bir [IAssemblyCacheItem](iassemblycacheitem-interface.md) nesnesine bir başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="2b824-103">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b824-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b824-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b824-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b824-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="2b824-106">'ndaki Fusion. IDL içinde tanımlanan bayraklar.</span><span class="sxs-lookup"><span data-stu-id="2b824-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="2b824-107">Aşağıdaki değerler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="2b824-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="2b824-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="2b824-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="2b824-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="2b824-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="2b824-110">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2b824-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="2b824-111">`pvReserved`null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b824-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="2b824-112">dışı Döndürülen `IAssemblyCacheItem` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2b824-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="2b824-113">[ın, isteğe bağlı] Uncanonicalized, virgülle ayrılmış `name=value` çiftler.</span><span class="sxs-lookup"><span data-stu-id="2b824-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b824-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b824-114">Requirements</span></span>  
 <span data-ttu-id="2b824-115">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b824-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b824-116">**Üst bilgi** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="2b824-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2b824-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b824-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b824-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b824-118">See also</span></span>

- [<span data-ttu-id="2b824-119">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b824-119">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="2b824-120">IAssemblyCacheItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b824-120">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
